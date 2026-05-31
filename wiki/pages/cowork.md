---
type: page
created: 2026-05-31
updated: 2026-05-31
tags: [cowork, claude-desktop, sub-agents, ai4gamma-corso]
---

Cowork is Claude's GUI-based agentic execution environment, designed for non-technical users to run autonomous multi-step tasks using the same engine as Claude Code, without the command-line interface.

## Overview

Cowork sits between Chat (interactive, bidirectional) and Claude Code (developer CLI) in the Claude suite. It targets users who want autonomous task execution — generating documents, analyzing sources, running multi-step workflows — without the complexity of a terminal. The key characteristic: Cowork's interaction mode is "launch and monitor." The user provides a task prompt, Cowork executes it autonomously (potentially over several minutes), and delivers a structured output. Mid-task interaction is possible but minimal.

## Key dimensions

### Comparison with Chat and Claude Code

| Dimension | Chat | Cowork | Claude Code |
|---|---|---|---|
| Interaction mode | Continuous question-answer | Minimal: launch → monitor → receive | Controlled diff-by-diff |
| Target user | All | Non-technical | Developers and power users |
| Underlying engine | Conversational model | Agentic (same as Code) | Agentic CLI |
| Status | Stable | Preview (with limitations) | Stable |

[[wiki/sources/manuale-seconda-lezione]]

### Launching from a project

Cowork is accessed directly from within a Claude project via the "Start task in Cowork" button. This automatically inherits the project's context: instructions, files, and memory. The workflow: open the relevant project → click "Start task in Cowork" → paste the task prompt → start and monitor the progress bar → optionally interact with the running task → receive the final output. [[wiki/sources/manuale-seconda-lezione]]

### Sub-agents and parallelization

The Cowork engine can spawn sub-agents — independent model instances with separate context windows — to parallelize operations on large tasks. For example, analyzing a documentation set can be structured as one sub-agent per chapter, with results assembled into a final document. This avoids context saturation on tasks that would exceed a single conversation's capacity. Requesting parallelization explicitly in the task prompt ("dedicate one sub-agent per chapter, then assemble the final document") is an advanced technique that improves both quality and completeness. [[wiki/sources/manuale-seconda-lezione]]

### Output quality diagnostics

Low-quality Cowork output can stem from: poorly structured prompt (AI misunderstands the task), insufficient or excessive context (wrong direction from the start), context saturation (quality degrades progressively), or non-determinism (high variability across runs). The diagnostic approach: run the same task multiple times. High variability → the prompt is under-constrained. Systematically poor results → structural or context problem. [[wiki/sources/manuale-seconda-lezione]]

### Resource cost

Cowork consumes significantly more resources than a standard chat session, due to multi-step agentic execution and potential sub-agent parallelization. Deep Research-level tasks in Cowork can deplete plan quotas quickly. Use Cowork for genuinely complex, multi-step tasks that justify the cost — not for simple queries. [[wiki/sources/manuale-seconda-lezione]]

### Creating Skills from Cowork

Cowork can also be used to create new Skills — when the Skill involves testing and debugging workflows that benefit from an isolated execution environment. This is one of the two primary Skill creation methods (the other being from a Claude Project). [[wiki/sources/manuale-sesta-lezione]]

## Connections

- [[wiki/pages/claude-desktop]] — Cowork is one of three operating modes in the Claude suite
- [[wiki/pages/sub-agents]] — Cowork uses sub-agents for parallel task execution
- [[wiki/pages/claude-projects]] — Cowork tasks inherit context from the project they are launched from
- [[wiki/pages/rag-retrieval-augmented-generation]] — project knowledge available to Cowork tasks via RAG
- [[wiki/pages/skills]] — Skills can be created and tested using Cowork

## Sources

- [[wiki/sources/manuale-seconda-lezione]] — Cowork introduced with the Beas documentation analysis exercise
- [[wiki/sources/manuale-quinta-lezione]] — Cowork in the SDD workflow: project configuration generation- [[wiki/sources/manuale-sesta-lezione]] — Cowork as a Skill creation environment