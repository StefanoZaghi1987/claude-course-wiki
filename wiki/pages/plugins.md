---
type: page
created: 2026-05-31
updated: 2026-05-31
tags: [plugins, claude-code, ai4gamma-corso]
---

Plugins are installable packages that extend Claude's capabilities with four types of components: Skills, MCP Connectors, Sub-agents, and Hooks.

## Overview

A plugin is a bundled package of one or more functional components that extend what Claude can do beyond its native conversational abilities. Plugins enable specialized workflows (Skills), external system integrations (MCP Connectors), parallel task delegation (Sub-agents), and event-driven automation (Hooks). For most professional use cases, Skills and MCP Connectors are sufficient; Sub-agents and Hooks are advanced components with a more limited practical audience.

## Key dimensions

### Four plugin components

**Skills**: packages of workflow instructions that teach Claude to perform a specific task in a controlled, reproducible way. Claude reads the Skill's instructions when triggered and executes the defined workflow. **MCP Connectors**: bridges between Claude and external systems — email, databases, APIs, file systems — via the Model Context Protocol. **Sub-agents**: specialized agent instances that execute specific tasks within a broader Claude Code session; used for parallelization in Advanced SDD workflows. **Hooks**: event-triggered automations that fire on events like receiving a response or sending a prompt; advanced usage with potential for unexpected behavior — not recommended for general use. [[wiki/sources/manuale-quarta-lezione]]

### Installation and restart requirement

Plugins are installed from the terminal (not the Claude Desktop GUI): `claude plugin install <plugin-name>`. After installation, Claude Desktop must be fully quit and relaunched (File → Quit, then reopen) for the new plugin to be available. The `/skills` slash command in Claude Code lists all currently active plugins. [[wiki/sources/manuale-quarta-lezione]]

### Organizational management levels

Within an organization's Claude settings, plugins can be assigned one of four distribution states: **Required** (installed for all users, cannot be removed), **Installed by default** (available to all, individually removable), **Available to install** (visible and downloadable on request), **Not available** (hidden from users). Organization-level plugins are available to all members without individual installation. [[wiki/sources/manuale-quarta-lezione]]

### Key plugins for SDD and professional use

| Plugin | Purpose |
|---|---|
| SuperPowers | Advanced SDD: socratic brainstorming + spec generation via `/brainstorming` |
| Feature Dev (Anthropic) | Guided feature development workflow for adding to existing projects |
| CLAUDE.md Management | Create, improve, and update CLAUDE.md; session review and iterative improvement |
| Code Simplifier | Post-implementation refactoring analysis |
| Frontend Design | UI design suggestions, layout, components |
| Playwright | Browser control for functional test automation |
| Skill Creator | Create new Skills using a guided workflow |
| Playground | Generate interactive HTML pages from specs; real-time UI preview |
| MCP Server Dev | Develop custom MCP servers |

[[wiki/sources/manuale-quarta-lezione]]

### Plugin architecture across platforms

Claude Desktop/Cowork uses `.plugin` (ZIP) format files with a GUI browser; Claude Code installs from the terminal. The same plugin can have different components available depending on which platform is running it. [[wiki/sources/plugin-guida]]

## Connections

- [[wiki/pages/skills]] — one of four plugin components; detailed treatment in Lesson 6
- [[wiki/pages/mcp-model-context-protocol]] — MCP Connectors are another plugin component
- [[wiki/pages/sub-agents]] — Sub-agents are the parallelization component of plugins
- [[wiki/pages/claude-code]] — the primary environment where plugins are installed and used
- [[wiki/pages/spec-driven-development]] — SuperPowers plugin enables the Advanced SDD workflow

## Sources

- [[wiki/sources/manuale-quarta-lezione]] — plugin architecture, installation, org management, SDD-relevant plugins
- [[wiki/sources/manuale-sesta-lezione]] — detailed Skills anatomy, Skill creation methods- [[wiki/sources/plugin-guida]] — complete plugin reference across all platforms