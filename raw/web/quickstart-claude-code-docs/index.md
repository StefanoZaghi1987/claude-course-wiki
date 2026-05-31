---
source_url: https://code.claude.com/docs/en/quickstart
title: Quickstart - Claude Code Docs
published: 2026-05-24
fetched: 2026-05-31
---

# Quickstart - Claude Code Docs

---
title: Quickstart - Claude Code Docs
url: https://code.claude.com/docs/en/quickstart
hostname: claude.com
description: Welcome to Claude Code!
sitename: Claude Code Docs
date: 2026-05-24
---
This quickstart guide will have you using AI-powered coding assistance in a few minutes. By the end, you’ll understand how to use Claude Code for common development tasks.## Documentation Index

Fetch the complete documentation index at:

[https://code.claude.com/docs/llms.txt]Use this file to discover all available pages before exploring further.


## Before you begin

Make sure you have:- A terminal or command prompt open
- If you’ve never used the terminal before, check out the
[terminal guide](https://code.claude.com/docs/en/terminal-guide)

- If you’ve never used the terminal before, check out the
- A code project to work with
- A
[Claude subscription](https://claude.com/pricing?utm_source=claude_code&utm_medium=docs&utm_content=quickstart_prereq)(Pro, Max, Team, or Enterprise),[Claude Console](https://console.anthropic.com/)account, or access through a[supported cloud provider](https://code.claude.com/docs/en/third-party-integrations)

This guide covers the terminal CLI. Claude Code is also available on the

[web](https://claude.ai/code), as a[desktop app](https://code.claude.com/docs/en/desktop), in[VS Code](https://code.claude.com/docs/en/vs-code)and[JetBrains IDEs](https://code.claude.com/docs/en/jetbrains), in[Slack](https://code.claude.com/docs/en/slack), and in CI/CD with[GitHub Actions](https://code.claude.com/docs/en/github-actions)and[GitLab](https://code.claude.com/docs/en/gitlab-ci-cd). See[all interfaces](https://code.claude.com/docs/en/overview#use-claude-code-everywhere).## Step 1: Install Claude Code

To install Claude Code, use one of the following methods:- Native Install (Recommended)
- Homebrew
- WinGet

**macOS, Linux, WSL:**

**Windows PowerShell:**

**Windows CMD:**

`The token '&&' is not a valid statement separator`

, you’re in PowerShell, not CMD. If you see `'irm' is not recognized as an internal or external command`

, you’re in CMD, not PowerShell. Your prompt shows `PS C:\`

when you’re in PowerShell and `C:\`

without the `PS`

when you’re in CMD.[Git for Windows](https://git-scm.com/downloads/win)is recommended on native Windows so Claude Code can use the Bash tool. If Git for Windows is not installed, Claude Code uses PowerShell as the shell tool instead. WSL setups do not need Git for Windows.

Native installations automatically update in the background to keep you on the latest version.

[apt, dnf, or apk](https://code.claude.com/docs/en/setup#install-with-linux-package-managers)on Debian, Fedora, RHEL, and Alpine.

## Step 2: Log in to your account

Claude Code requires an account to use. Start an interactive session with the`claude`

command and you’ll be prompted to log in on first use:
`/login`

inside the running session:
[Claude Pro, Max, Team, or Enterprise](https://claude.com/pricing?utm_source=claude_code&utm_medium=docs&utm_content=quickstart_login)(recommended)[Claude Console](https://console.anthropic.com/)(API access with pre-paid credits). On first login, a “Claude Code” workspace is automatically created in the Console for centralized cost tracking.[Amazon Bedrock, Google Vertex AI, or Microsoft Foundry](https://code.claude.com/docs/en/third-party-integrations)(enterprise cloud providers)

## Step 3: Start your first session

Open your terminal in any project directory and start Claude Code:`/help`

for available commands or `/resume`

to continue a previous conversation.
## Step 4: Ask your first question

Let’s start with understanding your codebase. Try one of these commands:Claude Code reads your project files as needed. You don’t have to manually add context.

## Step 5: Make your first code change

Now let’s make Claude Code do some actual coding. Try a simple task:- Find the appropriate file
- Show you the proposed changes
- Ask for your approval
- Make the edit

Claude Code always asks for permission before modifying files. You can approve individual changes or enable “Accept all” mode for a session.

## Step 6: Use Git with Claude Code

Claude Code makes Git operations conversational:## Step 7: Fix a bug or add a feature

Claude is proficient at debugging and feature implementation. Describe what you want in natural language:- Locate the relevant code
- Understand the context
- Implement a solution
- Run tests if available

## Step 8: Test out other common workflows

There are a number of ways to work with Claude:**Refactor code**

**Write tests**

**Update documentation**

**Code review**

## Essential commands

Here are the most important commands for daily use:| Command | What it does | Example |
|---|---|---|
`claude` | Start interactive mode | `claude` |
`claude "task"` | Run a one-time task | `claude "fix the build error"` |
`claude -p "query"` | Run one-off query, then exit | `claude -p "explain this function"` |
`claude -c` | Continue most recent conversation in current directory | `claude -c` |
`claude -r` | Resume a previous conversation | `claude -r` |
`/clear` | Clear conversation history | `/clear` |
`/help` | Show available commands | `/help` |
`exit` or Ctrl+D | Exit Claude Code | `exit` |

[CLI reference](https://code.claude.com/docs/en/cli-reference)for a complete list of commands.

## Pro tips for beginners

For more, see[best practices](https://code.claude.com/docs/en/best-practices)and

[common workflows](https://code.claude.com/docs/en/common-workflows).

Be specific with your requests


Be specific with your requests

Instead of: “fix the bug”Try: “fix the login bug where users see a blank screen after entering wrong credentials”

Use step-by-step instructions


Use step-by-step instructions

Break complex tasks into steps:

Let Claude explore first


Let Claude explore first

Before making changes, let Claude understand your code:

Save time with shortcuts


Save time with shortcuts

- Type
`/`

to see all commands and skills - Use Tab for command completion
- Press ↑ for command history
- Press
`Shift+Tab`

to cycle permission modes

## What’s next?

Now that you’ve learned the basics, explore more advanced features:## How Claude Code works

Understand the agentic loop, built-in tools, and how Claude Code interacts with your project

## Best practices

Get better results with effective prompting and project setup

## Common workflows

Step-by-step guides for common tasks

## Extend Claude Code

Customize with CLAUDE.md, skills, hooks, MCP, and more

## Getting help

**In Claude Code**: Type`/help`

or ask “how do I…”**Documentation**: You’re here! Browse other guides**Community**: Join our[Discord](https://www.anthropic.com/discord)for tips and support
