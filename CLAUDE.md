# CLAUDE.md

## Project

This is the `true-global` meta-repository containing analysis and documentation for the Pangia platform repos:
- `pangia-app` — React Native iOS mobile app (VoIP calling, SMS, phone numbers)
- `pangia-pass` — SvelteKit web app (eSIM campaigns, subscriptions, affiliates)
- `Pangia-Pass-Backend-Live` — Python backend (Flask/FastAPI, multi-provider eSIM, Stripe, analytics)

## Critical Rules

- **NEVER** create, close, comment on, or modify pull requests on GitHub for this repository or other repositories in this repo.
- **NEVER** perform any write operations on GitHub (issues, PRs, releases, etc.) for true-global.
- **ALWAYS** ask for explicit permission before running `git push`.

## Conventions

### File naming
All documents in the `ai/` directory must be prefixed with `YYYY-MM-DD` (e.g., `2026-04-06-summary.md`). This applies to summaries, analyses, reports, and any other generated documentation.

### Directory structure
```
ai/
├── pangia-app/           # Analysis docs for the mobile app
├── pangia-pass/          # Analysis docs for the web app
├── Pangia-Pass-Backend-Live/  # Analysis docs for the backend
└── reporting/            # Cumulative reports (no date prefix)
```

## Daily Summary

To generate a daily summary, ask Claude to "give me a daily summary". Workflow details and instructions are in `ai/reporting/CLAUDE.md`. Summaries are written to `ai/reporting/YYYY-MM-DD-daily-summary.md`.
