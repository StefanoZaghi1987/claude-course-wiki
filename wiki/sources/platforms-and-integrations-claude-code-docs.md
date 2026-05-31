---
type: source
created: 2026-05-31
updated: 2026-05-31
tags: [claude-code, platforms, official-docs]
source_url: https://code.claude.com/docs/en/platforms
source_path: raw/web/platforms-and-integrations-claude-code-docs/
---

Overview of all Claude Code surfaces and integrations — choosing the right platform and connecting external tools (May 2026).

## Summary

Claude Code runs the same underlying engine on all surfaces; the surface choice determines where execution happens and how you interact. The main platforms are: Terminal CLI (full features, third-party provider support), Desktop app (visual review, parallel sessions, computer use, Dispatch on Pro/Max), VS Code extension (inline diffs, @-mentions, plan review), JetBrains extension (same capabilities as VS Code), Web (cloud infrastructure, sessions continue when disconnected), Mobile (iOS/Android, thin client into cloud or local sessions via Remote Control).

Desktop and IDE extensions trade some CLI-only features for visual review and tighter editor integration. The web runs on Anthropic's cloud, so tasks continue after you disconnect. Mobile is a thin client into cloud sessions or into a local session via Remote Control, and can dispatch tasks to Desktop.

Integrations extend Claude Code's reach: GitHub Actions and GitLab CI/CD for CI automation, GitHub Code Review for automatic per-PR review, Slack for `@Claude` mentions in team channels, MCP servers and connectors for almost anything else (Linear, Notion, Google Drive, custom APIs). Chrome extension for browser automation.

For working away from your terminal, four options exist with different tradeoffs: Dispatch (phone → Desktop session, no setup), Remote Control (continue a running local session from any device), Channels (push events from chat apps into a session), Slack (`@Claude` in a channel with Claude Code on the web enabled), and Scheduled tasks (recurring prompts on CLI, Desktop, or cloud infrastructure).

## Key points

- Six surface types: CLI (full features), Desktop (visual + parallel + Dispatch), VS Code, JetBrains, Web (cloud, persists when disconnected), Mobile (thin client)
- Configuration (CLAUDE.md, MCP servers, settings) is shared across all local surfaces; web/mobile share cloud session state
- Integrations: GitHub Actions, GitLab CI/CD, Code Review (automatic PR), Slack, Chrome, MCP connectors
- Four away-from-terminal options: Dispatch, Remote Control, Channels, Slack — differ in trigger, execution location, and setup required

## Connections

- [[wiki/pages/claude-code]] — the CLI at the center
- [[wiki/pages/claude-desktop]] — the Desktop app surface
- [[wiki/pages/remote-control]] — continue local sessions from any device
- [[wiki/pages/mcp-model-context-protocol]] — the integration protocol
