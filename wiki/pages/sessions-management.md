---
type: page
created: 2026-05-31
updated: 2026-05-31
tags: [claude-code, sessions]
---

A Claude Code session is a saved conversation tied to a project directory — the unit of work that can be resumed, branched, renamed, and rewound across multiple sittings.

## Overview

Claude Code saves every conversation continuously as a JSONL file on disk. This means sessions are never lost on exit; you can return to any past session, branch it to try an alternative approach, or rewind to an earlier checkpoint. Each new session starts with a fresh context window — auto memory and CLAUDE.md carry knowledge forward, but the conversation history does not carry over automatically. Sessions are tied to directories: switching branches changes the files Claude sees but not the conversation history.

## Key dimensions

### Storage and lifecycle

Sessions are stored at `~/.claude/projects/<project>/<session-id>.jsonl`. The `<project>` path is derived from the working directory. Sessions are auto-deleted after 30 days (configurable via `cleanupPeriodDays`). To suppress transcript writes entirely, set `CLAUDE_CODE_SKIP_PROMPT_HISTORY` or pass `--no-session-persistence` in non-interactive (`-p`) mode. [[wiki/sources/manage-sessions-claude-code-docs]]

### Resume entry points

| Command | What it does |
|---------|-------------|
| `claude --continue` | Resumes most recent session in the current directory |
| `claude --resume` | Opens the interactive session picker |
| `claude --resume <name>` | Resumes by name across the current repository and its worktrees |
| `claude --from-pr <number>` | Resumes the session associated with a GitHub PR |
| `/resume` | Opens the picker from inside a running session |
| `/resume <name>` | Resumes by name (reports an error if ambiguous — use `/resume` to open the picker) |

[[wiki/sources/manage-sessions-claude-code-docs]]

### Session picker keyboard shortcuts

The picker defaults to interactive sessions from the current worktree. Keyboard shortcuts expand scope:

| Shortcut | Action |
|----------|--------|
| Ctrl+W | Widen to all worktrees of the current repository |
| Ctrl+A | Widen to all projects on this machine |
| Ctrl+B | Filter to sessions from the current git branch |
| → / ← | Expand or collapse forked session groups |
| Space / Ctrl+V | Preview session content |
| Ctrl+R | Rename the highlighted session |
| / or any printable char | Enter search mode; paste a PR URL to find its session |
| Esc | Exit picker or search mode |

[[wiki/sources/manage-sessions-claude-code-docs]]

### Naming sessions

Descriptive names make sessions findable by `--resume <name>` from any terminal. Set at startup (`claude -n auth-refactor`), rename during a session (`/rename auth-refactor`), rename from the picker (Ctrl+R), or accept the auto-generated name when approving a plan. Sessions created by `-p` non-interactive mode or the Agent SDK don't appear in the picker but can be resumed by passing their session ID to `--resume`. [[wiki/sources/manage-sessions-claude-code-docs]]

### Branching and forking

`/branch [name]` creates a copy of the conversation history in a new session ID, leaving the original unchanged. The confirmation output prints both session IDs. Permissions approved with "allow for this session" do not carry over to the branch. For checkpoint-based rewind *within* a single session (restoring files to an earlier state without creating a new session), use Esc+Esc or `/rewind`. [[wiki/sources/manage-sessions-claude-code-docs]]

### In-session context controls

Three commands control what's in the context window without leaving the session: `/clear` starts fresh context (previous conversation remains resumable), `/compact [instructions]` replaces history with a summary optionally focused on what you specify, and `/context` shows what is currently consuming context space. [[wiki/sources/manage-sessions-claude-code-docs]]

### Parallel sessions with worktrees

Since sessions are tied to directories, parallel Claude Code sessions require separate directories. Git worktrees create separate checkouts on their own branches, each with its own conversation and file state. This is the recommended pattern for working on a feature in one terminal while Claude fixes a bug in another without edits colliding. [[wiki/sources/manage-sessions-claude-code-docs]]

## Connections

- [[wiki/pages/claude-code]] — the environment where sessions live
- [[wiki/pages/context-window]] — /compact and /context operate within sessions
- [[wiki/pages/permission-modes]] — checkpoints (file snapshots) are the undo complement to permissions

## Sources

- [[wiki/sources/manage-sessions-claude-code-docs]] — session lifecycle, resume, naming, branching, picker, transcript storage
- [[wiki/sources/how-claude-code-works-claude-code-docs]] — session model, JSONL storage, resume and fork mechanics
