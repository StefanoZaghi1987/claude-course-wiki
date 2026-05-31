---
type: page
created: 2026-05-31
updated: 2026-05-31
tags: [skills, plugins, claude-code, ai4gamma-corso]
---

Skills are packages of structured instructions that make Claude deterministic — the same trigger always executes the same workflow and produces the same type of output, regardless of how the request is phrased.

## Overview

Without a Skill, Claude performs tasks in a non-deterministic way: the same request produces variably structured results across executions. With a Skill, Claude follows a fixed workflow defined in the Skill's instructions — guaranteeing consistency, reproducibility, and predictable quality. Skills are the mechanism for encoding expertise into Claude: they transform a "best-effort" behavior into a standardized, repeatable procedure. Claude does not pre-load all Skill content; it reads a Skill's SKILL.md dynamically only when a trigger is recognized.

## Key dimensions

### Anatomy of a Skill

A Skill is a folder containing: **(1) SKILL.md (required)** — a Markdown file with: metadata (name, description), a trigger (a description that tells Claude *when* to activate this Skill automatically — the most critical element), and the operational workflow (step-by-step instructions, output format, rules). **(2) References (optional)** — support files: output examples, domain glossaries, sector-specific rules, document templates. Claude reads these during execution to guide quality and consistency. [[wiki/sources/manuale-sesta-lezione]]

### The trigger is the most critical element

The trigger description in SKILL.md determines whether Claude will recognize the right prompts to activate the Skill automatically. A well-written trigger uses the vocabulary that users naturally employ when requesting the task. If the trigger is vague or uses terminology the user won't say, the Skill won't auto-activate. Users can always activate manually with `/skill-name`. [[wiki/sources/manuale-sesta-lezione]]

### Agent Virtual Machine

When a Skill needs to operate on files (read documents, generate outputs, execute scripts), Claude instantiates an Agent Virtual Machine — a sandboxed environment that bridges Claude and the user's file system. This VM mounts the required folders, executes requested operations (including Python or Node.js scripts), and returns results. This is why Word/PDF/PowerPoint handling in Claude is implemented as built-in Skills (`docx`, `pdf`, `pptx`): they are structured workflows that the VM executes, not native capabilities. [[wiki/sources/manuale-sesta-lezione]]

### Three management levels

**Built-in (Anthropic)**: always available, no configuration needed. Includes document Skills (`docx`, `pdf`, `pptx`) and development Skills (`skill-creator`, `mcp-builder`). **Organizational**: loaded by org admins via Organization Settings → Skills; available to all members. Gamma examples: `prompt-architect`, `technical-translation`. **Personal**: created or downloaded by individual users; managed via the Customize button in Cowork or Claude Code interfaces (not in profile settings). [[wiki/sources/manuale-sesta-lezione]]

### Activation: automatic vs. manual

**Automatic trigger**: Claude reads the prompt and, if keywords or context match the trigger description, activates the Skill transparently. **Manual slash command**: `/skill-name` forces Skill activation regardless of trigger. Use manual activation when the context isn't clear enough for automatic recognition or when you want to ensure a specific Skill is used. [[wiki/sources/manuale-sesta-lezione]]

### When to use Skills

Skills add value for: recurring tasks (same operation type performed repeatedly), specific workflows (a precise sequence of operations to crystallize), structured document generation (reports, meeting notes, manuals with defined structure), and corporate templates (standard formats applied automatically). Without a Skill, Claude can still perform these tasks — just inconsistently. [[wiki/sources/manuale-sesta-lezione]]

### Creation Method 1: from a Claude Desktop Project

Ideal for Skills with complex logic developed and refined over time. Process: (1) Create a dedicated Project with well-tested Instructions, (2) Refine behavior by testing with real documents, (3) Ask Claude to "create a Skill from this Project" — the built-in `skill-creator` Skill reads the entire Project context and generates the SKILL.md and any needed References. The user describes the desired workflow; Claude handles the technical structure. (4) Save, download, and distribute as needed. [[wiki/sources/manuale-sesta-lezione]]

### Creation Method 2: from Cowork

Ideal for Skills requiring iterative testing, file operations, or web access (e.g., scraping scripts). Process: (1) Brainstorming session in Cowork to produce a Skill specification, (2) Claude generates code (Python/Node.js scripts if needed), tests it in the VM, and iterates, (3) Testing phase on real examples, (4) Finalize and save the complete Skill package. Higher token cost than Method 1; preferred when the Skill's complexity is in its execution rather than its logic. [[wiki/sources/manuale-sesta-lezione]]

### Real examples from AI4Gamma

`technical-translation`: 7-step workflow for technical document translation (evaluate size, analyze structure, build glossary, confirm target language, translate, check consistency, generate output); multi-chunk processing for long documents; preserves structure and terminology. `website-to-document`: full web scraping to Word/PDF with configurable depth and page limit; Python script-backed; falls back to Claude-in-Chrome integration for anti-scraping sites. [[wiki/sources/manuale-sesta-lezione]]

## Connections

- [[wiki/pages/plugins]] — Skills are one of four plugin components
- [[wiki/pages/claude-desktop]] — Organizational Skills managed via Organization Settings
- [[wiki/pages/claude-projects]] — Method 1 Skill creation uses a Claude Desktop Project as the development environment
- [[wiki/pages/cowork]] — Method 2 Skill creation uses Cowork for testing-intensive Skills
- [[wiki/pages/mcp-model-context-protocol]] — the complementary extension mechanism for external system integrations

## Sources

- [[wiki/sources/manuale-sesta-lezione]] — full Skills treatment: anatomy, virtual machine, levels, activation, both creation methods, real examples
- [[wiki/sources/manuale-quarta-lezione]] — Skills introduced as a plugin component type
