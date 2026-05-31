---
type: source
created: 2026-05-31
updated: 2026-05-31
tags: [claude-code, sessions, official-docs]
source_url: https://code.claude.com/docs/en/sessions
source_path: raw/web/manage-sessions-claude-code-docs/
---

Reference guide for Claude Code session lifecycle — resuming, naming, branching, the session picker, and transcript storage (May 2026).

## Summary

A Claude Code session is a saved conversation tied to a project directory. Sessions are written continuously to JSONL files at `~/.claude/projects/<project>/<session-id>.jsonl` as you work, enabling resume, fork, and branch operations without losing history. This page covers CLI session management; Desktop, web, and VS Code each maintain their own session history.

Four entry points for resuming: `claude --continue` (resumes most recent session in current directory), `claude --resume` (opens the interactive session picker), `claude --resume <name>` (resumes by name — resolves across the current repository and its worktrees), and `claude --from-pr <number>` (resumes the session associated with a GitHub PR). The `/resume` command inside a running session opens the picker or resumes by name with the same resolution rules.

The session picker shows interactive sessions from the current worktree by default. Keyboard shortcuts expand the scope: Ctrl+W widens to all worktrees of the repository; Ctrl+A widens to every project on the machine; Ctrl+B filters to the current git branch. Forked sessions group under their root in the picker (→ to expand).

Sessions can be named at startup (`claude -n auth-refactor`), renamed during a session (`/rename auth-refactor`), or renamed from the picker (highlight + Ctrl+R). When a plan is accepted, Claude also auto-names the session from the plan content unless a name was already set. Descriptive names enable `claude --resume <name>` from any terminal.

Branching creates a copy of the conversation history without modifying the original: `/branch [name]` inside a session, or `--fork-session` on the command line with `--continue` or `--resume`. The branch confirmation prints both session IDs. Permissions approved with "allow for this session" do not carry over to the branch. For checkpoint-based rewind (file snapshots without creating a new session), use Esc+Esc or `/rewind`.

Three in-session context control commands: `/clear` (fresh context, previous session remains resumable), `/compact [instructions]` (replace history with a summary, optionally focused), `/context` (show current context window usage by category).

Session data is removed after 30 days by default (configurable via `cleanupPeriodDays`). To suppress transcript writes entirely, set `CLAUDE_CODE_SKIP_PROMPT_HISTORY` or pass `--no-session-persistence` in non-interactive mode.

## Key points

- Sessions stored as JSONL at `~/.claude/projects/<project>/<session-id>.jsonl`; auto-deleted after 30 days by default
- Four resume entry points: `--continue` (most recent), `--resume` (picker), `--resume <name>` (by name), `--from-pr <number>` (by PR)
- Session picker: Ctrl+W (all worktrees), Ctrl+A (all projects), Ctrl+B (current branch), → (expand forks)
- Branching (`/branch`) copies history into a new session ID, leaving the original intact; permissions do not carry over
- `/clear` resets context but keeps session resumable; `/compact` summarizes; `/context` shows usage
- `cleanupPeriodDays` controls transcript retention; `CLAUDE_CODE_SKIP_PROMPT_HISTORY` suppresses writes

## Connections

- [[wiki/pages/sessions-management]] — the wiki concept page for this system
- [[wiki/pages/claude-code]] — the environment where sessions live
- [[wiki/pages/context-window]] — /compact and /context commands work within sessions
