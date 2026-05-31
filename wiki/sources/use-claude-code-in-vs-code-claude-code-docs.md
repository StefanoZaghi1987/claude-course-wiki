---
type: source
created: 2026-05-31
updated: 2026-05-31
tags: [claude-code, vs-code, official-docs]
source_url: https://code.claude.com/docs/en/vs-code
source_path: raw/web/use-claude-code-in-vs-code-claude-code-docs/
---

Installation and usage guide for the Claude Code VS Code extension — inline diffs, @-mentions, plan review, plugin management, and keyboard shortcuts (May 2026).

## Summary

The Claude Code VS Code extension installs from the Marketplace (search "Claude Code") and requires VS Code 1.98.0 or later. It also installs in VS Code forks (Windsurf, Kiro) and the Open VSX registry. First use prompts for OAuth sign-in through the browser.

The extension opens as a panel that can be repositioned anywhere in VS Code (secondary sidebar, primary sidebar, editor area). The Spark icon in the Editor Toolbar, Activity Bar, and Status Bar provide access points. Multiple conversations can run in parallel via "Open in New Tab" or "Open in New Window".

When Claude proposes a file edit, the extension shows a side-by-side diff and prompts for approval. The user can accept, reject, or modify the proposed change directly in the diff view before accepting — Claude is informed of any modifications. The extension also supports checkpoints: hover over any message to reveal the rewind button, then choose fork-from-here, rewind-code-to-here, or fork-and-rewind.

Context is provided through @-mentions: type `@` followed by a filename for fuzzy file matching, or use `Option+K` / `Alt+K` to insert a reference to the current selection. `@terminal:name` references terminal output. `@browser` with the Chrome extension lets Claude interact with the browser.

Permission modes in VS Code match CLI modes and are selected from the mode indicator in the prompt box. The default can be set via `claudeCode.initialPermissionMode` in VS Code settings. Extended thinking (longer reasoning) is toggleable via the `/` command menu.

VS Code settings specific to the extension: `useTerminal` (CLI mode vs graphical panel), `initialPermissionMode`, `autosave`, `useCtrlEnterToSend`, `enableNewConversationShortcut`, `hideOnboarding`. Claude Code settings in `~/.claude/settings.json` are shared with the CLI.

The extension includes a built-in MCP server (named `ide`, hidden from `/mcp`) that the CLI connects to for diff viewing, reading editor selections for @-mentions, and Jupyter notebook execution. The `mcp__ide__getDiagnostics` tool returns language-server errors visible in the Problems panel; `mcp__ide__executeCode` runs Python in the active Jupyter kernel with a mandatory Quick Pick confirmation.

For third-party providers (Bedrock, Vertex, Foundry): disable the login prompt in settings and configure the provider in `~/.claude/settings.json`.

## Key points

- Requires VS Code 1.98.0+; installs in forks (Windsurf, Kiro) and Open VSX; multiple conversations in parallel
- Inline diff review with side-by-side comparison; user can modify proposed changes before accepting
- @-mentions for files/folders (fuzzy match), `@terminal:name` for terminal output, `@browser` for Chrome integration
- Permission modes match CLI modes; `claudeCode.initialPermissionMode` sets the default
- Built-in `ide` MCP server provides getDiagnostics and executeCode tools to the CLI; transparent to users
- `~/.claude/settings.json` is shared between extension and CLI — configure permissions, hooks, and MCP servers there

## Connections

- [[wiki/pages/claude-code]] — the CLI that this extends and shares configuration with
- [[wiki/pages/claude-desktop]] — Desktop is an alternative graphical interface
- [[wiki/pages/permission-modes]] — modes available in VS Code match CLI modes
- [[wiki/pages/mcp-model-context-protocol]] — the built-in ide MCP server and manual MCP configuration
