---
type: page
created: 2026-05-31
updated: 2026-05-31
tags: [claude-desktop, ai4gamma-corso]
---

Claude Desktop is the Windows application version of Anthropic's Claude platform, providing a unified interface across three distinct operating modes.

## Overview

Claude Desktop exposes three modes from its top bar: Chat (standard conversational use), Claude Code (terminal-integrated agentic development environment), and Cowork (autonomous multi-step task execution in an isolated virtual machine). The sidebar organizes conversations and projects; a recommended practice is to adopt a naming convention for chats (e.g., project-code prefix like `COR-001`) to keep them retrievable as their number grows. Each chat is best treated as a discrete task: start, work, output, close.

## Key dimensions

### Operating modes

Chat/Desktop handles analysis, drafting, research, and prompt engineering. Claude Code is the agentic CLI designed for software implementation with line-by-line diff review and explicit change approval. Cowork runs autonomous multi-step tasks producing files (Word, Excel, PowerPoint) in a virtual machine, suited to non-technical workflows that don't require step-by-step control. [[wiki/sources/manuale-prima-lezione]]

### Chat management

The sidebar lists conversations in reverse chronological order. Naming chats with a structured prefix (e.g., `SB1-023 – SAP query analysis`) enables filtering without opening them individually. Project chats are grouped separately from free chats and are the recommended default for recurring tasks. [[wiki/sources/manuale-prima-lezione]]

### Search

Two search mechanisms are available: simple search (title-only, accessible from the Chats panel sidebar — effective only with structured naming) and contextual search (Ctrl+K, searches within message body content). [[wiki/sources/manuale-prima-lezione]]

### Plans and token limits

Claude Desktop is available on individual plans (Pro, Max), team plans (minimum 5 users), enterprise plans, and API consumption plans. Plan Max provides approximately 5× the context window capacity of Plan Pro and access to preview features. Token consumption is tracked in Settings → Usage with daily resets. [[wiki/sources/manuale-prima-lezione]]

### Desktop Code tab features

The Code tab in the Desktop app is a graphical Claude Code interface designed for parallel sessions and visual review. Key capabilities beyond the CLI:

**Parallel sessions with git worktrees**: each new session gets its own isolated git worktree at `.claude/worktrees/` (configurable). Changes in one session don't affect others until committed. Sessions can be viewed side-by-side (Cmd/Ctrl+click in the sidebar). Auto-archive on PR merge/close is configurable.

**Diff view and code review**: after Claude edits files, a `+N -M` indicator appears. Click it to open the diff viewer. Add inline comments on specific lines and submit all at once. "Review code" asks Claude to evaluate the diffs and leave inline suggestions — focused on compile errors, logic errors, security issues, and obvious bugs.

**PR monitoring**: after opening a PR, a CI status bar tracks check results. Auto-fix iterates on failing checks; auto-merge merges the PR once all checks pass (squash merge; requires GitHub auto-merge enabled in the repo).

**Preview server**: Claude starts a dev server and verifies its own changes via an embedded browser. Auto-verify (on by default) takes screenshots and inspects the DOM after every edit. Configure via `.claude/launch.json`.

**Computer use** (macOS + Windows, Pro/Max only): Claude can open apps, click, type, and control the screen. Browser windows are view-only; terminals/IDEs are click-only; all other apps get full control.

**Dispatch**: Dispatch (in the Cowork tab) accepts tasks from your phone and spawns Code sessions for development work automatically. Requires Pro or Max plan.

**Environments**: Local (your machine), Remote (Anthropic cloud — continues after you close the app), SSH (remote machine, Desktop installs Claude Code automatically on first connect).

[[wiki/sources/desktop-application-claude-code-docs]] [[wiki/sources/get-started-with-the-desktop-app-claude-code-docs]]

### CLI vs. Desktop — what's different

Desktop adds visual review, Dispatch, Preview server, and git worktree automation. The CLI adds: `dontAsk` permission mode, agent teams, third-party providers (Bedrock/Foundry), and Linux support. Configuration (CLAUDE.md, MCP servers, hooks, skills, settings.json) is fully shared. `/desktop` moves a CLI session to Desktop; `/cli` or `claude --teleport` moves the other way. [[wiki/sources/desktop-application-claude-code-docs]]

## Connections

- [[wiki/pages/artifacts]] — output format available across all modes
- [[wiki/pages/claude-projects]] — the persistent workspace system within Claude Desktop
- [[wiki/pages/mcp-model-context-protocol]] — extensions that expand Claude Desktop's capabilities
- [[wiki/pages/memory-in-claude]] — how Claude stores user preferences and project context across sessions
- [[wiki/pages/context-window]] — the in-session information budget

## Sources

- [[wiki/sources/manuale-prima-lezione]] — full interface overview, operating modes, chat management, and plans
- [[wiki/sources/desktop-application-claude-code-docs]] — Code tab features: parallel sessions, diff view, computer use, Dispatch, SSH, Preview, enterprise config
- [[wiki/sources/get-started-with-the-desktop-app-claude-code-docs]] — Desktop quickstart: environments, first session, key features overview
- [[wiki/sources/use-claude-code-in-vs-code-claude-code-docs]] — VS Code extension as alternative graphical interface; built-in MCP server; permission modes match CLI
