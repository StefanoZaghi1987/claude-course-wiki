---
type: page
created: 2026-05-31
updated: 2026-05-31
tags: [claude-code, configuration]
---

The `.claude/` project directory and `~/.claude/` home directory are the two root locations where Claude Code reads all instructions, settings, skills, subagents, and memory — and writes all session data.

## Overview

Claude Code reads from two locations: `.claude/` inside your project (committed to git, shared with your team) and `~/.claude/` in your home directory (personal, applies across all projects). Most users only ever touch `CLAUDE.md` and `settings.json`. The rest of the directory structure is built incrementally as needs arise: skills when a workflow repeats, rules when instructions should be path-scoped, agents when a specialized subagent is needed, workflows for dynamic orchestration. On Windows, `~/.claude/` resolves to `%USERPROFILE%\.claude\`; the `CLAUDE_CONFIG_DIR` environment variable overrides this path.

## Key dimensions

### Project-scope config files

Committed to git and shared with the team. Live in the repo root or `.claude/` subfolder:

| File | What it does |
|------|-------------|
| `CLAUDE.md` | Persistent instructions loaded every session |
| `.claude/rules/*.md` | Topic instructions; `paths:` frontmatter enables path-scoped loading |
| `.claude/settings.json` | Permissions, hooks, environment variables, model defaults |
| `.claude/settings.local.json` | Personal overrides (gitignored) |
| `.mcp.json` | MCP server configurations at project scope |
| `.worktreeinclude` | Files to copy into new git worktrees (e.g., `.env`) |
| `.claude/skills/<name>/SKILL.md` | Reusable prompts/workflows invokable as `/<name>` |
| `.claude/agents/*.md` | Custom subagent definitions |
| `.claude/workflows/*.js` | Dynamic workflow scripts |
| `.claude/agent-memory/<name>/` | Persistent memory dirs for specific subagents |

[[wiki/sources/explore-the-claude-directory-claude-code-docs]]

### Global-scope config files

Personal, apply across all projects, live in `~/.claude/`:

| File | What it does |
|------|-------------|
| `~/.claude.json` | Global config: auth tokens, preferences, model defaults |
| `~/.claude/settings.json` | User-level permissions, hooks, environment variables |
| `~/.claude/CLAUDE.md` | User-level persistent instructions (all projects) |
| `~/.claude/rules/` | User-level path-scoped rules |
| `~/.claude/skills/` | User-level skills available across all projects |
| `~/.claude/keybindings.json` | Custom keyboard shortcuts |
| `~/.claude/themes/` | Custom terminal color themes |

[[wiki/sources/explore-the-claude-directory-claude-code-docs]]

### Session data in `~/.claude/`

Claude Code writes session data during every session. Auto-purged after 30 days (default, configurable via `cleanupPeriodDays`):

- `projects/<project>/<session-id>.jsonl` — full conversation transcript (every message, tool call, result)
- `file-history/<session>/` — file snapshots for checkpoint restore
- `plans/`, `debug/`, `paste-cache/`, `image-cache/`, `tasks/`

Kept until you manually delete them:
- `history.jsonl` — every prompt you've typed (up-arrow recall)
- `stats-cache.json` — aggregated token/cost counts for `/usage`
- `remote-settings.json` — cached remote settings

[[wiki/sources/explore-the-claude-directory-claude-code-docs]]

### Security: plaintext transcripts

Transcripts are not encrypted at rest. Any secret that passes through a tool call (a `.env` file read, credentials in command output) lands in the transcript JSONL. Mitigations: lower `cleanupPeriodDays`, set `CLAUDE_CODE_SKIP_PROMPT_HISTORY` to suppress writes, or add `permissions.deny` rules to block reads of credential files. [[wiki/sources/explore-the-claude-directory-claude-code-docs]]

### Purging project state

`claude project purge` deletes all state Claude Code holds for one project: transcripts, auto memory, per-session task/debug/file-history entries, and matching lines in `history.jsonl`. `--all` purges state for every project at once. Pass `-i` to step through the deletion plan interactively. The command leaves `shell-snapshots/` and `backups/` untouched (they are not project-scoped). [[wiki/sources/explore-the-claude-directory-claude-code-docs]]

## Connections

- [[wiki/pages/claude-md]] — CLAUDE.md and rules/ live within this structure
- [[wiki/pages/skills]] — skills/<name>/SKILL.md anatomy
- [[wiki/pages/sub-agents]] — agents/*.md custom subagent definitions
- [[wiki/pages/memory-in-claude]] — auto memory at projects/<project>/memory/
- [[wiki/pages/sessions-management]] — session transcripts and file history stored here

## Sources

- [[wiki/sources/explore-the-claude-directory-claude-code-docs]] — full file reference, application data layout, security notes, project purge
