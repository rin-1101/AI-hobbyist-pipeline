#### Week 11 - Build and deploy your own MCP server
**Understand:** MCP **tools vs resources vs prompts**, MCP clients/hosts/servers, local stdio, remote Streamable HTTP, JSON-RPC, authentication, consent, network boundaries and least privilege.

**Build:** `personal-knowledge-mcp`: a small MCP server exposing `search_notes`, `get_note`, and optionally `list_collections` to authorized clients.

**Do:**
- [ ] Use the **official MCP Python SDK v2** (follow its current API, not old v1 tutorial snippets).
- [ ] Start with local `stdio` and test with an MCP Inspector or compatible client.
- [ ] Expose the same *read-only* capabilities over Streamable HTTP as a service with a `/mcp` endpoint.
- [ ] Dockerize the remote server; protect it with appropriate authentication/authorization before allowing remote access.
- [ ] Test input validation, denial of unauthorized requests, and minimal credentials.
- [ ] Make it usable by at least one real MCP-capable client, preferably two.

**Exit check:** You understand why a local stdio MCP server is deployed differently from a remotely hosted HTTP MCP server.

**2026 note:** MCP specification `2026-07-28` introduces a stateless core, multi-round-trip interactions, routing changes, and authorization hardening. For new remote deployments, prefer Streamable HTTP; legacy standalone SSE transport is not the recommended new default.

> **Phase:** Agents & Protocols | **Week:** 11 of 16 | **Pace:** approx. 6–10 hours

---

## Lesson workflow

1. Read the **Understand** topics and visit the [official resources](../../AI_Hobbyist_Roadmap_2026.md#7-official-learning-resources-verified-october-2026).
2. Build the **Build** project in a separate Git repository or a local working directory.
3. Complete the **Do** checklist and retain screenshots, tests, or benchmark results as evidence.
4. Meet the **Exit check** before moving to the next lesson.

## Your learning notes

- **What I learned:** _Add your notes._
- **What I built:** _Link to your code or deployment._
- **Biggest blocker:** _Record the problem and the fix._
- **Evidence:** _Link to tests, screenshots, logs, or benchmark runs._

---

[← Course home](../../README.md) · [← Week 10](../10-durable-agents-and-memory/README.md) · [Week 12 →](../12-multi-agent-and-a2a/README.md)
