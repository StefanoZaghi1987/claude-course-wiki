---
type: source
created: 2026-05-31
updated: 2026-05-31
tags: [ai4gamma-corso, claude-projects, meta-prompting, rag, cowork, project-knowledge]
source_path: raw/local/manuale-seconda-lezione/
fetch_method: local-pdf
---

Course manual for the second session of the AI4Gamma training series on Claude, held on 20 March 2026 by Stefano Zaghi at Gamma SPA (~2 hours, Microsoft Teams).

## Summary

This lesson marks a qualitative shift in the training path: from individual prompt techniques to building structured, persistent work environments through Claude Projects. The session's red thread is the construction of the Beas Assistant — a virtual assistant for the Beas Manufacturing production management system integrated with SAP Business One — built step-by-step during the session.

The lesson begins with participants sharing feedback from their independent practice, surfacing practical techniques: using global preferences to define behavioral shortcuts (typing `/prompt` to auto-generate a TCOF-structured prompt), using artifacts as explicit context checkpoints before auto-compaction, and using exploratory open prompts when the objective isn't yet clear — a recognized limitation of TCOF.

The main new content covers Claude Projects in depth: the four project areas (Memory, Instructions, Files, Tool Access), the creation workflow, and the memory hierarchy that spans from global user preferences down to the current chat session. A particularly important section explains project knowledge technically: files are not loaded wholesale into the context window but are chunked, vectorized, and retrieved semantically via a vector database. Only relevant chunks are injected per query — meaning 100 documents don't saturate the window.

Meta-prompting is introduced as one of the lesson's key insights: instead of writing project instructions manually, one asks Claude to generate the optimal prompt for the task. The two-phase flow (generate → execute) produces higher-quality configuration than manual writing. For high-importance tasks, using the Opus model in the meta-prompting phase is recommended.

Cowork is introduced as an agentic execution environment for non-technical users — the same engine as Claude Code but with a GUI. It can spawn sub-agents for parallel operation, enabling large-scale document analysis without context saturation.

## Key points

- Claude Projects are isolated workspaces with persistent configuration: Instructions (system prompt), Files (knowledge base), Memory (auto-generated, per-user), and Tool Access
- Use a project for recurring themes and specialized assistants; use plain chat for one-off questions
- Project files are indexed in a vector database via semantic chunking — only relevant chunks are retrieved per query; the full document must be explicitly requested to load it whole
- Memory in Claude is hierarchical and additive: each level enriches context without overriding higher ones (global preferences → project → chat)
- Meta-prompting: ask Claude to generate the optimal prompt for the task instead of writing it manually; two-phase flow: generate → execute; use Opus for complex tasks
- Cowork is the GUI-based agentic execution environment; launches tasks from within a project, inheriting its context; can parallelize via sub-agents
- Web Search = single web lookup integrated in chat; Deep Research = autonomous multi-source research producing a structured report (10–15+ minutes, high resource cost)
- Extended Thinking should be kept always on — quality improvement outweighs the token cost increase; it also extends the maximum response length

## Connections

- [[wiki/pages/claude-projects]] — main topic of the lesson
- [[wiki/pages/rag-retrieval-augmented-generation]] — technical architecture behind project knowledge
- [[wiki/pages/meta-prompting]] — technique introduced here
- [[wiki/pages/cowork]] — introduced and demonstrated here
- [[wiki/pages/memory-in-claude]] — memory hierarchy fully mapped here
- [[wiki/pages/context-window]] — relationship to project knowledge and RAG
