---
type: page
created: 2026-05-31
updated: 2026-05-31
tags: [claude-code, sub-agents, spec-driven-development, ai4gamma-corso]
---

Sub-Agent Driven Development (SADD) is an execution pattern for Spec-Driven Development in which an approved development plan is distributed across parallel sub-agents for faster, higher-quality implementation.

## Overview

In standard sequential SDD, Claude Code implements each plan task one after another in a single context window. Sub-Agent Driven Development restructures execution: the orchestrator receives an approved spec and plan, then assigns each task to an independent sub-agent running in its own context. Tasks execute in parallel, reducing wall-clock time to approximately the duration of the slowest individual task rather than the sum of all tasks. The plan's "For Agentic Workers" section controls which tasks run in parallel and which must run sequentially due to dependencies.

## Key dimensions

### Parallel vs. sequential comparison

Parallel sub-agent execution is faster in wall-clock time and produces higher output quality because it includes automatic inter-agent code review — each sub-agent's output can be reviewed by another before integration. The cost is higher token consumption. Sequential execution costs fewer tokens but takes longer and lacks the automatic cross-agent review step. [[wiki/sources/manuale-quinta-lezione]]

### Plan structure for sub-agents

The development plan's "For Agentic Workers" section is the key control point: it specifies which tasks the orchestrator should assign to parallel sub-agents and which must execute sequentially. Tasks without cross-dependencies are parallelized; tasks that depend on a prior step's output are marked sequential. [[wiki/sources/manuale-quinta-lezione]]

### When to use it

SADD pays off when the plan has ≥3–4 independently executable tasks across multiple files. For small, tightly sequential changes, standard single-agent execution is simpler. The overhead of spawning and coordinating multiple agents is only worthwhile when genuine parallelism exists in the plan. [[wiki/sources/manuale-quinta-lezione]] [[wiki/sources/manuale-quarta-lezione]]

## Connections

- [[wiki/pages/sub-agents]] — the mechanism that makes SADD possible
- [[wiki/pages/spec-driven-development]] — SADD is the parallelized execution phase of the Advanced SDD workflow
- [[wiki/pages/claude-code]] — the environment where the orchestrator and sub-agents run

## Sources

- [[wiki/sources/manuale-quinta-lezione]] — SADD formally introduced, compared with sequential execution, plan structure for sub-agents
- [[wiki/sources/manuale-quarta-lezione]] — sub-agent execution introduced in the Advanced SDD workflow context
