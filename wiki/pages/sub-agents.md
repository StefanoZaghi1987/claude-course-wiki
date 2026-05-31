---
type: page
created: 2026-05-31
updated: 2026-05-31
tags: [sub-agents, claude-code, plugins, ai4gamma-corso]
---

Sub-agents are independent model instances launched within a Claude Code session to execute specific tasks in parallel, each with its own isolated context window.

## Overview

The Main Orchestrator Agent in Claude Code can spawn sub-agents — separate model instances with their own independent context windows — to parallelize work on complex tasks. This architecture solves the context saturation problem for large-scale work: instead of one agent processing a 100-page document sequentially (risking context overflow), the orchestrator assigns one sub-agent per chapter and assembles the results. Sub-agents are a plugin component and underpin both the Advanced SDD execution phase and Cowork's agentic automation engine.

## Key dimensions

### How parallelization works

The orchestrator receives a task, decomposes it into parallel subtasks, spawns one sub-agent per subtask, each running independently in its own context, then reassembles the outputs into a final result. Explicitly requesting parallelization in the task prompt — "dedicate one sub-agent per chapter, then assemble the final document" — is an advanced technique that improves both quality and completeness on large tasks. [[wiki/sources/manuale-seconda-lezione]] [[wiki/sources/manuale-quarta-lezione]]

### In the Advanced SDD workflow

The execution phase of the Brainstorming & Specification workflow uses sub-agent-driven development: after the specification and development plan are approved, Claude Code can assign each plan task to a sub-agent for parallel execution, then integrate the results. This reduces wall-clock time on multi-file implementations compared to sequential execution. [[wiki/sources/manuale-quarta-lezione]] [[wiki/sources/manuale-quinta-lezione]]

### In Cowork

Cowork's agentic engine uses the same sub-agent architecture to handle large document analysis tasks — one sub-agent per section, results assembled into a unified Markdown document. The parallelization is managed automatically by the engine, not by the user. [[wiki/sources/manuale-seconda-lezione]]

### Context isolation

Each sub-agent has its own isolated context window, independent of the orchestrator's. This is why large tasks can be parallelized without saturating the main context: the work is distributed across multiple independent windows. Sub-agents do not see each other's contexts; only the orchestrator integrates their outputs. [[wiki/sources/manuale-seconda-lezione]]

## Connections

- [[wiki/pages/claude-code]] — the CLI environment where the Main Orchestrator spawns sub-agents
- [[wiki/pages/plugins]] — sub-agents are one of four plugin components
- [[wiki/pages/cowork]] — Cowork uses sub-agent parallelization internally for large tasks
- [[wiki/pages/spec-driven-development]] — sub-agent execution is the parallelization layer of the Advanced SDD workflow
- [[wiki/pages/context-window]] — sub-agents avoid context saturation by distributing work across independent windows

## Sources

- [[wiki/sources/manuale-seconda-lezione]] — sub-agents introduced in the Cowork context
- [[wiki/sources/manuale-quarta-lezione]] — sub-agents in the Advanced SDD execution phase
- [[wiki/sources/manuale-quinta-lezione]] — sub-agent driven development in detail