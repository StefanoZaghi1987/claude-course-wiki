---
type: page
created: 2026-05-31
updated: 2026-05-31
tags: [meta-prompting, prompt-engineering, ai4gamma-corso]
---

Meta-prompting is the technique of asking Claude to generate the optimal prompt for a given task rather than writing that prompt directly — delegating prompt construction to the AI itself.

## Overview

Meta-prompting exploits the fact that language models understand their own input format better than most users do. Instead of manually writing a structured prompt and guessing at what Claude needs to produce a high-quality result, one describes the objective informally and asks Claude to produce the best possible prompt for achieving it. The result is typically more complete, better structured, and more precisely framed than a manually written prompt. It introduces a two-phase workflow: first a meta-request generates the prompt, then the generated prompt executes the actual task.

## Key dimensions

### The two-phase flow

Phase 1 — **Meta-prompting**: provide an informal description of the objective and ask Claude: "Generate the best prompt to produce [list of deliverables]." Claude returns a structured prompt as a downloadable artifact. Phase 2 — **Execution**: review and optionally edit the generated prompt, then execute it (in a new chat or the dedicated project) to obtain the actual output. Separating these phases allows reviewing the "strategy" before committing resources to execution. [[wiki/sources/manuale-seconda-lezione]]

### Two variants

**Variant A — Direct prompt**: describe the project context and ask Claude to generate the deliverable artifacts directly: "You are a trainer. [technical context]. Generate the following artifacts: (1) short description, (2) project context in Markdown, (3) project instructions (system prompt) in Markdown." **Variant B — Prompt for the prompt**: ask Claude to write the best prompt that would generate those same deliverables, then execute that prompt separately. Variant B generally produces a more elaborated result; for high-importance tasks, use Opus in the meta-prompting phase. [[wiki/sources/manuale-seconda-lezione]]

### Application to project configuration

The primary use case demonstrated in the course is generating Claude project configuration: instead of manually writing Instructions (system prompt) and the project context document, one describes the domain and asks Claude to generate all three configuration artifacts in a single conversation. The advantage of doing all three in one conversation: Claude maintains consistency across documents — in separate conversations it might introduce incoherent details. [[wiki/sources/manuale-seconda-lezione]]

### Reproducibility and non-determinism

LLMs are non-deterministic: the same prompt produces slightly different results each run. Well-structured prompts reduce this variance by providing a clear direction — they don't eliminate variability but make results more consistently high-quality. Saving effective prompts in a versioned prompt library is a recommended practice; this asset compounds over time. [[wiki/sources/manuale-seconda-lezione]]

### Meta-prompting in Claude Code

The `/brainstorming` command from the SuperPowers plugin implements a structured socratic dialogue form of meta-prompting: Claude asks questions to refine the user's objective before generating a specification and development plan. [[wiki/sources/manuale-quarta-lezione]]

## Connections

- [[wiki/pages/prompt-engineering]] — meta-prompting is an advanced extension of prompt engineering
- [[wiki/pages/claude-projects]] — primary application: generating project configuration artifacts
- [[wiki/pages/spec-driven-development]] — brainstorming-based meta-prompting leads into SDD specification generation

## Sources

- [[wiki/sources/manuale-seconda-lezione]] — meta-prompting introduced and demonstrated with the Beas Assistant exercise
- [[wiki/sources/manuale-terza-lezione]] — "Context is All You Need" exercise using meta-prompting for project config
- [[wiki/sources/manuale-quarta-lezione]] — `/brainstorming` as structured meta-prompting in SDD