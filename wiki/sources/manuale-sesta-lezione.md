---
type: source
created: 2026-05-31
updated: 2026-05-31
tags: [ai4gamma-corso, plugins, skills, mcp, browser-automation, cowork]
source_path: raw/local/manuale-sesta-lezione/
fetch_method: local-pdf
---

Course manual for the sixth and final session of the AI4Gamma training series on Claude, held on 5 May 2026 by Stefano Zaghi at Gamma SPA (~2 hours, Microsoft Teams).

## Summary

Lesson 6 is the course's concluding chapter: a "return to earth" after Lesson 5's complexity peak. It addresses the practical question of how to transform Claude from a generic assistant into a platform specialized for the team's specific needs. The answer is structured across three complementary layers: Skills, MCP Connectors, and Browser Automation.

Skills are defined as packages of structured instructions that make Claude deterministic: the same request always triggers the same workflow and produces the same type of output. Without a Skill, Claude varies across executions; with one, behavior is consistent and reproducible. A Skill's anatomy is: a SKILL.md file (mandatory — contains name, description, trigger, and workflow), plus an optional References folder (examples, glossaries, domain rules, document templates). Claude reads SKILL.md dynamically when a trigger is recognized — it does not pre-load all Skill content. For file-operating Skills, Claude instantiates an Agent Virtual Machine (a sandbox that bridges Claude and the user's file system, allowing script execution). Skills operate at three levels: built-in (Anthropic, e.g., docx, pdf, pptx, skill-creator), organizational (shared via Organization Settings), and personal (Customize menu in Cowork or Claude Code).

Two creation methods are covered. Method 1 (from a Claude Desktop Project) is ideal for Skills with complex workflows developed and refined over time: configure the Project, test it, then ask Claude to "create a Skill from this Project" — the built-in skill-creator handles the SKILL.md structure. Method 2 (from Cowork) is ideal for Skills requiring testing, iteration, and file/web operations: brainstorm spec in Cowork → generate code (e.g., Python scripts for scraping) → test iteratively → finalize and save. Real examples: technical-translation (Method 1, translates documents with a 7-step workflow, handles multi-chunk processing), website-to-document (Method 2, full web scraping to Word/PDF with configurable depth and page limits, MCP/Chrome fallback for anti-scraping sites).

MCP is presented as an industry-wide standard (born at Anthropic in 2023, now adopted by all major AI vendors) that enables Claude to access any external system via a client-server architecture. An MCP Server exposes three element types: Resources (data Claude can read), Tools (functions Claude can invoke), and Prompts (usage examples). The GammaBot integration is the primary Gamma example: two custom MCP servers expose SAP manual search/reading and TARIC customs classification. Configuration of remote MCP servers happens via `claude-desktop-config.json`. Local MCP servers can be built using the `mcp-builder` Skill and deployed to run automatically with Claude Desktop.

Browser automation via the Claude in Chrome extension allows Claude to navigate, click, fill forms, take screenshots, and extract content from any website — demonstrated by navigating the Gamma S.p.A. site to find job application instructions. Use cases: automated form filling, portal monitoring, data extraction, UI verification.

The session closes with Stefano's strategic vision for Gamma: GammaBot as the broad-adoption AI platform for all employees, Claude as the specialized development and integration tool for a small technical team that builds Skills and MCP integrations to be shared org-wide.

## Key points

- Skills make Claude deterministic: same trigger → same workflow → same output type; without a Skill, results vary across executions
- SKILL.md anatomy: metadata (name, description), trigger (when to activate), workflow (step-by-step instructions); References folder is optional support material
- Agent Virtual Machine: Claude instantiates a sandboxed VM for file-operating Skills; explains why Word/PDF/PPT handling is implemented as built-in Skills (docx, pdf, pptx)
- Three Skill levels: built-in (Anthropic), organizational (Organization Settings), personal (Customize menu — NOT in profile settings)
- Two Skill creation methods: Method 1 (from Project, for complex logic-heavy Skills) vs. Method 2 (from Cowork, for testing-intensive or file/web-dependent Skills)
- skill-creator is a built-in Skill that guides the creation of new Skills — user describes the workflow, Claude handles the SKILL.md structure
- Skill vs. MCP: use a Skill for text/document workflows within Claude; use MCP when you need to read/write external systems (databases, APIs, email, ERP)
- MCP client-server: Claude has an integrated MCP Client; external systems expose MCP Servers with Resources, Tools, and Prompts
- MCP is now an industry standard; all major AI vendors have adopted it; Gamma already has Microsoft 365, GitHub, Google Workspace, Slack, GammaBot, and more configured
- Custom MCP servers configured in `claude-desktop-config.json`; local MCP servers auto-start with Claude Desktop
- Browser automation via Claude in Chrome: navigate, click, fill forms, extract data; useful for form automation, portal monitoring, UI testing

## Connections

- [[wiki/pages/skills]] — main topic of sections 3–5
- [[wiki/pages/mcp-model-context-protocol]] — main topic of sections 6–7
- [[wiki/pages/plugins]] — contextual architecture overview
- [[wiki/pages/cowork]] — Method 2 Skill creation; Cowork as the agentic development environment for testing-intensive Skills
