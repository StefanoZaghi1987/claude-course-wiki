---
type: source
created: 2026-05-31
updated: 2026-05-31
tags: [claude-code, claude-desktop, official-docs]
source_url: https://code.claude.com/docs/en/desktop-quickstart
source_path: raw/web/get-started-with-the-desktop-app-claude-code-docs/
---

Quickstart for the Claude Code Desktop app — download, first session, and key features to try (May 2026).

## Summary

The Desktop app is available for macOS (universal) and Windows (x64 and ARM64). Not available on Linux — use the CLI instead. Requires a Pro, Max, Team, or Enterprise subscription. Download from claude.ai/download, install, sign in, then click the Code tab.

The Code tab has three environment choices: Local (your machine, default, direct file access), Remote (Anthropic cloud, continues after you close the app), and SSH (remote machine you manage). For local sessions, choose a folder and a model, then send a prompt. By default the Code tab starts in Ask permissions mode — Claude shows a diff and waits for approval before every edit.

Key things to explore after the first edit: interrupt Claude anytime by clicking Stop or typing a correction; add context with `@filename`, file attachments, or drag-and-drop; use `/` to browse built-in commands, custom skills, and plugin skills; open the diff view (`+N -M` indicator) to review and comment on changes; adjust permission mode (Ask → Auto accept edits → Plan); install plugins via the `+` button; arrange chat/diff/terminal/preview panes in any layout; use the Preview dropdown to run a dev server and let Claude verify changes visually; track CI status after opening a PR; set up scheduled tasks for recurring automation; open parallel sessions from the sidebar.

Desktop and CLI are interoperable: run both simultaneously on the same project, share CLAUDE.md/MCP/hooks/settings, and move a CLI session to Desktop with `/desktop`.

## Key points

- macOS and Windows only; requires paid subscription; installs from claude.ai/download
- Three environment types: Local, Remote (cloud, persists after close), SSH
- Default mode: Ask permissions — Claude shows diffs, waits for approval
- Interoperable with CLI: `/desktop` moves a CLI session to Desktop; shared config
- Key features to unlock: Preview (dev server + visual verification), diff view + review, parallel sessions, scheduled tasks, plugins

## Connections

- [[wiki/pages/claude-desktop]] — the Desktop app wiki page
- [[wiki/pages/claude-code]] — the CLI that shares configuration
- [[wiki/pages/permission-modes]] — permission modes available in the Desktop Code tab
- [[wiki/pages/plugins]] — plugins installed via the + button in Desktop Code
- [[wiki/pages/skills]] — skills accessible via the / command menu in Desktop Code
