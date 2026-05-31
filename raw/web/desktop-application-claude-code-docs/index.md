---
source_url: https://code.claude.com/docs/en/desktop
title: Desktop application - Claude Code Docs
published: 2026-05-29
fetched: 2026-05-31
---

# Desktop application - Claude Code Docs

---
title: Desktop application - Claude Code Docs
url: https://code.claude.com/docs/en/desktop
hostname: claude.com
description: Get more out of Claude Code Desktop: parallel sessions with Git isolation, drag-and-drop pane layout, integrated terminal and file editor, side chats, computer use, Dispatch sessions from your phone, visual diff review, app previews, PR monitoring, connectors, and enterprise configuration.
sitename: Claude Code Docs
date: 2026-05-29
---
The Claude Desktop app has three tabs:## Documentation Index

Fetch the complete documentation index at:

[https://code.claude.com/docs/llms.txt]Use this file to discover all available pages before exploring further.


**Chat**for conversations,

**Cowork**for

[Dispatch and longer agentic work](https://claude.com/product/cowork), and

**Code**for software development. This page is the reference for the Code tab.

## Download for macOS

Universal build for Intel and Apple Silicon

## Download for Windows

For x64 processors

[ARM64 installer](https://claude.ai/api/desktop/win32/arm64/setup/latest/redirect?utm_source=claude_code&utm_medium=docs). The desktop app is not available on Linux; use the

[CLI](https://code.claude.com/docs/en/quickstart)instead. After installing, launch Claude, sign in, and click the

**Code**tab. The first time you open it on Windows, you need

[Git for Windows](https://git-scm.com/downloads/win)installed; restart the app after installing it. For a walkthrough of your first session, see the

[Get started guide](https://code.claude.com/docs/en/desktop-quickstart). In the Code tab, each conversation is a

**session**: it has its own chat history, project folder, and code changes, independent of any other session. The sidebar lists your sessions and lets you run several in parallel. Within a session you can:

[Review and comment on diffs](https://code.claude.com#review-changes-with-diff-view), then[watch the resulting PR through CI](https://code.claude.com#monitor-pull-request-status)[Preview your running app](https://code.claude.com#preview-your-app)in an embedded browser while Claude verifies its own changes[Arrange panes](https://code.claude.com#arrange-your-workspace)for the chat, diff, preview, terminal, and file editor side by side- Ask a
[side question](https://code.claude.com#ask-a-side-question-without-derailing-the-session)that uses the session’s context without derailing it [Connect external tools](https://code.claude.com#connect-external-tools)like GitHub, Slack, and Linear- Let Claude
[open apps and control your screen](https://code.claude.com#let-claude-use-your-computer) - Run on your machine, in the
[cloud](https://code.claude.com#run-long-running-tasks-remotely), or over[SSH](https://code.claude.com#ssh-sessions)

[scheduled recurring work](https://code.claude.com/docs/en/desktop-scheduled-tasks),

[keyboard shortcuts](https://code.claude.com#keyboard-shortcuts), or

[sending tasks from your phone](https://code.claude.com#sessions-from-dispatch), see the linked pages and sections. If you already use the terminal-based CLI, see the

[CLI comparison](https://code.claude.com#coming-from-the-cli)for what carries over.

## Start a session

Before you send your first message, configure four things in the prompt area:**Environment**: choose where Claude runs. Select**Local**for your machine,**Remote**for Anthropic-hosted cloud sessions, or anfor a remote machine you manage. See**SSH connection**[environment configuration](https://code.claude.com#environment-configuration).**Project folder**: select the folder or repository Claude works in. For remote sessions, you can add[multiple repositories](https://code.claude.com#run-long-running-tasks-remotely).**Model**: pick a[model](https://code.claude.com/docs/en/model-config#available-models)from the dropdown next to the send button. You can change this during the session.**Permission mode**: choose how much autonomy Claude has from the[mode selector](https://code.claude.com#choose-a-permission-mode). You can change this during the session.

**Enter**to start. Each session tracks its own context and changes independently.

## Work with code

Give Claude the right context, control how much it does on its own, and review what it changed.### Use the prompt box

Type what you want Claude to do and press**Enter**to send. Claude reads your project files, makes changes, and runs commands based on your

[permission mode](https://code.claude.com#choose-a-permission-mode). You can redirect Claude at any point: click the stop button to interrupt immediately, or type a correction and press

**Enter**to send it without stopping the running action. Claude reads the correction as soon as the current action completes and adjusts before its next step. The

**+**button next to the prompt box gives you access to file attachments,

[skills](https://code.claude.com#use-skills),

[connectors](https://code.claude.com#connect-external-tools), and

[plugins](https://code.claude.com#install-plugins).

### Add files and context to prompts

The prompt box supports two ways to bring in external context:**@mention files**: type`@`

followed by a filename to add a file to the conversation context. Claude can then read and reference that file. @mention is not available in remote sessions.**Attach files**: attach images, PDFs, and other files to your prompt using the attachment button, or drag and drop files directly into the prompt. This is useful for sharing screenshots of bugs, design mockups, or reference documents.

### Choose a permission mode

Permission modes control how much autonomy Claude has during a session: whether it asks before editing files, running commands, or both. You can switch modes at any time using the mode selector next to the send button. Start with Ask permissions to see exactly what Claude does, then move to Auto accept edits or Plan mode as you get comfortable.| Mode | Settings key | Behavior |
|---|---|---|
Ask permissions | `default` | Claude asks before editing files or running commands. You see a diff and can accept or reject each change. Recommended for new users. |
Auto accept edits | `acceptEdits` | Claude auto-accepts file edits and common filesystem commands like `mkdir` , `touch` , and `mv` , but still asks before running other terminal commands. Use this when you trust file changes and want faster iteration. |
Plan mode | `plan` | Claude reads files and runs commands to explore, then proposes a plan without editing your source code. Good for complex tasks where you want to review the approach first. |
Auto | `auto` | Claude executes all actions with background safety checks that verify alignment with your request. Reduces permission prompts while maintaining oversight. Enable in your Settings → Claude Code. See
|

**Bypass permissions**`bypassPermissions`

`--dangerously-skip-permissions`

in the CLI. Enable in your Settings → Claude Code under “Allow bypass permissions mode”. Only use this in sandboxed containers or VMs. Enterprise admins can disable this option.`dontAsk`

permission mode is available only in the [CLI](https://code.claude.com/docs/en/permission-modes#allow-only-pre-approved-tools-with-dontask-mode). Auto mode is a research preview available to all users on the Anthropic API. It is not available on third-party providers. It requires Claude Opus 4.6 or later, or Sonnet 4.6. Remote sessions support Auto accept edits and Plan mode. Ask permissions is not available because remote sessions auto-accept file edits by default, and Bypass permissions is not available because the remote environment is already sandboxed. Enterprise admins can restrict which permission modes are available. See

[enterprise configuration](https://code.claude.com#enterprise-configuration)for details.

### Preview your app

Claude can start a dev server and open an embedded browser to verify its changes. This works for frontend web apps as well as backend servers: Claude can test API endpoints, view server logs, and iterate on issues it finds. In most cases, Claude starts the server automatically after editing project files. You can also ask Claude to preview at any time. By default, Claude[auto-verifies](https://code.claude.com#auto-verify-changes)changes after every edit. The preview pane can also open static HTML files, PDFs, images, and videos from your project. Click an HTML, PDF, image, or video path in the chat to open it in preview. From the preview pane, you can:

- Interact with your running app directly in the embedded browser
- Watch Claude verify its own changes automatically: it takes screenshots, inspects the DOM, clicks elements, fills forms, and fixes issues it finds
- Start or stop servers from the
**Preview**dropdown in the session toolbar - Persist cookies and local storage across server restarts by selecting
**Persist sessions**in the dropdown, so you don’t have to re-login during development - Edit the server configuration or stop all servers at once

`.claude/launch.json`

to match your setup. See [Configure preview servers](https://code.claude.com#configure-preview-servers)for the full reference. To clear saved session data, toggle

**Persist preview sessions**off in Settings → Claude Code. To disable preview entirely, toggle off

**Preview**in Settings → Claude Code.

### Review changes with diff view

After Claude makes changes to your code, the diff view lets you review modifications file by file before creating a pull request. When Claude changes files, a diff stats indicator appears showing the number of lines added and removed, such as`+12 -1`

. Click this indicator to open the diff viewer, which displays a file list on the left and the changes for each file on the right.
To comment on specific lines, click any line in the diff to open a comment box. Type your feedback and press **Enter**to add the comment. After adding comments to multiple lines, submit all comments at once:

**macOS**: press**Cmd+Enter****Windows**: press**Ctrl+Enter**

### Review your code

In the diff view, click**Review code**in the top-right toolbar to ask Claude to evaluate the changes before you commit. Claude examines the current diffs and leaves comments directly in the diff view. You can respond to any comment or ask Claude to revise. The review focuses on high-signal issues: compile errors, definite logic errors, security vulnerabilities, and obvious bugs. It does not flag style, formatting, pre-existing issues, or anything a linter would catch.

### Monitor pull request status

After you open a pull request, a CI status bar appears in the session. Claude Code uses the GitHub CLI to poll check results and surface failures.**Auto-fix**: when enabled, Claude automatically attempts to fix failing CI checks by reading the failure output and iterating.**Auto-merge**: when enabled, Claude merges the PR once all checks pass. The merge method is squash. Auto-merge must be[enabled in your GitHub repository settings](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/configuring-pull-request-merges/managing-auto-merge-for-pull-requests-in-your-repository)for this to work.

**Auto-fix**and

**Auto-merge**toggles in the CI status bar to enable either option. Claude Code also sends a desktop notification when CI finishes. To archive the session automatically once the PR merges or closes, turn on

[auto-archive](https://code.claude.com#work-in-parallel-with-sessions)in Settings → Claude Code.

PR monitoring requires the

[GitHub CLI (](https://cli.github.com/)to be installed and authenticated on your machine. If`gh`

)`gh`

is not installed, Desktop prompts you to install it the first time you try to create a PR.## Arrange your workspace

The Code tab is built around panes you can arrange in any layout: chat, diff, preview, terminal, file, plan, tasks, and subagent. Drag a pane by its header to reposition it, or drag a pane edge to resize it. Press**Cmd+\**on macOS or

**Ctrl+\**on Windows to close the focused pane. Open additional panes from the

**Views**menu in the session toolbar.

The pane layout, terminal, file editor, and view modes in this section require Claude Desktop v1.2581.0 or later. Open

**Claude → Check for Updates**on macOS or**Help → Check for Updates**on Windows to update.### Run commands in the terminal

The integrated terminal lets you run commands alongside your session without switching to another app. Open it from the**Views**menu or press

**Ctrl+`**on macOS or Windows. The terminal opens in your session’s working directory and shares the same environment as Claude, so commands like

`npm test`

or `git status`

see the same files Claude is editing. To open a second terminal tab, click **+**in the terminal pane header or right-click a folder in the chat to choose

**Open in terminal**. The terminal is available in local sessions only.

### Open and edit files

Click a file path in the chat or diff viewer to open it in the file pane. HTML, PDF, image, and video paths open in the[preview pane](https://code.claude.com#preview-your-app)instead. Make spot edits and click

**Save**to write them back. If the file changed on disk since you opened it, the pane warns you and lets you override or discard. Click

**Discard**to revert your edits, or click the path in the pane header to copy the absolute path. The file pane is available in local and SSH sessions. For remote sessions, ask Claude to make the change.

### Open files in other apps

Right-click any file path in the chat, diff viewer, or file pane to open a context menu:**Attach as context**: add the file to your next prompt**Open in**: open the file in an installed editor such as VS Code, Cursor, or Zed**Show in Finder**on macOS,**Show in Explorer**on Windows: open the containing folder**Copy path**: copy the absolute path to your clipboard

### Switch view modes

View modes control how much detail appears in the chat transcript. Switch modes from the**Transcript view**dropdown next to the send button, or press

**Ctrl+O**on macOS or Windows to cycle through them.

| Mode | What it shows |
|---|---|
Normal | Tool calls collapsed into summaries, with full text responses |
Verbose | Every tool call, file read, and intermediate step Claude takes |
Summary | Only Claude’s final responses and the changes it made |

### Keyboard shortcuts

Press**Cmd+/**on macOS or

**Ctrl+/**on Windows to see all shortcuts available in the Code tab. On Windows, use

**Ctrl**in place of

**Cmd**for the shortcuts below. Session cycling, the terminal toggle, and the view-mode toggle use

**Ctrl**on every platform.

| Shortcut | Action |
|---|---|
`Cmd` `/` | Show keyboard shortcuts |
`Cmd` `N` | New session |
`Cmd` `W` | Close session |
`Ctrl` `Tab` / `Ctrl` `Shift` `Tab` | Next or previous session |
`Cmd` `Shift` `]` / `Cmd` `Shift` `[` | Next or previous session |
`Esc` | Stop Claude’s response |
`Cmd` `Shift` `D` | Toggle diff pane |
`Cmd` `Shift` `P` | Toggle preview pane |
`Cmd` `Shift` `S` | Select an element in preview |
`Ctrl` ``` | Toggle terminal pane |
`Cmd` `\` | Close focused pane |
`Cmd` `;` | Open side chat |
`Ctrl` `O` | Cycle view modes |
`Cmd` `Shift` `M` | Open permission mode menu |
`Cmd` `Shift` `I` | Open model menu |
`Cmd` `Shift` `E` | Open effort menu |
`1` –`9` | Select item in an open menu |

[interactive mode shortcuts](https://code.claude.com/docs/en/interactive-mode#keyboard-shortcuts), such as

`Shift+Tab`

to cycle modes, do not apply in Desktop.
### Check usage

Click the usage ring next to the model picker to see your current context window usage and your plan usage for the period. Context usage is per session; plan usage is shared across all your Claude Code surfaces.## Let Claude use your computer

Computer use lets Claude open your apps, control your screen, and work directly on your machine the way you would. Ask Claude to test a native app in a mobile simulator, interact with a desktop tool that has no CLI, or automate something that only works through a GUI.Computer use is a research preview on macOS and Windows that requires a Pro or Max plan. It is not available on Team or Enterprise plans. The Claude Desktop app must be running.

[Enable it in Settings](https://code.claude.com#enable-computer-use)before Claude can control your screen. On macOS, you also need to grant Accessibility and Screen Recording permissions.

### When computer use applies

Claude has several ways to interact with an app or service, and computer use is the broadest and slowest. It tries the most precise tool first:- If you have a
[connector](https://code.claude.com#connect-external-tools)for a service, Claude uses the connector. - If the task is a shell command, Claude uses Bash.
- If the task is browser work and you have
[Claude in Chrome](https://code.claude.com/docs/en/chrome)set up, Claude uses that. - If none of those apply, Claude uses computer use.

[per-app access tiers](https://code.claude.com#app-permissions)reinforce this: browsers are capped at view-only, and terminals and IDEs at click-only, steering Claude toward the dedicated tool even when computer use is active. Screen control is reserved for things nothing else can reach, like native apps, hardware control panels, mobile simulators, or proprietary tools without an API.

### Enable computer use

Computer use is off by default. If you ask Claude to do something that needs it while it’s off, Claude tells you it could do the task if you enable computer use in Settings.Update the desktop app

Make sure you have the latest version of Claude Desktop. Download or update at

[claude.com/download](https://claude.com/download), then restart the app.Turn on the toggle

In the desktop app, go to

**Settings > General**(under**Desktop app**). Find the**Computer use**toggle and turn it on. On Windows, the toggle takes effect immediately and setup is complete. On macOS, continue to the next step.If you don’t see the toggle, confirm you’re on macOS or Windows with a Pro or Max plan, then update and restart the app.Grant macOS permissions

On macOS, grant two system permissions before the toggle takes effect:

**Accessibility**: lets Claude click, type, and scroll**Screen Recording**: lets Claude see what’s on your screen

### App permissions

The first time Claude needs to use an app, a prompt appears in your session. Click**Allow for this session**or

**Deny**. Approvals last for the current session, or 30 minutes in

[Dispatch-spawned sessions](https://code.claude.com#sessions-from-dispatch). The prompt also shows what level of control Claude gets for that app. These tiers are fixed by app category and can’t be changed:

| Tier | What Claude can do | Applies to |
|---|---|---|
| View only | See the app in screenshots | Browsers, trading platforms |
| Click only | Click and scroll, but not type or use keyboard shortcuts | Terminals, IDEs |
| Full control | Click, type, drag, and use keyboard shortcuts | Everything else |

**Settings > General**(under

**Desktop app**):

**Denied apps**: add apps here to reject them without prompting. Claude may still affect a denied app indirectly through actions in an allowed app, but it can’t interact with the denied app directly.**Unhide apps when Claude finishes**: while Claude is working, your other windows are hidden so it interacts with only the approved app. When Claude finishes, hidden windows are restored unless you turn this setting off.

## Manage sessions

Each session is an independent conversation with its own context and changes. You can run multiple sessions in parallel, branch off side chats, send work to the cloud, or let Dispatch start sessions for you from your phone.### Work in parallel with sessions

Click**+ New session**in the sidebar, or press

**Cmd+N**on macOS or

**Ctrl+N**on Windows, to work on multiple tasks in parallel. Press

**Ctrl+Tab**and

**Ctrl+Shift+Tab**to cycle through sessions in the sidebar. For Git repositories, each session gets its own isolated copy of your project using

[Git worktrees](https://code.claude.com/docs/en/worktrees), so changes in one session don’t affect other sessions until you commit them. To view two sessions at once, hold

**Cmd**on macOS or

**Ctrl**on Windows and click a session in the sidebar. The session opens in a second pane alongside the one you already have open. While the split is active, clicking another sidebar session replaces whichever pane has focus. Press

**Cmd+\**on macOS or

**Ctrl+\**on Windows to close the focused pane and return to a single session. Worktrees are stored in

`<project-root>/.claude/worktrees/`

by default. You can change this to a custom directory in Settings → Claude Code under “Worktree location”. You can also set a branch prefix that gets prepended to every worktree branch name, which is useful for keeping Claude-created branches organized. To remove a worktree when you’re done, hover over the session in the sidebar and click the archive icon. To have sessions archive themselves when their pull request merges or closes, turn on **Auto-archive after PR merge or close**in Settings → Claude Code. Auto-archive only applies to local sessions that have finished running. To include gitignored files like

`.env`

in new worktrees, create a [in your project root.](https://code.claude.com/docs/en/worktrees#copy-gitignored-files-into-worktrees)

`.worktreeinclude`

fileSession isolation requires

[Git](https://git-scm.com/downloads). Most Macs include Git by default. Run`git --version`

in Terminal to check. On Windows, Git is required for the Code tab to work: [download Git for Windows](https://git-scm.com/downloads/win), install it, and restart the app. If you run into Git errors, ask Claude in the[Cowork tab](https://claude.com/product/cowork)to help troubleshoot your setup.[Check usage](https://code.claude.com#check-usage). When context fills up, Claude automatically summarizes the conversation and continues working. You can also type

`/compact`

to trigger summarization earlier and free up context space. See [the context window](https://code.claude.com/docs/en/how-claude-code-works#the-context-window)for details on how compaction works. The desktop app sends an OS notification when a Code session finishes a task and you aren’t currently viewing that session.

### Ask a side question without derailing the session

A side chat lets you ask Claude a question that uses your session’s context but doesn’t add anything back to the main conversation. Use it when you want to understand a piece of code, check an assumption, or explore an idea without steering the session off course. Press**Cmd+;**on macOS or

**Ctrl+;**on Windows to open a side chat, or type

`/btw`

in the prompt box. The side chat can read everything in the main thread up to that point. When you’re done, close the side chat and continue the main session where you left off. Side chats are available in local and SSH sessions.
### Watch background tasks

The tasks pane shows the background work running inside the current session: subagents, background shell commands, and[dynamic workflows](https://code.claude.com/docs/en/workflows). Open it from the

**Views**menu or drag it into your layout. Click any entry to see its output in the subagent pane or stop it. To see what other sessions are doing, use the

[sidebar](https://code.claude.com#work-in-parallel-with-sessions).

### Run long-running tasks remotely

For large refactors, test suites, migrations, or other long-running tasks, select**Remote**instead of

**Local**when starting a session. Remote sessions run on Anthropic’s cloud infrastructure and continue even if you close the app or shut down your computer. Check back anytime to see progress or steer Claude in a different direction. You can also monitor remote sessions from

[claude.ai/code](https://claude.ai/code)or the Claude iOS app. Remote sessions also support multiple repositories. After selecting a cloud environment, click the

**+**button next to the repo pill to add additional repositories to the session. Each repo gets its own branch selector. This is useful for tasks that span multiple codebases, such as updating a shared library and its consumers. See

[Claude Code on the web](https://code.claude.com/docs/en/claude-code-on-the-web)for more on how remote sessions work.

### Continue in another surface

The**Continue in**menu, accessible from the VS Code icon in the bottom right of the session toolbar, lets you move your session to another surface:

**Claude Code on the Web**: sends your local session to continue running remotely. Desktop pushes your branch, generates a summary of the conversation, and creates a new remote session with the full context. You can then choose to archive the local session or keep it. This requires a clean working tree, and is not available for SSH sessions.**Your IDE**: opens your project in a supported IDE at the current working directory.

### Sessions from Dispatch

[Dispatch](https://support.claude.com/en/articles/13947068)is a persistent conversation with Claude that lives in the

[Cowork](https://claude.com/product/cowork#dispatch-and-computer-use)tab. You message Dispatch a task, and it decides how to handle it. A task can end up as a Code session in two ways: you ask for one directly, such as “open a Claude Code session and fix the login bug”, or Dispatch decides the task is development work and spawns one on its own. Tasks that typically route to Code include fixing bugs, updating dependencies, running tests, or opening pull requests. Research, document editing, and spreadsheet work stay in Cowork. Either way, the Code session appears in the Code tab’s sidebar with a

**Dispatch**badge. You get a push notification on your phone when it finishes or needs your approval. If you have

[computer use](https://code.claude.com#let-claude-use-your-computer)enabled, Dispatch-spawned Code sessions can use it too. App approvals in those sessions expire after 30 minutes and re-prompt, rather than lasting the full session like regular Code sessions. For setup, pairing, and Dispatch settings, see the

[Dispatch help article](https://support.claude.com/en/articles/13947068). Dispatch requires a Pro or Max plan and is not available on Team or Enterprise plans. Dispatch is one of several ways to work with Claude when you’re away from your terminal. See

[Platforms and integrations](https://code.claude.com/docs/en/platforms#work-when-you-are-away-from-your-terminal)to compare it with Remote Control, Channels, Slack, and scheduled tasks.

## Extend Claude Code

Connect external services, add reusable workflows, customize Claude’s behavior, and configure preview servers. To manage connectors, skills, and plugins in one place, click**Customize**in the sidebar.

### Connect external tools

For local and[SSH](https://code.claude.com#ssh-sessions)sessions, click the

**+**button next to the prompt box and select

**Connectors**to add integrations like Google Calendar, Slack, GitHub, Linear, Notion, and more. You can add connectors before or during a session. The

**+**button is not available in remote sessions, but

[routines](https://code.claude.com/docs/en/routines)configure connectors at routine creation time. To manage or disconnect connectors, go to Settings → Connectors in the desktop app, or select

**Manage connectors**from the Connectors menu in the prompt box. Once connected, Claude can read your calendar, send messages, create issues, and interact with your tools directly. You can ask Claude what connectors are configured in your session. Connectors are

[MCP servers](https://code.claude.com/docs/en/mcp)with a graphical setup flow. Use them for quick integration with supported services. For integrations not listed in Connectors, add MCP servers manually via

[settings files](https://code.claude.com/docs/en/mcp#installing-mcp-servers). You can also

[create custom connectors](https://support.claude.com/en/articles/11175166-getting-started-with-custom-connectors-using-remote-mcp).

### Use skills

[Skills](https://code.claude.com/docs/en/skills)extend what Claude can do. Claude loads them automatically when relevant, or you can invoke one directly: type

`/`

in the prompt box or click the **+**button and select

**Slash commands**to browse what’s available. This includes

[built-in commands](https://code.claude.com/docs/en/commands), your

[custom skills](https://code.claude.com/docs/en/skills#create-your-first-skill), project skills from your codebase, and skills from any

[installed plugins](https://code.claude.com/docs/en/plugins). Select one and it appears highlighted in the input field. Type your task after it and send as usual.

### Install plugins

[Plugins](https://code.claude.com/docs/en/plugins)are reusable packages that add skills, agents, hooks, MCP servers, and LSP configurations to Claude Code. You can install plugins from the desktop app without using the terminal. For local and

[SSH](https://code.claude.com#ssh-sessions)sessions, click the

**+**button next to the prompt box and select

**Plugins**to see your installed plugins and their skills. To add a plugin, select

**Add plugin**from the submenu to open the plugin browser, which shows available plugins from your configured

[marketplaces](https://code.claude.com/docs/en/plugin-marketplaces)including the official Anthropic marketplace. Select

**Manage plugins**to enable, disable, or uninstall plugins. Plugins can be scoped to your user account, a specific project, or local-only. If your organization manages plugins centrally, those plugins are available in desktop sessions the same way they are in the CLI. Plugins are not available for remote sessions. For the full plugin reference including creating your own plugins, see

[plugins](https://code.claude.com/docs/en/plugins).

### Configure preview servers

Claude automatically detects your dev server setup and stores the configuration in`.claude/launch.json`

at the root of the folder you selected when starting the session. Preview uses this folder as its working directory, so if you selected a parent folder, subfolders with their own dev servers won’t be detected automatically. To work with a subfolder’s server, either start a session in that folder directly or add a configuration manually.
To customize how your server starts, for example to use `yarn dev`

instead of `npm run dev`

or to change the port, edit the file manually or click **Edit configuration**in the Preview dropdown to open it in your code editor. The file supports JSON with comments.

[examples](https://code.claude.com#examples)below.

#### Auto-verify changes

When`autoVerify`

is enabled, Claude automatically verifies code changes after editing files. It takes screenshots, checks for errors, and confirms changes work before completing its response.
Auto-verify is on by default. Disable it per-project by adding `"autoVerify": false`

to `.claude/launch.json`

, or toggle it from the **Preview**dropdown menu.

#### Configuration fields

Each entry in the`configurations`

array accepts the following fields:
| Field | Type | Description |
|---|---|---|
`name` | string | A unique identifier for this server |
`runtimeExecutable` | string | The command to run, such as `npm` , `yarn` , or `node` |
`runtimeArgs` | string[] | Arguments passed to `runtimeExecutable` , such as `["run", "dev"]` |
`port` | number | The port your server listens on. Defaults to 3000 |
`cwd` | string | Working directory relative to your project root. Defaults to the project root. Use `${workspaceFolder}` to reference the project root explicitly |
`env` | object | Additional environment variables as key-value pairs, such as `{ "NODE_ENV": "development" }` . Don’t put secrets here since this file is committed to your repo. To pass secrets to your dev server, set them in the
|
`autoPort` | boolean | How to handle port conflicts. See below |
`program` | string | A script to run with `node` . See
`program` vs `runtimeExecutable` |
`args` | string[] | Arguments passed to `program` . Only used when `program` is set |

##### When to use `program`

vs `runtimeExecutable`


Use `runtimeExecutable`

with `runtimeArgs`

to start a dev server through a package manager. For example, `"runtimeExecutable": "npm"`

with `"runtimeArgs": ["run", "dev"]`

runs `npm run dev`

.
Use `program`

when you have a standalone script you want to run with `node`

directly. For example, `"program": "server.js"`

runs `node server.js`

. Pass additional flags with `args`

.
#### Port conflicts

The`autoPort`

field controls what happens when your preferred port is already in use:
: Claude finds and uses a free port automatically. Suitable for most dev servers.`true`

: Claude fails with an error. Use this when your server must use a specific port, such as for OAuth callbacks or CORS allowlists.`false`

**Not set (default)**: Claude asks whether the server needs that exact port, then saves your answer.

`PORT`

environment variable.
#### Examples

These configurations show common setups for different project types:- Next.js
- Multiple servers
- Node.js script

This configuration runs a Next.js app using Yarn on port 3000:

## Environment configuration

The environment you pick when[starting a session](https://code.claude.com#start-a-session)determines where Claude executes and how you connect:

**Local**: runs on your machine with direct access to your files**Remote**: runs on Anthropic’s cloud infrastructure. Sessions continue even if you close the app.**SSH**: runs on a remote machine you connect to over SSH, such as your own servers, cloud VMs, or dev containers

### Local sessions

The desktop app does not always inherit your full shell environment. On macOS, when you launch the app from the Dock or Finder, it reads your shell profile, such as`~/.zshrc`

or `~/.bashrc`

, to extract `PATH`

and a fixed set of Claude Code variables, but other variables you export there are not picked up. On Windows, the app inherits user and system environment variables but does not read PowerShell profiles.
To set environment variables for local sessions and dev servers on any platform, open the environment dropdown in the prompt box, hover over **Local**, and click the gear icon to open the local environment editor. Variables you save here are stored encrypted on your machine and apply to every local session and preview server you start. You can also add variables to the

`env`

key in your `~/.claude/settings.json`

file, though these reach Claude sessions only and not dev servers. See [environment variables](https://code.claude.com/docs/en/env-vars)for the full list of supported variables.

[Extended thinking](https://code.claude.com/docs/en/model-config#extended-thinking)is enabled by default, which improves performance on complex reasoning tasks but uses additional tokens. To disable thinking entirely, set

`MAX_THINKING_TOKENS`

to `0`

in the local environment editor. On models with [adaptive reasoning](https://code.claude.com/docs/en/model-config#adjust-effort-level), any other

`MAX_THINKING_TOKENS`

value is ignored because adaptive reasoning controls thinking depth instead. On Opus 4.6 and Sonnet 4.6, set `CLAUDE_CODE_DISABLE_ADAPTIVE_THINKING`

to `1`

to use a fixed thinking budget; Opus 4.7 and later always use adaptive reasoning and have no fixed-budget mode.
### Remote sessions

Remote sessions continue in the background even if you close the app. Usage counts toward your[subscription plan limits](https://code.claude.com/docs/en/costs)with no separate compute charges. You can create custom cloud environments with different network access levels and environment variables. Select the environment dropdown when starting a remote session and choose

**Add environment**. See

[the cloud environment](https://code.claude.com/docs/en/claude-code-on-the-web#the-cloud-environment)for details on configuring network access and environment variables.

### SSH sessions

SSH sessions let you run Claude Code on a remote machine while using the desktop app as your interface. This is useful for working with codebases that live on cloud VMs, dev containers, or servers with specific hardware or dependencies. To add an SSH connection, click the environment dropdown before starting a session and select**+ Add SSH connection**. The dialog asks for:

**Name**: a friendly label for this connection**SSH Host**:`user@hostname`

or a host defined in`~/.ssh/config`

**SSH Port**: defaults to 22 if left empty, or uses the port from your SSH config**Identity File**: path to your private key, such as`~/.ssh/id_rsa`

. Leave empty to use the default key or your SSH config.

#### Pre-configure SSH connections for your team

Administrators can distribute SSH connections to team members by adding`sshConfigs`

to a [managed settings](https://code.claude.com/docs/en/settings#settings-precedence)file. Connections defined this way appear in each user’s environment dropdown automatically and are shown as managed, so users can select them but cannot edit or delete them in the app. The following example pre-configures a single connection that opens in

`~/projects`

on the remote host:
`id`

, `name`

, and `sshHost`

. The `sshPort`

, `sshIdentityFile`

, and `startDirectory`

fields are optional. Users can also add `sshConfigs`

to their own `~/.claude/settings.json`

, which is where connections added through the dialog are stored.
#### Restrict which SSH hosts users can connect to

Administrators can limit Desktop’s SSH sessions to an approved set of hosts by adding`sshHostAllowlist`

to a [managed settings](https://code.claude.com/docs/en/settings#settings-precedence)file. When set, users can only connect to hosts whose resolved hostname matches one of the patterns. Set it to an empty array to disable SSH sessions entirely. The following example allows connections to any host under

`devboxes.example.com`

and to a single named bastion host:
`*`

matches any host, and `*.example.com`

matches `example.com`

and any subdomain. Anything else is an exact match. The check runs against the hostname after `~/.ssh/config`

resolution via `ssh -G`

, so `Host`

aliases and `ProxyCommand`

/`ProxyJump`

entries are permitted as long as the resolved `HostName`

matches.
`sshHostAllowlist`

is read from managed settings only; values in user or project settings are ignored. Only the Claude Desktop app honors this setting; the Claude Code CLI and IDE extensions do not read it, and it does not restrict `ssh`

commands run through the Bash tool. It governs which hosts the Desktop app connects to, not network egress, so pair it with your organization’s network or zero-trust controls if you need a hard boundary.
## Enterprise configuration

Organizations on Team or Enterprise plans can manage desktop app behavior through admin console controls, managed settings files, and device management policies.### Admin console controls

These settings are configured through the[admin settings console](https://claude.ai/admin-settings/claude-code):

**Code in the desktop**: control whether users in your organization can access Claude Code in the desktop app**Code in the web**: enable or disable[web sessions](https://code.claude.com/docs/en/claude-code-on-the-web)for your organization**Remote Control**: enable or disable[Remote Control](https://code.claude.com/docs/en/remote-control)for your organization**Disable Bypass permissions mode**: prevent users in your organization from enabling bypass permissions mode

### Managed settings

Managed settings override project and user settings and apply when Desktop spawns CLI sessions. You can set these keys in your organization’s[managed settings](https://code.claude.com/docs/en/settings#settings-precedence)file or push them remotely through the admin console.

| Key | Description |
|---|---|
`permissions.disableBypassPermissionsMode` | set to `"disable"` to prevent users from enabling Bypass permissions mode. |
`disableAutoMode` | set to `"disable"` to prevent users from enabling
`permissions` . |
`autoMode` | customize what the auto mode classifier trusts and blocks across your organization. See
|

`sshConfigs`

[SSH connections](https://code.claude.com#pre-configure-ssh-connections-for-your-team)that appear in the environment dropdown. Users cannot edit or delete managed connections.`sshHostAllowlist`

[SSH sessions](https://code.claude.com#restrict-which-ssh-hosts-users-can-connect-to)to hosts whose resolved hostname matches one of these patterns. An empty array disables SSH sessions. Read from managed settings only.`managedMcpServers`

`"http"`

, `"sse"`

, or `"stdio"`

, connection details, and optionally a `toolPolicy`

map that restricts which tools in that server users can invoke. Available in third-party (3P) Desktop deployments only.[admin console controls](https://code.claude.com#admin-console-controls)above.

`permissions.disableBypassPermissionsMode`

and `disableAutoMode`

also work in user and project settings, but placing them in managed settings prevents users from overriding them. `autoMode`

is read from user settings, `.claude/settings.local.json`

, and managed settings, but not from the checked-in `.claude/settings.json`

: a cloned repo cannot inject its own classifier rules. For the complete list of managed-only settings including `allowManagedPermissionRulesOnly`

and `allowManagedHooksOnly`

, see [managed-only settings](https://code.claude.com/docs/en/permissions#managed-only-settings).

### Device management policies

IT teams can manage the desktop app through MDM on macOS or group policy on Windows. Available policies include enabling or disabling the Claude Code feature, controlling auto-updates, and setting a custom deployment URL.**macOS**: configure via`com.anthropic.Claude`

preference domain using tools like Jamf or Kandji**Windows**: configure via registry at`SOFTWARE\Policies\Claude`


### Authentication and SSO

Enterprise organizations can require SSO for all users. See[authentication](https://code.claude.com/docs/en/authentication)for plan-level details and

[Setting up SSO](https://support.claude.com/en/articles/13132885-setting-up-single-sign-on-sso)for SAML and OIDC configuration.

### Data handling

Claude Code processes your code locally in local sessions or on Anthropic’s cloud infrastructure in remote sessions. Conversations and code context are sent to Anthropic’s API for processing. See[data handling](https://code.claude.com/docs/en/data-usage)for details on data retention, privacy, and compliance.

### Deployment

Desktop can be distributed through enterprise deployment tools:**macOS**: distribute via MDM such as Jamf or Kandji using the`.dmg`

installer**Windows**: deploy via MSIX package or`.exe`

installer. See[Deploy Claude Desktop for Windows](https://support.claude.com/en/articles/12622703-deploy-claude-desktop-for-windows)for enterprise deployment options including silent installation

[network configuration](https://code.claude.com/docs/en/network-config). For the full enterprise configuration reference, see the

[enterprise configuration guide](https://support.claude.com/en/articles/12622667-enterprise-configuration).

## Coming from the CLI?

If you already use the Claude Code CLI, Desktop runs the same underlying engine with a graphical interface. You can run both simultaneously on the same machine, even on the same project. Each maintains separate session history, but they share configuration and project memory via CLAUDE.md files. To move a CLI session into Desktop, run`/desktop`

in the terminal. Claude saves your session and opens it in the desktop app, then exits the CLI. This command is available on macOS and Windows when you are signed in with a Claude subscription. It is not available with API key authentication or on Bedrock, Vertex, or Foundry.
### CLI flag equivalents

This table shows the desktop app equivalent for common CLI flags. Flags not listed have no desktop equivalent because they are designed for scripting or automation.| CLI | Desktop equivalent |
|---|---|
`--model sonnet` | Model dropdown next to the send button |
`--resume` , `--continue` | Click a session in the sidebar |
`--permission-mode` | Mode selector next to the send button |
`--dangerously-skip-permissions` | Bypass permissions mode. Enable in Settings → Claude Code → “Allow bypass permissions mode”. Enterprise admins can disable this setting. |
`--add-dir` | Add multiple repos with the + button in remote sessions |
`--allowedTools` , `--disallowedTools` | No per-session equivalent. Permission rules in
|

`--verbose`

[Verbose view mode](https://code.claude.com#switch-view-modes)in the Transcript view dropdown`--print`

, `--output-format`

`ANTHROPIC_MODEL`

env var`MAX_THINKING_TOKENS`

env var[environment configuration](https://code.claude.com#environment-configuration).### Shared configuration

Desktop and CLI read the same configuration files, so your setup carries over:and[CLAUDE.md](https://code.claude.com/docs/en/memory)`CLAUDE.local.md`

files in your project are used by bothconfigured in[MCP servers](https://code.claude.com/docs/en/mcp)`~/.claude.json`

or`.mcp.json`

work in bothand[Hooks](https://code.claude.com/docs/en/hooks)defined in settings apply to both[skills](https://code.claude.com/docs/en/skills)in[Settings](https://code.claude.com/docs/en/settings)`~/.claude.json`

and`~/.claude/settings.json`

are shared. Permission rules, allowed tools, and other settings in`settings.json`

apply to Desktop sessions.**Models**: Sonnet, Opus, and Haiku are available in both. In Desktop, select the model from the dropdown next to the send button. You can change the model mid-session from the same dropdown.

**MCP servers: desktop chat app vs Claude Code**: MCP servers configured for the Claude Desktop chat app in

`claude_desktop_config.json`

are separate from Claude Code and will not appear in the Code tab. To use MCP servers in Claude Code, configure them in `~/.claude.json`

or your project’s `.mcp.json`

file. See [MCP configuration](https://code.claude.com/docs/en/mcp#installing-mcp-servers)for details.

### Feature comparison

This table compares core capabilities between the CLI and Desktop. For a full list of CLI flags, see the[CLI reference](https://code.claude.com/docs/en/cli-reference).

| Feature | CLI | Desktop |
|---|---|---|
| Permission modes | All modes including `dontAsk` | Ask permissions, Auto accept edits, Plan mode, Auto, and Bypass permissions via Settings |
`--dangerously-skip-permissions` | CLI flag | Bypass permissions mode. Enable in Settings → Claude Code → “Allow bypass permissions mode” |
|

[enterprise configuration guide](https://support.claude.com/en/articles/12622667-enterprise-configuration).[MCP servers](https://code.claude.com/docs/en/mcp)[Plugins](https://code.claude.com/docs/en/plugins)`/plugin`

command[flag](https://code.claude.com/docs/en/cli-reference)`--worktree`

[Scheduled tasks](https://code.claude.com/docs/en/desktop-scheduled-tasks)[Enable via](https://code.claude.com/docs/en/computer-use)on macOS`/mcp`

[App and screen control](https://code.claude.com#let-claude-use-your-computer)on macOS and Windows[Dispatch sessions](https://code.claude.com#sessions-from-dispatch)in the sidebar[,](https://code.claude.com/docs/en/cli-reference)`--print`

[Agent SDK](https://code.claude.com/docs/en/headless)### What’s not available in Desktop

The following features are only available in the CLI or VS Code extension:**Third-party providers**: Desktop connects to Anthropic’s API by default. Enterprise deployments can configure Vertex AI and gateway providers via[managed settings](https://support.claude.com/en/articles/12622667-enterprise-configuration). For Bedrock or Foundry, use the[CLI](https://code.claude.com/docs/en/quickstart).**Linux**: the desktop app is available on macOS and Windows only. On Linux, use the[CLI](https://code.claude.com/docs/en/quickstart).**Inline code suggestions**: Desktop does not provide autocomplete-style suggestions. It works through conversational prompts and explicit code changes.**Agent teams**: parallel Claude Code sessions that message each other are available in the[CLI](https://code.claude.com/docs/en/agent-teams), not in Desktop. For multi-agent work inside one session, use[dynamic workflows](https://code.claude.com/docs/en/workflows), which run in Desktop.**Terminal-dialog commands**: built-in commands that open an interactive panel in the terminal, such as`/permissions`

,`/config`

,`/agents`

, and`/doctor`

, are not available in the Code tab and reply with`isn't available in this environment`

. Edit[settings files](https://code.claude.com/docs/en/settings)directly to manage permission rules and configuration, or run the command from the standalone CLI.

## Troubleshooting

The sections below cover issues specific to the desktop app. For runtime API errors that appear in the chat such as`API Error: 500`

, `529 Overloaded`

, `429`

, or `Prompt is too long`

, see the [Error reference](https://code.claude.com/docs/en/errors). Those errors and their fixes are the same across the CLI, desktop, and web.

### Check your version

To see which version of the desktop app you’re running:**macOS**: click**Claude**in the menu bar, then**About Claude****Windows**: click**Help**, then**About**

### 403 or authentication errors in the Code tab

If you see`Error 403: Forbidden`

or other authentication failures when using the Code tab:
- Sign out and back in from the app menu. This is the most common fix.
- Verify you have an active paid subscription: Pro, Max, Team, or Enterprise.
- If the CLI works but Desktop does not, quit the desktop app completely, not just close the window, then reopen and sign in again.
- Check your internet connection and proxy settings.

### Blank or stuck screen on launch

If the app opens but shows a blank or unresponsive screen:- Restart the app.
- Check for pending updates. The app auto-updates on launch.
- On Windows, check Event Viewer for crash logs under
**Windows Logs → Application**.

### ”Failed to load session”

If you see`Failed to load session`

, the selected folder may no longer exist, a Git repository may require Git LFS that isn’t installed, or file permissions may prevent access. Try selecting a different folder or restarting the app.
### Session not finding installed tools

If Claude can’t find tools like`npm`

, `node`

, or other CLI commands, verify the tools work in your regular terminal, check that your shell profile properly sets up PATH, and restart the desktop app to reload environment variables.
### Git and Git LFS errors

On Windows, Git is required for the Code tab to start local sessions. If you see “Git is required,” install[Git for Windows](https://git-scm.com/downloads/win)and restart the app. If you see “Git LFS is required by this repository but is not installed,” install Git LFS from

[git-lfs.com](https://git-lfs.com/), run

`git lfs install`

, and restart the app.
### MCP servers not working on Windows

If MCP server toggles don’t respond or servers fail to connect on Windows, check that the server is properly configured in your settings, restart the app, verify the server process is running in Task Manager, and review server logs for connection errors.### App won’t quit

**macOS**: press Cmd+Q. If the app doesn’t respond, use Force Quit with Cmd+Option+Esc, select Claude, and click Force Quit.**Windows**: use Task Manager with Ctrl+Shift+Esc to end the Claude process.

### Windows-specific issues

**PATH not updated after install**: open a new terminal window. PATH updates only apply to new terminal sessions.**Concurrent installation error**: if you see an error about another installation in progress but there isn’t one, try running the installer as Administrator.

### ”Branch doesn’t exist yet” when opening in CLI

Remote sessions can create branches that don’t exist on your local machine. Click the branch name in the session toolbar to copy it, then fetch it locally:### Still stuck?

- Search or file a bug on
[GitHub Issues](https://github.com/anthropics/claude-code/issues) - Visit the
[Claude support center](https://support.claude.com/)
