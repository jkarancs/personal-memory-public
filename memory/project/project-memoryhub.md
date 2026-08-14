---
id: project-memoryhub
title: MemoryHub
type: project
description: Content-agnostic engine over a markdown memory store with schema-validated writes and an MCP server.
tags: [python, tooling, knowledge-base, mcp, ai-engineering]
status: active
visibility: public
created: 2026-07-02
updated: 2026-08-10
stack: [Python, Pydantic, Typer, FastMCP, LanceDB, pytest]
url: https://github.com/jkarancs/MemoryHub
role: Author (spec-driven, built with AI agents)
related: [skill-mcp-development, skill-rag, skill-python, skill-embeddings-note]
source: agent
---

A reusable Python engine over a markdown memory store with YAML frontmatter: schema profiles,
Pydantic-validated guarded atomic writes, hybrid semantic search (BAAI/bge-m3 embeddings +
LanceDB + full-text fallback), a Typer CLI, and a FastMCP server for agent access. Content
lives in separate repos (private + public export). Notably, the engine itself was built by AI
agents from written multi-phase specs - a concrete demonstration of the spec-driven agentic
methodology.

Deployment (since 2026-07-18): the MCP server runs as a persistent background HTTP daemon
(streamable HTTP on a loopback port) rather than a per-session stdio process. A launcher script
starts it once, singleton-guarded (port bind + pid file), and keeps the embedding model warm in
one shared process - agent sessions attach to the running daemon instead of each paying a ~45s
model load and ~1.4 GB of RAM.
