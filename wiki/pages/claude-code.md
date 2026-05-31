---
type: page
created: 2026-05-31
updated: 2026-05-31
tags: [claude-code, ai4gamma-corso]
---

Claude Code is Anthropic's CLI-based agentic environment for structured, file-producing work — it operates from the terminal, auto-loads project configuration, and supports granular human control through an explicit diff-review workflow.

## Overview

Claude Code is distributed as an npm package and runs from the command line. Unlike Claude Desktop, which is a conversational interface, Claude Code is an agent that takes actions: reads and writes files, executes plans across multiple sessions, coordinates sub-agents, and integrates with the local filesystem. When launched in a folder, that folder becomes the project context for the session. CLAUDE.md in that folder is auto-loaded as the agent's configuration. Claude Code is not only for developers — any task that requires structured multi-step output benefits from its workflow.

## Key dimensions

### The Main Orchestrator Agent

Claude Code's interlocutor is not a generic model but the Main Orchestrator Agent, which runs a fixed Anthropic-authored system prompt optimized for coordinating complex tasks and delegating to specialized sub-agents. This system prompt cannot be user-modified, unlike Claude Desktop's project instructions. [[wiki/sources/manuale-terza-lezione]]

### Installation and authentication

Installed as a global npm package (requires Node.js). Windows: `irm https://claude.ai/install.ps1 | iex`. macOS/Linux: `curl -fsSL https://claude.ai/install.sh | bash`. First-run authentication opens an OAuth browser flow; SSO (corporate) login is automatic. The `claude` command launches a session in the current directory. [[wiki/sources/manuale-terza-lezione]]

### Key slash commands

| Command | Purpose |
|---|---|
| `/context` | Show current token usage, available tools, loaded files, context fill % |
| `/compact [instructions]` | Compact conversation history into a summary; optional focus instructions |
| `/resume` | List and restore previous sessions for the current folder |
| `/config` | Interactive settings panel: thinking mode, auto-compact, default model |
| `/model` | Switch model within session (warning: contexts do not transfer across models) |
| `/clear` | Wipe conversation history without compaction |
| `/exit` | Exit Claude Code, return to OS terminal |

[[wiki/sources/manuale-terza-lezione]]

### Three operating modes

**Standard (Ask Permission)**: default mode — Claude requests explicit approval for every file creation or modification, displaying a diff before applying. Recommended for learning and critical tasks. **Auto-Accept Edits**: all changes applied without confirmation; fast but risky — errors apply without intervention opportunity. Use only after plan verification on well-defined tasks. **Plan Mode**: exploration-first mode — Claude reads the codebase, asks guided questions to fill information gaps, then produces a structured development plan without writing any files. Best with Opus model. Recommended workflow: Plan Mode with Opus to generate the plan → save plan as file → new clean session in Standard mode to execute. [[wiki/sources/manuale-terza-lezione]]

### Context management specifics

Claude Code begins every session with a baseline context cost: the Orchestrator system prompt + loaded tools and skills + CLAUDE.md. At 50% context fill, warnings appear and the counter switches from absolute tokens to remaining %. At 65%, the auto-compact buffer is reserved (≈16.5% of total) and automatic compaction may trigger. Manual `/compact` before reaching the threshold is strongly preferred: the auto-compact summary is frequently imprecise and loses important details. Alternatively, save the current output and start a new session. [[wiki/sources/manuale-terza-lezione]]

### Model switching caveat

Each model in Claude Code maintains an independent context. Switching from Opus to Sonnet and back does not transfer conversation history — the two contexts do not communicate. Claude Code treats them as separate agents in the same session. Do not switch models mid-session; multi-model orchestration should be handled by the agent architecture, not manual switching. [[wiki/sources/manuale-terza-lezione]]

### Plugins and skills

Claude Code's capabilities are extended via plugins: Skills (workflow instructions), MCP Connectors (external service integrations), Sub-agents (specialized agents), and Hooks (event-driven automations). Plugins are installed via `claude plugin install <name>` from the terminal; Claude Desktop must be fully restarted after installation. [[wiki/sources/manuale-quarta-lezione]]

### The agentic loop

Claude Code runs a three-phase loop for every task: **gather context** (reads files, searches codebases, fetches documentation), **take action** (edits files, runs shell commands, executes tests), and **verify results** (re-runs tests, checks outputs, adjusts). The phases blend together rather than running strictly sequentially. The loop is driven by the Claude model (reasoning) executing through the harness (tool calls). [[wiki/sources/how-claude-code-works-claude-code-docs]]

### Built-in tool categories

Five categories of built-in tools give the agent concrete agency: **File operations** (read, edit, create, rename, reorganize); **Search** (glob patterns, regex content search, directory exploration); **Execution** (shell commands, start servers, run tests, use git); **Web** (search the web, fetch docs, look up errors); **Code intelligence** (LSP-sourced type errors and symbol navigation — requires a connected IDE extension). These are the foundation layer; skills, MCP, hooks, and sub-agents extend them. [[wiki/sources/how-claude-code-works-claude-code-docs]]

### Execution environments

Claude Code runs in three distinct environments: **Local** (default — your machine, full filesystem and tool access); **Cloud** (Anthropic-managed VMs, for tasks that don't require local files, sessions continue when you disconnect); **Remote Control** (your machine controlled from a browser or phone — execution stays local, only the interface moves). All interfaces — terminal CLI, Desktop app, IDE extensions, web, Slack, CI/CD — run the same underlying agentic loop. [[wiki/sources/how-claude-code-works-claude-code-docs]] [[wiki/sources/overview-claude-code-docs]]

### Extension layer overview

Seven extensions plug into the agentic loop on top of the built-in tools: CLAUDE.md (persistent context loaded every session), Skills (on-demand instructions and workflows), Code intelligence (LSP for typed language navigation), MCP (external service connections), Sub-agents (isolated context workers that return only summaries), Agent teams (multiple coordinated Claude Code sessions), and Hooks (lifecycle-event automation). Plugins package these for distribution. The key tradeoff: CLAUDE.md and skills add to your context window; sub-agents and hooks do not — they are the tools for context discipline. [[wiki/sources/extend-claude-code-claude-code-docs]]

## Connections

- [[wiki/pages/claude-md]] — the static project configuration file auto-loaded at session start
- [[wiki/pages/memory-in-claude]] — memory.md as the dynamic session scratchpad
- [[wiki/pages/context-window]] — context monitoring and compaction specific to Claude Code
- [[wiki/pages/spec-driven-development]] — the methodology Claude Code is optimized to support
- [[wiki/pages/plugins]] — the extension system for Skills, MCP, Sub-agents, Hooks
- [[wiki/pages/claude-desktop]] — the planning environment used upstream of Claude Code

## Sources

- [[wiki/sources/manuale-terza-lezione]] — installation, commands, operating modes, CLAUDE.md, memory.md, Desktop→Code workflow
- [[wiki/sources/manuale-quarta-lezione]] — plugins, SDD workflows, brainstorming
- [[wiki/sources/manuale-quinta-lezione]] — advanced slash commands, sub-agent driven development
- [[wiki/sources/manuale-sesta-lezione]] — Skills and MCP connector architecture
- [[wiki/sources/overview-claude-code-docs]] — capabilities overview, surfaces, cross-surface mobility
- [[wiki/sources/quickstart-claude-code-docs]] — installation, authentication, essential CLI forms
- [[wiki/sources/how-claude-code-works-claude-code-docs]] — agentic loop, tool categories, execution environments, session model
- [[wiki/sources/extend-claude-code-claude-code-docs]] — extension layer decision guide: CLAUDE.md vs skills vs subagents vs MCP vs hooks