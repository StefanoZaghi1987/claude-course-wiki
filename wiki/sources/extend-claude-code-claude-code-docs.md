---
type: source
created: 2026-05-31
updated: 2026-05-31
tags: [claude-code, official-docs]
source_url: https://code.claude.com/docs/en/features-overview
source_path: raw/web/extend-claude-code-claude-code-docs/
---

Decision guide for Claude Code's extension layer — when to use CLAUDE.md vs. skills vs. subagents vs. MCP vs. hooks vs. plugins, with comparison tables and context cost breakdown (May 2026).

## Summary

Claude Code's built-in tools cover most coding tasks. The extension layer adds seven features that customize what Claude knows, connects it to external services, and automates workflows. These plug into different parts of the agentic loop: CLAUDE.md adds persistent context loaded every session; skills add reusable knowledge and invocable workflows loaded on demand; MCP connects to external services; subagents run in isolated context windows and return summaries; agent teams coordinate multiple independent sessions; hooks fire on lifecycle events and execute scripts, HTTP requests, prompts, or subagents; plugins package all of the above into installable units distributed via marketplaces.

The document provides a decision table for choosing between similar features. CLAUDE.md vs Skill: use CLAUDE.md for "always-on" rules like coding standards; use skills for reference material or workflows that don't need to be in context every session. Skill vs Subagent: skills provide reusable content inside your current context (adding to your context window); subagents run in a completely separate context window and return only a summary (no bloat to your main session). Subagent vs Agent team: a single subagent handles an isolated task; an agent team coordinates multiple independent Claude Code sessions with a shared task list and peer-to-peer messaging.

Context cost varies significantly by feature. CLAUDE.md loads fully on every request. Skills load descriptions at session start; full bodies load only when invoked (use `disable-model-invocation: true` to hide a skill from Claude until you invoke it manually, reducing cost to zero). MCP loads tool names at start; full schemas load on demand via tool search. Subagents are fully isolated from the main context. Hooks execute externally and add zero context unless the hook returns additional content.

Feature layering: CLAUDE.md files are additive — all levels (managed, user, project, local) load simultaneously, ordered from root to working directory. Skills override by name (priority: managed > user > project > plugin). MCP overrides by name (local > project > user). Hooks merge — all registered hooks fire regardless of source.

The recommended build-over-time approach: start with CLAUDE.md when Claude makes the same mistake twice, add a skill when a multi-step workflow repeats, add MCP when you need external data, add a code intelligence plugin for typed languages, add a subagent when context grows, add a hook for automation that must run on every matching event.

## Key points

- Seven extensions: CLAUDE.md, Skills, Code intelligence (LSP), MCP, Subagents, Agent teams, Hooks — Plugins package these for distribution
- Skill vs Subagent: key distinction is context isolation — skill content adds to your window; subagent work stays out entirely, only summary returns
- Context cost: CLAUDE.md highest (every request), skills low (descriptions only until invoked), MCP low (names only until used), subagents isolated, hooks zero
- Feature override behavior: CLAUDE.md files additive; skills/subagents/MCP override by name; hooks merge
- Combination patterns: Skill + MCP, Skill + Subagent, CLAUDE.md + Skills, Hook + MCP

## Connections

- [[wiki/pages/claude-code]] — the environment this extension layer wraps
- [[wiki/pages/skills]] — reusable instructions and workflow packages
- [[wiki/pages/sub-agents]] — isolated context workers; key for managing context bloat
- [[wiki/pages/mcp-model-context-protocol]] — external service connections
- [[wiki/pages/plugins]] — packaging and distribution of all extension types
- [[wiki/pages/claude-md]] — the always-on context layer
- [[wiki/pages/context-window]] — context cost breakdown referenced here
