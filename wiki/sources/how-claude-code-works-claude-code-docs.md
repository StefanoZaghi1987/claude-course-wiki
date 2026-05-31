---
type: source
created: 2026-05-31
updated: 2026-05-31
tags: [claude-code, official-docs]
source_url: https://code.claude.com/docs/en/how-claude-code-works
source_path: raw/web/how-claude-code-works-claude-code-docs/
---

Authoritative technical reference for Claude Code's internal architecture — the agentic loop, built-in tool categories, execution environments, session model, and context management (May 2026).

## Summary

Claude Code is an agentic harness around a Claude model: the harness provides tools, context management, and execution environment; the model does the reasoning. When given a task Claude runs three blended phases — gather context (reads files, searches), take action (edits, runs commands), verify results (runs tests, checks output) — repeatedly until the task is done. The phrase "Claude decides" in the docs means the model is doing the reasoning; the phrase "Claude Code does" means the harness is executing a tool call.

Five categories of built-in tools give Claude concrete agency. File operations: read, edit, create, rename, reorganize. Search: glob patterns, regex content search, directory exploration. Execution: shell commands, servers, tests, git — any command you can run from the CLI. Web: search the web, fetch documentation, look up error messages. Code intelligence: LSP-sourced type errors and symbol navigation (requires a connected IDE extension or language server). These are the foundation; skills, MCP, hooks, and sub-agents are the extension layer on top.

Three execution environments determine where code actually runs: local (your machine, default, full filesystem and tool access), cloud (Anthropic-managed VMs, for tasks that don't need local files), and remote control (your machine controlled from a browser or phone — the session stays local but the interface moves to claude.ai/code). Each interface (terminal CLI, Desktop app, IDE extensions, web, remote control, Slack, CI/CD) runs the same underlying loop.

Sessions are saved continuously as JSONL files at `~/.claude/projects/<project>/<session-id>.jsonl`. Each new session starts with a fresh context window; auto memory and CLAUDE.md carry knowledge across sessions. Sessions can be resumed (`--continue` or `--resume`), forked (`/branch` or `--fork-session`), or rewound using checkpoints — before every file edit Claude snapshots the file, enabling `Esc+Esc` rewind.

The context window holds conversation history, file contents, command outputs, CLAUDE.md, auto memory, loaded skills, and system instructions. Auto-compaction clears older tool outputs first, then summarizes if needed. A "thrashing" error occurs when a single file or tool output is so large that context refills immediately after each compaction — Claude stops auto-compacting after a few attempts and shows an error. Put persistent rules in CLAUDE.md rather than relying on conversation history, and use `/compact [focus]` for manual control before the threshold.

## Key points

- Agentic loop: gather context → take action → verify results, blended and repeated; the model reasons, the harness executes
- Five built-in tool categories: file operations, search, execution, web, code intelligence (LSP requires IDE connection)
- Three execution environments: local (default), cloud (Anthropic VMs), remote control (local machine + remote interface)
- Sessions stored as JSONL at `~/.claude/projects/`; every file edit is checkpointed for `Esc+Esc` rewind
- Auto-compaction clears tool outputs first, then summarizes; put persistent rules in CLAUDE.md, not in conversation
- Thrashing error: if a single source refills context immediately, auto-compaction stops and shows an error rather than looping

## Connections

- [[wiki/pages/claude-code]] — the environment this document describes
- [[wiki/pages/context-window]] — what fills the window and how compaction works
- [[wiki/pages/sessions-management]] — session lifecycle, resume, fork, rewind
- [[wiki/pages/permission-modes]] — checkpoints and safety mechanisms described here
- [[wiki/pages/claude-md]] — the persistent configuration loaded every session
- [[wiki/pages/memory-in-claude]] — auto memory as the cross-session learning mechanism
