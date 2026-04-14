# Daily Summary — 2026-04-14

**Period covered:** 2026-04-07 → 2026-04-14

---

## pangia-app (React Native Mobile)

### Work Done (Will Flowers, Frederik List)

**Voice/VoIP (Will):**
- Story 4-47: Capture inbound call CCID from push payload and backend lookup
- Story 4-48: Bridge CallKit audio session to WebRTC RTCAudioSession
- Story 4-49: Adaptive answer timeout for push-delivered calls
- Security: redact CCID from console.log, remove dead AbortController

**KYC/Telephony (Will):**
- Story 5-13: Country-specific KYC gating for number provisioning + dev tools override (TestFlight dev menu)

**UI/UX (Frederik):**
- Call history redesign: clean tab UI, voicemail tab, mock data fix
- Phone tab → call history landing, Manage Numbers screen with back button
- "Get a Number" prompt when user has no phone numbers
- Consistent ScreenHeader with profile button across all tab screens
- Skip onboarding screen, fix sun at low position, remove expo-glass-effect

### Open PRs — 17 total (5 human, 12 dependabot)

| # | Title | Author | Created |
|---|-------|--------|---------|
| 33 | UI fixes 2 | Will Flowers | Apr 13 |
| 28 | feat: restore branch work for crashlytics, posthog, pending stories | Will Flowers | Mar 31 |
| 23 | feat(19-2): UK porting status UX coherence | Will Flowers | Mar 20 |
| 17 | feat: multi-epic mobile delivery — KYC, porting, voice, messaging, design system | Will Flowers | Mar 11 |
| 15 | feat(kyc,fcm): stories 11-2, 11-8, 14-19 — Veriff SDK, KYC nav, FCM lifecycle | Will Flowers | Mar 6 |
| 32 | Bump lodash 4.17.23 → 4.18.1 in /functions | dependabot | Apr 10 |
| 31 | Bump fast-xml-parser 5.3.4 → 5.5.11 in /functions | dependabot | Apr 9 |
| 27 | Bump path-to-regexp 0.1.12 → 0.1.13 in /functions | dependabot | Mar 30 |
| 26 | Bump brace-expansion in /functions | dependabot | Mar 29 |
| 25 | Bump picomatch in /functions | dependabot | Mar 26 |
| 22 | Bump fast-xml-parser + @google-cloud/storage in /functions | dependabot | Mar 20 |
| 20 | Bump undici 6.23.0 → 6.24.1 | dependabot | Mar 14 |
| 18 | Bump tar 7.5.7 → 7.5.11 | dependabot | Mar 11 |
| 11 | Bump minimatch in /functions | dependabot | Mar 1 |
| 8 | Bump minimatch 3.1.2 → 3.1.4 | dependabot | Feb 25 |
| 7 | Bump ajv 8.17.1 → 8.18.0 | dependabot | Feb 20 |
| 4 | Bump qs 6.14.1 → 6.14.2 in /functions | dependabot | Feb 14 |

---

## pangia-pass (SvelteKit Web)

### Work Done (Matthew Kirkham)

- PostHog deep integration + Meta Conversions API (CAPI) setup (Apr 13)

### Open PRs — 10 total (5 human, 5 dependabot)

| # | Title | Author | Created |
|---|-------|--------|---------|
| 175 | PostHog deep integration + Meta CAPI | Matthew Kirkham | Apr 13 |
| 105 | Black Friday campaign details | Ahmad | Nov 2025 |
| 81 | Add UI to indicate which discount will be applied | Will Flowers | Sep 2025 |
| 77 | Blog | plitarko | Sep 2025 |
| 26 | Add frontend_url to frontend for some endpoints | Will Flowers | Jul 2025 |
| 9 | Bump @sveltejs/kit 2.5.18 → 2.8.3 | dependabot | Nov 2024 |
| 7 | Bump rollup 4.19.1 → 4.23.0 | dependabot | Oct 2024 |
| 6 | Bump vite 5.3.5 → 5.4.8 | dependabot | Oct 2024 |
| 2 | Bump micromatch 4.0.7 → 4.0.8 | dependabot | Sep 2024 |
| 1 | Bump svelte 4.2.18 → 4.2.19 | dependabot | Aug 2024 |

---

## Pangia-Pass-Backend-Live (Python Backend)

### Work Done

**Ahmad — Usage Dashboard & n8n Integration:**
- Story 76-1: Firebase user-created → n8n webhook relay (email/name to users_secure) — **done**
- Story 76-2: BICS location change → n8n webhook relay — **done**
- Story 77-2: Replace Holt-Winters forecast with QoQ weighted-avg model — **in review**
- Story 79-1: Docs viewer for internal dashboard + Stripe-Firebase data mapping — **in progress**
- Story 75-9-b: Affiliates/countries revenue parity hardening
- Fix: Skip email alert for non-numeric BICS volumeAccumulated values
- Expanded Stripe-Firebase data mapping doc with 21 missed fields + coupon_details keys
- Added markdown2 + pygments dependencies

**Raja (DrRaja82) — Supabase Migration (Epic 35):**
- Story 35a-9: Partnership tables — merged
- Story 35a-11: Event fact tables + record_event() service — merged (4 review cycles)
- Story 35a-12: RLS policies — merged (9 review cycles)
- Story 35a-13: Supabase Broadcast from Database realtime triggers — merged (4 review cycles)
- Sprint status cleanup (mojibake fix, UTF-8 docs)

**Will Flowers — Porting & KYC:**
- Story 5-15: Porting form cleanup + donor auto-provisioning (5 review cycles) — **in review**
- Story 5-14: CloudNumbering auto-submit porting — in progress
- Story 5-13: KYC country gating (backend merge to debug-crashlytics)
- CI/CD async integration merge

**Merged PRs (Apr 7-14):** #438, #447, #448, #449, #450, #451, #452, #453, #454, #455, #456, #457, #458, #459

### Open PRs — 36 total (32 human, 4 dependabot)

| # | Title | Author | Created |
|---|-------|--------|---------|
| 431 | Bump flask 3.0.3 → 3.1.3 in /app/utils/keepgo | dependabot | Mar 28 |
| 423 | Bump requests 2.32.3 → 2.33.0 in /app/utils/keepgo | dependabot | Mar 26 |
| 422 | Bump requests 2.32.3 → 2.33.0 | dependabot | Mar 26 |
| 415 | docs(epic-35): migration epics, sprint planning, research docs | Raja | Mar 22 |
| 394 | Story 14.12: Terraform Module Consolidation | Will Flowers | Feb 20 |
| 385 | Story 3.2: Telnyx Full Provider Adapter | Will Flowers | Feb 18 |
| 384 | Story 14.9: snake_case standardization + mobile handoff | Will Flowers | Feb 18 |
| 382 | Story 14-8: DI convention consolidation | Will Flowers | Feb 17 |
| 377 | fix(tests): align 37 test files | Will Flowers | Feb 16 |
| 376 | Telnyx full provider adapter | Raja | Feb 16 |
| 371 | epics-12-13 code review remediation + alerting/monitoring | Will Flowers | Feb 16 |
| 370 | Epic 3, 7, 8, 11 Implementation Sprint Batch | Will Flowers | Feb 15 |
| 369 | Epic 5: Number Porting System | Will Flowers | Feb 13 |
| 366 | Bump pillow 11.0.0 → 12.1.1 | dependabot | Feb 11 |
| 365 | Story 1.19: KMS envelope encryption for SMS body storage | Will Flowers | Feb 10 |
| 364 | Story 4.14: WebRTC credential endpoint | Will Flowers | Feb 10 |
| 363 | Story 4.13: VoIP push infrastructure | Will Flowers | Feb 9 |
| 360 | docs(story): Story 3.2 - Telnyx full provider adapter | Will Flowers | Feb 3 |
| 359 | Story 3.1: Provider-neutral infrastructure | Will Flowers | Feb 3 |
| 334 | Story 1.13: Rate Limiting & Abuse Prevention | Will Flowers | Jan 23 |
| 332 | Story 4.11: Telnyx Built-in Voicemail Support | Will Flowers | Jan 22 |
| 331 | Story 4.5: DTMF Input Handling for IVR Support | Will Flowers | Jan 22 |
| 330 | Story 4-4: Call Forwarding Configuration | Will Flowers | Jan 22 |
| 329 | Epic 4: Voice calling — SIP trunk, outbound/inbound | Will Flowers | Jan 22 |
| 311 | Firebase security rules + API bug fixes | Will Flowers | Jan 12 |
| 299 | Bump gunicorn 20.1.0 → 22.0.0 | dependabot | Jan 6 |
| 237 | Story 1.7: Provider Health Monitoring | Will Flowers | Dec 2025 |
| 236 | Story 1-10: Google Cloud Tasks Configuration | Will Flowers | Dec 2025 |
| 201 | Story 1-8: Flask/FastAPI Coexistence | Will Flowers | Nov 2025 |
| 200 | Story 1.6: Real-Time SMS Delivery with FCM | Will Flowers | Nov 2025 |
| 199 | Story 1.5: Inbound SMS Webhook Handling | Will Flowers | Nov 2025 |
| 198 | Story 1-4: SMS Sending via CloudNumbering | Will Flowers | Nov 2025 |
| 189 | Story 1.3: Number Inventory Management | Will Flowers | Nov 2025 |
| 186 | Story 1.2: CloudNumbering Provider Integration | Will Flowers | Nov 2025 |
| 167 | Add Claude Code GitHub Workflow | Will Flowers | Nov 2025 |
| 132 | Feature/stripe crypto payments | Ahmad | Oct 2025 |
| 91 | Affiliate Dashboard | Will Flowers | Sep 2025 |

---

## BMAD Tickets Worked On (Apr 7–14)

### Backend — Ahmad
| Story | Epic | Description | Status |
|-------|------|-------------|--------|
| 76-1 | 76 (n8n Webhooks) | Firebase user-created → n8n webhook relay | done |
| 76-2 | 76 (n8n Webhooks) | BICS location change → n8n webhook relay | done |
| 77-2 | 77 (Dashboard V2 Forecast) | QoQ weighted-avg forecast replacing Holt-Winters | review |
| 79-1 | 79 (Internal Dashboard) | Docs viewer section + Stripe-Firebase mapping | in-progress |
| 75-7-b | 75 (Dashboard V1) | FastAPI dashboard auth (port Firebase session cookies) | drafted |
| 75-10 | 75 (Dashboard V1) | Dual revenue KPIs (actual vs normalized) | ready-for-dev |

### Backend — Raja (DrRaja82)
| Story | Epic | Description | Status |
|-------|------|-------------|--------|
| 35a-9 | 35 (Supabase Migration) | Partnership tables | merged |
| 35a-11 | 35 (Supabase Migration) | Event fact tables + record_event() service | merged |
| 35a-12 | 35 (Supabase Migration) | RLS policies (Row Level Security) | merged |
| 35a-13 | 35 (Supabase Migration) | Realtime triggers (Supabase Broadcast) | merged |

### Backend — Will Flowers
| Story | Epic | Description | Status |
|-------|------|-------------|--------|
| 5-15 | 5 (Porting) | Porting form cleanup + donor auto-provisioning | review |
| 5-14 | 5 (Porting) | CloudNumbering auto-submit porting | in-progress |
| 5-13 | 5 (KYC/Porting) | KYC country gating (backend) | merged |

### Mobile — Will Flowers
| Story | Epic | Description | Status |
|-------|------|-------------|--------|
| 4-47 | 4 (Voice) | Capture inbound call CCID from push payload | done |
| 4-48 | 4 (Voice) | Bridge CallKit → WebRTC RTCAudioSession | done |
| 4-49 | 4 (Voice) | Adaptive answer timeout for push-delivered calls | done |
| 5-13 | 5 (KYC) | KYC country gating + dev menu TestFlight | done |

### Mobile — Frederik List
No BMAD story numbers referenced — UI/UX work (call history redesign, manage numbers, screen headers).

---

## Open PR Counts Summary

| Repo | Human PRs | Dependabot PRs | Total |
|------|-----------|----------------|-------|
| pangia-app | 5 | 12 | 17 |
| pangia-pass | 5 | 5 | 10 |
| Pangia-Pass-Backend-Live | 32 | 4 | 36 |
| **Total** | **42** | **21** | **63** |
