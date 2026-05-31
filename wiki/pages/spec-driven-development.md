---
type: page
created: 2026-05-31
updated: 2026-05-31
expanded: 2026-05-31
tags: [spec-driven-development, claude-code, ai4gamma-corso]
---

Spec-Driven Development (SDD) is a methodology in which specifications — not code or output — are the source of truth, and the human defines precisely what to build before delegating implementation to AI.

## Overview

SDD inverts the traditional software development paradigm: previously, specifications were written upfront but became historical documentation as the codebase diverged from them. With LLMs, the specification can remain authoritative because the code is regenerated from it on demand. SDD applies beyond software — to any complex, quality-sensitive output — and is the guiding methodology of the AI4Gamma training course. Its central principle: the quality of AI output is directly proportional to the quality of the specification that drives it.

## Key dimensions

### The paradigm shift

In traditional development: write specs → build software → specs drift from reality → code becomes the source of truth. With LLMs: write specs → AI generates code → spec remains the source of truth → quality is determined by spec quality. This inversion means writing good specifications is the highest-leverage activity in AI-assisted work. [[wiki/sources/manuale-terza-lezione]]

### Five core principles

1. **Preventive analysis**: analyze requirements and define them clearly before any activity. 2. **Separation of what/how**: specifications describe *what* to build; the AI determines *how* (unless explicit constraints are given). 3. **Granular decomposition**: break the project into atomic tasks, each with its own analysis-implementation-review cycle. 4. **Human-in-the-loop**: the human is always at the center, approving each step before the next. 5. **Structured iteration**: the Spec → Implementation → Review → Refinement cycle guarantees progressive quality. [[wiki/sources/manuale-quarta-lezione]]

### Seven components of an effective specification

A well-formed specification includes: **Overview** (problem context and general objective), **Functional requirements** (what the system must do), **Non-functional requirements** (performance, security, architectural constraints), **Acceptance criteria** (how we verify success — makes the spec testable), **Use cases** (how the solution will be used in practice), **Error handling** (failure scenarios to address upfront), **Technology stack** (if defined — specific implementation constraints). [[wiki/sources/manuale-quarta-lezione]]

### SDD vs. vibe coding

The key distinction: SDD requires more upfront investment (analysis, specification, plan) but produces reproducible, maintainable, and high-quality results. Vibe coding is faster to start but unpredictable and hard to maintain at scale. SDD is not a rejection of AI autonomy — it is the structured frame that makes AI autonomy predictable and high-quality. [[wiki/sources/manuale-prima-lezione]] [[wiki/sources/manuale-quarta-lezione]]

### Workflow variants

**Traditional workflow (Planning Mode)**: structured prompt → Claude Code Plan Mode → plan review → Standard mode execution. Six phases: context gathering, analysis, planning, implementation, review, delivery. **Advanced workflow (Brainstorming & Specification)**: socratic dialogue via `/brainstorming` (SuperPowers plugin) → specification generation → development plan → sub-agent execution. Three operational tiers: Lite (minimal structure, small tasks), Intermediate (CLAUDE.md + structured prompt), Advanced (full brainstorming + spec + multi-agent execution). [[wiki/sources/manuale-quarta-lezione]] [[wiki/sources/manuale-quinta-lezione]]

### Specifications as assets

Development plans and specifications should be saved and versioned like code — they are the asset that drives quality. Every iteration that improves a spec improves all future executions from it. The course recommendation: build prompt and spec libraries organized by category. [[wiki/sources/manuale-terza-lezione]]

## Connections

- [[wiki/pages/claude-code]] — the primary execution environment for SDD workflows
- [[wiki/pages/claude-md]] — the project configuration that grounds each SDD session
- [[wiki/pages/vibe-coding]] — the unstructured alternative SDD replaces for complex work
- [[wiki/pages/prompt-engineering]] — spec writing is the evolution of prompt engineering
- [[wiki/pages/sub-agents]] — SDD advanced workflow delegates to parallel sub-agents
- [[wiki/pages/meta-prompting]] — brainstorming-based meta-prompting feeds into spec generation
- [[wiki/pages/agent-driven-development]] — SADD is the parallelized execution phase of the Advanced SDD workflow

## Sources

- [[wiki/sources/manuale-prima-lezione]] — paradigm introduced briefly; vibe coding as the foil
- [[wiki/sources/manuale-terza-lezione]] — paradigm shift and specs-as-source-of-truth framing
- [[wiki/sources/manuale-quarta-lezione]] — full methodology: 5 principles, 7 spec components, two workflow variants
- [[wiki/sources/manuale-quinta-lezione]] — three operational tiers, sub-agent driven development

## Deep dive

### The paradigm inversion in depth

SDD rests on a single structural claim: with LLMs, the spec-to-code relationship inverts. In traditional software engineering, specifications pre-exist the codebase but progressively diverge from it — by delivery, the code is authoritative and the spec is archaeology. With LLMs, if the spec is of sufficient quality, the AI can regenerate the implementation from it on demand. The spec no longer decays relative to reality; it *is* reality, and the code is a reconstructible artifact. This inversion has a precise ROI implication: an hour invested in a better spec does not just save correction hours on the current task — it compounds across every future execution from that spec. [[wiki/sources/manuale-terza-lezione]]

### Four approaches, one decision

The course situates SDD within a four-approach model of AI-assisted work: Waterfall (linear upfront planning), Agile (iterative decomposition), generic/unstructured AI use, and Vibe Coding. The distinction between "generic AI" and "Vibe Coding" matters: the former at least uses AI for ideation before iteration; the latter — coined by Andrej Karpathy — is pure in-the-moment responsiveness with no structure at any stage. SDD is not a fifth approach but what makes any of the structured three coherent in an AI context: it provides the specification that transforms Claude from a probabilistic generator into a deterministic executor. [[wiki/sources/manuale-prima-lezione]]

The course instructor's "stone" metaphor: "I don't throw the stone and look where it landed. I throw the stone. Meanwhile I run, I chase the stone to see how it's progressing. The time is roughly the same, but I end up with a result qualitatively much better than what I'd have produced alone." This reframes the SDD value proposition from "saves time" to "enables work I couldn't produce alone" — particularly relevant for non-developers. [[wiki/sources/manuale-prima-lezione]]

### The five principles: two formulations

The five SDD principles have two distinct formulations across the course materials. Lesson 4 presents: (1) Separazione del cosa dal come, (2) Granularità controllata, (3) Review iterativa con cicli di feedback, (4) Controllo umano sulle decisioni critiche, (5) La specifica come documentazione di progetto. Lesson 5 re-labels them: (1) Analisi preventiva, (2) Separazione cosa/come, (3) Decomposizione granulare, (4) Human-in-the-Loop, (5) Iterazione strutturata. The underlying substance is identical; lesson 5 shifts principle 1 from "what/how separation" to "preventive analysis" — foregrounding *upfront analysis* as the first mental discipline, before the what/how distinction becomes operative. This page uses the lesson 5 formulation as the more pedagogically complete version. [[wiki/sources/manuale-quarta-lezione]] [[wiki/sources/manuale-quinta-lezione]]

**What/how separation** is the hardest to execute. Both failure modes are identified explicitly: a spec too restrictive limits Claude's creativity; a spec too vague causes the AI to make unintended architectural decisions autonomously — described as "the worst possible scenario." The practical rule is to specify behavior and constraints, not code structure. [[wiki/sources/manuale-quarta-lezione]]

**Granular decomposition** is what makes context management tractable. Breaking work into atomic tasks — each with a fresh session that reads only CLAUDE.md, the spec, and the plan — keeps each session's starting context minimal and focused, avoiding context-window degradation over long sessions. [[wiki/sources/manuale-terza-lezione]]

**Spec-as-documentation** has concrete engineering implications: specs and plans should be version-controlled alongside code as first-class assets. The course recommends building personal spec and prompt libraries organized by category. [[wiki/sources/manuale-terza-lezione]]

### The SuperPowers plugin: mechanics

SuperPowers, developed by Jess Vincent, is the plugin that enables the Advanced SDD Workflow. Its primary skill is `/brainstorming` — a structured Socratic dialogue that co-produces a specification with the human. It also provides the Sub-Agent Driven Development execution skill used in the execution phase. Both workflow phases — brainstorming *and* sub-agent execution — run through SuperPowers, making it the single dependency for the entire Advanced Workflow.

Installation follows the standard plugin procedure (`claude plugin install <name>` from a terminal outside any Claude Code session, then a full Claude Desktop restart). Currently loaded plugins can be verified at any time via `/skills` inside a Claude Code session. [[wiki/sources/manuale-quarta-lezione]]

### `/brainstorming`: step-by-step mechanics

The command signature is `/brainstorming [STRUCTURED PROMPT]`. A well-formed invocation follows the TCOF schema (Task, Context, Output, Format) and typically includes a reference to the existing development plan:

```
/brainstorming # Task: Sprint Zero - Setup Infrastruttura
## Obiettivo Configurare l'architettura base del progetto Shopping List
## Requisiti Test Hello World funzionante al termine
## Contesto Leggi il piano di sviluppo in /docs/development-plan.md
```

The more structured the initial prompt, the more targeted Claude's questions — a TCOF prompt with a plan reference allows Claude to skip obvious questions and focus on genuinely non-trivial ambiguities. [[wiki/sources/manuale-quinta-lezione]]

Once triggered, the session proceeds in four stages:

**Stage 1 — Context loading.** Claude reads the project's CLAUDE.md to anchor questions in the existing architecture and conventions, then explores the codebase to understand current state.

**Stage 2 — Socratic Q&A.** Claude asks targeted questions covering: blocking constraints not considered initially (e.g., unavailable external services), architectural decisions that will affect implementation, user preferences on alternative approaches, and scope definition (what is in-scope vs. out-of-scope). Some questions are textual; some appear as clickable choice menus. For questions involving architectural trade-offs the user cannot evaluate without domain knowledge, the recommended practice is to open a parallel Claude chat to understand the options before answering within the brainstorming — this preserves human-in-the-loop without forcing uninformed decisions. Claude can also start a local server and display interactive mockups in the browser during this phase (observed spontaneously in the Shopping List live demo). [[wiki/sources/manuale-quarta-lezione]]

**Stage 3 — Automatic spec generation.** At the end of the dialogue, Claude generates a structured specification document covering: objective and task scope, architectural decisions made during brainstorming, dependencies and packages to install, tasks deferred to future sprints (out-of-scope), and acceptance criteria. The spec is saved to `/specs/`. Claude performs a **self-review** of the spec before presenting it to the user — a built-in quality gate that catches internal inconsistencies before human review. [[wiki/sources/manuale-quinta-lezione]]

**Stage 4 — Development plan generation.** After the user approves the spec, Claude generates the development plan in `/plans/`. The plan contains: a detailed action sequence; for each action — objective, files to create/modify, expected result. Critically, the plan includes a **"For Agentic Workers" section** that explicitly specifies which tasks can run in parallel and which must run sequentially — this is what the orchestrator reads when Sub-Agent Driven Development is activated. At sprint end, it is good practice to update the macro plan explicitly: `"Aggiorna il piano di sviluppo macro in /docs/development-plan.md in base a ciò che abbiamo appreso e deciso durante questo sprint."` [[wiki/sources/manuale-quinta-lezione]]

### `/feature-dev:feature-dev`: the Anthropic-official alternative

Feature Dev is Anthropic's own plugin for structured feature development on existing projects. Its positioning is explicitly distinct from `/brainstorming`: designed for situations where the architecture is already defined and the goal is to add a controlled, well-scoped feature. The practical distinction is scope and exploration depth:

- **`/brainstorming`** (SuperPowers): performs codebase exploration, proposes architectural options, asks Socratic questions, generates spec + plan from scratch. Best for: new projects, complex cross-layer problems, algorithm design, unknown architecture, broad scope.
- **`/feature-dev:feature-dev`** (Anthropic): follows a guided workflow for adding features to an established project. Best for: well-defined features, standard CRUD/UI/report patterns, settled architecture, clear requirements.

The key decision signal: if you could write the spec manually with confidence (architecture and requirements both clear), `/feature-dev:feature-dev` is appropriate; if you need exploration to discover what the spec should even contain, `/brainstorming` is required. In practice, `/feature-dev:feature-dev` occupies the same problem space as the Traditional Workflow but with plugin-guided structure rather than raw Planning Mode — it is not a replacement for brainstorming on complex problems. [[wiki/sources/manuale-quarta-lezione]]

### Sub-Agent Driven Development: execution layer

The execution phase runs through SuperPowers. The orchestrator reads the plan (specifically the "For Agentic Workers" section), identifies parallelizable tasks, and instantiates sub-agents — each receiving CLAUDE.md as base context plus task-specific instructions. Sub-agents work independently without communicating during execution; they report results to the orchestrator, which consolidates, resolves conflicts, and coordinates review. The plan generated by the Advanced Workflow already includes cross-agent code review tasks — automatic inter-agent quality checking before the human's final review. This is the source of the quality advantage over sequential execution, not just the speed gain.

| Aspect | Sequential | Sub-Agent (Parallel) |
|--------|-----------|---------------------|
| Speed | Slower | Faster |
| Token cost | Lower | Higher |
| Output quality | Good | Higher (automatic review included) |
| Intermediate review | Manual per step | Automatic + manual final |

[[wiki/sources/manuale-quinta-lezione]]

### Three operational configuration tiers

A separate dimension of SDD maturity: how deeply the Claude Code environment is configured before development begins.

**Workflow Lite** generates a CLAUDE.md directly from the project idea. Fast setup; spec and configuration quality depend heavily on the initial prompt. Appropriate for quick prototypes.

**Workflow Intermediate** (recommended default) uses a Claude Desktop Project as the knowledge base. The sequence: brainstorm in Desktop → metaprompt to generate three configuration artifacts (short description, project context, project instructions) → enrich the knowledge base with Cowork analyses (framework analysis, SRS document) → generate a modularized CLAUDE.md from within the project. The configuration produced this way has access to all accumulated project knowledge, producing qualitatively more grounded CLAUDE.md content.

**Workflow Advanced** adds five specialized best-practice guide documents to the project before CLAUDE.md generation: Claude Code config best practices, enforcement rules, modularization guidelines, file referencing guide, and universal cross-framework best practices. The Advanced Workflow's CLAUDE.md generation also produces a macro development plan (with sprints) and a project file map automatically — foundational artifacts for starting the SDD cycle in Claude Code. [[wiki/sources/manuale-quinta-lezione]]

### CLAUDE.md structure and modularization

CLAUDE.md functions as the per-session system prompt — the "operating system" of the project folder, auto-loaded at every session start. Recommended sections: Purpose and Context; Absolute Principles (inviolable rules: "max 200 lines per file", "app must always work offline"); Technology Stack; Architecture; Proactive Instructions (tasks Claude executes autonomously after each sprint, such as updating a project map); File Reading Rules (lazy vs. eager loading); and Enforcement Rules (programming best-practice reminders).

Modularization is strongly recommended for medium and large projects. Each sub-agent spawned during parallel execution loads CLAUDE.md as its base context — a monolithic 2000-line file consumes significant context window before any task-specific information is loaded; a modular system with lazy loading lets each agent load only what its task requires. [[wiki/sources/manuale-quinta-lezione]]

### Advanced slash commands for CLAUDE.md lifecycle

The CLAUDE.md Management plugin provides commands that treat the configuration file as a living document: `/revise-claude-md` (proposes updates after each sprint based on what was learned — requires approval before applying), `/claude-md-improver` (structural improvement analysis with a quality score — not limited to incremental additions, proposes structural optimizations), `/automation-recommender` (suggests plugins, MCP servers, or skills the project could benefit from — best used at advanced development stages, not every sprint), and `/advisor` (configures Claude Code to automatically consult a more capable model when blocked — slight token increase, useful for complex debugging or architectural decisions). [[wiki/sources/manuale-quinta-lezione]]

### Production evidence: two case studies

**Traditional Workflow limitation (EV-002 — Configurable Working Hours):** a 35-line prompt produced ~60–70% AI coverage because the spec lacked the three-level hierarchy model (default → weekly pattern → override), absence migration logic, holiday integration, and UI specifics. Retrospective analysis showed a 150-line spec — 7 detailed functional requirements, 4 data entities with fields and constraints, explicit UI specs, explicit business rules — would have achieved ~95% coverage. Claude identified 5+ ambiguities during Q&A; each unresolved ambiguity became a post-implementation correction cycle. [[wiki/sources/manuale-quarta-lezione]]

**Advanced Workflow capability (EV-003 — Modified Gantt Date Calculation):** the complete cycle (brainstorming + spec + plan + development + test + refactoring + user manual + release) was completed in approximately one working day. Time breakdown: ~3h brainstorming and planning (including codebase exploration), ~2h development, ~1h test and bug fixing, ~4h code refactoring, ~30min documentation and release. One post-implementation correction cycle was required for an MVC-WebAPI separation constraint the brainstorming had not surfaced — confirming that brainstorming reduces specification gaps but does not eliminate the need for post-implementation review. [[wiki/sources/manuale-quarta-lezione]]

### Limitations and open questions

**Gaps persist even with brainstorming.** EV-003 required a correction cycle after implementation for an MVC-WebAPI constraint the brainstorming had not surfaced. Post-implementation review remains necessary. Brainstorming reduces correction frequency and cost — it does not eliminate it.

**Spec quality still requires domain judgment.** The Advanced Workflow co-produces the spec, but the human must answer architectural choice questions with sufficient knowledge. For unfamiliar technical domains, the course mitigation — open a parallel chat to understand trade-offs before answering within the brainstorming — works but means the human is not always genuinely in-the-loop on technical decisions.

**Token economics are a real operational constraint.** Sub-Agent Driven Development is token-intensive; the configuration phase is expensive. Practical guidance: separate configuration sessions from development sessions, use Sonnet for code generation and Opus for strategic analysis, modularize CLAUDE.md, and plan sprint boundaries against weekly usage limits. [[wiki/sources/manuale-quinta-lezione]]

**The coverage figures are self-assessed.** The 60–70% vs. ~95% AI coverage comparison between the 35-line and 150-line specifications is based on Claude's own retrospective assessment of EV-002, not an independent empirical measurement. It is a useful heuristic but should not be treated as a precise empirical claim.