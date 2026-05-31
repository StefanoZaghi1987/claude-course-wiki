---
type: page
created: 2026-05-31
updated: 2026-05-31
tags: [vibe-coding, spec-driven-development, ai4gamma-corso]
---

Vibe coding is an unstructured approach to AI-assisted work in which actions are driven by immediate intuition rather than prior specification, producing fast results for simple tasks but unreliable and hard-to-maintain outcomes for complex ones.

## Overview

The term was coined by Andrej Karpathy to describe working with AI by following the moment: form an idea, ask the AI to implement it, observe the output, ask for adjustments, repeat — without upfront specification, explicit plan, or structured review cycle. The course uses vibe coding as a conceptual foil for Spec-Driven Development: understanding where each approach is appropriate is the first step to using AI productively.

## Key dimensions

### When it is acceptable

Vibe coding is productive for monouso, disposable tasks that don't require maintenance: formatting a table once, cleaning a short document, generating a one-off summary. The output is small enough to review and correct manually. The investment in a structured prompt exceeds the task complexity. [[wiki/sources/manuale-prima-lezione]]

### When it fails

For complex tasks, vibe coding produces unpredictable outputs (results vary across executions), accumulates quality debt (correction costs exceed original task cost), and yields results that are difficult to maintain, extend, or reproduce. From the course: "Il Vibe Coding per un report di 10 righe è accettabile. Per un'analisi da 50 pagine o un'applicazione software, non lo è." [[wiki/sources/manuale-prima-lezione]]

### The four-approach taxonomy

Lesson 1 presented a four-approach taxonomy for AI-assisted work: **Waterfall** (linear planned execution), **Agile** (iterative, modular), **Generic AI** (unstructured ad hoc), and **Vibe Coding** (inspiration-driven, no methodology). Vibe coding occupies the lowest rigor position; Spec-Driven Development is the structured alternative for the same complex task types. [[wiki/sources/manuale-prima-lezione]]

### AI-assisted work as the correct frame

The course proposes "AI-assisted work" (not "vibe coding" and not "pure SDD") as the operative frame: a human-AI team where the human provides context, requirements, domain knowledge, and quality control; the AI provides generation speed and structural transformation capacity. The key metaphor: "I don't throw the rock and check where it landed — I throw it and run alongside it." Time invested is comparable to solo work; quality of output is substantially higher. [[wiki/sources/manuale-prima-lezione]]

## Connections

- [[wiki/pages/spec-driven-development]] — the structured alternative for complex, quality-sensitive work
- [[wiki/pages/prompt-engineering]] — the first discipline that separates vibe coding from methodical AI use

## Sources

- [[wiki/sources/manuale-prima-lezione]] — introduced, defined, and contextualized in Lesson 1
- [[wiki/sources/manuale-quarta-lezione]] — SDD as the full methodological contrast