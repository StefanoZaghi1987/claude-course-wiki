---
type: source
created: 2026-05-31
updated: 2026-05-31
tags: [ai4gamma-corso, spec-driven-development, plugins, claude-code, brainstorming]
source_path: raw/local/manuale-quarta-lezione/
fetch_method: local-pdf
---

Course manual for the fourth session of the AI4Gamma training series on Claude, held on 10 April 2026 by Stefano Zaghi at Gamma SPA (~2.5 hours, Microsoft Teams).

## Summary

Lesson 4 is the methodological core of the course. Its central principle: "The quality of the result you get from AI is directly proportional to the quality of the specification you provide." The lesson introduces the plugin system for Claude Code and then delivers the full Spec-Driven Development methodology — both as theory and through two real-world case studies from Gamma's production system.

The plugin architecture is introduced as four components: Skills (workflow instructions), MCP Connectors (external system integrations), Sub-agents (specialized parallel agents), and Hooks (event-driven automations). Installation is via `claude plugin install <name>` from the terminal; a full Claude Desktop restart is required after installation. The organizational plugin management system (Required, Installed by default, Available to install, Not available) is explained. The key plugins for SDD are listed: SuperPowers (brainstorming + spec generation), Feature Dev (Anthropic, for feature additions to existing projects), CLAUDE.md Management, Code Simplifier, Frontend Design, Playwright, Skill Creator, Playground, and MCP Server Dev.

The SDD methodology is fully mapped: definition, 5 principles (what/how separation, granular decomposition, iterative review, human-in-the-loop, spec-as-documentation), the 4-phase development cycle, the two specification types (functional vs. technical), and the 7 components of an effective specification.

Two workflow variants are presented and compared. The Traditional Workflow (Planning Mode) uses a structured prompt → Q&A → plan → controlled execution. The Advanced Workflow (Brainstorming & Specification via SuperPowers `/brainstorming`) uses a socratic dialogue → co-produced specification → detailed plan → sub-agent execution. The Advanced workflow produces higher-quality specifications but requires more upfront time; the choice between them depends on problem complexity and how well-defined requirements are.

Two real cases from Gamma's Task Management application demonstrate the difference: EV-002 (Configurable Working Hours) used the Traditional workflow, revealing retrospectively that a 150-line spec would have achieved ~95% AI coverage vs. the original 35-line prompt's 60-70%. EV-003 (Modified Gantt Date Calculation) used the Advanced workflow and was completed (brainstorm + spec + plan + dev + test + refactor + manual) in approximately one working day.

## Key points

- Plugin architecture: Skills, MCP Connectors, Sub-agents, Hooks — installed via `claude plugin install <name>`, require full Claude Desktop restart
- SuperPowers is the key plugin for the Advanced SDD workflow: `/brainstorming` triggers a socratic dialogue that co-produces a specification and development plan
- SDD 5 principles: what/how separation, granular decomposition, iterative review with feedback cycles, human-in-the-loop on critical decisions, spec-as-project-documentation
- 7 spec components: Overview, Functional requirements, Non-functional requirements, Technical constraints, Acceptance criteria, Use cases/examples, Error handling
- Traditional workflow (Planning Mode): fast, ideal for well-defined tasks with clear architecture and limited scope
- Advanced workflow (Brainstorming & Spec): slower upfront, dramatically higher specification quality, necessary for complex/exploratory/cross-layer problems
- A well-crafted 150-line spec achieves ~95% AI coverage vs. 60-70% for a vague 35-line prompt — every hour in spec saves multiple hours in corrections
- The Effort setting (Low/Medium/High thinking mode) controls reasoning depth: Medium is recommended for most work; High burns context fast without proportionally better results

## Connections

- [[wiki/pages/plugins]] — main topic of section 2
- [[wiki/pages/spec-driven-development]] — main topic of section 3–5
- [[wiki/pages/claude-code]] — the execution environment for all SDD workflows
- [[wiki/pages/sub-agents]] — parallelization mechanism in the Advanced workflow
- [[wiki/pages/meta-prompting]] — brainstorming is meta-prompting taken to a structured socratic form
- [[wiki/pages/vibe-coding]] — the explicit contrast throughout the lesson
- [[wiki/pages/skills]] — one of the four plugin component types; primary workflow orchestration tool
