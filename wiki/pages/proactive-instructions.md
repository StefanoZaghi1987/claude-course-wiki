---
type: page
created: 2026-05-31
updated: 2026-05-31
tags: [claude-code, claude-md, ai4gamma-corso]
---

Proactive Instructions are the CLAUDE.md section that defines tasks Claude should execute autonomously at the end of each sprint, without being explicitly asked.

## Overview

Proactive Instructions is one of the seven recommended sections of a well-structured CLAUDE.md. Unlike reactive instructions (which tell Claude how to respond to specific user requests), Proactive Instructions program recurring maintenance behaviors into the agent: after every sprint, Claude runs these tasks before returning control, ensuring the project stays clean and documented without the user needing to remember to ask each time.

## Key dimensions

### Common examples

Typical Proactive Instructions include: "after each task, update the project architecture map in `docs/architecture.md`", "after each component, run tests and summarize failures", "after each sprint, run `/revise-claude-md` to keep the CLAUDE.md current", "after each file edit, verify the build still passes". [[wiki/sources/manuale-quinta-lezione]]

### Relation to sprint discipline

Proactive Instructions fire at the end of each defined sprint unit, so they are most effective when the development plan has clear sprint boundaries. The instructions should be lightweight enough to run after every sprint without consuming excessive context — one or two targeted actions, not a comprehensive audit. [[wiki/sources/manuale-quinta-lezione]]

## Connections

- [[wiki/pages/claude-md]] — Proactive Instructions is one section of the recommended CLAUDE.md structure
- [[wiki/pages/spec-driven-development]] — Proactive Instructions support sprint-cycle discipline in SDD

## Sources

- [[wiki/sources/manuale-quinta-lezione]] — recommended CLAUDE.md structure with Proactive Instructions defined
