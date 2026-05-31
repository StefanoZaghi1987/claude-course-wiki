---
type: source
created: 2026-05-31
updated: 2026-05-31
tags: [claude-code, context-window, official-docs]
source_url: https://code.claude.com/docs/en/context-window
source_path: raw/web/explore-the-context-window-claude-code-docs/
---

Interactive walkthrough of the Claude Code context window — what loads at session start, what each action costs, and what survives /compact (May 2026).

## Summary

Claude Code's context window holds everything Claude can see in a session: conversation history, file contents, command outputs, CLAUDE.md, auto memory, loaded skills, system instructions. This document provides a session-timeline view of what enters the window and when.

Before the first prompt, four things pre-load automatically: CLAUDE.md (full content), auto memory (first 200 lines of MEMORY.md), MCP tool names (schemas load later on demand via tool search), and skill descriptions (full bodies load only when a skill is invoked). Path-scoped rules (rules with `paths:` frontmatter in `.claude/rules/`) do not load at session start — they load when Claude reads a file matching their pattern. An output style or `--append-system-prompt` content also loads here, in the system prompt.

During the session, each file read adds to context. When Claude works in a subdirectory, the nested CLAUDE.md for that subdirectory loads alongside the first file read there. A PostToolUse hook fires after each edit, and its return value (if any) enters context. When you delegate research to a subagent, the subagent runs in a completely separate context window — all its file reads and searches stay there; only a summary returns to your main window. This is the most effective way to keep large explorations out of your context.

After `/compact`, different mechanisms survive in different ways. The project-root CLAUDE.md and unscoped rules re-inject from disk automatically. Auto memory re-injects from disk. But path-scoped rules and nested CLAUDE.md files from subdirectories are lost until a file in the matching directory is read again. Invoked skill bodies re-inject with caps: 5,000 tokens per skill, 25,000 tokens total across all skills; the oldest-invoked skills are dropped first when the total budget is exceeded, and truncation keeps the start of the file. The system prompt and output style are unchanged throughout.

To check actual context usage live: run `/context` for a breakdown by category with optimization suggestions. Run `/memory` to see which CLAUDE.md and auto memory files loaded at startup.

## Key points

- Pre-session load order: CLAUDE.md (full) → auto memory (200 lines MEMORY.md) → MCP tool names → skill descriptions; path-scoped rules load lazily on file access
- Subagents completely isolate their work — large research stays out of your main context; only the summary returns
- Post-compaction survival: project-root CLAUDE.md and unscoped rules re-inject from disk; path-scoped rules and nested CLAUDE.md files do NOT re-inject automatically
- Skill body re-injection after compaction: capped at 5,000 tokens/skill and 25,000 total; oldest dropped first; truncation preserves start of file
- Live inspection: `/context` for current breakdown; `/memory` for which memory files are loaded

## Connections

- [[wiki/pages/context-window]] — the concept this document illustrates
- [[wiki/pages/claude-code]] — the environment in which this applies
- [[wiki/pages/sub-agents]] — how subagent isolation protects your main context
- [[wiki/pages/skills]] — skill body capping and lazy loading
- [[wiki/pages/claude-md]] — what CLAUDE.md content survives compaction
- [[wiki/pages/memory-in-claude]] — auto memory load behavior at session start
