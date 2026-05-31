---
type: source
created: 2026-05-31
updated: 2026-05-31
tags: [ai4gamma-corso, claude-desktop, prompt-engineering, context-window, mcp, artifacts]
source_path: raw/local/manuale-prima-lezione/
fetch_method: local-pdf
---

Course manual for the first session of the AI4Gamma training series on Claude, held on 6 March 2026 by Stefano Zaghi at Gamma SPA (~3 hours, Microsoft Teams).

## Summary

This manual covers the foundational concepts introduced in the first session of Gamma SPA's internal AI4Gamma training course. The session aimed to give participants working knowledge of Claude Desktop — its interface, plans, memory architecture, and extensions — before moving into prompt engineering and context management.

The central thesis is that Claude has no native memory between sessions: every chat starts from zero. This makes the context window the primary resource to manage. Participants were shown how the context window fills over a conversation and how to avoid saturation through structured prompts, short chat cycles, and strategic use of Artifacts as incremental output checkpoints.

The second major theme is the distinction between unstructured AI use (vibe coding) and methodological use (Spec-Driven Development). For simple, disposable tasks an exploratory approach is acceptable; for complex or quality-sensitive work, writing well-structured specifications is not optional — it is the only path to reproducible results. This distinction is framed as the course's guiding thread.

Prompt engineering was introduced through the TCOF framework (Task, Context, Output, Format) and five core principles: clarity, specificity, context, format, and examples. Role prompting was presented as a practical extension of the Context component: assigning Claude a professional role narrows its interpretation space and improves domain relevance.

The session ended with an introduction to Claude Projects as the answer to re-writing context on every new chat — a topic to be deepened in Lesson 2.

## Key points

- Every Claude session starts from a blank slate; the context window holds all session state and is limited by plan tier (Plan Max ≈ 5× Plan Pro capacity)
- Claude Desktop has three operating modes: Chat (conversational), Claude Code (software development CLI), and Cowork (autonomous multi-step task automation)
- The TCOF framework (Task, Context, Output, Format) is the standard structure for effective prompts; role prompting is a sub-technique within the Context component
- Artifacts are self-contained downloadable outputs; iterating on an artifact within the same chat enables structured revisions without losing context
- Memory in Claude operates at three non-overwriting levels: global user preferences, automatically extracted chat memories, and project-level instructions
- MCP (Model Context Protocol) servers allow Claude to interface with external tools: file system, browser, databases, APIs
- Vibe coding works for simple monouso tasks; Spec-Driven Development is required for complex, quality-sensitive work
- Claude Projects fix context permanently in project instructions, eliminating the need to re-write it per chat

## Connections

- [[wiki/pages/claude-desktop]] — the application documented in this lesson
- [[wiki/pages/artifacts]] — output format introduced here
- [[wiki/pages/prompt-engineering]] — TCOF framework and 5 principles
- [[wiki/pages/context-window]] — central concept of the lesson
- [[wiki/pages/memory-in-claude]] — three memory levels explained here
- [[wiki/pages/mcp-model-context-protocol]] — introduced in this lesson
- [[wiki/pages/vibe-coding]] — introduced and critiqued here
- [[wiki/pages/claude-projects]] — introduced as the next step
