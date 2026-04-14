# true-global

Personal AI-assisted overview of development work across the Pangia platform.

This repo tracks analysis, reporting, and documentation for the three Pangia repos:

- **pangia-app** — React Native iOS mobile app (VoIP calling, SMS, phone numbers)
- **pangia-pass** — SvelteKit web app (eSIM campaigns, subscriptions, affiliates)
- **Pangia-Pass-Backend-Live** — Python backend (Flask/FastAPI, multi-provider eSIM, Stripe, analytics)

## Structure

```
ai/
├── pangia-app/           # Analysis docs for the mobile app
├── pangia-pass/          # Analysis docs for the web app
├── Pangia-Pass-Backend-Live/  # Analysis docs for the backend
└── reporting/            # Daily summaries, PR counts, BMAD ticket tracking
```

## Daily Summaries

Daily summaries are generated with Claude Code and cover commits, open PRs, and BMAD ticket status across all repos. See `ai/reporting/CLAUDE.md` for the workflow.
