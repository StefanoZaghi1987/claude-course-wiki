---
type: page
created: 2026-05-31
updated: 2026-05-31
tags: [claude-code, claude-md, ai4gamma-corso]
---

File Reading Rules are the CLAUDE.md section that instructs Claude on when to load which files — distinguishing between files that must always be read eagerly and files that should only be read when specifically relevant.

## Overview

File Reading Rules is one of the seven recommended sections of a well-structured CLAUDE.md. Every file Claude reads costs context tokens, so CLAUDE.md should explicitly specify the reading strategy for the project's key files. Without guidance, Claude may over-read (saturating context with rarely-relevant files) or under-read (missing important context when needed). File Reading Rules divide files into two categories: **eager** (read at session start regardless of task) and **lazy** (read only when working on the related area).

## Key dimensions

### Eager vs. lazy reading

**Eager files** are always loaded because they provide invariant context: the project architecture overview, API contracts, naming conventions. **Lazy files** are domain-specific and only relevant for certain tasks: the payment module spec when working on billing, test fixtures when writing tests. Loading eager files every session ensures core context is always present; restricting lazy files prevents saturation. [[wiki/sources/manuale-quinta-lezione]]

### Context economy

File Reading Rules are a token-management technique. A well-specified set of rules prevents the "context thrashing" pattern where Claude re-reads large files for every subtask. Combined with CLAUDE.md modularization, File Reading Rules make per-session context cost predictable and bounded. [[wiki/sources/manuale-quinta-lezione]]

## Connections

- [[wiki/pages/claude-md]] — File Reading Rules is one section of the recommended CLAUDE.md structure
- [[wiki/pages/context-window]] — File Reading Rules directly manage context token consumption per session

## Sources

- [[wiki/sources/manuale-quinta-lezione]] — recommended CLAUDE.md structure with File Reading Rules defined
