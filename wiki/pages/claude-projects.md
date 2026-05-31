---
type: page
created: 2026-05-31
updated: 2026-05-31
tags: [claude-projects, claude-desktop, ai4gamma-corso]
---

Claude Projects are persistent workspaces within Claude Desktop that hold fixed context — instructions, documents, and team sharing — applicable to all conversations within the project.

## Overview

A Project solves the "long prompt on every chat" problem. Without projects, users must re-write context, role, and constraints every time they start a new conversation. With a project, that context is written once in the project instructions and is loaded automatically into every chat within the project scope. Projects are the recommended container for any recurring work domain, specialized assistant, or collaborative team task. They transform Claude from a stateless conversational tool into a persistent, specialized AI assistant for a given context.

## Key dimensions

### Four project areas

A project is composed of four areas: **Memory** (auto-generated memories from project conversations), **Instructions** (the system prompt — permanent context and role definition for all chats), **Files** (the knowledge base — uploaded documents, specs, and reference material retrieved via RAG), and **Tool Access** (which connectors and extensions are active within this project). [[wiki/sources/manuale-prima-lezione]]

### Main advantage

The primary benefit is context permanence: a rich system prompt and knowledge base are configured once; individual chats within the project can then be short and task-focused. Example from the course: the "SAP Business One Assistant" project at Gamma SPA holds all infrastructure details, naming conventions, stored procedures, and technical constraints. A prompt like "Analyze this query and show improvement points" produces a fully contextualized response without any preamble. [[wiki/sources/manuale-prima-lezione]]

### Project knowledge and RAG

Files uploaded to the project's Files area are not injected wholesale into the context window — they are chunked, vectorized, and indexed in a vector database. When a chat prompt is sent, semantically relevant chunks are retrieved and injected into the context automatically. This is the RAG (Retrieval-Augmented Generation) architecture. [[wiki/sources/manuale-seconda-lezione]]

### Memory hierarchy

Project instructions sit between global user preferences and the in-session context window in Claude's memory hierarchy. Each level adds specificity without erasing broader ones: global preferences apply everywhere, project instructions apply within the project, and session content applies only to the current chat. [[wiki/sources/manuale-seconda-lezione]]

### Team sharing

Projects can be shared with other team members, providing consistent access to the same instructions, knowledge base, and context across the organization. This enables team-level rather than individual-level AI configuration. [[wiki/sources/manuale-prima-lezione]]

## Connections

- [[wiki/pages/claude-desktop]] — projects live within the Claude Desktop interface
- [[wiki/pages/memory-in-claude]] — project instructions are one of the three memory levels
- [[wiki/pages/rag-retrieval-augmented-generation]] — the architecture behind project file retrieval
- [[wiki/pages/context-window]] — projects reduce per-session context overhead
- [[wiki/pages/meta-prompting]] — technique for generating high-quality project instructions automatically

## Sources

- [[wiki/sources/manuale-prima-lezione]] — projects introduced briefly; four areas and main advantage
- [[wiki/sources/manuale-seconda-lezione]] — full coverage: creation workflow, all four areas in depth, memory hierarchy, when to use projects vs. chat
