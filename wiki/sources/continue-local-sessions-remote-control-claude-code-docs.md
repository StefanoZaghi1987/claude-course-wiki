---
type: source
created: 2026-05-31
updated: 2026-05-31
tags: [claude-code, remote-control, official-docs]
source_url: https://code.claude.com/docs/en/remote-control
source_path: raw/web/continue-local-sessions-from-any-device-with-remote-control-claude-code-docs/
---

Reference for Remote Control — continuing a local Claude Code session from any browser or mobile device while keeping execution on your machine (May 2026).

## Summary

Remote Control connects claude.ai/code or the Claude mobile app to a Claude Code session running on your local machine. The session keeps running locally the entire time — nothing moves to the cloud. Your filesystem, MCP servers, tools, and project configuration stay fully available. You can type from your terminal, browser, and phone interchangeably, and the conversation stays in sync across all connected devices. If your laptop sleeps or your network drops, the session reconnects automatically when the machine comes back online.

Remote Control is distinct from Claude Code on the web (which runs on Anthropic cloud infrastructure). Use Remote Control when you are mid-task on a local project and want to keep going from another device. Use Claude Code on the web when you want to start a new task without local setup or run multiple tasks in parallel on cloud infrastructure.

Starting a Remote Control session: `claude remote-control` (server mode — stays running, handles multiple concurrent connections), `claude --remote-control` inside a new interactive session, or `/remote-control` inside a running session. Server mode supports multiple concurrent sessions via `--spawn worktree` (each connection gets its own git worktree) or `--spawn session` (single-session mode). The terminal displays a session URL and QR code (spacebar toggles the QR).

Connecting from another device: open the session URL in any browser, scan the QR code with the Claude mobile app, or open claude.ai/code and find the session by name. Remote Control sessions show a computer icon with a green dot when online.

Push notifications work when Remote Control is active: Claude sends one when a long-running task finishes or when it needs a decision. Request them explicitly in your prompt ("notify me when the tests finish").

Security model: the local Claude Code process makes outbound HTTPS requests only and never opens inbound ports. All traffic routes through the Anthropic API over TLS. Multiple short-lived credentials, each scoped to a single purpose, handle authentication. Remote Control requires claude.ai OAuth — not API key authentication.

Limitations: one remote session per interactive process (use server mode for multiple); the local process must keep running; network outage > ~10 minutes causes session timeout; some interactive CLI commands (e.g., `/mcp`, `/resume`) work only from the local terminal.

## Key points

- Execution stays on your machine; browser/mobile is just the interface — filesystem, MCP, and tools remain available
- Three start modes: server mode (multiple concurrent sessions), `--remote-control` flag (interactive session), `/remote-control` command (existing session)
- `--spawn worktree` gives each concurrent connection its own git worktree; `--spawn session` is single-session only
- Push notifications available when active; Claude decides when to send; explicit requests in the prompt work
- Security: outbound HTTPS only, no inbound ports, all traffic through Anthropic API over TLS
- Requires claude.ai OAuth subscription (Pro/Max/Team/Enterprise) — API keys not supported

## Connections

- [[wiki/pages/remote-control]] — the wiki concept page
- [[wiki/pages/claude-code]] — the local session being remotely accessed
- [[wiki/pages/sessions-management]] — session continuity mechanics
- [[wiki/pages/claude-desktop]] — Dispatch is the alternative for phone → Desktop tasks
