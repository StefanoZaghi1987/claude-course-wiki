---
type: source
created: 2026-05-31
updated: 2026-05-31
tags: [claude-code, official-docs]
source_url: https://code.claude.com/docs/en/overview
source_path: raw/web/overview-claude-code-docs/
---

Official Anthropic landing-page overview of Claude Code — capabilities, available surfaces, and cross-surface mobility (May 2026).

## Summary

Claude Code is an AI-powered coding assistant that understands an entire codebase and can work across multiple files and tools to accomplish tasks. It is available in the terminal CLI, VS Code and JetBrains IDE extensions, a dedicated Desktop app, a web interface, and mobile — every surface runs the same underlying engine, so CLAUDE.md files, settings, and MCP servers work everywhere.

The core capabilities fall into six clusters. First, task automation: writing tests for untested code, fixing lint errors, resolving merge conflicts, updating dependencies, writing release notes. Second, feature work and bug fixing: Claude plans the approach, writes code across multiple files, and verifies it works; for bugs it traces the issue through the codebase and implements a fix. Third, git integration: staging changes, writing commit messages, creating branches, opening pull requests; in CI, GitHub Actions and GitLab CI/CD automation is available. Fourth, MCP connections: the Model Context Protocol lets Claude read design docs in Google Drive, update Jira tickets, pull Slack data, or call custom internal tooling. Fifth, customization via CLAUDE.md (persistent project instructions), skills (reusable workflows), and hooks (shell commands that fire on lifecycle events). Sixth, agent teams: a lead agent coordinates multiple Claude Code sub-agents that work in parallel on different subtasks.

For automation, Claude Code follows Unix philosophy — it can be piped, scripted, and chained. Scheduled Routines run on Anthropic-managed infrastructure and can trigger on API calls or GitHub events; Desktop scheduled tasks run locally. The `/loop` command repeats a prompt within a CLI session for quick polling.

Cross-surface mobility is a core design goal: Remote Control lets you continue a local session from any browser or phone without moving execution to the cloud; Dispatch lets you send a task from your phone to Desktop; `claude --teleport` pulls a web or iOS session into the terminal; `/desktop` hands off a terminal session to the Desktop app for visual diff review.

## Key points

- All surfaces (CLI, VS Code, JetBrains, Desktop, Web, mobile) share the same engine — CLAUDE.md, MCP servers, and settings are consistent across them
- Six capability areas: task automation, feature/bug work, git operations, MCP tool connections, CLAUDE.md/skills/hooks customization, agent teams and parallel sub-agents
- Routines run on Anthropic infrastructure even when your machine is off; Desktop scheduled tasks run locally with direct filesystem access
- Remote Control, Dispatch, teleport, and `/desktop` enable session continuity across surfaces without losing local execution

## Connections

- [[wiki/pages/claude-code]] — the CLI at the center of all surfaces
- [[wiki/pages/mcp-model-context-protocol]] — the protocol powering external tool connections
- [[wiki/pages/skills]] — reusable workflows invokable as slash commands
- [[wiki/pages/sub-agents]] — parallel agent execution within a session
- [[wiki/pages/claude-md]] — the persistent project configuration file
- [[wiki/pages/plugins]] — bundles of skills, hooks, MCP servers, and sub-agents
- [[wiki/pages/remote-control]] — continue local sessions from any device
