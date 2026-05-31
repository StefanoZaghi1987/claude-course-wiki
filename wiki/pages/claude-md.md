---
type: page
created: 2026-05-31
updated: 2026-05-31
tags: [claude-code, claude-md, ai4gamma-corso]
---

CLAUDE.md is the static project configuration file for Claude Code — auto-loaded at every session start, it provides the agent with its role, context, constraints, and conventions without any user action.

## Overview

CLAUDE.md is a Markdown file placed in a project's root directory (or in a `.claude/` subfolder). When Claude Code is launched in that directory, CLAUDE.md is the first thing loaded into the agent's context, before any user prompt. It is the Claude Code equivalent of Claude Desktop's project Instructions (system prompt) — the stable knowledge layer that defines who the agent is and what it knows about the project. Unlike Claude Desktop's Instructions, CLAUDE.md is a file on disk: it is versioned, shareable, and can be edited with any text editor.

## Key dimensions

### CLAUDE.md vs. memory.md

CLAUDE.md is the "project wiki" — stable documentation that changes rarely: the agent's role, project objectives, naming conventions, architectural constraints, technical context. `memory.md` is the "agent scratchpad" — a dynamic file updated during sessions to record volatile preferences and notes (e.g., "never run git commands autonomously," "always open pages in a new tab"). The two complement each other: CLAUDE.md provides the invariant context; memory.md accumulates session-to-session learning. [[wiki/sources/manuale-terza-lezione]]

### Comparison with Claude Desktop

| Element (Claude Desktop) | Equivalent (Claude Code) |
|---|---|
| Instructions / System Prompt | CLAUDE.md |
| Files / Project Knowledge | Files in the project folder (explicitly read) |
| Project | Working directory |

Key difference: in Claude Desktop, project files are indexed in RAG and retrieved automatically. In Claude Code, only CLAUDE.md is auto-loaded — all other files must be explicitly referenced in the prompt: "Read the file `specs.md` and…". [[wiki/sources/manuale-terza-lezione]]

### Generation via meta-prompting

The recommended way to create a high-quality CLAUDE.md is to meta-prompt Claude from within an already-configured Claude Desktop project: ask it to generate the best CLAUDE.md for use in Claude Code, specifying the expected structure. The resulting artifact is downloaded and placed in the project folder. This approach leverages the Desktop project's existing Instructions and knowledge base, producing a richer configuration than starting from scratch in Code. [[wiki/sources/manuale-terza-lezione]]

### Location and storage

CLAUDE.md can be placed in the project root or in a `.claude/` subfolder (preferred for cleanliness). Claude Code session data (conversations, sub-agent tasks, development plans) is stored in `C:\Users\[username]\.Claude\projects\[folder-name]\` on Windows. Session files are JSON and can be resumed with `/resume`. [[wiki/sources/manuale-terza-lezione]]

### Recommended structure

A well-structured CLAUDE.md contains: **Purpose and Context** (brief project description and main objective), **Absolute Principles** (inviolable rules — e.g., "app must always work offline", "maximum 200 lines per file"), **Technology Stack** (frameworks, libraries, dependencies), **Architecture** (logical app structure, module breakdown), **Proactive Instructions** (tasks Claude should execute autonomously after each sprint — e.g., "after each task, update the project map"), **File Reading Rules** (when to load which files: lazy vs. eager), **Enforcement Rules** (programming best-practice reminders that repeat each session). [[wiki/sources/manuale-quinta-lezione]]

### Modularization

For medium-to-large projects, split CLAUDE.md into thematic module files referenced by a master file. Benefits: each agent loads only relevant modules (lower per-session token cost), individual files are smaller and easier to update, each file has a clear focused scope. Thematic modules: one for stack, one for architecture, one for sync rules, one for enforcement rules. The master file is an index that tells Claude when to read which module. [[wiki/sources/manuale-quinta-lezione]]

### Desktop→Code bridge

CLAUDE.md is the manual bridge between the two environments: configure in Desktop → meta-prompt to generate CLAUDE.md → download artifact → copy to local project folder → launch Code. The two environments do not auto-sync; CLAUDE.md is the deliberate handoff mechanism. [[wiki/sources/manuale-terza-lezione]]

### The four-level CLAUDE.md hierarchy

Claude Code loads CLAUDE.md files from four scopes, in this order from broadest to most specific:

| Scope | Location | Purpose | Shared with |
|-------|----------|---------|-------------|
| Managed policy | System path (OS-dependent) | Org-wide rules deployed by IT/DevOps | All users on the machine; cannot be excluded |
| User | `~/.claude/CLAUDE.md` | Personal preferences across all projects | Just you, all projects |
| Project | `./CLAUDE.md` or `./.claude/CLAUDE.md` | Team-shared project standards | Team via git |
| Local | `./CLAUDE.local.md` (gitignored) | Personal per-project notes | Just you, this project |

All levels load additively and are concatenated, ordered from the filesystem root down to the working directory, so project instructions appear after user instructions in context. Block-level HTML comments (`<!-- ... -->`) are stripped before injection — use them for maintainer notes without spending tokens. [[wiki/sources/how-claude-remembers-your-project-claude-code-docs]]

### Rules directory: `.claude/rules/`

For larger projects, CLAUDE.md can be split into topic files placed in `.claude/rules/`. Each file should cover one topic with a descriptive filename (e.g., `testing.md`, `api-design.md`). Two modes: files **without** `paths:` frontmatter load every session alongside CLAUDE.md; files **with** `paths:` frontmatter load only when Claude reads a file matching the specified glob pattern — saving context for instructions irrelevant to the current task. Rules support symlinks for sharing sets across multiple repositories. [[wiki/sources/how-claude-remembers-your-project-claude-code-docs]]

### @import syntax and CLAUDE.local.md

CLAUDE.md files can import other files using `@path/to/import` syntax. Imported files are expanded and loaded into context at launch alongside the importing file. Relative paths resolve relative to the file containing the import (not the working directory). Recursive imports are supported up to four hops deep. `CLAUDE.local.md` at the project root is treated identically to `CLAUDE.md` but appended after it, and is gitignored by default — use it for personal sandbox URLs, preferred test data, or local workflow notes. [[wiki/sources/how-claude-remembers-your-project-claude-code-docs]]

### AGENTS.md compatibility

Claude Code reads `CLAUDE.md`, not `AGENTS.md`. For repos that already use AGENTS.md for other coding agents, create a CLAUDE.md that starts with `@AGENTS.md` to import it, then add Claude-specific instructions below. Running `/init` in a repo with AGENTS.md, `.cursorrules`, or `.windsurfrules` reads those files and incorporates the relevant parts into the generated CLAUDE.md automatically. [[wiki/sources/how-claude-remembers-your-project-claude-code-docs]]

## Connections

- [[wiki/pages/claude-code]] — the CLI environment where CLAUDE.md is consumed
- [[wiki/pages/claude-desktop]] — the environment where CLAUDE.md is best generated via meta-prompting
- [[wiki/pages/memory-in-claude]] — memory.md is the dynamic complement to the static CLAUDE.md
- [[wiki/pages/meta-prompting]] — the recommended technique for generating CLAUDE.md content
- [[wiki/pages/spec-driven-development]] — CLAUDE.md is the project configuration that grounds SDD sessions

## Sources

- [[wiki/sources/manuale-terza-lezione]] — CLAUDE.md introduced, compared with Desktop, generation workflow, Desktop→Code bridge
- [[wiki/sources/manuale-quinta-lezione]] — recommended structure, modularization, Intermediate and Advanced generation workflows, /revise-claude-md and /claude-md-improver commands
- [[wiki/sources/how-claude-remembers-your-project-claude-code-docs]] — 4-level hierarchy, rules/ directory, @import syntax, CLAUDE.local.md, AGENTS.md compatibility
- [[wiki/sources/extend-claude-code-claude-code-docs]] — CLAUDE.md vs skills decision framework; feature layering rules
