---
type: source
created: 2026-05-31
updated: 2026-05-31
tags: [ai4gamma-corso, claude-code, claude-md, spec-driven-development, context-window]
source_path: raw/local/manuale-terza-lezione/
fetch_method: local-pdf
---

Course manual for the third session of the AI4Gamma training series on Claude, held on 30 March 2026 by Stefano Zaghi at Gamma SPA (~2 hours, Microsoft Teams).

## Summary

Lesson 3 is the transition point from planning and configuration (Claude Desktop) to implementation (Claude Code). It builds a concrete bridge between the two environments using the CLAUDE.md file as the connector. The practical exercise — composing a song titled "Context is All You Need" — is deliberately non-technical to demonstrate that Claude Code applies to any domain, not just software development.

The lesson opens with a recap of meta-prompting and RAG, then moves into Claude Code: what it is, how to install and authenticate it (npm package, SSO login), and how it operates as the Main Orchestrator Agent with a fixed Anthropic-written system prompt that the user cannot modify. The command reference covers the most-used slash commands: `/context` (monitor token usage), `/compact` (manual compaction with optional instructions), `/resume` (restore a prior session), `/config` (settings including thinking mode), and `/model` (switch model within session, with the warning that model contexts don't transfer).

The three operating modes are detailed: Standard (ask permission for each operation, recommended), Auto-Accept Edits (all changes applied without confirmation, use with caution), and Plan Mode (exploration → guided Q&A → structured plan output, best with Opus model). The recommended workflow is: Plan Mode with Opus to generate the plan, then start a new clean conversation with Standard mode to execute.

CLAUDE.md is the static configuration backbone: auto-loaded at every session start, equivalent to Instructions in Claude Desktop. The memory.md is the dynamic counterpart: an agent-updated scratch pad for session-to-session preferences. Together they cover stable project context and volatile session notes.

The Desktop→Code workflow is formalized: configure in Desktop → meta-prompt to generate CLAUDE.md → copy to local folder → launch Code. Specs and development plans are positioned as the session's closing theme and the preview for Lesson 4: the shift to Spec-Driven Development means specifications become the source of truth, not documentation history.

## Key points

- Claude Code is an npm-packaged CLI agentic environment; launched in a folder, that folder becomes the project; CLAUDE.md is auto-loaded
- Three operating modes: Standard (ask permission, recommended), Auto-Accept (no confirmation), Plan Mode (exploration + structured plan output)
- `/context` shows current token usage; `/compact [instructions]` compacts the history; auto-compact triggers at 65% context fill
- Model contexts in Claude Code are independent: switching from Opus to Sonnet does not transfer the conversation; do not switch models mid-session
- CLAUDE.md (static wiki) vs. memory.md (dynamic agent scratchpad): two complementary memory files with different update patterns
- The Desktop→Code workflow: configure project in Desktop → meta-prompt for CLAUDE.md → copy to local folder → launch Code
- Specs and development plans are first-class assets, not temporary files — save and version them
- SDD paradigm: with LLMs, specifications become the source of truth; quality of output is proportional to quality of specification

## Connections

- [[wiki/pages/claude-code]] — main topic of the lesson
- [[wiki/pages/claude-md]] — the static project configuration file
- [[wiki/pages/spec-driven-development]] — paradigm shift introduced here, deepened in L4/L5
- [[wiki/pages/context-window]] — `/context` and `/compact` commands for in-session management
- [[wiki/pages/meta-prompting]] — used to generate CLAUDE.md from a Desktop project
- [[wiki/pages/memory-in-claude]] — memory.md as the dynamic complement to CLAUDE.md
