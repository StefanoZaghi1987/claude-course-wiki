---
type: page
created: 2026-05-31
updated: 2026-05-31
tags: [claude-code, claude-md, ai4gamma-corso]
---

Absolute Principles are the inviolable rules section of a CLAUDE.md file — hard constraints that Claude must never break regardless of the task.

## Overview

Absolute Principles is one of the seven recommended sections of a well-structured CLAUDE.md. Unlike Enforcement Rules (which are best-practice reminders Claude should apply during implementation), Absolute Principles are non-negotiable constraints that define the outer boundary of what the agent may do. They belong in CLAUDE.md because they are loaded at every session start — they cannot be lost to context compaction the way in-conversation instructions can.

## Key dimensions

### Distinction from Enforcement Rules

Absolute Principles are constraints (what Claude must never do, or invariants it must always preserve); Enforcement Rules are reminders (what Claude should prefer when making implementation decisions). Violating an Absolute Principle breaks the project's integrity; drifting from an Enforcement Rule degrades quality but does not corrupt the codebase. [[wiki/sources/manuale-quinta-lezione]]

### Common examples

Typical Absolute Principles include: maximum file length limits ("no file may exceed 200 lines"), offline-first requirements ("the app must always work without a network connection"), database schema immutability rules, mandatory test coverage gates, and constraints on which commands may run autonomously ("never run git push without explicit user confirmation"). [[wiki/sources/manuale-quinta-lezione]]

## Connections

- [[wiki/pages/claude-md]] — Absolute Principles is one section of the recommended CLAUDE.md structure
- [[wiki/pages/claude-code]] — the environment where CLAUDE.md (and its rules) are loaded at session start

## Sources

- [[wiki/sources/manuale-quinta-lezione]] — recommended CLAUDE.md structure introduced; Absolute Principles defined
