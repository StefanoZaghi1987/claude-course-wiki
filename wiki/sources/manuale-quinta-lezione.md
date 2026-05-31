---
type: source
created: 2026-05-31
updated: 2026-05-31
tags: [ai4gamma-corso, spec-driven-development, claude-code, sub-agents, cowork, token-management]
source_path: raw/local/manuale-quinta-lezione/
fetch_method: local-pdf
---

Course manual for the fifth session of the AI4Gamma training series on Claude, held on 17 April 2026 by Stefano Zaghi at Gamma SPA (~2.5 hours, Microsoft Teams).

## Summary

Lesson 5 is the practical apex of the course — the most complex session, which assembles all prior concepts into a complete end-to-end SDD workflow. The exercise thread is building the Shopping List web app from initial idea to prototype launch, walking through each phase step-by-step.

The lesson introduces three operational workflow tiers for SDD environment setup, calibrated to project complexity. **Workflow Lite** is the simplest: define the idea, select features and stack, generate CLAUDE.md, start the SDD cycle. It depends on a well-structured initial prompt — without a project structure, output quality is less predictable. **Workflow Intermediate** is the recommended default: brainstorm in Claude Desktop, use meta-prompting to generate the three project configuration artifacts (short description, project context, project instructions), enrich the knowledge base with Cowork analyses (e.g., framework analysis, SRS), then generate a modularized CLAUDE.md. **Workflow Advanced** extends Intermediate by loading five specialized guidance documents (best practice config, enforcement rules, modularization, file referencing, universal cross-framework best practices) into the project before CLAUDE.md generation — producing a higher-quality configuration for long-term projects.

CLAUDE.md's recommended structure is detailed: Purpose and Context, Absolute Principles (inviolable rules), Technology Stack, Architecture, Proactive Instructions (tasks Claude should execute autonomously after each sprint), File Reading Rules (lazy vs. eager loading), and Enforcement Rules (programming best-practice reminders). Modularization — splitting into thematic module files referenced by a master file — reduces per-session token consumption and improves maintainability.

The Brainstorming & Specification workflow is shown in detail within a Claude Code session: `/brainstorming [TCOF prompt]` → socratic Q&A → specification document saved to `/specs/` → plan saved to `/plans/` → execution. The plan's "For Agentic Workers" section explicitly controls sequential vs. parallel sub-agent execution.

Sub-Agent Driven Development is formally compared to sequential execution: parallel is faster in wall-clock time and produces higher-quality output (includes automatic inter-agent code review) at the cost of higher token consumption.

Advanced slash commands from the CLAUDE.md Management plugin round out the lesson: `/revise-claude-md` (updates config after a sprint), `/claude-md-improver` (structural improvements from codebase analysis), `/automation-recommender` (suggests additional plugins/MCP/skills), and `/advisor` (escalates to a more capable model when blocked).

The token management section is practical: separate configuration sessions from development sessions (config is expensive), use Sonnet for coding and Opus for strategic analysis, modularize CLAUDE.md, plan sprint boundaries against weekly limits.

## Key points

- Three SDD configuration workflow tiers: Lite (minimal, prompt-dependent), Intermediate (Claude Desktop project + Cowork + modular CLAUDE.md, recommended), Advanced (+ 5 best-practice guide documents, for long-term structured projects)
- CLAUDE.md recommended sections: Purpose, Absolute Principles, Stack, Architecture, Proactive Instructions, File Reading Rules, Enforcement Rules
- Modularize CLAUDE.md into thematic files: reduces per-session token cost and simplifies maintenance; master file acts as an index
- Brainstorming & Specification in Claude Code: `/brainstorming [TCOF prompt]` → Q&A → spec (saved to `/specs/`) → plan (saved to `/plans/`) with "For Agentic Workers" execution instructions
- Sub-Agent Driven Development: parallel execution via sub-agents; faster, higher quality (includes automatic code review), higher token cost; plan includes cross-agent review tasks
- /revise-claude-md: update CLAUDE.md at end of each sprint (proposes changes, requires approval)
- /claude-md-improver: structural improvement analysis of existing CLAUDE.md (not just incremental updates)
- /advisor: escalate to a more capable model when stuck; slight token cost increase, unblocks difficult situations
- Token strategy: separate config from dev sessions; Sonnet for dev, Opus for analysis; modular CLAUDE.md; plan sprint boundaries

## Connections

- [[wiki/pages/spec-driven-development]] — three workflow tiers and sub-agent execution
- [[wiki/pages/claude-md]] — recommended structure, modularization, generation workflows
- [[wiki/pages/sub-agents]] — sequential vs. parallel execution comparison
- [[wiki/pages/cowork]] — used for knowledge base enrichment and CLAUDE.md generation
- [[wiki/pages/meta-prompting]] — three configuration artifacts generated via meta-prompting
- [[wiki/pages/artifacts]] — project configuration artifacts (short description, project context, project instructions) generated via meta-prompting
- [[wiki/pages/plugins]] — CLAUDE.md Management plugin and plugin-based slash commands (/revise-claude-md, /claude-md-improver, /advisor)
- [[wiki/pages/skills]] — skill-based workflows (/brainstorming) used throughout the SDD cycle
