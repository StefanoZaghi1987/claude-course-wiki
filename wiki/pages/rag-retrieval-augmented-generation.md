---
type: page
created: 2026-05-31
updated: 2026-05-31
tags: [rag, claude-projects, project-knowledge, ai4gamma-corso]
---

Retrieval-Augmented Generation (RAG) is the architecture that allows Claude's project knowledge base to scale to hundreds of documents without saturating the context window, by indexing files as semantic vectors and retrieving only relevant chunks per query.

## Overview

RAG is the technical foundation of Claude's project knowledge system. When files are uploaded to a project, they are not stored as raw text and injected wholesale into each conversation. Instead, they are processed into a vector database — a mathematical structure where semantically similar concepts are positioned near each other in multidimensional space. When a user sends a prompt, the system finds the chunks of those documents that are conceptually closest to the query and loads only those into the context window. The rest stays in the database, unused. This is why a project with 100 documents doesn't saturate the context: Claude sees only what is relevant.

## Key dimensions

### Vector database vs. full-text search

Traditional search (Ctrl+F, keyword grep) finds exact matches. A vector database performs semantic search: it finds documents that are conceptually related even if they use entirely different words. The memorable course analogy: "latte + uova = torta" — the database knows "milk" and "eggs" are near "cake" without any explicit link between the terms. This enables Claude to answer questions using documents that don't share vocabulary with the query. [[wiki/sources/manuale-seconda-lezione]]

### Chunking and selective retrieval

Documents are split into fragments (chunks) during indexing. Each chunk is independently vectorized. When a query arrives, semantic distance between the query and all indexed chunks is computed; the closest chunks are retrieved and loaded into the context window. This mechanism has two critical implications: (1) loading 100 documents doesn't fill the context — only relevant fragments do; (2) if you need Claude to analyze an entire specific document, you must request it explicitly: "Read the full document X from the project knowledge." The system will then load it whole for that interaction. [[wiki/sources/manuale-seconda-lezione]]

### File quality over quantity

Because retrieval precision depends on semantic signal quality, fewer well-structured relevant documents produce better results than a large indiscriminate dump. The recommended criteria for including a file in project knowledge: (1) official and validated, (2) relevant across all project conversations (not just one specific chat), (3) stable over time (infrequently updated). Temporary or chat-specific documents should be loaded at the chat level, not the project level. [[wiki/sources/manuale-seconda-lezione]]

### Building knowledge from Cowork output

An effective pattern for building project knowledge: use Cowork to generate structured analyses and summaries from online documentation or complex source documents, then load the generated Markdown artifact into the project knowledge base. This converts web-based or inaccessible documentation into stable, query-able project files. [[wiki/sources/manuale-seconda-lezione]]

## Connections

- [[wiki/pages/claude-projects]] — RAG is the retrieval architecture behind project Files
- [[wiki/pages/context-window]] — RAG prevents project files from saturating the context window
- [[wiki/pages/cowork]] — Cowork can be used to generate structured documents for loading into the knowledge base

## Sources

- [[wiki/sources/manuale-seconda-lezione]] — full technical explanation of vector database, chunking, and retrieval in Lesson 2
