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

## Sources

- [[wiki/sources/manuale-prima-lezione]] — paradigm introduced briefly; vibe coding as the foil
- [[wiki/sources/manuale-terza-lezione]] — paradigm shift and specs-as-source-of-truth framing
- [[wiki/sources/manuale-quarta-lezione]] — full methodology: 5 principles, 7 spec components, two workflow variants
- [[wiki/sources/manuale-quinta-lezione]] — three operational tiers, sub-agent driven development

## Deep dive

### The paradigm inversion in depth

SDD rests on a single structural claim: with LLMs, the spec-to-code relationship inverts. In traditional software engineering, specifications pre-exist the codebase but progressively diverge from it — by delivery, the code is authoritative and the spec is archaeology. With LLMs, if the spec is of sufficient quality, the AI can regenerate the implementation from it on demand. The spec no longer decays relative to reality; it *is* reality, and the code is a reconstructible artifact. This inversion has a precise ROI implication: an hour invested in a better spec does not just save correction hours on the current task — it compounds across every future execution from that spec. [[wiki/sources/manuale-terza-lezione]]

### Four approaches, one decision

The course situates SDD within a four-approach model of AI-assisted work: Waterfall (linear upfront planning), Agile (iterative decomposition), generic/unstructured AI use, and Vibe Coding. The distinction between "generic AI" and "Vibe Coding" matters: the former at least uses AI for ideation before iteration; the latter — coined by Andrej Karpathy — is pure in-the-moment responsiveness with no structure at any stage. SDD is not a fifth approach but what makes any of the first three coherent in an AI context: it provides the specification structure that transforms Claude from a probabilistic generator into a deterministic executor. [[wiki/sources/manuale-prima-lezione]]

The course instructor's "stone" metaphor is clarifying: "I don't throw the stone and look where it landed. I throw the stone. Meanwhile I run, I chase the stone to see how it's progressing. The time is roughly the same, but I end up with a result qualitatively much better than what I'd have produced alone." This reframes the SDD value proposition from "saves time" to "enables work I couldn't produce alone" — particularly relevant for non-developers. [[wiki/sources/manuale-prima-lezione]]

### The five principles as a system

The five principles are mutually reinforcing, not independent guidelines:

**What/how separation** is the hardest to execute. The course identifies both failure modes explicitly: a spec too restrictive limits Claude's creativity; a spec too vague causes the AI to make unintended architectural decisions autonomously — described as "the worst possible scenario." The practical rule is to specify behavior and constraints, not code structure. [[wiki/sources/manuale-quarta-lezione]]

**Granular decomposition** is what makes context management tractable. Claude Code's context window degrades over long sessions as compaction loses detail. Breaking work into atomic tasks — each with a fresh clean-context session that reads only CLAUDE.md, the spec, and the plan — sidesteps this problem entirely, keeping each session's starting context minimal and focused. [[wiki/sources/manuale-terza-lezione]]

**Iterative review** closes the loop. The most important evidence here is the EV-002 case study: a real production feature (Configurable Working Hours) implemented with a 35-line prompt produced ~60–70% AI coverage because the spec lacked the hierarchy model, migration logic, and UI details. Retrospective analysis showed a 150-line spec would have achieved ~95% coverage with far fewer correction cycles. Review does not just catch bugs — it reveals specification gaps that, if identified during spec authoring instead, would have prevented the bugs entirely. [[wiki/sources/manuale-quarta-lezione]]

**Human-in-the-loop** is a gating mechanism, not a stylistic preference. In the Traditional Workflow it is enforced by Planning Mode (Claude refuses to write files). In the Advanced Workflow it is enforced by the brainstorming process, which surfaces architectural decisions for explicit human approval before the spec document is produced. Architectural trade-offs — framework selection, database design, state management — are never delegated silently. [[wiki/sources/manuale-quarta-lezione]]

**Spec-as-documentation** has concrete engineering implications: specs and development plans should be version-controlled alongside code as first-class assets. A spec that produced good results is a reusable asset; the same spec, run on a future model version with minor modifications, should reproduce the result. The course recommends building personal spec and prompt libraries organized by category. [[wiki/sources/manuale-terza-lezione]]

### The seven-component schema: what each element does

The specification schema maps directly to why vague prompts fail:

| Component | Why it matters |
|-----------|----------------|
| Overview | Domain grounding that lets Claude interpret ambiguous requirements correctly |
| Functional requirements | The core contract — expressed as behavior, not code |
| Non-functional requirements | Most commonly omitted, most expensive to retrofit: security, performance, accessibility |
| Technical constraints | Narrows implementation space when architecture is pre-decided |
| Acceptance criteria | Makes the spec testable; without them, "done" is a judgment call |
| Use cases / examples | Reduces interpretation variance more than any other element; concrete beats abstract |
| Error handling | Surfaces failure modes the AI would otherwise invent ad hoc |

The EV-002 comparison quantifies what happens when several components are missing: 3 generic functional requirements vs. 7 detailed ones; no data schema vs. 4 entities with fields and constraints; no UI spec vs. labels, editor, layout, error messages; implicit business rules vs. explicit holiday, cascade, and exception logic. Adding those components raised estimated AI coverage by ~35 percentage points. [[wiki/sources/manuale-quarta-lezione]]

### Two workflow variants: evidence from production

The **Traditional Workflow** follows six sequential phases: structured prompt → Claude Q&A to resolve ambiguities → development plan → refined spec → diff-by-diff controlled execution → post-implementation review. Its strength is speed for well-defined, scope-limited tasks. Its weakness is that spec quality depends entirely on the human's ability to anticipate all requirements before starting — an unrealistic expectation for complex cross-layer problems.

The **Advanced Workflow** addresses this by making spec co-production collaborative. Activated by `/brainstorming` (SuperPowers plugin), Claude reads the CLAUDE.md, explores the existing codebase, proposes architectural options with trade-offs, asks interactive questions (some as clickable menus), and at the end auto-generates a specification document — which it self-reviews before presenting for human approval. Only after approval does it generate the development plan. The EV-003 case study demonstrates the outcome: the complete cycle for a production Gantt date-calculation feature (brainstorming + spec + plan + development + test + refactoring + user manual + release) was completed in approximately one working day, with only one post-implementation correction cycle needed (an MVC-WebAPI controller detail the brainstorming had not surfaced). [[wiki/sources/manuale-quarta-lezione]]

Workflow selection heuristic: use the Traditional Workflow when requirements are clear and architecture is settled (standard CRUD, small scope, time pressure); use the Advanced Workflow when the problem requires exploration (new algorithms, cross-layer refactoring, unknown architecture, broad scope, or building a prototype from scratch). [[wiki/sources/manuale-quarta-lezione]]

### Three operational configuration tiers

Lesson 5 introduces a separate dimension of SDD maturity: how deeply the Claude Code environment is configured before development begins.

**Workflow Lite** generates a CLAUDE.md directly from the project idea. Fast setup; spec and configuration quality depend heavily on the initial prompt. Appropriate for quick prototypes.

**Workflow Intermediate** (recommended default) uses a Claude Desktop Project as the knowledge base. The sequence: brainstorm in Desktop → metaprompt to generate three configuration artifacts (short description, project context, project instructions) → enrich the knowledge base with Cowork analyses (framework analysis, SRS document) → generate a modularized CLAUDE.md from within the project. The configuration produced this way has access to all accumulated project knowledge, producing qualitatively more grounded CLAUDE.md content.

**Workflow Advanced** adds five specialized best-practice guide documents to the project before CLAUDE.md generation: Claude Code config best practices, enforcement rules, modularization guidelines, file referencing guide, and universal cross-framework best practices. With these in the knowledge base, the generator has explicit domain knowledge rather than having to infer it — producing a superior configuration for long-term structured projects at the cost of a heavier initial setup. [[wiki/sources/manuale-quinta-lezione]]

### CLAUDE.md structure and modularization

CLAUDE.md functions as the per-session system prompt — the "operating system" of the project folder, auto-loaded at every session start. Recommended sections: Purpose and Context; Absolute Principles (inviolable rules: "max 200 lines per file", "app must always work offline"); Technology Stack; Architecture; Proactive Instructions (tasks Claude executes autonomously after each sprint, such as updating a project map); File Reading Rules (lazy vs. eager loading); and Enforcement Rules (programming best-practice reminders).

Modularization is strongly recommended for medium and large projects. Each sub-agent spawned during parallel execution loads CLAUDE.md as its base context — a monolithic 2000-line file consumes significant context window before any task-specific information is loaded; a modular system with lazy loading lets each agent load only what its task requires. [[wiki/sources/manuale-quinta-lezione]]

### Sub-Agent Driven Development

The development plan's "For Agentic Workers" section controls parallel vs. sequential execution. The orchestrator reads the plan, identifies parallelizable tasks, and instantiates sub-agents — each receiving CLAUDE.md as base context plus task-specific instructions. Sub-agents work independently, report results to the orchestrator, which consolidates and resolves conflicts before coordinating review. The plan generated by the Advanced Workflow already includes cross-agent code review tasks, providing automatic inter-agent quality checking before the human's final review.

| Aspect | Sequential | Sub-Agent (Parallel) |
|--------|-----------|---------------------|
| Speed | Slower | Faster |
| Token cost | Lower | Higher |
| Output quality | Good | Higher (automatic review included) |
| Intermediate review | Manual per step | Automatic + manual final |

[[wiki/sources/manuale-quinta-lezione]]

### Advanced slash commands for CLAUDE.md lifecycle

The CLAUDE.md Management plugin provides commands that treat the configuration file as a living document: `/revise-claude-md` (proposes updates after each sprint based on what was learned — requires approval before applying), `/claude-md-improver` (structural improvement analysis of the existing file with a quality score), `/automation-recommender` (suggests plugins, MCP servers, or skills the project could benefit from), and `/advisor` (escalates to a stronger model when Claude is blocked — slight token increase, useful for complex debugging or architectural decisions). [[wiki/sources/manuale-quinta-lezione]]

### Limitations and open questions

**Gaps persist even with brainstorming.** EV-003 required a correction cycle after implementation for an MVC-WebAPI separation constraint the brainstorming had not surfaced. Post-implementation review remains necessary. Brainstorming reduces correction frequency and cost — it does not eliminate the need.

**Spec quality still requires domain judgment.** The Advanced Workflow co-produces the spec, but the human must answer architectural choice questions with sufficient knowledge. For unfamiliar technical domains, the course's mitigation — open a parallel chat to understand trade-offs before answering within the brainstorming session — works but means the human is not always genuinely in-the-loop on technical decisions.

**Token economics are a real operational constraint.** Sub-Agent Driven Development is token-intensive; the configuration phase is expensive. Practical guidance: separate configuration sessions from development sessions, use Sonnet for code generation and Opus for strategic analysis, modularize CLAUDE.md, and plan sprint boundaries against weekly usage limits. [[wiki/sources/manuale-quinta-lezione]]

**The coverage figures are self-assessed.** The 60–70% vs. ~95% AI coverage comparison between the 35-line and 150-line specifications is based on Claude's own retrospective assessment of the EV-002 feature, not an independent empirical measurement. It is a useful heuristic but should not be treated as a precise empirical claim.