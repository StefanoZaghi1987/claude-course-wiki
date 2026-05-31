---
type: source
created: 2026-05-31
updated: 2026-05-31
tags: [claude-code, configuration, official-docs]
source_url: https://code.claude.com/docs/en/claude-directory
source_path: raw/web/explore-the-claude-directory-claude-code-docs/
---

Reference for the `.claude/` project directory and `~/.claude/` home directory — every file Claude reads, writes, and manages (May 2026).

## Summary

Claude Code reads instructions, settings, skills, subagents, and memory from two root locations: the `.claude/` directory inside your project (committed to git, shared with team) and `~/.claude/` in your home directory (personal, applies across all projects). On Windows, `~/.claude/` resolves to `%USERPROFILE%\.claude\`; `CLAUDE_CONFIG_DIR` overrides this path.

Most users only ever touch `CLAUDE.md` and `settings.json`. The rest of the project `.claude/` directory is optional and built incrementally: skills when a workflow repeats, rules when instructions should be path-scoped, agents when a specialized subagent is needed, workflows for dynamic orchestration.

**Project-scope files** (in repo root or `.claude/` subfolder, committed to git):

| File | What it does |
|------|-------------|
| `CLAUDE.md` | Persistent instructions loaded every session |
| `rules/*.md` | Topic-scoped instruction files; optional `paths:` frontmatter for path-specific loading |
| `settings.json` | Permissions, hooks, environment variables, model defaults |
| `settings.local.json` | Personal overrides, gitignored |
| `.mcp.json` | MCP server configurations at project scope |
| `.worktreeinclude` | Files to copy into new worktrees (e.g., `.env`) |
| `skills/<name>/SKILL.md` | Reusable prompt/workflow packages invokable as `/<name>` |
| `commands/*.md` | Legacy skill format (same behavior) |
| `output-styles/*.md` | Output style definitions |
| `agents/*.md` | Custom subagent definitions |
| `workflows/*.js` | Dynamic workflow scripts |
| `agent-memory/<name>/` | Persistent memory directories for subagents |

**Global-scope files** (in `~/.claude/`, personal, all projects):

| File | What it does |
|------|-------------|
| `~/.claude.json` | Global config: auth, preferences, model defaults |
| `~/.claude/settings.json` | User-level permissions, hooks, env vars |
| `projects/<project>/memory/` | Auto memory for each project |
| `keybindings.json` | Custom keyboard shortcuts |
| `themes/*.json` | Custom terminal themes |

Beyond authored config, `~/.claude/` holds data Claude writes during sessions. Transcripts (`projects/<project>/<session>.jsonl`), file history snapshots for checkpoints (`file-history/<session>/`), plan files, paste/image caches, subagent outputs, and debug logs are cleaned up automatically after 30 days (configurable via `cleanupPeriodDays`). `history.jsonl` (prompt history), `stats-cache.json` (token totals), and `remote-settings.json` persist until manually deleted.

**Security note**: transcripts are plaintext and not encrypted at rest. Any secret that passes through a tool (a `.env` file read, a credential in command output) lands in the transcript JSONL. Mitigation: lower `cleanupPeriodDays`, set `CLAUDE_CODE_SKIP_PROMPT_HISTORY` to suppress transcript writes, or use permission deny rules to block reads of credential files.

`claude project purge` deletes all state Claude Code holds for one project: transcripts, auto memory, per-session tasks, debug entries, and matching history lines.

## Key points

- Two root locations: `.claude/` in the project (team-shared via git) and `~/.claude/` in the home dir (personal, all projects)
- Most common edits: `CLAUDE.md`, `settings.json`, `skills/`, `agents/`, `.mcp.json`
- `~/.claude/` holds both config (persistent until deleted) and session data (auto-purged after 30 days)
- Transcripts are plaintext — any secret that enters a tool call lands in the JSONL; use `cleanupPeriodDays` and deny rules to limit exposure
- `claude project purge` removes all project state including auto memory; `--all` purges all projects

## Connections

- [[wiki/pages/claude-directory]] — the wiki concept page for this reference
- [[wiki/pages/claude-md]] — CLAUDE.md files live at project root or in .claude/
- [[wiki/pages/claude-code]] — the environment that reads all these files
- [[wiki/pages/skills]] — `skills/<name>/SKILL.md` structure lives here
- [[wiki/pages/sub-agents]] — `agents/*.md` files define custom subagents
- [[wiki/pages/memory-in-claude]] — auto memory stored at `~/.claude/projects/<project>/memory/`
