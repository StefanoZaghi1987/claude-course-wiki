---
type: page
created: 2026-05-31
updated: 2026-05-31
tags: [memory, claude-desktop, ai4gamma-corso]
---

Claude manages persistent context across three non-overwriting memory levels that range from user-global to project-specific scope.

## Overview

LLMs have no native inter-session memory: each new conversation starts from a blank slate. Claude compensates through three structured memory levels that are hierarchically additive — each lower level adds specificity without overriding higher ones. Understanding which level to use for which type of information determines whether Claude behaves consistently across sessions or requires constant re-briefing.

## Key dimensions

### Global user preferences

Stored in Settings → Preferences, this level holds stable, user-wide instructions applicable to all work: communication style, preferred output formats, recurring context such as company name and role. This is the right level for information that is true in every context — for example, corporate email templates that should be available across all projects. [[wiki/sources/manuale-prima-lezione]]

### Chat memory (automatic extraction)

Claude automatically extracts facts learned during conversations and saves them as memories that persist across future chats. These are viewable and editable by the user. Unlike preferences (manually authored), chat memories are AI-generated inferences from interaction patterns. They can be selectively deleted if incorrect. [[wiki/sources/manuale-prima-lezione]]

### Project-level memory

Project instructions and uploaded files scope context to a specific project. This is the right level for domain knowledge, client details, naming conventions, technical constraints, and stored procedures relevant to a particular work area. Project memory sits between global preferences and the session-level context window in the hierarchy. [[wiki/sources/manuale-prima-lezione]]

### Hierarchy principle

The key invariant from the course: "ogni nuova conversazione parte da un contesto vuoto" — every new conversation starts empty. Memory levels are the mechanism that pre-populates that emptiness with relevant context at the appropriate scope. Lower levels (project) override higher ones (global) where they conflict, but do not erase them for other contexts. [[wiki/sources/manuale-seconda-lezione]]

### Claude Code: two session-bridging mechanisms

Claude Code has a distinct, more granular memory architecture than Claude Desktop. Two complementary mechanisms carry knowledge across sessions:

| | CLAUDE.md files | Auto memory |
|--|-----------------|-------------|
| Who writes it | You | Claude |
| What it contains | Instructions and rules | Learnings and patterns discovered during sessions |
| Scope | Project, user, or org (4 levels) | Per repository, shared across worktrees |
| Loaded into | Every session (full content) | Every session (first 200 lines / 25KB of MEMORY.md) |
| Best for | Coding standards, workflows, architecture decisions | Build commands, debugging insights, preferences Claude discovers |

[[wiki/sources/how-claude-remembers-your-project-claude-code-docs]]

### Auto memory architecture

Claude writes auto memory to `~/.claude/projects/<project>/memory/MEMORY.md`, with detailed notes stored in separate topic files (e.g., `debugging.md`, `patterns.md`). All worktrees and subdirectories within the same git repo share one auto memory directory. At session start, the first 200 lines (or 25KB, whichever comes first) of `MEMORY.md` load automatically; topic files load on demand when Claude needs the information. Claude decides what is worth saving — it does not write to auto memory every session, only when something would be useful in a future conversation. [[wiki/sources/how-claude-remembers-your-project-claude-code-docs]]

### The /memory command

Running `/memory` in a Claude Code session shows all CLAUDE.md, CLAUDE.local.md, and rules files loaded in the current session, provides a link to the auto memory folder, and lets you toggle auto memory on or off. Select any file to open it in your editor. When you ask Claude to remember something, it saves to auto memory; to add to CLAUDE.md instead, ask Claude explicitly ("add this to CLAUDE.md") or edit the file via `/memory`. [[wiki/sources/how-claude-remembers-your-project-claude-code-docs]]

## Connections

- [[wiki/pages/context-window]] — the in-session working space; resets each session (distinct from persistent memory)
- [[wiki/pages/claude-projects]] — the container for project-level memory
- [[wiki/pages/rag-retrieval-augmented-generation]] — how project files are retrieved into the context when referenced

## Sources

- [[wiki/sources/manuale-prima-lezione]] — three memory levels introduced in Lesson 1
- [[wiki/sources/manuale-seconda-lezione]] — full memory hierarchy table: global preferences → project (shared + per-user AI memory) → current chat
- [[wiki/sources/how-claude-remembers-your-project-claude-code-docs]] — Claude Code dual mechanisms: CLAUDE.md + auto memory; auto memory architecture and /memory command
