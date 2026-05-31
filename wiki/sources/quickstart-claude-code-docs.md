---
type: source
created: 2026-05-31
updated: 2026-05-31
tags: [claude-code, official-docs]
source_url: https://code.claude.com/docs/en/quickstart
source_path: raw/web/quickstart-claude-code-docs/
---

Step-by-step first-run guide for Claude Code in the terminal CLI — installation, authentication, and essential commands (May 2026).

## Summary

Claude Code is installed via native script on macOS/Linux/WSL (`curl -fsSL https://claude.ai/install.sh | bash`) or Windows PowerShell (`irm https://claude.ai/install.ps1 | iex`). WinGet and Homebrew are alternatives. Native installs auto-update in the background; Linux package managers (apt, dnf, apk) are also supported. On Windows, Git for Windows is recommended so Claude Code can use the Bash tool; without it, PowerShell is used instead.

Authentication is required on first run. Three account types work: a Claude subscription (Pro, Max, Team, or Enterprise) accessed through claude.ai, an Anthropic Console API account with pre-paid credits, or a supported third-party cloud provider (Amazon Bedrock, Google Vertex AI, Microsoft Foundry). Running `claude` in a project directory launches an interactive session; `/login` inside the session lets you switch account.

The core CLI forms are: `claude` (interactive session), `claude "task"` (one-time task), `claude -p "query"` (non-interactive query then exit), `claude -c` (continue most recent session in current directory), `claude -r` (resume a previous session via picker). Essential in-session shortcuts: `/help` for commands, `/clear` to reset context, `Shift+Tab` to cycle permission modes, Tab for command completion, ↑ for prompt history.

Effective beginner habits from the guide: be specific about files and scenarios rather than vague ("fix the login bug where users see a blank screen after entering wrong credentials", not "fix the bug"); break complex tasks into explicit steps; let Claude explore before implementing ("Read the codebase and list the main modules before making changes").

## Key points

- Installation: native script (recommended, auto-updates), Homebrew, WinGet, or Linux package managers
- Authentication: Claude subscription via claude.ai, Console API, or Bedrock/Vertex/Foundry
- Five CLI invocation forms: interactive, one-time task, non-interactive query, continue recent, resume picker
- `Shift+Tab` cycles permission modes (Standard → Accept Edits → Plan) without leaving the session
- Best results from specificity: reference exact files, state constraints, point to example patterns

## Connections

- [[wiki/pages/claude-code]] — full feature set of which this is the entry point
- [[wiki/pages/permission-modes]] — the modes cycled with Shift+Tab
