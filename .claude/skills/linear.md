---
name: linear
description: This skill should be used when the user asks to "create an issue", "list my tasks", "update a ticket", "search issues", "check my Linear", "create a project", or mentions Linear issues, projects, teams, milestones, or initiatives.
version: 0.1.0
---

# Linear

Interact with Linear project management using the `linear` CLI binary at `~/.local/bin/linear`.

## Usage

Run commands via Bash tool:

```bash
linear <command> [flags]
```

Use `MCPORTER_LOG_LEVEL=info` if OAuth is needed on first run.

## Key Commands

### Issues
- `linear list-issues` — List issues. Use `--assignee me` for my issues, `--team <team>` to filter by team, `--status <status>` to filter by status
- `linear get-issue --id <id>` — Get issue details (supports ID like `ENG-123`)
- `linear create-issue --title <title> --team <team>` — Create issue. Optional: `--description`, `--priority <0-4>`, `--status`, `--assignee`, `--label`
- `linear update-issue --id <id>` — Update issue. Optional: `--title`, `--description`, `--status`, `--priority`, `--assignee`

### Comments
- `linear list-comments --issue <id>` — List comments on an issue
- `linear create-comment --issue <id> --body <text>` — Add comment (supports markdown)

### Projects & Milestones
- `linear list-projects` — List all projects
- `linear get-project --id <id>` — Get project details
- `linear save-project --name <name> --team <team>` — Create project
- `linear list-milestones --project <id>` — List milestones
- `linear create-milestone --project <id> --name <name>` — Create milestone

### Teams & Users
- `linear list-teams` — List teams
- `linear get-team --id <id>` — Get team details
- `linear list-users` — List workspace users

### Initiatives
- `linear list-initiatives` — List initiatives
- `linear create-initiative --name <name>` — Create initiative

### Other
- `linear list-issue-statuses --team <team>` — List available statuses
- `linear list-issue-labels` — List available labels
- `linear search-documentation --query <query>` — Search Linear docs

## Output Formats

All commands support `--output <format>`: `text` (default), `json`, `markdown`, `raw`.
Use `--timeout <ms>` to adjust call timeout (default 30000).

## Tips

- Always use `--output json` when parsing results programmatically
- Use `--raw '<json>'` to pass complex arguments as JSON directly
- Issue IDs can be short form like `ENG-123` or full UUIDs
