# 11 — Build and deploy your own MCP server

**Project:** `personal-knowledge-mcp`: a small MCP server exposing `search_notes`, `get_note`, and optionally `list_collections` to authorized clients.

## Lesson files

1. [Theory](theory.md) — key concepts and design questions.
2. [Hands-on](hands-on.md) — build instructions and success criteria.
3. [Resources](resources.md) — official documentation.

**Completion criterion:** You understand why a local stdio MCP server is deployed differently from a remotely hosted HTTP MCP server.

**2026 note:** MCP specification `2026-07-28` introduces a stateless core, multi-round-trip interactions, routing changes, and authorization hardening. For new remote deployments, prefer Streamable HTTP; legacy standalone SSE transport is not the recommended new default.

[Course directory](../../README.md) · [← 10](../10_durable_agents_and_memory/README.md) · [12 →](../12_multi_agent_and_a2a/README.md)
