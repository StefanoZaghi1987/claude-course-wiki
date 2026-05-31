---
type: page
created: 2026-05-31
updated: 2026-05-31
tags: [prompt-engineering, tcof, ai4gamma-corso]
---

Prompt engineering is the practice of constructing structured, precise instructions for an LLM to obtain targeted, high-quality outputs rather than relying on vague or iterative correction.

## Overview

Prompt engineering is not about being polite or verbose — it is about giving Claude all the information it needs before it can ask for more. Claude begins every session knowing nothing about the user, their company, or the task. The prompt is the only information channel. Well-structured prompts reduce iterative correction cycles; poorly constructed prompts diverge from intent and require rework that can exceed the original task cost. The central metaphor from the course: "Claude is a highly expert colleague who knows nothing about you or your company. Every chat starts from zero."

## Key dimensions

### The TCOF framework

TCOF (Task, Context, Output, Format) is the current standard for prompt structure. **Task**: the specific action to perform. **Context**: professional background, constraints, and relevant information — not too much (limits the AI's solution space in exploratory work) and not too little (causes incorrect assumptions). **Output**: the expected result type, required sections, and level of detail. **Format**: formatting specifics — Markdown, tables, maximum length, language. [[wiki/sources/manuale-prima-lezione]]

### Five core principles

Beyond structure, five principles govern effective prompting. **Clarity**: be explicit, leave no interpretive room. **Specificity**: use precise vocabulary; avoid vague requests like "make me a report." **Context**: supply the professional domain and operative constraints. **Format**: specify the output format upfront, not after seeing the result. **Examples**: include sample input/output pairs for complex or ambiguous tasks. [[wiki/sources/manuale-prima-lezione]]

### Role prompting

Role prompting assigns Claude a specific professional identity within the Context component: "You are an expert Fortran developer working in aerospace engineering..." This narrows Claude's interpretation frame, increases domain relevance, and reduces generic answers. It is a sub-technique within TCOF's Context component, not a standalone framework. [[wiki/sources/manuale-prima-lezione]]

### Practical habits

Draft prompts in an external editor (Notepad++, VS Code) before submitting — this allows structuring, saving, and reuse, and prevents accidental early submission (Enter in Claude Desktop sends immediately). Save prompt files as `.txt` or `.md` for reuse across sessions. A well-prepared 40-line prompt typically requires fewer correction cycles than a short improvised one. [[wiki/sources/manuale-prima-lezione]]

## Connections

- [[wiki/pages/context-window]] — prompt quality directly determines how efficiently the context window is used
- [[wiki/pages/spec-driven-development]] — SDD extends prompt engineering into a full specification-driven methodology
- [[wiki/pages/artifacts]] — well-structured prompts typically yield structured artifact outputs
- [[wiki/pages/vibe-coding]] — the unstructured alternative that prompt engineering replaces for serious work
- [[wiki/pages/meta-prompting]] — technique of asking Claude to generate its own optimal prompt

## Sources

- [[wiki/sources/manuale-prima-lezione]] — TCOF framework, 5 principles, role prompting, structured templates
