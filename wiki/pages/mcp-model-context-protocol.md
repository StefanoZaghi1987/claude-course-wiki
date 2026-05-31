---
type: page
created: 2026-05-31
updated: 2026-05-31
tags: [mcp, plugins, ai4gamma-corso]
---

MCP (Model Context Protocol) is an open standard that enables Claude to connect to external tools and services through a client-server architecture, transforming it from a text generator into an agent that can take actions.

## Overview

A Claude agent is defined as an LLM plus a set of tools capable of performing concrete operations in the world. MCP is the protocol layer through which those tools are registered and invoked. Without tools, Claude can only produce text; with MCP connectors, it can read and write files, control a browser, query databases, call APIs, and interact with any service that exposes an MCP-compatible interface. MCP connectors are one of four components within Claude's plugin system, alongside Skills, Sub-agents, and Hooks.

## Key dimensions

### Tool and agent concept

A tool in Claude's context can be a calculator, a database connection, a web browser, a code execution environment, or any system that accepts requests and returns results. The agent orchestrator (in Claude Code: the Main Orchestrator Agent) decides which tools to invoke to fulfill a task, delegating sub-tasks to specialized sub-agents when needed. [[wiki/sources/manuale-prima-lezione]]

### Built-in connectors in Claude Desktop

Claude Desktop ships with several configurable MCP connectors: **File System** (read/write local files), **Control Chrome** (browser automation), **Windows MCP / Desktop Commander** (OS-level actions on Windows), and **Claude in Chrome** (chat overlay on any webpage). Node.js and Python must be installed for these connectors to function — visible in Settings → Extensions → Advanced Settings. [[wiki/sources/manuale-prima-lezione]]

### Client-server architecture

MCP follows a client-server model: Claude is the client, external systems are servers. The protocol standardizes how capabilities (tools) are advertised by servers and how Claude invokes them. This architecture allows any service to become a Claude tool by implementing the MCP server interface. [[wiki/sources/manuale-sesta-lezione]]

### Organizational access control

Organization admins can whitelist specific web domains that Claude is permitted to access via Network Access settings. For Gamma SPA: SAP community and help portals, Bears Cloud support, and Boyum IT support are authorized. Any domain not on the list is blocked regardless of connector configuration. [[wiki/sources/manuale-prima-lezione]]

### What an MCP Server exposes

An MCP Server exposes three types of elements: **Resources** — static or dynamic data Claude can read to get context (files, web pages, database records); **Tools** — executable functions Claude can invoke to take actions on external systems (database queries, email send, SQL, API calls); **Prompts** — usage examples the server provides to guide effective interaction. [[wiki/sources/manuale-sesta-lezione]]

### Custom MCP servers

Organizations can develop internal MCP servers to expose proprietary systems to Claude. The `mcp-builder` Skill in the Anthropic catalog guides the development process. For Gamma SPA, GammaBot exposes two custom MCP servers: MCP Manuali SAP (semantic search + full-document reading of SAP manuals) and MCP TARIC (customs product classification). Remote MCP servers are configured in `claude-desktop-config.json` in the Developer settings; local MCP servers start automatically with Claude Desktop. [[wiki/sources/manuale-sesta-lezione]]

## Connections

- [[wiki/pages/claude-desktop]] — MCP extensions are configured within Claude Desktop settings
- [[wiki/pages/skills]] — skills and MCP connectors are two complementary extension mechanisms within plugins
- [[wiki/pages/plugins]] — MCP connectors are one of four plugin components
- [[wiki/pages/sub-agents]] — agents use MCP tools to delegate concrete actions

## Sources

- [[wiki/sources/manuale-prima-lezione]] — introductory coverage: tool/agent concept, built-in connectors, org-level access
- [[wiki/sources/manuale-sesta-lezione]] — client-server architecture, custom MCP servers, Skill vs MCP tradeoffs