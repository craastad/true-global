# Daily Summary — 2026-04-20

**Window:** commits since 2026-04-16 (last daily summary) through 2026-04-20 (Asia/Makassar).

## Pangia-Pass-Backend-Live

### Work done (grouped by contributor)

**Ahmad** (epic-80 — Bridge4IP Static Egress IP)
- `8216fcbf` — docs(epic-80): added Bridge4IP epic + stories 80-1, 80-2, 80-7
- `4f89797d`, `46835b4e` — promoted stories 80-1 and 80-2 to ready-for-dev
- `f7c6d89a` — story 80-1: Terraform scaffolding + 42 contract tests
- `dd61a02d` — story 80-2: proxy VM + static IP Terraform module
- `ab72223d` — fix(80-2): Phase 2e remediation (D1 + P1-P12 from Phase 2d code review)
- `f118eb95` — close 80-1 + 80-2 per sprint change proposal (stories marked done-with-followups; 274 unit tests passing; deferred items moved to `deferred-work.md`; Terraform lock files committed)
- `7c8f705e`, `12572f38` — temporary FastAPI smoketest endpoint for Bridge4IP proxy VMs, extended with egress-check probe
- ~15 `chore(sprint)` commits with sprint-story session artifacts for 80-1 and 80-2
- `5e17f118` — un-quarantine 80-1 and 80-2 after `find_story_file` patch
- All epic-80 work is on `origin/feature/bridge4ip-flow` — **not yet merged to main**

**Ahmad** (other)
- `47f25ad4` → merge `60b7bb27` (PR #464) — fix(email): route generic trial cancellations to dark template
- `001ce7cc` → merge `999853a8` (PR #465) — chore: remove stale `docs/sprint-status.yaml`

### Open PRs

| # | Title | Author | Created | Branch |
|---|---|---|---|---|
| 462 | fix(email): route trial cancellation to correct dark-themed template | NarutoAH (Ahmad) | 2026-04-16 | update/trial-emails |
| 461 | Validation/async ci cd integration | will-flowers-pangia | 2026-04-15 | validation/async-ci-cd-integration |
| 415 | docs(epic-35): add migration epics, sprint planning, and research docs | DrRaja82 | 2026-03-22 | epic-35-firebase-to-supabase-postgresql-migration-clean |
| 167 | Add Claude Code GitHub Workflow | will-flowers-pangia | 2025-11-06 | add-claude-github-actions |
| 132 | Feature/stripe crypto payments | NarutoAH | 2025-10-08 | feature/stripe-crypto-payments |
| 91 | Affiliate Dashboard | will-flowers-pangia | 2025-09-19 | sync-out-of-data-to-firebase-from-stripe |

**Dependabot (5):** #431 flask, #423 requests (keepgo), #422 requests, #366 pillow, #299 gunicorn.

---

## pangia-pass

### Work done (grouped by contributor)

**Germain Machleidt**
- `abbb9b0` — make partner logos on campaign pages clickable
- `424e1a9` — add Alicante Nomad Summit campaign landing page

**Matthew Kirkham**
- `65297c6` — address PR review feedback from Will
- `96343cd` — add code comments addressing PR review concerns

**plitarko** (merges)
- `4854f51` — PR #177 (partner-logo-clickable)
- `52008f1` — PR #178 (alicante-nomad-summit-campaign)
- `6d39d67` — PR #179 (dev → main)

### Open PRs

| # | Title | Author | Created | Branch |
|---|---|---|---|---|
| 175 | PostHog deep integration + Meta CAPI | MatthewMakesMagic | 2026-04-13 | matthewbranch |
| 105 | black friday campaign details | NarutoAH | 2025-11-26 | campaign/black-friday-2025 |
| 81 | Add potential UI to indicate which discount will be applied | will-flowers-pangia | 2025-09-25 | PP-152-fix-double-referral-campaign-discount |
| 77 | Blog | plitarko | 2025-09-17 | blog |
| 26 | Add frontend_url to frontend for some endpoints? | will-flowers-pangia | 2025-07-31 | feature/campaign-data-on-fe |

**Dependabot (5):** #9 @sveltejs/kit, #7 rollup, #6 vite, #2 micromatch, #1 svelte.

---

## pangia-app

### Work done (grouped by contributor)

**dependabot**
- `ee606b0` — bump protobufjs 7.5.4 → 7.5.5 in /functions

No human commits in window.

### Open PRs

| # | Title | Author | Created | Branch |
|---|---|---|---|---|
| 33 | UI fixes 2 | will-flowers-pangia | 2026-04-13 | ui-fixes-2 |
| 28 | feat: restore branch work for crashlytics, posthog, and pending story updates | will-flowers-pangia | 2026-03-31 | debug-crashlytics |
| 23 | feat(19-2): UK porting status UX coherence | will-flowers-pangia | 2026-03-20 | feat/19-2-uk-porting-status-ux-coherence |
| 17 | feat: multi-epic mobile delivery — KYC, porting, voice, messaging, design system | will-flowers-pangia | 2026-03-11 | ralph-loop-existing-stories |
| 15 | feat(kyc,fcm): stories 11-2, 11-8, 14-19 — Veriff SDK, KYC nav, FCM lifecycle | will-flowers-pangia | 2026-03-06 | 11-2-veriff-integration |

**Dependabot (13):** #34 protobufjs, #32 lodash, #31 fast-xml-parser, #27 path-to-regexp, #26 brace-expansion, #25 picomatch, #22 fast-xml-parser+storage, #20 undici, #18 tar, #11 minimatch, #8 minimatch, #7 ajv, #4 qs.

---

## BMAD Ticket Status (activity this window)

| Story | Epic | Description | Status |
|---|---|---|---|
| 80-1 | 80 Bridge4IP | Terraform foundation + GCS state (115 tests) | done (was quarantined; operator ACs pending live apply) |
| 80-2 | 80 Bridge4IP | Provision proxy VM + static IP module (159 tests / 2 skipped) | done (was quarantined; operator ACs + NOC whitelist pending — blocks 80-3) |
| 80-7 | 80 Bridge4IP | Terraform CI/CD GitHub Actions (PR plan + dev auto-apply + prod manual approval) | drafted |
| 80-3 | 80 Bridge4IP | Bridge4IP client module (config, retry decorator) | backlog |
| 80-4 | 80 Bridge4IP | Cloud Tasks async writes (dev/prod queues, OIDC, dead-letter) | backlog |
| 80-5 | 80 Bridge4IP | Monitoring + alerting (uptime checks, queue backlog, error rate) | backlog |
| 80-6 | 80 Bridge4IP | Documentation + runbook + ADR (IP rotation, HA scaling) | backlog |
| epic-80 | — | Bridge4IP Static Egress IP — proxy VM + Cloud Tasks | in-progress (was backlog) |

Epic-80 is a new initiative: the first Terraform module in the project, scoped to Bridge4IP only to avoid blast radius on Stripe/BICS/Telnyx. All updates live on `feature/bridge4ip-flow`; the `main` branch still shows pre-epic-80 sprint state.

---

## Open PR Counts Summary

| Repo | Human PRs | Dependabot PRs | Total |
|---|---|---|---|
| Pangia-Pass-Backend-Live | 6 | 5 | 11 |
| pangia-pass | 5 | 5 | 10 |
| pangia-app | 5 | 13 | 18 |
| **Total** | **16** | **23** | **39** |
