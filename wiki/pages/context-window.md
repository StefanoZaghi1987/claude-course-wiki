---
type: page
created: 2026-05-31
updated: 2026-05-31
tags: [context-window, ai4gamma-corso]
---

The context window is the total set of information Claude can see and use simultaneously in a session — the finite working memory of a conversation.

## Overview

The context window is Claude's "desk": everything that fits on the desk is what Claude can reason with. It includes the full chat history, attached files, system instructions, and generated outputs. As a conversation grows and files are attached, the window fills. Unlike human memory, Claude cannot selectively prioritize: when the window approaches capacity, it auto-compacts the earlier content into a summary, but with degraded fidelity. The practical consequence is that response quality degrades as saturation approaches. Managing context deliberately is one of the most important skills for consistently productive Claude use.

## Key dimensions

### What fills the context

Every element of a session consumes tokens: user messages, Claude responses, attached files, project instructions, and system prompts. A single Excel file containing embedded logging data (not just the primary table) can saturate the window alone. Files should be stripped of irrelevant content before attachment. One token ≈ 0.75 words. [[wiki/sources/manuale-prima-lezione]]

### Saturation signals

Signs that the window is approaching capacity: Claude referring inaccurately to earlier messages, responses becoming less targeted or more generic, Settings → Usage showing high token consumption. Auto-compaction summarizes older turns but loses specific details — quality does not recover by waiting. [[wiki/sources/manuale-prima-lezione]]

### Four management strategies

**Zero-shot prompting**: put all necessary information in the first prompt, fully structured, so fewer follow-up messages are needed. **Few-shot prompting**: include input/output examples within the prompt to guide behavior without iterative correction. **Continuation in new chat**: save an artifact or summary from the current session, open a fresh chat, paste the artifact as the initial context to continue with a clean window. **Prefer lightweight files**: use Markdown over Word, strip logs from Excel before attaching, split large documents into focused excerpts. [[wiki/sources/manuale-prima-lezione]]

### Plan tier differences

Plan Max offers approximately 5× the context window capacity of Plan Pro. For Gamma SPA users the team plan applies, with capacity levels aligned to the team tier. Larger windows reduce saturation frequency but do not eliminate the need for deliberate management. [[wiki/sources/manuale-prima-lezione]]

### Auto-compaction in Claude Code

In Claude Code, `/compact` triggers manual compaction with optional custom instructions for what to prioritize in the summary. `/context` shows the current token count and remaining capacity. Automatic compaction triggers at configurable thresholds. [[wiki/sources/manuale-terza-lezione]]

### What loads at session start

Before the first prompt, four things pre-load: CLAUDE.md (full content), auto memory (first 200 lines of MEMORY.md), MCP tool names (schemas load later on demand), and skill descriptions (full bodies load only when invoked). Path-scoped rules in `.claude/rules/` with `paths:` frontmatter load lazily when Claude reads a matching file, not at startup. An output style or `--append-system-prompt` content also loads in the system prompt at this point. [[wiki/sources/explore-the-context-window-claude-code-docs]]

### What survives compaction

After `/compact`, different elements behave differently:

| Mechanism | After compaction |
|-----------|-----------------|
| System prompt and output style | Unchanged — not part of message history |
| Project-root CLAUDE.md and unscoped rules | Re-injected from disk automatically |
| Auto memory | Re-injected from disk automatically |
| Rules with `paths:` frontmatter | Lost until a matching file is read again |
| Nested CLAUDE.md in subdirectories | Lost until a file in that subdirectory is read again |
| Invoked skill bodies | Re-injected, capped at 5,000 tokens/skill and 25,000 total; oldest invoked skills dropped first |
| Hooks | Not applicable — hooks run as code, not context |

Put persistent instructions in project-root CLAUDE.md rather than nested files or conversation history to ensure they survive compaction. [[wiki/sources/explore-the-context-window-claude-code-docs]]

### Context cost by extension feature

| Feature | When it loads | What loads | Context cost |
|---------|--------------|------------|-------------|
| CLAUDE.md | Session start | Full content | Every request |
| Skills | Session start + when used | Descriptions at start; bodies on use | Low until invoked |
| MCP servers | Session start | Tool names; schemas on demand | Low until a tool is used |
| Code intelligence | After file edits and on demand | Diagnostics; symbol locations | Low — reduces file reads |
| Subagents | When spawned | Fresh isolated context | Zero impact on main session |
| Hooks | On trigger | Nothing (runs externally) | Zero unless hook returns context |

Use `disable-model-invocation: true` in a skill's frontmatter to hide it from Claude entirely until manually invoked, reducing its cost to zero. [[wiki/sources/extend-claude-code-claude-code-docs]]

## Connections

- [[wiki/pages/artifacts]] — artifacts serve as context checkpoints for bridging saturated sessions
- [[wiki/pages/prompt-engineering]] — prompt structure determines how efficiently the context is used
- [[wiki/pages/memory-in-claude]] — the three memory levels persist context across sessions; the context window resets each session
- [[wiki/pages/claude-projects]] — project instructions and files provide persistent cross-session context
- [[wiki/pages/claude-code]] — `/context` and `/compact` commands for in-session context management

## Sources

- [[wiki/sources/manuale-prima-lezione]] — definition, saturation signals, four management strategies, plan differences
- [[wiki/sources/manuale-terza-lezione]] — `/compact` and `/context` commands in Claude Code
- [[wiki/sources/explore-the-context-window-claude-code-docs]] — session-start load order, what survives compaction, live inspection commands
- [[wiki/sources/extend-claude-code-claude-code-docs]] — context cost by extension feature