# Pangia App - Android Feasibility Analysis

Generated: 2026-04-06

## Executive Summary

An Android version of the Pangia app is **feasible but non-trivial**. The app is built with React Native / Expo, which inherently supports both platforms, and several foundational pieces (Firebase, UI components, navigation) are already cross-platform. However, the app's core value proposition — VoIP calling — relies heavily on three iOS-exclusive technologies: **PushKit**, **CallKit**, and a **custom Objective-C native module**. These require complete Android-specific reimplementation using `ConnectionService`, FCM high-priority messages, and a custom Android native module.

**Verdict:** Feasible. Estimated 9-13 weeks of engineering effort, with the VoIP/call subsystem being the critical path.

---

## What's Already Android-Ready

These components work cross-platform today with little to no changes:

| Component | Status | Notes |
|-----------|--------|-------|
| React Native / Expo SDK 54 | Ready | Framework supports Android natively |
| Firebase Auth | Ready | `@react-native-firebase/app` is cross-platform |
| Firebase Realtime Database | Ready | Cross-platform SDK |
| Firebase Cloud Messaging (FCM) | Ready | FCM is Google's platform — Android is primary target |
| `google-services.json` | Ready | Already present and configured for `com.pangia.app` |
| Android section in `app.json` | Ready | Package name, adaptive icon, permissions already defined |
| UI Screens & Components | Ready | Only minor `Platform.OS` keyboard behavior checks |
| React Navigation (tabs, stack) | Ready | Cross-platform |
| AsyncStorage | Ready | Cross-platform |
| SunCalc | Ready | Pure JavaScript, no native dependencies |
| Expo modules (location, notifications, clipboard, crypto, fonts) | Ready | All cross-platform |
| Theme system (light/dark) | Ready | Context-based, no native dependency |
| API service layer (`src/services/api.ts`) | Ready | Pure HTTP calls, fully cross-platform |

---

## What Needs to Change

### 1. VoIP Push Notifications (CRITICAL - Architecture Change)

**iOS (current):** Uses Apple PushKit (`PKPushRegistry`) via the custom `VoIPPushHandler` native module. PushKit provides a **guaranteed app wake-up** for incoming calls, even when the app is killed or the device is in low-power mode. This is a privileged iOS capability exclusive to VoIP apps.

**Android equivalent:** FCM high-priority data messages with a foreground service.

| Aspect | iOS (PushKit) | Android (FCM) |
|--------|--------------|---------------|
| Wake guarantee | Yes — OS always delivers | Conditional — Doze mode may delay |
| Background execution | Allowed for VoIP | Requires foreground service |
| Token type | Separate VoIP token | Same FCM token, differentiated by payload |
| System UI | Automatic via CallKit | Must use `ConnectionService` or custom notification |

**Work required:**
- Build an Android native module that listens for FCM data messages with a `call` type
- Launch a foreground service with an incoming-call notification
- Request battery optimization exemption (`REQUEST_IGNORE_BATTERY_OPTIMIZATIONS`)
- Backend must differentiate iOS VoIP push vs Android FCM high-priority push by device platform
- Implement `FirebaseMessagingService` override for background delivery

**Risk:** Android cannot guarantee 100% reliable call delivery like PushKit. Mitigations include high-priority FCM, foreground services, and battery optimization whitelisting, but some edge cases (aggressive OEM battery management on Xiaomi, Samsung, etc.) may still cause missed calls.

---

### 2. CallKit -> ConnectionService (CRITICAL - Major Rewrite)

**iOS (current):** `callKitHandler.ts` (656 lines) uses `react-native-callkeep` to integrate with iOS CallKit. This provides:
- Incoming call UI on lock screen and Dynamic Island
- Call history in the native Phone app
- Audio session management
- Call answering/ending from lock screen, headphones, CarPlay
- Mute/speaker controls in system UI

**Android equivalent:** `android.telecom.ConnectionService`

| Feature | iOS CallKit | Android ConnectionService |
|---------|------------|--------------------------|
| Lock screen call UI | Built-in | Must register as default phone app or use `ConnectionService` |
| Call history | Automatic | Must write to `CallLog` provider |
| Audio routing | Managed by CallKit | Manual via `AudioManager` |
| Dynamic Island | Supported | No equivalent (Android 14+ has notification-based approach) |
| CarPlay/Auto | Via CallKit | Via Android Auto SDK |
| Headphone controls | Via CallKit | Via `MediaSession` |

**Work required:**
- Create Android native module wrapping `ConnectionService`
- Register the service in `AndroidManifest.xml`
- Implement `Connection` class for each active call
- Handle `onAnswer()`, `onDisconnect()`, `onHold()`, `onPlayDtmfTone()`
- Bridge events to React Native JavaScript layer
- Rewrite `callKitHandler.ts` to use platform-appropriate module:
  ```typescript
  if (Platform.OS === 'ios') {
    // existing CallKit flow
  } else {
    // new ConnectionService flow
  }
  ```
- Alternative: `react-native-callkeep` does have partial Android support — evaluate if it's sufficient before building custom

**Note:** `react-native-callkeep` (v4.3.16) does include Android `ConnectionService` support. It may cover the basic use case, reducing the custom native work. This should be the **first thing evaluated** in a spike.

---

### 3. Custom VoIPPushHandler Native Module (CRITICAL - Must Build)

**iOS (current):** `plugins/withVoIPPushHandler.js` injects a custom Objective-C module (`VoIPPushHandler.m`, ~450 lines) that:
- Registers for PushKit VoIP tokens
- Receives VoIP push payloads and emits events to JS
- Deduplicates incoming calls (120-second window)
- Posts missed-call local notifications
- Reports calls to CallKit with UUID
- Provides debug state for the dev menu

**Android equivalent needed:** A custom Android native module (Kotlin/Java) that:
- Extends `FirebaseMessagingService` for background message handling
- Detects call-type payloads in FCM data messages
- Starts a foreground service with incoming-call notification (full-screen intent)
- Emits events to React Native JS layer (matching the iOS event names)
- Implements call deduplication logic
- Posts missed-call notifications
- Provides debug state
- Manages `ConnectionService` lifecycle

**Work required:**
- Write Kotlin module (~300-500 lines estimated)
- Create Expo config plugin to inject it into the Android build (similar pattern to iOS plugin)
- Wire up the same JS event interface so `callKitHandler.ts` can consume both

---

### 4. Telnyx SDK Android Support (MUST VERIFY)

**Package:** `@telnyx/react-native-voice-sdk@^0.3.0`

**Current usage:** Creates `TelnyxRTC` instance, connects to WebRTC server, handles call states, processes VoIP notifications, links CallKit UUIDs to SDK calls.

**Unknown:**
- Whether v0.3.0 has full Android support
- Whether `processTelnyxVoipNotification()` works on Android
- Whether `setPushNotificationCallKitUUID()` has an Android equivalent
- What Android-specific initialization is needed

**Action required:**
- Check Telnyx React Native SDK documentation and changelog
- Test basic call flow on Android emulator
- If unsupported, evaluate alternative WebRTC solutions or direct SIP integration

**This is the single biggest unknown and should be investigated first.**

---

### 5. Expo Config Plugins (Moderate)

| Plugin | iOS | Android | Work Needed |
|--------|-----|---------|-------------|
| `withVoIPPushHandler` | Injects Obj-C module | N/A | Write Android equivalent plugin |
| `withDarkSplash` | Splash colors + APNs entitlement | N/A | Add `values-night` theme resources |
| `withModularHeaders` | Podfile fix | N/A | Not needed (Android uses Gradle) |

---

### 6. Build & Deployment (Moderate)

**Current state:** iOS-only build scripts and EAS config.

**Work required:**

| Item | What to Do |
|------|-----------|
| `eas.json` | Add `production.android` with `image: "latest"` |
| Android keystore | Generate release signing keystore, configure in EAS or locally |
| `deploy-android.sh` | Script using `eas build --platform android` or local Gradle build |
| Play Store setup | Create app listing, configure internal testing track |
| `deploy-playstore.sh` | Script using `eas submit --platform android` or `bundletool` |
| Android permissions | Add `FOREGROUND_SERVICE`, `USE_FULL_SCREEN_INTENT`, `READ_PHONE_STATE` to `app.json` |

---

### 7. Backend Changes (Minor)

The backend (`Pangia-Pass-Backend-Live`) needs minor changes:

- **VoIP push routing:** When sending an incoming call notification, check device platform:
  - iOS → send via APNs VoIP push (PushKit)
  - Android → send via FCM high-priority data message
- **Token storage:** Store device platform alongside VoIP/FCM tokens
- **Push payload format:** May need different payload structure for Android FCM vs iOS PushKit

These are small changes (~1-2 days of backend work).

---

## Component-by-Component Risk Assessment

| Component | Effort | Risk | Notes |
|-----------|--------|------|-------|
| Telnyx SDK Android verification | 1 week | **HIGH** | Blocker if unsupported |
| Android native module (VoIP + ConnectionService) | 3-4 weeks | **HIGH** | Core complexity |
| `callKitHandler.ts` platform abstraction | 1-2 weeks | **MEDIUM** | Depends on `react-native-callkeep` Android quality |
| FCM call push handling | 1-2 weeks | **MEDIUM** | Doze mode / OEM battery management risks |
| Expo config plugins for Android | 1 week | **LOW** | Well-documented pattern |
| EAS / build / deployment setup | 1 week | **LOW** | Standard Expo workflow |
| Backend push routing | 2-3 days | **LOW** | Minor conditional logic |
| UI / screen adjustments | 2-3 days | **LOW** | Already mostly cross-platform |
| Device testing matrix | 1-2 weeks | **MEDIUM** | Android fragmentation (OEM skins, API levels) |

---

## Recommended Approach

### Phase 1: Spike & Validate (1-2 weeks)
1. **Verify Telnyx SDK Android support** — this is the go/no-go gate
2. **Test `react-native-callkeep` on Android** — evaluate if its `ConnectionService` support is sufficient
3. **Run `expo prebuild --platform android`** — verify the base app builds and launches
4. **Document gaps** — catalog exactly what fails or is missing

### Phase 2: Core Android Infrastructure (3-4 weeks)
1. Build Android native module for incoming call handling (FCM -> foreground service -> call UI)
2. Implement `ConnectionService` integration (or validate `react-native-callkeep` Android path)
3. Abstract `callKitHandler.ts` into platform-specific implementations
4. Set up Android build in EAS

### Phase 3: VoIP Push & Call Reliability (2-3 weeks)
1. Implement FCM high-priority data message handling for calls
2. Add battery optimization exemption flow
3. Backend: add platform-aware push routing
4. Test call reliability across Android versions (API 26+) and OEM skins
5. Implement missed-call notification fallback

### Phase 4: Polish & Release (2 weeks)
1. Device testing across form factors (phones, tablets)
2. OEM-specific testing (Samsung, Xiaomi, Pixel, OnePlus — battery management varies)
3. Play Store listing and internal testing track
4. Android deployment scripts
5. Documentation

### Total Estimate: 9-13 weeks

---

## Key Risks & Mitigations

| Risk | Impact | Likelihood | Mitigation |
|------|--------|-----------|------------|
| Telnyx SDK lacks Android support | Blocker | Medium | Evaluate alternatives: direct WebRTC, Location SIP client |
| Missed calls due to Doze mode | User experience | High | Battery optimization exemption, high-priority FCM, foreground service |
| OEM battery management kills app | User experience | High | Guide users to disable battery optimization; test on major OEMs |
| `react-native-callkeep` Android bugs | Delays | Medium | Be prepared to write custom ConnectionService module |
| Android fragmentation | Testing burden | Medium | Target API 26+ (Android 8.0+), test on 4-5 major OEMs |
| Audio routing differences | Call quality | Low | Test speaker/receiver/bluetooth switching thoroughly |

---

## Decision Points

1. **Telnyx SDK support** — If unsupported on Android, the project scope increases significantly (need alternative WebRTC/SIP solution). Investigate first.
2. **`react-native-callkeep` quality** — If its Android `ConnectionService` support is solid, saves 2-3 weeks. If not, plan for custom native module.
3. **Call reliability bar** — What's acceptable? iOS PushKit offers near-100% reliability. Android will be lower (~95-98% depending on device). Define requirements upfront.
4. **Target API level** — API 26 (Android 8.0) is the minimum for notification channels and `ConnectionService`. API 31+ (Android 12) changes foreground service restrictions. Recommend targeting API 26+ for maximum reach.
