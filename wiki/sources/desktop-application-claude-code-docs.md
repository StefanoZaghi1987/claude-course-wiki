---
type: source
created: 2026-05-31
updated: 2026-05-31
tags: [claude-code, claude-desktop, official-docs]
source_url: https://code.claude.com/docs/en/desktop
source_path: raw/web/desktop-application-claude-code-docs/
---

Full reference for the Claude Code Desktop app's Code tab — parallel sessions, diff view, computer use, Dispatch, SSH, Preview server, pane layout, and enterprise configuration (May 2026).

## Summary

The Claude Desktop app has three tabs: Chat (conversation), Cowork (Dispatch and agentic background tasks), and Code (software development). The Code tab is a graphical Claude Code interface built for parallel sessions and visual review. Each Code session has its own conversation history, project folder, and file changes — sessions are independent by design.

Desktop runs the same engine as the CLI; configuration is shared (CLAUDE.md files, MCP servers, hooks, skills, settings). Differences: Desktop adds visual diff review, parallel sessions with automated git worktree isolation, an integrated terminal, app preview, PR monitoring with auto-fix/auto-merge, and Dispatch sessions from your phone. The CLI has features not available in Desktop: `dontAsk` permission mode, third-party providers (Bedrock/Foundry — VS Code/CLI only), Linux (Desktop is macOS/Windows only), inline agent teams.

**Parallel sessions with git worktrees**: each new session gets its own isolated git worktree at `.claude/worktrees/` by default. Changes in one session don't affect others until committed. Sessions can be viewed side by side (Cmd/Ctrl+click in the sidebar). Sessions auto-archive after PR merge/close when auto-archive is enabled.

**Diff view and code review**: after Claude makes changes, a `+12 -1` indicator appears. Click it to open the diff viewer. Add inline comments on specific lines (Enter to add, Cmd/Ctrl+Enter to submit all). Click "Review code" to have Claude leave inline suggestions on the diffs — it focuses on compile errors, logic errors, security vulnerabilities, and obvious bugs (not style or linting).

**PR monitoring**: after opening a PR, a CI status bar appears. Auto-fix has Claude iterate on failing CI checks. Auto-merge merges the PR (squash) once all checks pass (requires GitHub auto-merge enabled in repo settings). Uses the `gh` CLI.

**Preview server**: Claude starts a dev server and opens an embedded browser to verify its changes. Auto-verify (on by default) has Claude take screenshots and inspect the DOM after every edit. Configure via `.claude/launch.json` in the project root. Supports Next.js, multiple servers, Node.js scripts.

**Computer use** (macOS and Windows, Pro/Max only): Claude can open apps, click, type, and control the screen. Restricted by app tier: browsers view-only, terminals/IDEs click-only, everything else full control. Requires enabling in Settings + macOS Accessibility and Screen Recording permissions.

**Dispatch sessions**: Dispatch (in the Cowork tab) lets you message a task from your phone; if it is development work, Dispatch spawns a Code session automatically. Requires Pro or Max plan.

**SSH sessions**: connect to remote machines over SSH. Desktop installs Claude Code on the remote machine automatically on first connect. Enterprise admins can pre-configure SSH connections and restrict allowed hosts via `sshConfigs` and `sshHostAllowlist` in managed settings.

**Enterprise**: managed settings override user/project settings. Admins can control permission modes (`permissions.disableBypassPermissionsMode`, `disableAutoMode`), configure auto mode behavior (`autoMode`), pre-distribute SSH connections, restrict SSH hosts, and deploy via MDM (macOS) or MSIX/Group Policy (Windows).

## Key points

- Code tab = graphical Claude Code with git worktree isolation per session, visual diff review, PR monitoring, Preview, and Dispatch
- Shared config with CLI: CLAUDE.md, MCP, hooks, skills, settings.json all apply to both
- Parallel sessions: each gets its own git worktree; view two sessions side-by-side; auto-archive on PR close
- Computer use: available on macOS+Windows Pro/Max; tier-capped by app category (browsers view-only, terminals click-only)
- Desktop not available on Linux; dontAsk mode and agent teams are CLI-only; third-party providers (Bedrock/Foundry) require CLI or VS Code
- Enterprise: managed settings distributed via MDM/MSIX; SSH connection pre-configuration and host allowlists

## Connections

- [[wiki/pages/claude-desktop]] — the wiki page for the Desktop app
- [[wiki/pages/claude-code]] — the CLI that shares configuration with Desktop
- [[wiki/pages/remote-control]] — alternative way to access a local session from another device
- [[wiki/pages/sessions-management]] — session lifecycle applies to Desktop Code tab sessions
- [[wiki/pages/permission-modes]] — all modes available in Desktop except dontAsk
