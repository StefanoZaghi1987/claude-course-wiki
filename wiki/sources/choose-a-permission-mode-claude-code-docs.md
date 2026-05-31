---
type: source
created: 2026-05-31
updated: 2026-05-31
tags: [claude-code, permissions, official-docs]
source_url: https://code.claude.com/docs/en/permission-modes
source_path: raw/web/choose-a-permission-mode-claude-code-docs/
---

Official reference for Claude Code's permission mode system — the six modes, switching mechanics, auto mode classifier, and protected paths (May 2026).

## Summary

Permission modes control how often Claude pauses to ask for approval before acting. Claude Code ships six modes with different tradeoffs between oversight and autonomy:

**default**: Claude reads without prompting; asks before every file edit and shell command. Best for sensitive work and new users.

**acceptEdits**: file edits and common filesystem commands (mkdir, touch, rm, mv, cp, sed, and their PowerShell equivalents) run without prompting. Claude still asks for other shell commands. Best for users who prefer to review via `git diff` after the fact rather than approving each change inline.

**plan**: Claude uses only read-only tools to explore and write a plan, then waits for explicit approval before executing. No source files are modified until the user approves the plan. Useful before large refactors.

**auto**: a server-side classifier model evaluates each action before execution. Read-only actions and file edits in the working directory are auto-approved; everything else goes to the classifier. The classifier blocks scope escalation (e.g., curl | bash, production deploys, mass deletion, granting IAM permissions, force-pushing to main) and allows routine work (file operations, installing declared dependencies, read-only HTTP, pushing to the working branch). Requires Claude Opus 4.6+ or Sonnet 4.6, Anthropic API only. If the classifier blocks an action 3 consecutive times or 20 times total, auto mode falls back to prompting.

**dontAsk**: auto-denies every action that would otherwise prompt; only actions matching explicit `permissions.allow` rules can execute. Designed for fully non-interactive CI pipelines.

**bypassPermissions**: disables all permission checks and safety checks so tool calls execute immediately. Only for isolated environments (containers, VMs, dev containers). Cannot be entered from a running session — must be started with `--dangerously-skip-permissions` or `--permission-mode bypassPermissions`.

Modes are switched with Shift+Tab (cycles default → acceptEdits → plan in the CLI), a startup flag (`--permission-mode`), or `defaultMode` in settings. Protected paths are never auto-approved in any mode except bypassPermissions: `.git`, `.vscode`, `.idea`, `.husky`, `.claude` (except commands/agents/skills/worktrees subdirs), shell profile files, `.mcp.json`, `.claude.json`.

The auto mode classifier uses conversation history, tool calls, and CLAUDE.md content. Tool results are stripped so hostile content in a file or web page cannot manipulate it directly. Conversation-stated boundaries ("don't push", "wait until I review") act as block signals for the classifier and persist until explicitly lifted — but can be lost after compaction, so use deny rules for hard guarantees.

## Key points

- Six modes from most to least oversight: default → acceptEdits → plan → auto → dontAsk → bypassPermissions
- `acceptEdits` auto-approves file edits and common filesystem commands; other shell commands still prompt
- `auto` uses a server-side classifier; blocks scope escalation by default; falls back to prompting after 3 consecutive or 20 total blocks
- `bypassPermissions` requires `--dangerously-skip-permissions` at startup; cannot be entered mid-session
- Protected paths are never auto-approved in any mode except bypassPermissions: includes .git, .vscode, .claude, shell profiles
- Conversation boundaries ("don't push") block the auto classifier but can be lost after compaction — use `permissions.deny` rules for hard guarantees

## Connections

- [[wiki/pages/permission-modes]] — the wiki concept page for this system
- [[wiki/pages/claude-code]] — the environment where modes apply
- [[wiki/pages/sessions-management]] — checkpoints (file snapshots) are the undo mechanism companion to permissions
