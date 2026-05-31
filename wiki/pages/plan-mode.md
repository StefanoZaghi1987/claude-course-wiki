---
type: page
created: 2026-05-31
updated: 2026-05-31
tags: [claude-code, permissions]
---

Plan mode is a Claude Code permission mode in which the agent reads and explores the codebase but makes no file edits until the user approves a written plan.

## Overview

Plan mode is one of six Claude Code permission modes, positioned between `acceptEdits` and `auto` on the oversight spectrum. In plan mode, Claude is restricted to read-only tools — it can open files, search the codebase, and ask clarifying questions — but cannot write or edit any file until the user explicitly approves the plan it produces. This makes it the recommended starting point for large refactors, unfamiliar codebases, and any task where understanding the full scope before touching code is important.

## Key dimensions

### Activating plan mode

In the CLI, press `Shift+Tab` to cycle through default → acceptEdits → plan. Set `defaultMode: "plan"` in `settings.json` for a persistent default. Pass `--permission-mode plan` at startup for a single session. [[wiki/sources/choose-a-permission-mode-claude-code-docs]]

### What happens in plan mode

Claude uses only read-only tools: file reads, searches, web lookups. It produces a structured plan describing what files to create or modify and why. No source files are modified. Only when the user switches to a different mode and re-sends the prompt (or explicitly approves) does execution begin. [[wiki/sources/choose-a-permission-mode-claude-code-docs]] [[wiki/sources/common-workflows-claude-code-docs]]

### Recommended workflow

A productive pattern: enter plan mode → let Claude read files and ask questions → approve or refine the plan → switch mode and execute. For complex changes, using the Opus model during plan mode produces higher-quality plans; then switching to Sonnet for execution reduces token cost. [[wiki/sources/best-practices-for-claude-code-claude-code-docs]] [[wiki/sources/common-workflows-claude-code-docs]]

## Connections

- [[wiki/pages/permission-modes]] — plan mode is one of the six Claude Code permission modes
- [[wiki/pages/claude-code]] — the environment where plan mode operates
- [[wiki/pages/spec-driven-development]] — plan mode is the tool for the exploration-first phase of SDD

## Sources

- [[wiki/sources/choose-a-permission-mode-claude-code-docs]] — plan mode in the six-mode permission system
- [[wiki/sources/common-workflows-claude-code-docs]] — plan before editing workflow pattern
- [[wiki/sources/best-practices-for-claude-code-claude-code-docs]] — explore-plan-code as a best practice
