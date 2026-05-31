# Index

Catalog of the vault. Updated on every write operation.

## Pages

- [artifacts](pages/artifacts.md) — Claude's self-contained downloadable output units; iterative workflow and context checkpoints
- [claude-code](pages/claude-code.md) — CLI agentic environment: commands, operating modes, CLAUDE.md, sub-agents
- [claude-desktop](pages/claude-desktop.md) — Claude Desktop app: three operating modes, chat management, plans
- [claude-md](pages/claude-md.md) — CLAUDE.md: static project config for Claude Code, auto-loaded at session start
- [spec-driven-development](pages/spec-driven-development.md) — specifications-as-source-of-truth methodology; 5 principles, 7 components, /brainstorming mechanics, /feature-dev:feature-dev positioning, sub-agent execution (expanded)
- [claude-projects](pages/claude-projects.md) — persistent workspaces with fixed instructions, knowledge base (RAG), and team sharing
- [context-window](pages/context-window.md) — session working memory: saturation, strategies, plan tier differences
- [memory-in-claude](pages/memory-in-claude.md) — three non-overwriting memory levels: global preferences, chat extraction, project scope
- [mcp-model-context-protocol](pages/mcp-model-context-protocol.md) — protocol enabling Claude to interface with external tools and services
- [plugins](pages/plugins.md) — plugin architecture: Skills, MCP Connectors, Sub-agents, Hooks; install and org management
- [prompt-engineering](pages/prompt-engineering.md) — TCOF framework, 5 core principles, role prompting
- [sub-agents](pages/sub-agents.md) — independent parallel model instances for large-scale task execution
- [cowork](pages/cowork.md) — GUI-based agentic execution environment; sub-agents, project integration, resource cost
- [meta-prompting](pages/meta-prompting.md) — asking Claude to generate its own optimal prompt; two-phase flow
- [rag-retrieval-augmented-generation](pages/rag-retrieval-augmented-generation.md) — vector database, semantic chunking, selective retrieval for project knowledge
- [skills](pages/skills.md) — Skills anatomy (SKILL.md + References), Agent VM, three levels, two creation methods
- [vibe-coding](pages/vibe-coding.md) — unstructured AI-assisted work: when acceptable, when it fails
- [permission-modes](pages/permission-modes.md) — six Claude Code modes from default to bypassPermissions; auto classifier; protected paths; checkpoints
- [sessions-management](pages/sessions-management.md) — session lifecycle: resume, fork, branch, name; picker; context controls; worktrees for parallel work
- [claude-directory](pages/claude-directory.md) — .claude/ project files and ~/.claude/ home directory: every file Claude reads and writes
- [remote-control](pages/remote-control.md) — continue a local Claude Code session from any browser or phone; execution stays on your machine
- [plan-mode](pages/plan-mode.md) — read-only exploration mode; Claude proposes a plan before any file is edited
- [agent-driven-development](pages/agent-driven-development.md) — parallel sub-agent execution pattern for SDD; faster wall-clock, higher quality, more tokens
- [absolute-principles](pages/absolute-principles.md) — inviolable CLAUDE.md rules that Claude must never break, regardless of task
- [proactive-instructions](pages/proactive-instructions.md) — CLAUDE.md tasks Claude executes autonomously at the end of each sprint
- [file-reading-rules](pages/file-reading-rules.md) — CLAUDE.md section controlling eager vs. lazy file loading to manage context cost

## Sources

- [manuale-prima-lezione](sources/manuale-prima-lezione.md) — AI4Gamma Lesson 1 (6 Mar 2026): Claude Desktop, prompt engineering, context window, MCP, vibe coding
- [manuale-seconda-lezione](sources/manuale-seconda-lezione.md) — AI4Gamma Lesson 2 (20 Mar 2026): Claude Projects, RAG, meta-prompting, Cowork, memory hierarchy
- [manuale-terza-lezione](sources/manuale-terza-lezione.md) — AI4Gamma Lesson 3 (30 Mar 2026): Claude Code, CLAUDE.md, operating modes, Desktop→Code workflow, SDD intro
- [manuale-quarta-lezione](sources/manuale-quarta-lezione.md) — AI4Gamma Lesson 4 (10 Apr 2026): SDD methodology, plugins, Traditional vs Advanced workflows
- [manuale-quinta-lezione](sources/manuale-quinta-lezione.md) — AI4Gamma Lesson 5 (17 Apr 2026): SDD workflow tiers, CLAUDE.md structure, sub-agent driven development, token management
- [manuale-sesta-lezione](sources/manuale-sesta-lezione.md) — AI4Gamma Lesson 6 (5 May 2026): Skills anatomy, creation methods, MCP architecture, browser automation
- [plugin-guida](sources/plugin-guida.md) — Complete plugin reference guide: all plugins across Claude Desktop/Code/Cowork, workflows, install counts
- [overview-claude-code-docs](sources/overview-claude-code-docs.md) — Official Claude Code overview: capabilities, surfaces, cross-surface mobility (May 2026)
- [quickstart-claude-code-docs](sources/quickstart-claude-code-docs.md) — Claude Code quickstart: installation, auth, essential CLI forms (May 2026)
- [how-claude-code-works-claude-code-docs](sources/how-claude-code-works-claude-code-docs.md) — Agentic loop, built-in tool categories, execution environments, session model (May 2026)
- [extend-claude-code-claude-code-docs](sources/extend-claude-code-claude-code-docs.md) — Extension layer guide: CLAUDE.md vs skills vs subagents vs MCP vs hooks vs plugins (May 2026)
- [explore-the-context-window-claude-code-docs](sources/explore-the-context-window-claude-code-docs.md) — Session-start load order, what survives compaction, context cost by feature (May 2026)
- [how-claude-remembers-your-project-claude-code-docs](sources/how-claude-remembers-your-project-claude-code-docs.md) — CLAUDE.md 4-level hierarchy, rules/ directory, @import, auto memory architecture (May 2026)
- [choose-a-permission-mode-claude-code-docs](sources/choose-a-permission-mode-claude-code-docs.md) — Six permission modes, auto classifier, protected paths, switching mechanics (May 2026)
- [manage-sessions-claude-code-docs](sources/manage-sessions-claude-code-docs.md) — Session lifecycle: resume, naming, branching, picker, transcript storage (May 2026)
- [explore-the-claude-directory-claude-code-docs](sources/explore-the-claude-directory-claude-code-docs.md) — .claude/ and ~/.claude/ file reference, application data, security notes (May 2026)
- [platforms-and-integrations-claude-code-docs](sources/platforms-and-integrations-claude-code-docs.md) — All Claude Code surfaces and integrations; away-from-terminal options (May 2026)
- [continue-local-sessions-remote-control-claude-code-docs](sources/continue-local-sessions-remote-control-claude-code-docs.md) — Remote Control: start modes, connections, push notifications, security model (May 2026)
- [use-claude-code-in-vs-code-claude-code-docs](sources/use-claude-code-in-vs-code-claude-code-docs.md) — VS Code extension: install, diff review, @-mentions, plugin management, built-in MCP server (May 2026)
- [get-started-with-the-desktop-app-claude-code-docs](sources/get-started-with-the-desktop-app-claude-code-docs.md) — Desktop quickstart: environments, first session, key features (May 2026)
- [desktop-application-claude-code-docs](sources/desktop-application-claude-code-docs.md) — Desktop Code tab full reference: parallel sessions, diff, computer use, Dispatch, SSH, enterprise (May 2026)
- [common-workflows-claude-code-docs](sources/common-workflows-claude-code-docs.md) — Everyday development recipes: explore, debug, test, PR, sessions, parallel, piping (May 2026)
- [best-practices-for-claude-code-claude-code-docs](sources/best-practices-for-claude-code-claude-code-docs.md) — Context management, verification-first, explore-plan-code, environment setup, scaling (May 2026)

## Views

<!-- Timelines, comparisons, slides, etc. -->
