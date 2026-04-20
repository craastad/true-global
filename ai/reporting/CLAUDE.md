# Reporting — Workflow Instructions

⚠️ **Daily summaries are now saved to `pangia-ops`, not this repo.**
Write daily summary files to `/Users/craastad/pangia/pangia-ops/dev/reporting/YYYY-MM-DD-daily-summary.md` and commit/push there.

## Daily Summary — `YYYY-MM-DD-daily-summary.md`

Generated on request ("give me a daily summary", "daily report", etc.). Each summary covers work since the previous daily summary.

### Steps

1. **Pull all three repos** (branches: `master` for pangia-app, `dev` for pangia-pass, `main` for backend):
   ```
   cd /Users/craastad/code/pangia/true-global/pangia-app && git pull
   cd /Users/craastad/code/pangia/true-global/pangia-pass && git pull
   cd /Users/craastad/code/pangia/true-global/Pangia-Pass-Backend-Live && git pull
   cd /Users/craastad/code/pangia/true-global && git pull
   ```

2. **Gather commits since last daily summary** across all branches:
   ```
   git log --since="<last-summary-date>" --all --oneline --format="%h %ad %an - %s" --date=short
   ```

3. **Fetch open PRs for all three repos in parallel:**
   ```
   gh pr list --repo True-Global/Pangia-Pass-Backend-Live --state open --json number,title,author,createdAt,headRefName --limit 50
   gh pr list --repo True-Global/pangia-app --state open --json number,title,author,createdAt,headRefName --limit 50
   gh pr list --repo True-Global/pangia-pass --state open --json number,title,author,createdAt,headRefName --limit 50
   ```

4. **Identify BMAD tickets worked on** by cross-referencing commit messages with story/epic numbers. Sprint status is in:
   - `Pangia-Pass-Backend-Live/docs/sprint-artifacts/sprint-status.yaml`
   - `Pangia-Pass-Backend-Live/docs/stories/` and `docs/epics/`
   - BMAD Method reference: `/Users/craastad/code/ai-tools/BMAD-METHOD/docs/`

5. **Write the summary** to `ai/reporting/YYYY-MM-DD-daily-summary.md` with sections:
   - Per-repo work done (grouped by contributor)
   - Per-repo open PR tables (human + dependabot counts)
   - BMAD ticket status matrix (story, epic, description, status)
   - Open PR counts summary table

### Finding the last summary date

Check for the most recent `*-daily-summary.md` in this directory:
```
ls -1 ai/reporting/*-daily-summary.md | tail -1
```
If none exists, ask the user for a start date.

### Hard rules (from project CLAUDE.md)

- **Read-only on GitHub.** Never create, close, comment on, or modify PRs, issues, or releases on any True-Global repo.
- **Never `git push`** without explicit user permission.
- **Do not commit** unless the user asks.
