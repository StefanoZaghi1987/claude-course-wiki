---
type: page
created: 2026-05-31
updated: 2026-05-31
tags: [artifacts, claude-desktop, ai4gamma-corso]
---

Artifacts are self-contained, downloadable output units that Claude generates for structured content, enabling iterative refinement within a chat without restarting from scratch.

## Overview

An artifact is Claude's preferred format for any output that is long, self-contained, and meant to be used independently — documents, reports, code files, HTML pages, SVG graphics. Claude generates artifacts automatically when it detects content meeting these criteria; users can also request them explicitly. Artifacts appear as clickable blocks within the chat and open in a dedicated side panel with copy, download, and iteration options. Their secondary function — as context checkpoints that can be loaded into new chats when the original window is exhausted — makes them a key tool for managing long workflows.

## Key dimensions

### Types

Supported artifact types include Markdown documents, Word files (.docx), Excel spreadsheets, HTML pages, SVG graphics, and code files. Markdown is the recommended default for intermediate work: it is token-efficient, easy for Claude to manipulate, and preserves document structure. [[wiki/sources/manuale-prima-lezione]]

### Generation and explicit request

Automatic generation triggers when Claude determines content is sufficiently long and self-contained. Explicit requests use prompt phrasing such as: "Return the output as a downloadable artifact in Markdown format." Both paths produce the same artifact block in the chat. [[wiki/sources/manuale-prima-lezione]]

### Iterative workflow

Once an artifact exists, subsequent prompts can refine it without rebuilding from zero. The practical example from Lesson 1: after generating a full issue report, a second prompt — "Make it shorter, keep only bug summary by priority, overall assessment, and top 5 issues" — produced a refined artifact that preserved structure while reducing content. This generate → refine → generate loop is the recommended workflow for structured documents. [[wiki/sources/manuale-prima-lezione]]

### Artifacts as context checkpoints

An artifact preserves a structured snapshot of work done, which can be referenced in a new chat when the original context window is saturated. This pattern — save the artifact, start a fresh chat, paste the artifact as starting context — is one of the four context management strategies taught in the course. [[wiki/sources/manuale-prima-lezione]]

## Connections

- [[wiki/pages/claude-desktop]] — the platform where artifacts are generated and iterated
- [[wiki/pages/context-window]] — artifacts serve as checkpoints to bridge saturated sessions

## Sources

- [[wiki/sources/manuale-prima-lezione]] — artifact types, generation, iterative workflow, and context-checkpoint use
