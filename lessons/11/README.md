# 11 — Build and deploy your own MCP server

**Phase:** Agents and MCP · **Estimated effort:** 6–10 hours

## Goal

`personal-knowledge-mcp`: a small MCP server exposing `search_notes`, `get_note`, and optionally `list_collections` to authorized clients.

## Study and build

1. [Theory](theory.md) — underlying concepts, trade-offs, and understanding checks.
2. [Hands-on](hands-on.md) — practical project, implementation steps, testing and acceptance checklist.
3. [Resources](resources.md) — official documentation and study pointers.

## Exit criteria

You understand why a local stdio MCP server is deployed differently from a remotely hosted HTTP MCP server.

**2026 note:** MCP specification `2026-07-28` introduces a stateless core, multi-round-trip interactions, routing changes, and authorization hardening. For new remote deployments, prefer Streamable HTTP; legacy standalone SSE transport is not the recommended new default.

[Course index](../../README.md) · [Previous: 10](../10/README.md) · [Next: 12](../12/README.md)
