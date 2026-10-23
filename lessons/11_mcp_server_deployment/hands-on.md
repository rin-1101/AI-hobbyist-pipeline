# Hands-on — Build and deploy your own MCP server

[Overview](README.md) · [Theory](theory.md) · [Resources](resources.md)

## Build

`personal-knowledge-mcp`: a small MCP server exposing `search_notes`, `get_note`, and optionally `list_collections` to authorized clients.

## Implementation workflow

1. Create a project directory and reproducible Python environment.
2. Define inputs, outputs, security boundaries, and expected errors.
3. Implement a minimal working version and run it locally.
4. Add tests for expected, edge, and failure cases.
5. Demonstrate or deploy the project as required.
6. Record benchmark results, known limitations, and next improvements.

## Required exercises

- [ ] Use the **official MCP Python SDK v2** (follow its current API, not old v1 tutorial snippets).
- [ ] Start with local `stdio` and test with an MCP Inspector or compatible client.
- [ ] Expose the same *read-only* capabilities over Streamable HTTP as a service with a `/mcp` endpoint.
- [ ] Dockerize the remote server; protect it with appropriate authentication/authorization before allowing remote access.
- [ ] Test input validation, denial of unauthorized requests, and minimal credentials.
- [ ] Make it usable by at least one real MCP-capable client, preferably two.

## Deliverables

- [ ] Working project with setup and run instructions.
- [ ] Reproducible tests or screenshots of results.
- [ ] No secrets or private information committed to Git.
- [ ] Notes on at least one failure and how it was resolved.

## Definition of done

> You understand why a local stdio MCP server is deployed differently from a remotely hosted HTTP MCP server.

**2026 note:** MCP specification `2026-07-28` introduces a stateless core, multi-round-trip interactions, routing changes, and authorization hardening. For new remote deployments, prefer Streamable HTTP; legacy standalone SSE transport is not the recommended new default.

[Course directory](../../README.md) · [← 10](../10_durable_agents_and_memory/README.md) · [12 →](../12_multi_agent_and_a2a/README.md)
