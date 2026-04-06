# Pangia Pass Backend - Open PR Analysis

Generated: 2026-04-06
Source: github.com/True-Global/Pangia-Pass-Backend-Live
Open PRs: 43

---

## Active Feature Work (will-flowers-pangia)

### PR #438: Debug crashlytics
**+5,351/-176 (43 files) | 2026-04-01 | `debug-crashlytics` -> `ralph-loop-existing-stories`**

Modifies FCM services, voice APIs, notification sound mapping, and Firebase database access for crash diagnostics. The bulk of the changes are debug documentation (wolf-fence analysis, mobile device logging guides) plus new implementation artifact stories (4-35 through 4-39, 8-13, 14-24, 14-38, 2-18, 11-9) covering FCM token self-healing, voice transport readiness, Crashlytics hardening, and PostHog autocapture.

### PR #411: feat: multi-epic sprint delivery -- telephony, porting, DND, voice, monitoring
**+1,594,076/-25,068 (6,920 files) | 2026-03-11 | `ralph-loop-existing-stories` -> `11-2-veriff-integration`**

Massive umbrella delivery covering new telephony features (DND mode, call transfer, port-out workflow, country verification), voice API endpoints and pricing, FCM enhancements, admin dashboard, incident management, monitoring Terraform configs, structured logging, and the full BMAD v6 workflow tree with sprint-accelerator tooling. The enormous file count includes implementation artifacts, story specs, and infrastructure configs for epics 2-8 and 11-15.

### PR #410: feat(kyc,fcm): stories 11-2, 11-7, 11-8, 14-17, 14-18, 14-19 + debug RCAs
**+21,356/-12,075 (103 files) | 2026-03-07 | `11-2-veriff-integration` -> `3-10-fix-cloudnumbering-endpoint-routes`**

Delivers six stories across KYC and FCM domains. Adds Veriff fullauto webhook compatibility with decision/AML idempotency (11-2), KYC post-verification reliability via a gate service and sanctions checking (11-7), KYC navigation fixes with FCM/APNs push notification bridging (11-8), FCM token lifecycle management including deregister endpoints and staleness cron (14-17/14-19), and a tech-spec story pipeline with BATS tests (14-18). Includes an RCA document for FCM/KYC push notification failures.

### PR #402: feat(telephony): stories 3-10, 4-18--4-26, 14-14 + Epic 15 docs + docs reorg
**+43,100/-4,678 (331 files) | 2026-02-24 | `3-10-fix-cloudnumbering-endpoint-routes` -> `epic-8-e2e-testing-additional-stories`**

Builds out the voice call pipeline with stories 4-18 through 4-26 covering call hangup logging, inbound session deduplication, Telnyx call parking, phantom leg elimination, smart sink dedup, dev console WebRTC fixes, and SIP URI resolution. Also fixes CloudNumbering endpoint routes (3-10), adds telephony observability hardening (14-14), introduces Meta Pixel story docs (Epic 15), and reorganizes sprint artifacts.

### PR #400: docs(epic-15): Meta Pixel stories 15.1, 15.2 + tech spec
**+1,413/-43 (5 files) | 2026-02-22 | `implement-meta-pixel` -> `epic-8-e2e-testing-additional-stories`**

Documentation-only. Adds planning artifacts for Meta Pixel integration: Story 15.1 (base pixel setup with SPA PageView tracking and ad blocker detection) and Story 15.2 (conversion event tracking for InitiateCheckout, Purchase, CompleteRegistration), plus a full tech spec with 12 technical decisions and two adversarial review rounds.

### PR #395: feat(testing): Stories 8.9-8.12 E2E testing framework + review fixes
**+19,752/-2,380 (124 files) | 2026-02-20 | `epic-8-e2e-testing-additional-stories` -> `14-12-terraform-module-consolidation`**

Delivers a comprehensive API E2E testing framework with 349 tests across 12 test files covering all 164 FastAPI routes. Includes Schemathesis contract/fuzz testing, cost-controlled Locust stress testing, a GitHub Actions CI/CD pipeline, lifecycle diagrams, and a traceability matrix. Also includes review-driven fixes: Firebase path normalization, ED25519 webhook key decoding corrections, expanded unit test coverage for Telnyx webhooks and call control, and cross-story telephony work (Story 4.16 SIP dial bridge, Story 14.11 degradation alerting).

### PR #394: Story 14.12: Terraform Module Consolidation
**+6,988/-342 (44 files) | 2026-02-20 | `14-12-terraform-module-consolidation` -> `3-2-merge-deploy`**

Consolidates and reorganizes Terraform infrastructure configuration. Adds new monitoring alert policies, Firebase monitoring, log-based metrics, notification channels, and environment-specific tfvars for dev/prod separation, while removing legacy cloud-tasks-monitoring and telnyx-voice-monitoring configurations. Includes architecture documentation (ADRs, mobile app architecture) and sprint planning docs for Epic 14 stories.

### PR #385: Story 3.2: Telnyx Full Provider Adapter (SMS, Numbers, Voice)
**+2,249/-133 (15 files) | 2026-02-18 | `3-2-merge-deploy` -> `mobile-stories-hand-off`**

Implements a complete Telnyx telephony provider adapter with a new `telnyx/` provider package containing adapter, client, and models modules for SMS sending, number management, and voice call capabilities. Adds Telnyx-specific webhook security verification, updates the provider factory for Telnyx registration, and includes comprehensive unit and integration tests.

### PR #384: Story 14.9: snake_case standardization + mobile developer handoff
**+18,646/-3,026 (78 files) | 2026-02-18 | `mobile-stories-hand-off` -> `14-8-telephony-api-di-convention-consolidation`**

Standardizes API response fields to snake_case across the telephony module, adds the Telnyx provider adapter (overlapping with PR #385), and creates extensive mobile developer handoff documentation. Rewrites and adds numerous sprint artifact docs for Epics 2, 4, 5, 6, 8, and 11 with mobile-focused implementation specs, updates FCM and rate-limit services, adds analytics/observability runbooks, and includes a logging query helper script.

### PR #382: feat(telephony): Story 14-8 -- DI convention consolidation to singleton getters
**+4,358/-934 (72 files) | 2026-02-17 | `14-8-telephony-api-di-convention-consolidation` -> `epics-12-and-13-fix-failing-tests`**

Refactors dependency injection across the telephony module to use a consistent singleton getter pattern instead of ad-hoc instantiation. Updates all API endpoint files, services, and utilities to follow the new DI convention, adds an ADR documenting the pattern, creates a DI convention checker script, and aligns 37+ test files with the updated service initialization approach.

### PR #377: fix(tests): align 37 test files with actual implementations
**+2,881/-2,398 (45 files) | 2026-02-16 | `epics-12-and-13-fix-failing-tests` -> `epics-12-and-13`**

Fixes and realigns 45 test files to match current production implementations. Rewrites or significantly updates e2e tests (admin dashboard, coverage degradation, GDPR compliance), unit tests (audit endpoints, audit hooks, sanctions admin API, FCM service, multi-provider health), and integration tests (consent, delivery pipeline, KYC gate), while adding new test files for account deletion, admin degradation analytics, and coverage degradation service.

### PR #371: feat(epics-12-13): PR-370 code review remediation + alerting/monitoring
**+12,603/-5,392 (146 files) | 2026-02-16 | `epics-12-and-13` -> `rest-of-epic-3-7-and-8`**

Addresses code review feedback from PR #370. Removes dead code (CRM integrations, legacy KPI alerting service, frontend error logging), adds a Vercel log proxy cloud function, creates Cloud Monitoring metrics utility, introduces Firebase path standardization (ADR-029), adds a service registry, refactors admin API and webhook handlers, and expands Terraform monitoring with new alert policies and log-based metrics.

### PR #370: feat(telephony): Epic 3, 7, 8, 11 Implementation - Sprint Batch
**+141,980/-93 (316 files) | 2026-02-15 | `rest-of-epic-3-7-and-8` -> `5-1-number-porting-request-submission-domestic-porting`**

Massive multi-epic batch implementing DirectConnect provider adapter, extensive telephony services (account deletion, audit logging, consent, data export, DPA, encryption, escalation, GDPR compliance, KYC, retention, sanctions), admin API endpoints, middleware (audit, request metrics), Cloud Task handlers, coverage degradation monitoring, and KPI alerting/metrics services. Includes comprehensive documentation covering architecture, compliance (GDPR Articles 28/30), deployment, and API reference.

### PR #369: feat(telephony): Epic 5 - Number Porting System & Regulatory Compliance
**+59,449/-877 (194 files) | 2026-02-13 | `5-1-number-porting-request-submission-domestic-porting` -> `1-19-kms-envelope-encryption-sms-body-storage`**

Implements the full number porting system: porting services (CloudNumbering porting, Telnyx porting, fast-port, LOA resolution, port-out, porting status tracking, notifications, deadlines), compliance and verification services (Veriff KYC, verification endpoints), FCM push notification enhancements, extensive porting models and validation, and regulatory compliance documentation for 10+ countries.

### PR #365: feat(telephony): Story 1.19 - KMS envelope encryption for SMS body storage
**+1,635/-38 (16 files) | 2026-02-10 | `1-19-kms-envelope-encryption-sms-body-storage` -> `4-14-webrtc-credential-endpoint-telnyx-telephony-credentials`**

Adds Google Cloud KMS envelope encryption for SMS message bodies at rest. Introduces a `KMS` config class, `MessageEncryptor` utility with DEK caching, a `kms_envelope` module for encrypt/decrypt operations, and Terraform KMS key ring infrastructure. Updates the SMS inbox endpoint to batch-decrypt messages in parallel using `ThreadPoolExecutor` (max 8 workers).

### PR #364: feat(telephony): Story 4.14 - WebRTC credential endpoint
**+3,103/-2 (9 files) | 2026-02-10 | `4-14-webrtc-credential-endpoint-telnyx-telephony-credentials` -> `4-13-voip-push-infrastructure`**

Adds a new `GET /api/v1/telephony/voice/telnyx/webrtc-token` endpoint returning Telnyx JWT and SIP credentials for mobile WebRTC authentication. Introduces `WebRTCCredentialService` for Telnyx credential lifecycle management (creation, JWT generation, Firebase caching, revocation with tenacity retry logic) and includes ADR-020 documentation.

### PR #363: feat(telephony): Story 4.13 - VoIP push infrastructure
**+3,263/-18 (14 files) | 2026-02-09 | `4-13-voip-push-infrastructure` -> `3-9-telnyx-verified-numbers-cloudnumbering-integration`**

Implements VoIP push token management for iOS PushKit and Android FCM. Adds API endpoints (`POST/DELETE /api/v1/telephony/voip/register-token`) for token registration/deregistration, `VoIPPushService` for sending push notifications to registered devices, and updates the webhook handler to invoke VoIP push delivery for incoming calls.

### PR #360: docs(story): Create Story 3.2 - Telnyx full provider adapter
**+19,456/-2,639 (127 files) | 2026-02-03 | `3-2-telnyx-full-provider-adapter-sms-numbers-voice` -> `3-1-provider-abstraction-refactoring-provider-neutral-infrastructure`**

Despite the docs-only title, this is a large mixed PR. Creates Story 3.2 sprint artifact for the Telnyx provider adapter but also bundles substantial code: complete Telnyx provider adapter, Telnyx verification service (Story 3.9) with endpoint manager and webhook handlers, Firebase client refactoring, quality service fixes, and Epic 2 story documentation overhaul.

### PR #359: feat(telephony): Story 3.1 - Provider-neutral infrastructure
**+7,488/-1,597 (48 files) | 2026-02-03 | `3-1-provider-abstraction-refactoring-provider-neutral-infrastructure` -> `1-13-rate-limiting-abuse-prevention`**

Introduces provider-neutral abstraction layer. Adds a `webhook_security.py` module with a strategy pattern (`WebhookVerifier` base class, `IPAllowlistVerifier` for CloudNumbering), refactors webhook handler to remove hardcoded CloudNumbering imports in favor of factory pattern, adds provider-neutral schemas and Firebase database methods, and updates the telephony factory with multi-provider configuration.

### PR #334: Story 1.13: Rate Limiting & Abuse Prevention - Complete Implementation
**+59,288/-2,820 (160 files) | 2026-01-23 | `1-13-rate-limiting-abuse-prevention` -> `4-11-voicemail-support-tbd-provider-dependent`**

Implements comprehensive rate limiting and abuse prevention. Adds `RateLimitService` with soft daily limits (100 SMS, 50 calls) and hard limits (3 number provisions/day), `TokenBucket` provider rate limiter for CloudNumbering (50 req/s), `AbuseDetectionService` with spike/velocity/geographic anomaly detection, admin dashboard API endpoints for flagged users and usage stats, and a `cooldown` utility for number release management.

### PR #332: Story 4.11: Telnyx Built-in Voicemail Support (Backend MVP)
**+4,320/-1 (12 files) | 2026-01-22 | `4-11-voicemail-support-tbd-provider-dependent` -> `4-5-dtmf-input-handling-ivr-support`**

Adds voicemail management with CRUD endpoints (list, get with signed audio URL, mark as read, delete). Introduces `VoicemailService`, `Voicemail` Pydantic models, a `VOICEMAIL_ENABLED` feature flag, FCM service updates for voicemail push notifications, and voicemail webhook handling for processing Telnyx voicemail events.

### PR #331: Story 4.5: DTMF Input Handling for IVR Support
**+6,328/-98 (31 files) | 2026-01-22 | `4-5-dtmf-input-handling-ivr-support` -> `4-4-call-forwarding-configuration-user-settings`**

Adds DTMF (touch-tone) input handling and IVR support along with call quality monitoring. Introduces `quality_service.py` for MOS/packet-loss/jitter metrics, `transaction_metrics.py` for Firebase transaction monitoring, call quality analytics admin endpoints, `ForwardingService` with forwarding loop prevention, and Cloud Scheduler-based quality aggregation. Expands `TELEPHONY` config with nested domain constant classes.

### PR #330: Story 4-4: Call Forwarding Configuration & User Settings
**+2,928/-14 (18 files) | 2026-01-22 | `4-4-call-forwarding-configuration-user-settings` -> `4-1-cloudnumbering-sip-trunk-configuration-validation`**

Adds call forwarding configuration endpoints (`POST/GET/DELETE /{number_id}/forwarding`) with support for unconditional and no-answer forwarding types. Introduces `ForwardingService` for forwarding lifecycle management with loop detection, `TelnyxCallControlService` updates for SIP REFER-based forwarding, Firebase RTDB schemas for forwarding config storage, and Cloud Tasks integration via `TaskManager`.

### PR #329: feat(epic-4): Voice calling - SIP trunk config, outbound/inbound calls (Stories 4.1-4.3)
**+11,961/-183 (48 files) | 2026-01-22 | `4-1-cloudnumbering-sip-trunk-configuration-validation` -> `1-11-infrastructure-setup-firebase-security-rules`**

Foundational voice calling stack. Adds admin endpoints for SIP trunk configuration (`configure-voice`, `activate-voice`, `verify-voice`), `VoiceConfigService` for voice config lifecycle, `TelnyxCallControlService` for outbound call initiation and inbound call routing, Telnyx webhook handlers for call events (initiated, answered, hangup, missed), `PricingService` for per-minute cost tracking, and FCM push notification service for incoming calls.

### PR #311: 1 11 infrastructure setup firebase security rules + api bug fixes
**+26,695/-830 (107 files) | 2026-01-12 | `1-11-infrastructure-setup-firebase-security-rules` -> `1-7-provider-health-monitoring-logging-fcm-integration`**

Merges Firebase security rules infrastructure with API bug fixes. Touches the full telephony stack (API endpoints for FCM, health, numbers, SMS, users, webhooks), database layer (Firebase client, schemas, protocols), CloudNumbering provider integration, and service logic. Adds extensive architecture documentation (ADRs for telephony provisioning, Firebase client protocol, number schema consolidation, voice calling) and Terraform infrastructure for cloud tasks and monitoring.

---

## Older Feature Work (will-flowers-pangia)

### PR #237: Story 1.7: Provider Health Monitoring
**+2,949/-224 (18 files) | 2025-12-11 | `1-7-provider-health-monitoring-logging-fcm-integration` -> `1-10-infrastructure-setup-google-cloud-tasks-configuration-attempt-three`**

Implements provider health monitoring, logging, and FCM integration. Adds health check service, health API endpoint, telephony DB schemas and number models, SMS service and task handler updates, and comprehensive test coverage for health monitoring, delivery pipeline, and inbox API.

### PR #236: Story 1-10: Infrastructure Setup - Google Cloud Tasks Configuration
**+9,584/-28 (39 files) | 2025-12-11 | `1-10-infrastructure-setup-google-cloud-tasks-configuration-attempt-three` -> `1-8-infrastructure-setup-flask-fastapi-coexistence`**

Sets up Google Cloud Tasks infrastructure: task manager, task handlers, SMS/webhook API integration. Adds Terraform configs for Cloud Tasks and monitoring, dead letter queue management script, CI workflow updates, and debug/RCA reports for Stripe and GCP issues.

### PR #201: Story 1-8: Multi-Service Flask/FastAPI Architecture Documentation
**+7,722/-26 (24 files) | 2025-11-27 | `1-8-infrastructure-setup-flask-fastapi-coexistence` -> `1-6-real-time-sms-delivery-architecture-decision-implementation`**

Documentation-only. Adds comprehensive architecture documentation for Flask/FastAPI coexistence: ADRs (environment segregation, user-number mapping, SMS metadata GDPR, strangler-fig migration, Cloud Run public access), architecture guides (visual guide, technology stack, project structure, implementation patterns), and developer docs for CI/CD, environment configuration, and local multi-service development.

### PR #200: Story 1.6: Real-Time SMS Delivery with FCM
**+4,385/-68 (22 files) | 2025-11-27 | `1-6-real-time-sms-delivery-architecture-decision-implementation` -> `1-5-inbound-sms-webhook-handling-cloudnumbering-integration`**

Adds real-time SMS delivery via Firebase Cloud Messaging. Introduces FCM service and API endpoint, FCM device token models, Firebase auth middleware, error handling improvements, and SMS service updates to trigger push notifications on inbound messages. Includes integration and unit tests.

### PR #199: Story 1.5: Inbound SMS Webhook Handling - CloudNumbering Integration
**+2,217/-64 (12 files) | 2025-11-27 | `1-5-inbound-sms-webhook-handling-cloudnumbering-integration` -> `1-4-sms-sending-outbound-messages-via-cloudnumbering`**

Implements inbound SMS webhook processing for CloudNumbering. Adds webhook API endpoint with signature validation and payload parsing, webhook models, CloudNumbering adapter updates for inbound message handling, SMS service enhancements for receiving messages, Firebase schema updates for message storage, and a webhook failure runbook.

### PR #198: Story 1-4: SMS Sending - Outbound Messages via CloudNumbering (FR-24 GDPR Compliant)
**+1,584/-66 (12 files) | 2025-11-27 | `1-4-sms-sending-outbound-messages-via-cloudnumbering` -> `1-3-number-inventory-management-user-assignment`**

Implements outbound SMS sending through CloudNumbering with GDPR-compliant metadata-only storage. Adds SMS send API endpoint, CloudNumbering adapter updates for outbound dispatch, phone number validation and SMS encoding utilities, Firebase database security rules for message paths, and unit tests.

### PR #189: Story 1.3: Number Inventory Management & User Assignment
**+2,886/-502 (33 files) | 2025-11-26 | `1-3-number-inventory-management-user-assignment` -> `1-2-cloudnumbering-provider-integration-number-search-provisioning`**

Adds number inventory management and user assignment functionality. Introduces API endpoints for number management and user operations, Firebase database layer with schemas for number tracking, number models, database security rules, and updates to existing Flask-side utilities (campaign validator, cron jobs, Firebase client, Stripe webhooks).

### PR #186: feat(telephony): Story 1.2 - CloudNumbering Provider Integration
**+8,330/-7 (35 files) | 2025-11-21 | `1-2-cloudnumbering-provider-integration-number-search-provisioning` -> `validation/async-ci-cd-integration`**

Implements CloudNumbering provider integration for number search and provisioning. Adds CloudNumbering adapter (implementing the base provider interface), API client, number search/provisioning API endpoints, Firebase database layer and schemas, core error handling and telephony models, provider factory pattern, CI test workflow updates, and Terraform/Firebase config changes.

---

## DrRaja82 Work

### PR #415: docs(epic-35): add migration epics, sprint planning, and research docs
**+40,598/-192 (96 files) | 2026-03-22 | `epic-35-firebase-to-supabase-postgresql-migration-clean` -> `ralph-loop-existing-stories`**

Documentation-heavy PR adding Epic 35 planning artifacts for a Firebase-to-Supabase/PostgreSQL migration. Introduces four sub-epic documents (35A-35D), full story breakdowns for schema infrastructure, new signup flows, existing user migration, and storage/ancillary platform completion. Includes initial code scaffolding in `app/core/supabase.py`, `app/config.py`, and `app/telephony/db/schemas.py`, plus `.gitattributes` for LFS handling and a `CLAUDE.md` project instructions file.

### PR #376: 3 2 telnyx full provider adapter sms numbers voice
**+1,845/-4 (14 files) | 2026-02-16 | `3-2-telnyx-full-provider-adapter-sms-numbers-voice` -> `14-8-telephony-api-di-convention-consolidation`**

Adds the Telnyx provider adapter -- appears to be an earlier or parallel version of PR #385 by will-flowers-pangia. Introduces the same core Telnyx package structure (adapter, client, models), webhook security for Telnyx signature verification, factory registration, and corresponding unit/integration tests. Slightly smaller than #385.

---

## NarutoAH Work

### PR #132: Feature/stripe crypto payments
**+25,182/-877 (139 files) | 2025-10-08 | `feature/stripe-crypto-payments` -> `staging`**

Despite the branch name, this is a large infrastructure and telephony foundation PR rather than just crypto payments. Adds the full telephony module skeleton (core config, encryption, logging, error handling, DB schemas, models, providers, services, tasks), Secret Manager integration, Firebase backup/restore tooling, analytics computation pipelines, CI/CD workflow updates, async callback handlers for BICS, campaign analytics utilities, and multiple new cron jobs (analytics cache warmer, computation, backup).

### PR #91: Affiliate Dashboard
**+3,001/-83 (17 files) | 2025-09-19 | `sync-out-of-data-to-firebase-from-stripe` -> `staging`**

Introduces a comprehensive affiliate dashboard and coupon analytics system. Adds `unified_affiliate_cache.py` (+702 lines) for caching affiliate/coupon data, `stripe_coupon_analytics.py` (+1,614 lines) for detailed Stripe coupon performance analytics, significantly expands the affiliate dashboard HTML template and backend logic, and includes coupon utility enhancements.

---

## Dependabot (Automated Dependency Updates)

### PR #431: Bump flask from 3.0.3 to 3.1.3 in /app/utils/keepgo
**+1/-1 (1 file) | 2026-03-28** — Security fix for session access tracking advisory (GHSA-68rp-wp8r-4726).

### PR #423: Bump requests from 2.32.3 to 2.33.0 in /app/utils/keepgo
**+1/-1 (1 file) | 2026-03-26** — Fixes CVE-2026-25645 (malicious file replacement via `extract_zipped_paths`).

### PR #422: Bump requests from 2.32.3 to 2.33.0
**+2/-2 (2 files) | 2026-03-26** — Same CVE fix as #423 but for the main project `pyproject.toml` and `requirements.txt`.

### PR #366: Bump pillow from 11.0.0 to 12.1.1
**+2/-2 (2 files) | 2026-02-11** — Pillow image processing library security/maintenance upgrade.

### PR #299: Bump gunicorn from 20.1.0 to 22.0.0
**+2/-2 (2 files) | 2026-01-06** — Gunicorn WSGI HTTP server maintenance upgrade.

---

## CI/CD

### PR #167: Add Claude Code GitHub Workflow
**+107/-0 (2 files) | 2025-11-06 | `add-claude-github-actions-1762441772325` -> `main`**

Adds two GitHub Actions workflow files: `claude.yml` for automated Claude-powered PR assistance and `claude-code-review.yml` for automated code review. Infrastructure-only, no application code changes.

---

## Key Observations

**Chained PR structure:** Will Flowers' telephony PRs form a long chain where each PR targets the previous one as its base branch (not `main`). The chain goes: #186 -> #189 -> #198 -> #199 -> #200 -> #201 -> #236 -> #237 -> #311 -> #329 -> ... -> #411 -> #438. This means they must be merged sequentially bottom-up, and none have been merged since #362 (Feb 5).

**Stale PRs:** PRs #91 and #132 (from Sep-Oct 2025) target `staging` which appears to be a deprecated branch. These may be abandoned.

**Duplicate work:** PRs #376 (DrRaja82) and #385 (will-flowers-pangia) both implement the Telnyx provider adapter with very similar code, suggesting parallel work that wasn't coordinated.

**Documentation-heavy:** Many of will-flowers-pangia's PRs contain significant documentation (sprint artifacts, ADRs, architecture guides) alongside code changes, inflating the diff sizes substantially.

**Security debt:** 4 open Dependabot PRs with security fixes (Flask, requests, Pillow, gunicorn) remain unmerged, some since January 2026.
