---
type: source
created: 2026-05-31
updated: 2026-05-31
tags: [ai4gamma-corso, plugins, claude-code, claude-desktop, cowork, skills, mcp, sub-agents, hooks]
source_path: raw/local/plugin-guida/
fetch_method: local-pdf
---

Complete plugin reference guide for the AI4Gamma training course on Claude. Version 1.0, March 2026. Covers Claude Desktop, Claude Code, and Cowork. 44 pages.

## Summary

This guide is a comprehensive reference for understanding, configuring, and using plugins across all three Claude platforms. It covers both theoretical architecture and practical workflows with real use cases for enterprise environments.

The document opens with a timeline of Claude's most significant releases from August 2025 to March 2026: Sonnet 4.5 and Cowork launch, Extended Thinking, file creation capabilities, memory for all users, Opus 4.6 and Sonnet 4.6, the official plugin marketplace, PowerPoint add-in, and persistent Cowork threads. This timeline anchors the plugin ecosystem in its current state of maturity.

For Claude Desktop/Cowork, official plugins are cataloged by category: **Operations** (Anthropic — workflow automation, document management, meeting notes), **Design** (Anthropic — UX/UI), **Engineering** (Anthropic — software development), **Data** (Anthropic — data analysis, SQL queries, dashboard generation), **Productivity** (Anthropic — personal productivity), **Enterprise Search** (Anthropic — cross-system enterprise search), **Brand Voice**, **Human Resources**, **Product Management**, **Financial Analysis**, **Sales**, and **Legal**.

For Claude Code, the top plugins by install count (March 2026) are: Frontend Design (371k+), SuperPowers (233k+ — the SDD brainstorming methodology), Context7 (189k+ — live documentation retrieval), Code Review (169k+), GitHub (141k+), Code Simplifier (140k+), Feature Dev (131k+), Playwright (118k+), Ralph Loop (110k+), Firecrawl (web scraping), Figma (design-to-code), Sentry, HuggingFace, Security Guidance.

The technical architecture section covers the four plugin components (Skills, Sub-agents, Hooks, MCP) in detail, including the trigger mechanism for Skills, pre-defined agent types in Claude Code (Explore, code-reviewer, code-architect, etc.), hook types and lifecycle events, and MCP integration patterns.

Five complete multi-plugin workflow case studies demonstrate practical combinations: (1) Software development with Claude Code + SuperPowers (brainstorming → explore → feature-dev → executing-plans → parallel agents → code review → simplify → finishing branch), (2) Documentation management with Operations + Productivity, (3) Design collaboration with Design + Figma plugins, (4) Data analysis with Data + Enterprise Search, (5) HR workflows with Human Resources + Brand Voice.

The guide concludes with a synoptic table of all plugins, official resource links, and a technical glossary.

## Key points

- Plugin marketplace officially launched in February 2026; plugins are now the primary discovery and distribution mechanism for Claude extensions
- Top Claude Code plugins by adoption: Frontend Design (371k+), SuperPowers (233k+), Context7 (189k+), Code Review (169k+), Code Simplifier (140k+)
- Plugin architecture differences across platforms: Claude Desktop/Cowork uses `.plugin` ZIP format + GUI browser; Claude Code installs via terminal `claude plugin install`
- Pre-defined agent types in Claude Code: Explore (codebase analysis), code-reviewer, code-architect, code-explorer, and others — agents have defined scopes and tools
- Hook lifecycle events: PreToolUse, PostToolUse, Stop, Notification — hooks fire at specific Claude lifecycle moments; custom hooks are advanced features
- Five official resource links provided: plugin marketplace, official plugin repos (GitHub), standard agent skills registry (agentskills.io), and release notes
- Context7 plugin resolves a key pain point: it fetches current library/framework documentation at query time, avoiding training data staleness for code generation
- The Ralph Loop plugin enables autonomous iterative development: Claude works in a loop until the task is complete, with configurable stopping conditions

## Connections

- [[wiki/pages/plugins]] — architectural overview this guide elaborates on
- [[wiki/pages/skills]] — Skills architecture detailed in Section 5
- [[wiki/pages/sub-agents]] — pre-defined agent types (Explore, code-reviewer, etc.)
- [[wiki/pages/mcp-model-context-protocol]] — MCP integration patterns
- [[wiki/pages/spec-driven-development]] — SuperPowers plugin methodology described in Section 6.13
- [[wiki/pages/claude-code]] — primary platform for most Claude Code plugins
- [[wiki/pages/cowork]] — Cowork-specific plugin characteristics in Section 7
