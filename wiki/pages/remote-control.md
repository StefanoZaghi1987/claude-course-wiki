---
type: page
created: 2026-05-31
updated: 2026-05-31
tags: [claude-code, remote-control]
---

Remote Control lets you continue a local Claude Code session from any browser or mobile device while keeping all execution on your own machine.

## Overview

When you start a Remote Control session, Claude Code registers with Anthropic's API and makes itself accessible via a session URL. You can then connect from claude.ai/code or the Claude mobile app and interact with the running session as if you were at the terminal — the conversation stays in sync across all connected surfaces simultaneously. The key distinction from Claude Code on the web is that execution never moves to the cloud: your local filesystem, MCP servers, tools, and project configuration remain fully available. Remote Control is in research preview and available on all plans.

## Key dimensions

### Starting a session

Three invocation forms from the CLI: `claude remote-control` (server mode — stays running in the terminal, handles multiple concurrent connections), `claude --remote-control` (embedded in a new interactive session), and `/remote-control` (activate inside a running session). The VS Code extension provides the same via `/remote-control` in the prompt box. Server mode displays a session URL and QR code (press spacebar to toggle the QR); press `w` at runtime to toggle between `same-dir` and `worktree` spawn modes. [[wiki/sources/continue-local-sessions-remote-control-claude-code-docs]]

### Connecting from another device

Three connection methods: open the session URL in any browser to go directly to claude.ai/code, scan the QR code with the Claude mobile app, or open claude.ai/code and find the session by name in the session list (Remote Control sessions show a computer icon with a green dot when online). Session names are derived from the `--name` flag, `/rename`, the last meaningful message, or an auto-generated hostname prefix. [[wiki/sources/continue-local-sessions-remote-control-claude-code-docs]]

### Spawn modes (server mode)

`--spawn same-dir` (default): all concurrent connections share the current working directory. `--spawn worktree`: each on-demand connection gets its own git worktree, preventing edit collisions. `--spawn session`: single-session mode — the server serves exactly one session and rejects additional connections. Press `w` at runtime to toggle between `same-dir` and `worktree`. [[wiki/sources/continue-local-sessions-remote-control-claude-code-docs]]

### Push notifications

While Remote Control is active, Claude sends push notifications to your registered mobile device when a long-running task finishes or when it needs a decision. Request them explicitly in your prompt ("notify me when the tests finish"). Toggle on/off via the Remote Control settings; no per-event configuration is available. Requires Claude Code v2.1.110+. [[wiki/sources/continue-local-sessions-remote-control-claude-code-docs]]

### Security model

The local Claude Code process makes outbound HTTPS requests only — no inbound ports are opened on your machine. All traffic routes through the Anthropic API over TLS, the same transport as any Claude Code session. Multiple short-lived credentials, each scoped to a single purpose, handle authentication. Remote Control requires claude.ai OAuth; API key authentication is not supported. [[wiki/sources/continue-local-sessions-remote-control-claude-code-docs]]

### When to use Remote Control vs. alternatives

| Need | Best option |
|------|------------|
| Continue a local session from another device | Remote Control |
| Start a new task without local setup | Claude Code on the web |
| Run multiple parallel cloud tasks | Claude Code on the web |
| Phone → spawn a Desktop session | Dispatch (Cowork tab) |
| Recurring automation (cloud) | Routines |

[[wiki/sources/continue-local-sessions-remote-control-claude-code-docs]]

## Connections

- [[wiki/pages/claude-code]] — the local session being accessed remotely
- [[wiki/pages/sessions-management]] — session continuity mechanics
- [[wiki/pages/claude-desktop]] — Dispatch is the alternative for phone-initiated Desktop sessions

## Sources

- [[wiki/sources/continue-local-sessions-remote-control-claude-code-docs]] — start modes, connection methods, spawn modes, push notifications, security model
- [[wiki/sources/platforms-and-integrations-claude-code-docs]] — comparison of away-from-terminal options
