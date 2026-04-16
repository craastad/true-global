# Epic 35 — Firebase RTDB → Supabase PostgreSQL Migration

**Repo:** Pangia-Pass-Backend-Live
**Branch:** `epic-35-firebase-to-supabase-postgresql-migration-clean` (PR #415)
**Date:** 2026-04-14

---

| Epic | Description | Stories | GitHub |
|------|-------------|---------|--------|
| **35A** | Schema, Infrastructure & Foundation | 13 | [epic-35a](https://github.com/True-Global/Pangia-Pass-Backend-Live/blob/epic-35-firebase-to-supabase-postgresql-migration-clean/docs/epics/epic-35a-schema-infrastructure-foundation.md) |
| **35B** | New Signup Flow — Multi-Product Checkout | 9 | [epic-35b](https://github.com/True-Global/Pangia-Pass-Backend-Live/blob/epic-35-firebase-to-supabase-postgresql-migration-clean/docs/epics/epic-35b-new-signup-flow-multi-product-checkout.md) |
| **35C** | Existing User Migration | 12 | [epic-35c](https://github.com/True-Global/Pangia-Pass-Backend-Live/blob/epic-35-firebase-to-supabase-postgresql-migration-clean/docs/epics/epic-35c-existing-user-migration.md) |
| **35D** | Storage, Ancillary & Platform Completion | 7 | [epic-35d](https://github.com/True-Global/Pangia-Pass-Backend-Live/blob/epic-35-firebase-to-supabase-postgresql-migration-clean/docs/epics/epic-35d-storage-ancillary-platform-completion.md) |

**Total: 41 stories across 4 epics**

## Dependency Chain

```
35A (Foundation) ──→ 35B (New Signup) ──→ 35C (User Migration)
       │                                         │
       └──→ 35D (Storage & Ancillary) ←──────────┘ (partial)
```

## Epic Summaries

### 35A — Schema, Infrastructure & Foundation
Foundation layer. Supabase project setup, ~30 tables, Firebase Auth JWT bridge, RLS policies, realtime triggers, event recording. Raja has merged stories 35a-9 through 35a-13 to this branch. **Prerequisite for everything else.**

### 35B — New Signup Flow — Multi-Product Checkout
New user flow. Account creation, product catalog API, Stripe Setup Intent checkout, subscription creation with partial-failure rollback, webhook handlers, subscription management API, plus two mobile stories (order summary screen, realtime SDK).

### 35C — Existing User Migration
Migrate ~10K existing users. ETL from Firebase, handle ~75 lifetime members, Stripe subscription restructuring (dry-run then production), dual-write mode, n8n workflow migration, cutover to Supabase-primary reads, rollback playbook, Firebase decommission. External dependencies on n8n owner and possibly Stripe support.

### 35D — Storage, Ancillary & Platform Completion
KYC metadata migration (no raw media), voicemail storage spike, Pangia Gold bundling research spike, member-attribute pricing engine, KYC requirements by product/country, dev seed data, production product catalog sync.
