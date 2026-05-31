---
type: source
created: 2026-05-31
updated: 2026-05-31
tags: [claude-code, best-practices, official-docs]
source_url: https://code.claude.com/docs/en/best-practices
source_path: raw/web/best-practices-for-claude-code-claude-code-docs/
---

Proven patterns for getting the best results from Claude Code — context management, prompting, environment setup, and scaling to parallel sessions (May 2026).

## Summary

The document opens with the fundamental constraint: Claude's context window fills fast, and performance degrades as it fills. Every message, file read, and command output consumes tokens. Managing context deliberately is the most important skill for consistent results.

**Give Claude a way to verify its work.** Without a check it can run, "looks done" is Claude's only signal. Provide a test suite, build exit code, linter, output diff, or screenshot comparison. Ask Claude to run the check and iterate in the same message. Use a Stop hook to make the check a deterministic gate. Use a verification subagent for an independent second opinion — one that didn't do the original work.

**Explore first, then plan, then code.** Use plan mode to separate exploration from execution: enter plan mode, let Claude read files and answer questions, then ask for a detailed implementation plan, then switch to implementation. Skip planning for small, clearly scoped tasks (a typo fix, a log line).

**Provide specific context.** Reference exact files, state constraints, point to example patterns. Instead of "add tests for foo.py": "write a test for foo.py covering the logged-out edge case, no mocks." Provide rich content via `@file`, pasted images, URLs, piped data, and letting Claude fetch context itself.

**Configure your environment.** Write an effective CLAUDE.md (run `/init` for a starting point; ruthlessly prune — bloated CLAUDE.md causes Claude to ignore important rules). Use permission allowlists or auto mode to reduce approval fatigue. Install the `gh` CLI for GitHub work. Connect MCP servers for external services. Set up hooks for deterministic automation. Create skills for repeatable workflows. Install code intelligence plugins for typed languages.

**Manage your session.** Course-correct early: press Esc to stop, Esc+Esc to rewind with code restore. Use `/clear` between unrelated tasks. Use subagents for large investigations rather than filling your main context. Use `/compact [focus]` before hitting the threshold. Start fresh sessions with better prompts rather than correcting over and over in a long polluted session.

**Avoid common failure patterns.** Kitchen sink session (unrelated tasks in one session — use `/clear`). Correcting over and over (after two failed corrections, `/clear` and write a better prompt). Over-specified CLAUDE.md (prune ruthlessly; convert to hooks if you need guarantees). Trust-then-verify gap (always provide verification). Infinite exploration (scope narrowly or use subagents).

**Scale with parallel sessions and automation.** Non-interactive mode (`claude -p`) for CI and pre-commit hooks. Worktrees for parallel local sessions. Desktop for visual parallel session management. Claude Code on the web for cloud sessions. Agent teams for automated coordination. Fan-out patterns for large migrations (list files → distribute across parallel Claude invocations). Add an adversarial review subagent step before counting long unattended runs as done.

## Key points

- Context window is the primary constraint — manage it explicitly with /clear, /compact, and subagents
- Verification-first: give Claude a test/check to run, not just "look done" as the signal
- Explore-plan-code: use plan mode for non-trivial changes; skip for small obvious tasks
- CLAUDE.md discipline: ruthlessly prune; bloated files cause Claude to ignore the important rules
- Course-correct early: Esc to stop, Esc+Esc to rewind, /clear between unrelated tasks
- Fan out: parallel sessions (worktrees/Desktop/web), non-interactive mode for CI, agent teams for coordination

## Connections

- [[wiki/pages/claude-code]] — the environment these practices apply to
- [[wiki/pages/context-window]] — context management is the central theme
- [[wiki/pages/permission-modes]] — auto mode and plan mode referenced
- [[wiki/pages/sub-agents]] — subagents as the primary tool for context isolation
- [[wiki/pages/claude-md]] — CLAUDE.md discipline and pruning
- [[wiki/pages/sessions-management]] — session management patterns
- [[wiki/pages/plugins]] — hooks, MCP connections, and skills referenced as environment setup tools
- [[wiki/pages/skills]] — skills as repeatable workflow automation
