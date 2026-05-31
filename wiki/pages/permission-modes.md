---
type: page
created: 2026-05-31
updated: 2026-05-31
tags: [claude-code, permissions]
---

Permission modes control how often Claude Code pauses to request approval before editing files or running commands, setting the balance between oversight and autonomous operation.

## Overview

Every action Claude Code takes — file edits, shell commands, network requests — passes through a permission layer that decides whether to prompt the user, auto-approve, or auto-deny. The active mode sets the baseline for this layer. Modes range from full oversight (default, prompt before every action) to full autonomy (bypassPermissions, no checks). Most users operate between these extremes: acceptEdits for fast iteration on trusted tasks, plan for pre-reviewing large changes, and auto for extended autonomous runs with background safety checks.

## Key dimensions

### The six modes

| Mode | What runs without asking | Best for |
|------|--------------------------|----------|
| `default` | Reads only | New users, sensitive work, learning |
| `acceptEdits` | File edits + filesystem commands (mkdir, touch, rm, mv, cp, sed) | Fast iteration; reviewing changes via git diff |
| `plan` | Reads only (Claude writes a plan but makes no edits until approved) | Large refactors, unknown codebases |
| `auto` | Everything passing the classifier (read ops, working-dir edits, declared-dep installs, read-only HTTP, push to current branch) | Extended autonomous runs with oversight |
| `dontAsk` | Only pre-approved `permissions.allow` rules + read-only commands | Fully non-interactive CI pipelines |
| `bypassPermissions` | Everything (no checks) | Isolated containers/VMs only |

[[wiki/sources/choose-a-permission-mode-claude-code-docs]]

### Switching modes

In the CLI, press `Shift+Tab` to cycle default → acceptEdits → plan. Set `defaultMode` in `settings.json` for a persistent default. Pass `--permission-mode <mode>` at startup for a single session. `auto` appears in the cycle only when your account meets requirements (Opus/Sonnet 4.6+, Anthropic API only); `bypassPermissions` appears only after starting with the enabling flag. [[wiki/sources/choose-a-permission-mode-claude-code-docs]]

### The auto mode classifier

Auto mode runs a server-side classifier model that evaluates each action before execution. The classifier works independently of your `/model` selection and adds a round-trip before shell commands and network operations (reads and working-dir edits skip it). By default the classifier blocks: downloading and executing code (curl | bash), sending credentials to unknown endpoints, production deploys and migrations, mass cloud storage deletion, IAM permission changes, and force-pushes to main. It allows: local file operations, installing dependencies declared in lock files, read-only HTTP, and pushing to the current working branch. If the classifier blocks an action 3 consecutive times or 20 times in total, auto mode falls back to manual prompting. [[wiki/sources/choose-a-permission-mode-claude-code-docs]]

### Protected paths

Writes to a small set of paths are never auto-approved in any mode except `bypassPermissions`, preventing accidental corruption of repository state and Claude's own configuration. Protected: `.git/`, `.vscode/`, `.idea/`, `.husky/`, `.cargo/`, `.claude/` (except its `commands/`, `agents/`, `skills/`, and `worktrees/` subdirectories), `.gitconfig`, `.bashrc`/`.zshrc`/`.profile`, `.ripgreprc`, `.mcp.json`, `.claude.json`. [[wiki/sources/choose-a-permission-mode-claude-code-docs]]

### Checkpoints: the undo complement

Before Claude edits any file, it snapshots the current contents. If something goes wrong, press Esc twice to open the rewind menu, or run `/rewind`. Options: restore code only, restore conversation only, or both. Checkpoints are local to the session, separate from git. They do not cover actions that affect remote systems — which is why Claude asks before running commands with external side effects. [[wiki/sources/how-claude-code-works-claude-code-docs]]

## Connections

- [[wiki/pages/claude-code]] — the environment where permission modes apply
- [[wiki/pages/sessions-management]] — checkpoints and rewind operate within sessions
- [[wiki/pages/plan-mode]] — plan mode as a dedicated concept page within the six-mode spectrum

## Sources

- [[wiki/sources/choose-a-permission-mode-claude-code-docs]] — all six modes, auto classifier, protected paths, switching mechanics
- [[wiki/sources/how-claude-code-works-claude-code-docs]] — checkpoint/rewind mechanism
