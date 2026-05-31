---
type: source
created: 2026-05-31
updated: 2026-05-31
tags: [claude-code, workflows, official-docs]
source_url: https://code.claude.com/docs/en/common-workflows
source_path: raw/web/common-workflows-claude-code-docs/
---

Short recipes for everyday Claude Code development tasks — prompt patterns, session resumption, parallel sessions, plan mode, subagent delegation, and CLI piping (May 2026).

## Summary

This page collects practical patterns for everyday development. The core prompt recipes cover: getting a codebase overview (ask for structure, architecture, and entry points), finding relevant code, fixing bugs by pasting the error message and asking Claude to trace it and write a failing test first, refactoring to modern patterns, writing tests that match existing style, creating PRs (ask directly or guide step-by-step), updating documentation, working in non-code folders (notes vaults, documentation), working with images (drag-and-drop, Ctrl+V paste, or provide a path), and referencing files/directories with `@`.

Cross-cutting workflow patterns:
- **Resume conversations**: `claude --continue` for the most recent session; `claude --resume` for a list; `/resume` inside a running session. Sessions are saved locally — you never need to re-explain context.
- **Parallel sessions with worktrees**: run separate CLI sessions in isolated git checkouts so edits don't collide. Use background agents or the Desktop sidebar to monitor parallel sessions from one screen.
- **Plan before editing**: enter plan mode (Shift+Tab or `/plan` prefix) so Claude reads and proposes without editing. Review the plan, then approve or refine.
- **Delegate research to subagents**: instead of having Claude read hundreds of files in your main context, ask it to use a subagent for the exploration. Only the findings come back.
- **Pipe Claude into scripts**: `cat error.log | claude`, non-interactive mode with `claude -p "..."`, JSON output for programmatic consumption.
- **Scheduled tasks**: Routines for cloud-based recurring tasks; Desktop scheduled tasks for local recurring tasks; GitHub Actions for CI triggers; `/loop` for quick in-session repetition.

## Key points

- Prompt patterns: explore first (ask for overview before making changes), paste full error messages, ask Claude to write a failing test before fixing
- Session patterns: `--continue`, `--resume`, `/resume`; sessions save locally and resume without re-explaining context
- Parallel work: worktrees prevent edit collisions between concurrent sessions; monitor with Desktop sidebar or background agents
- Plan mode: explore → plan → implement; use Shift+Tab or `/plan` prefix
- Subagent delegation: keeps large file reads out of your main context window
- CLI composability: pipe stdin, use `-p` for non-interactive, use `--verbose` for debugging

## Connections

- [[wiki/pages/claude-code]] — the environment all these patterns apply to
- [[wiki/pages/sessions-management]] — resume and parallel session patterns
- [[wiki/pages/sub-agents]] — subagent delegation for context isolation
- [[wiki/pages/permission-modes]] — plan mode is accessed via Shift+Tab
