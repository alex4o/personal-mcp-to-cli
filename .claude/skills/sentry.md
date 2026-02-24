---
name: sentry
description: This skill should be used when the user asks to "check errors", "find bugs", "look at Sentry", "search issues in Sentry", "analyze an error", "resolve an issue", "check what's broken", or mentions Sentry issues, errors, traces, releases, or production problems.
version: 0.1.0
---

# Sentry

Interact with Sentry error tracking using the `sentry` CLI binary at `~/.local/bin/sentry`.

## Usage

Run commands via Bash tool:

```bash
sentry <command> [flags]
```

Use `MCPORTER_LOG_LEVEL=info` if OAuth is needed on first run.

## Key Commands

### Discovery
- `sentry whoami` — Get authenticated user info
- `sentry find-organizations` — List orgs. Optional: `--query <search>`
- `sentry find-teams --organization-slug <org>` — List teams
- `sentry find-projects --organization-slug <org>` — List projects
- `sentry find-releases --organization-slug <org>` — List releases. Optional: `--project-slug`, `--query`

### Issues
- `sentry search-issues --organization-slug <org> --query <natural language>` — Search issues using natural language
- `sentry get-issue-details --issue-id <id> --organization-slug <org>` — Get issue details with stacktrace. Also accepts `--issue-url <sentry-url>`
- `sentry update-issue --issue-id <id> --organization-slug <org>` — Update issue. `--status resolved|unresolved|ignored`, `--assigned-to user:<id>|team:<id>`
- `sentry get-issue-tag-values --issue-id <id> --organization-slug <org> --tag-key <key>` — Tag distribution (url, browser, os, environment, release)

### Events & Traces
- `sentry search-events --organization-slug <org> --query <natural language>` — Search events, get counts/aggregations
- `sentry search-issue-events --issue-id <id> --organization-slug <org> --query <query>` — Filter events within an issue
- `sentry get-trace-details --organization-slug <org> --trace-id <id>` — Get trace info
- `sentry get-event-attachment --organization-slug <org> --project-slug <proj> --event-id <id>` — Download attachments

### AI Analysis
- `sentry analyze-issue-with-seer --issue-id <id> --organization-slug <org>` — AI root cause analysis with code fixes. Also accepts `--issue-url`

### Documentation
- `sentry search-docs --query <query>` — Search Sentry docs. Optional: `--guide <platform/framework>`
- `sentry get-doc --path <path>` — Fetch full doc page (use paths from search-docs results)

## Output Formats

All commands support `--output <format>`: `text` (default), `json`, `markdown`, `raw`.
Use `--timeout <ms>` to adjust call timeout (default 30000).

## Tips

- When given a Sentry URL, pass it directly to `--issue-url` — it extracts org/issue automatically
- Use `search-issues` for listing issues, `search-events` for counts/aggregations
- `analyze-issue-with-seer` gives AI-powered root cause + code fixes (may take 2-5 min first time)
- Always get `--organization-slug` first via `find-organizations` if not known
