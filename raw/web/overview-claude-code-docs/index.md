---
source_url: https://code.claude.com/docs/en/overview
title: Overview - Claude Code Docs
published: 2026-05-18
fetched: 2026-05-31
---

# Overview - Claude Code Docs

---
title: Overview - Claude Code Docs
url: https://code.claude.com/docs/en/overview
hostname: claude.com
description: Claude Code is an agentic coding tool that reads your codebase, edits files, runs commands, and integrates with your development tools. Available in your terminal, IDE, desktop app, and browser.
sitename: Claude Code Docs
date: 2026-05-18
---
Claude Code is an AI-powered coding assistant that helps you build features, fix bugs, and automate development tasks. It understands your entire codebase and can work across multiple files and tools to get things done.## Documentation Index

Fetch the complete documentation index at:

[https://code.claude.com/docs/llms.txt]Use this file to discover all available pages before exploring further.


## Get started

Choose your environment to get started. Most surfaces require a[Claude subscription](https://claude.com/pricing?utm_source=claude_code&utm_medium=docs&utm_content=overview_pricing)or

[Anthropic Console](https://console.anthropic.com/)account. The Terminal CLI and VS Code also support

[third-party providers](https://code.claude.com/docs/en/third-party-integrations).

- Terminal
- VS Code
- Desktop app
- Web
- JetBrains

The full-featured CLI for working with Claude Code directly in your terminal. Edit files, run commands, and manage your entire project from the command line.To install Claude Code, use one of the following methods:If you see You can also install with You’ll be prompted to log in on first use. That’s it!

- Native Install (Recommended)
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

[apt, dnf, or apk](https://code.claude.com/docs/en/setup#install-with-linux-package-managers)on Debian, Fedora, RHEL, and Alpine.Then start Claude Code in any project:[Continue with the Quickstart →](https://code.claude.com/docs/en/quickstart)## What you can do

Here are some of the ways you can use Claude Code:Automate the work you keep putting off


Automate the work you keep putting off

Claude Code handles the tedious tasks that eat up your day: writing tests for untested code, fixing lint errors across a project, resolving merge conflicts, updating dependencies, and writing release notes.

Build features and fix bugs


Build features and fix bugs

Describe what you want in plain language. Claude Code plans the approach, writes the code across multiple files, and verifies it works.For bugs, paste an error message or describe the symptom. Claude Code traces the issue through your codebase, identifies the root cause, and implements a fix. See

[common workflows](https://code.claude.com/docs/en/common-workflows)for more examples.Create commits and pull requests


Create commits and pull requests

Claude Code works directly with git. It stages changes, writes commit messages, creates branches, and opens pull requests.In CI, you can automate code review and issue triage with

[GitHub Actions](https://code.claude.com/docs/en/github-actions)or[GitLab CI/CD](https://code.claude.com/docs/en/gitlab-ci-cd).Connect your tools with MCP


Connect your tools with MCP

The

[Model Context Protocol (MCP)](https://code.claude.com/docs/en/mcp)is an open standard for connecting AI tools to external data sources. With MCP, Claude Code can read your design docs in Google Drive, update tickets in Jira, pull data from Slack, or use your own custom tooling.Customize with instructions, skills, and hooks


Customize with instructions, skills, and hooks

[is a markdown file you add to your project root that Claude Code reads at the start of every session. Use it to set coding standards, architecture decisions, preferred libraries, and review checklists. Claude also builds](https://code.claude.com/docs/en/memory)

`CLAUDE.md`

[auto memory](https://code.claude.com/docs/en/memory#auto-memory)as it works, saving learnings like build commands and debugging insights across sessions without you writing anything.Create

[skills](https://code.claude.com/docs/en/skills)to package repeatable workflows your team can share, like

`/review-pr`

or `/deploy-staging`

.[Hooks](https://code.claude.com/docs/en/hooks)let you run shell commands before or after Claude Code actions, like auto-formatting after every file edit or running lint before a commit.

Run agent teams and build custom agents


Run agent teams and build custom agents

Spawn

[multiple Claude Code agents](https://code.claude.com/docs/en/sub-agents)that work on different parts of a task simultaneously. A lead agent coordinates the work, assigns subtasks, and merges results.To run several full sessions in parallel and watch them from one screen, use[background agents](https://code.claude.com/docs/en/agent-view). For fully custom workflows, the[Agent SDK](https://code.claude.com/docs/en/agent-sdk/overview)lets you build your own agents powered by Claude Code’s tools and capabilities, with full control over orchestration, tool access, and permissions.Pipe, script, and automate with the CLI


Pipe, script, and automate with the CLI

Claude Code is composable and follows the Unix philosophy. Pipe logs into it, run it in CI, or chain it with other tools:See the

[CLI reference](https://code.claude.com/docs/en/cli-reference)for the full set of commands and flags.Schedule recurring tasks


Schedule recurring tasks

Run Claude on a schedule to automate work that repeats: morning PR reviews, overnight CI failure analysis, weekly dependency audits, or syncing docs after PRs merge.

[Routines](https://code.claude.com/docs/en/routines)run on Anthropic-managed infrastructure, so they keep running even when your computer is off. They can also trigger on API calls or GitHub events. Create them from the web, the Desktop app, or by running`/schedule`

in the CLI.[Desktop scheduled tasks](https://code.claude.com/docs/en/desktop-scheduled-tasks)run on your machine, with direct access to your local files and toolsrepeats a prompt within a CLI session for quick polling`/loop`


Work from anywhere


Work from anywhere

Sessions aren’t tied to a single surface. Move work between environments as your context changes:

- Step away from your desk and keep working from your phone or any browser with
[Remote Control](https://code.claude.com/docs/en/remote-control) - Message
[Dispatch](https://code.claude.com/docs/en/desktop#sessions-from-dispatch)a task from your phone and open the Desktop session it creates - Kick off a long-running task on the
[web](https://code.claude.com/docs/en/claude-code-on-the-web)or[iOS app](https://apps.apple.com/app/claude-by-anthropic/id6473753684), then pull it into your terminal with`claude --teleport`

- Hand off a terminal session to the
[Desktop app](https://code.claude.com/docs/en/desktop)with`/desktop`

for visual diff review - Route tasks from team chat: mention
`@Claude`

in[Slack](https://code.claude.com/docs/en/slack)with a bug report and get a pull request back

## Use Claude Code everywhere

Each surface connects to the same underlying Claude Code engine, so your CLAUDE.md files, settings, and MCP servers work across all of them. Beyond the[Terminal](https://code.claude.com/docs/en/quickstart),

[VS Code](https://code.claude.com/docs/en/vs-code),

[JetBrains](https://code.claude.com/docs/en/jetbrains),

[Desktop](https://code.claude.com/docs/en/desktop), and

[Web](https://code.claude.com/docs/en/claude-code-on-the-web)environments above, Claude Code integrates with CI/CD, chat, and browser workflows:

| I want to… | Best option |
|---|---|
| Continue a local session from my phone or another device |
|

[Channels](https://code.claude.com/docs/en/channels)[Web](https://code.claude.com/docs/en/claude-code-on-the-web)or[Claude iOS app](https://apps.apple.com/app/claude-by-anthropic/id6473753684)[Routines](https://code.claude.com/docs/en/routines)or[Desktop scheduled tasks](https://code.claude.com/docs/en/desktop-scheduled-tasks)[GitHub Actions](https://code.claude.com/docs/en/github-actions)or[GitLab CI/CD](https://code.claude.com/docs/en/gitlab-ci-cd)[GitHub Code Review](https://code.claude.com/docs/en/code-review)[Slack](https://code.claude.com/docs/en/slack)[Chrome](https://code.claude.com/docs/en/chrome)[Agent SDK](https://code.claude.com/docs/en/agent-sdk/overview)## Next steps

Once you’ve installed Claude Code, these guides help you go deeper.[Quickstart](https://code.claude.com/docs/en/quickstart): walk through your first real task, from exploring a codebase to committing a fix[Store instructions and memories](https://code.claude.com/docs/en/memory): give Claude persistent instructions with CLAUDE.md files and auto memory[Common workflows](https://code.claude.com/docs/en/common-workflows)and[best practices](https://code.claude.com/docs/en/best-practices): patterns for getting the most out of Claude Code[Settings](https://code.claude.com/docs/en/settings): customize Claude Code for your workflow[Troubleshooting](https://code.claude.com/docs/en/troubleshooting): solutions for common issues[code.claude.com](https://code.claude.com/): demos, pricing, and product details
