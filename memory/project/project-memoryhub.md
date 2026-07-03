---
id: project-memoryhub
title: MemoryHub
type: project
description: Content-agnostic engine over a markdown memory store with schema-validated writes and an MCP server.
tags: [python, tooling, knowledge-base, mcp, ai-engineering]
status: active
visibility: public
created: 2026-07-02
updated: 2026-07-03
stack: [Python, Pydantic, Typer, FastMCP, LanceDB, pytest]
url: https://github.com/jkarancs/MemoryHub
role: Author (spec-driven, built with AI agents)
related: [skill-mcp-development, skill-rag, skill-python, skill-embeddings-note]
source: agent
---

A reusable Python engine over a markdown memory store with YAML frontmatter: schema profiles,
Pydantic-validated guarded atomic writes, full-text query, a Typer CLI, and a FastMCP stdio server
for agent access. Content lives in separate repos (private + public export). Phases 0-2 are
implemented (engine core + MCP server); embeddings/LanceDB hybrid search and public export are
planned. Notably, the engine itself was built by AI agents from written multi-phase specs - a
concrete demonstration of the spec-driven agentic methodology.
