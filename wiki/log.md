# Log

Append-only log of vault operations.

Format: `## [YYYY-MM-DD] op | title`

## [2026-05-31] ingest | manuale-prima-lezione
Pages created: claude-desktop, artifacts, prompt-engineering, context-window, memory-in-claude, mcp-model-context-protocol, vibe-coding, claude-projects

## [2026-05-31] ingest | manuale-seconda-lezione
Pages created: rag-retrieval-augmented-generation, meta-prompting, cowork
Pages updated: claude-projects, memory-in-claude

## [2026-05-31] ingest | manuale-terza-lezione
Pages created: claude-code, claude-md, spec-driven-development

## [2026-05-31] ingest | manuale-quarta-lezione
Pages created: plugins, sub-agents
Pages updated: spec-driven-development

## [2026-05-31] ingest | manuale-quinta-lezione
Pages updated: claude-md (recommended structure, modularization), sub-agents (sequential vs parallel)

## [2026-05-31] ingest | manuale-sesta-lezione
Pages created: skills
Pages updated: mcp-model-context-protocol (MCP Server types, GammaBot, custom MCP)

## [2026-05-31] ingest | plugin-guida
Pages updated: plugins (install counts, platform architecture differences)

## [2026-05-31] ingest | official-docs-batch-c (7 sources)
Sources ingested: platforms-and-integrations-claude-code-docs, continue-local-sessions-remote-control-claude-code-docs, use-claude-code-in-vs-code-claude-code-docs, get-started-with-the-desktop-app-claude-code-docs, desktop-application-claude-code-docs, common-workflows-claude-code-docs, best-practices-for-claude-code-claude-code-docs
Pages created: remote-control
Pages updated: claude-desktop (Code tab features, parallel sessions, diff view, computer use, Dispatch, SSH, CLI comparison)

## [2026-05-31] ingest | official-docs-batch-b (3 sources)
Sources ingested: choose-a-permission-mode-claude-code-docs, manage-sessions-claude-code-docs, explore-the-claude-directory-claude-code-docs
Pages created: permission-modes, sessions-management, claude-directory

## [2026-05-31] lint-fix | full vault repair
Orphans resolved (3): best-practices-for-claude-code-claude-code-docs, common-workflows-claude-code-docs, use-claude-code-in-vs-code-claude-code-docs linked from wiki pages
Cross-references added (17): connections added to 10 source files (best-practices, choose-a-permission-mode, desktop-application, get-started-desktop, how-claude-code-works, manuale-prima, quarta, quinta, seconda, sesta lezione)
Pages created (5): plan-mode, agent-driven-development, absolute-principles, proactive-instructions, file-reading-rules

## [2026-05-31] expand | spec-driven-development
Re-expanded with workflow tool focus: /superpowers mechanics, /brainstorming 4-stage protocol (TCOF invocation, /specs and /plans output paths, self-review step, "For Agentic Workers" section), /feature-dev:feature-dev positioning vs brainstorming, two-formulation resolution for 5 SDD principles (Lesson 4 vs Lesson 5 naming). Also resolves open review finding B-1.

## [2026-05-31] review | scope: all | findings: 5
## [2026-05-31] review-fix | applied 2 findings from review report
Fixed: C-1 formatting (cowork.md, meta-prompting.md, plugins.md — merged Sources list entries separated); B-2 plugins.md (/skills claim corrected: "plugins" → "skills")
Pending manual review: B-1 (5 SDD principle names — raw PDF required), B-3 (50% context threshold citation — raw PDF required)

## [2026-05-31] ingest | official-docs-batch-a (6 sources)
Sources ingested: overview-claude-code-docs, quickstart-claude-code-docs, how-claude-code-works-claude-code-docs, extend-claude-code-claude-code-docs, explore-the-context-window-claude-code-docs, how-claude-remembers-your-project-claude-code-docs
Pages updated: claude-code (agentic loop, tool categories, execution environments, extension layer overview), context-window (session-start load order, what-survives-compaction table, context cost by feature), claude-md (4-level hierarchy, rules/ directory, @import, CLAUDE.local.md, AGENTS.md compat), memory-in-claude (Claude Code dual mechanisms, auto memory architecture, /memory command)
