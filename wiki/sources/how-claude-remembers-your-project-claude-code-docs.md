---
type: source
created: 2026-05-31
updated: 2026-05-31
tags: [claude-code, memory, claude-md, official-docs]
source_url: https://code.claude.com/docs/en/memory
source_path: raw/web/how-claude-remembers-your-project-claude-code-docs/
---

Official reference for Claude Code's two cross-session memory mechanisms: CLAUDE.md files (user-authored instructions) and auto memory (Claude-authored learnings) (May 2026).

## Summary

Each Claude Code session starts with a fresh context window. Two mechanisms bridge sessions: CLAUDE.md files (instructions the user writes) and auto memory (notes Claude writes itself). Both load at session start; neither provides strict enforcement — they are context, not configuration. To block an action regardless of Claude's judgment, use a PreToolUse hook instead.

CLAUDE.md files live in four scopes, loaded in this order from broadest to most specific: managed policy (system-path file deployed by IT/DevOps, cannot be excluded), user (~/.claude/CLAUDE.md, personal preferences across all projects), project (./CLAUDE.md or ./.claude/CLAUDE.md, team-shared, committed to git), and local (./CLAUDE.local.md, personal per-project, gitignored). Claude walks up the directory tree from the working directory collecting all CLAUDE.md and CLAUDE.local.md files; they are concatenated, with content ordered from root down to working directory so more-specific instructions appear last (read last = higher priority in context). Block-level HTML comments are stripped before injection, saving context tokens while preserving maintainer notes.

The `.claude/rules/` directory lets you split CLAUDE.md into topic files. Rules without a `paths:` frontmatter field load every session alongside CLAUDE.md. Rules with `paths:` frontmatter load only when Claude reads files matching the specified glob patterns — this reduces noise and saves context. Rules support symlinks for sharing across multiple repositories. A user-level `~/.claude/rules/` directory applies rules across all projects.

CLAUDE.md can import other files with `@path/to/file` syntax anywhere in the body. Relative paths resolve from the file containing the import, not the working directory. Imports are expanded and loaded at launch alongside the importing file; up to four hops of recursive import are permitted. CLAUDE.local.md is treated the same as CLAUDE.md but is appended after it at each directory level.

For teams already using AGENTS.md (for other coding agents), create a CLAUDE.md that imports it: `@AGENTS.md` on the first line. Running `/init` in a repo with AGENTS.md, .cursorrules, or .windsurfrules reads those files and incorporates the relevant parts into the generated CLAUDE.md.

Auto memory lets Claude accumulate knowledge without the user writing anything. Claude saves to `~/.claude/projects/<project>/memory/MEMORY.md` and optional topic files. All worktrees and subdirectories within the same git repo share one auto memory directory. At session start, the first 200 lines (or 25KB) of MEMORY.md load; topic files load on demand when Claude needs them. Claude decides what is worth remembering based on whether it would be useful in a future conversation. Toggle auto memory via `/memory` or set `autoMemoryEnabled` in settings. Run `/memory` to browse, edit, or delete saved memories.

## Key points

- Two cross-session mechanisms: CLAUDE.md (user writes, instructions) + auto memory (Claude writes, learnings); both load at session start as context, not enforced configuration
- Four CLAUDE.md scopes: managed policy → user → project → local; all load additively, ordered root-to-working-directory
- `.claude/rules/` directory: topic files that load every session (no paths frontmatter) or lazily on file access (paths: frontmatter)
- `@path/to/file` import syntax: expands at launch, up to 4 hops, relative to the importing file
- AGENTS.md compatibility: import with `@AGENTS.md`; `/init` reads AGENTS.md/.cursorrules and generates CLAUDE.md
- Auto memory storage: `~/.claude/projects/<project>/memory/`; first 200 lines of MEMORY.md load at start; topic files load on demand

## Connections

- [[wiki/pages/claude-md]] — CLAUDE.md as a concept including the 4-level hierarchy
- [[wiki/pages/memory-in-claude]] — the broader memory architecture including Claude Desktop levels
- [[wiki/pages/context-window]] — where CLAUDE.md and auto memory load in the startup sequence
- [[wiki/pages/claude-code]] — the environment where both mechanisms operate
- [[wiki/pages/sub-agents]] — subagents can have their own persistent memory
