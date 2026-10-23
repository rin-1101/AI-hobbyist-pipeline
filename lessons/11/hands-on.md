# Hands-on — 11: Build and deploy your own MCP server

[Lesson overview](README.md) · [Theory](theory.md) · [Resources](resources.md)

## Project brief

`personal-knowledge-mcp`: a small MCP server exposing `search_notes`, `get_note`, and optionally `list_collections` to authorized clients.

## Suggested implementation workflow

1. **Prepare:** Create a local project folder and virtual environment; record dependencies and model/runtime versions.
2. **Design:** Draw a minimal data-flow diagram, define inputs/outputs, and identify secrets or permissions.
3. **Build:** Implement the smallest end-to-end version of the project brief.
4. **Test:** Create success, failure, and edge-case scenarios; retain reproducible input/output examples.
5. **Deploy or demonstrate:** Run the project according to the lesson requirements; preserve a repeatable run command.
6. **Document:** Capture measurements, known limitations, and your solution to one debugging issue.

## Required tasks

- [ ] Use the **official MCP Python SDK v2** (follow its current API, not old v1 tutorial snippets).
- [ ] Start with local `stdio` and test with an MCP Inspector or compatible client.
- [ ] Expose the same *read-only* capabilities over Streamable HTTP as a service with a `/mcp` endpoint.
- [ ] Dockerize the remote server; protect it with appropriate authentication/authorization before allowing remote access.
- [ ] Test input validation, denial of unauthorized requests, and minimal credentials.
- [ ] Make it usable by at least one real MCP-capable client, preferably two.

## Deliverables

- [ ] Working code with a short setup guide (in a separate project repository or local folder).
- [ ] Reproducible run/deployment instructions, including any environment variables **by name only**.
- [ ] Evidence of tests or sample outputs; remove API keys and sensitive data.
- [ ] Short comparison of at least one design alternative or limitation.
- [ ] Learning notes: what succeeded, what failed, and what to improve.

## Definition of done

> You understand why a local stdio MCP server is deployed differently from a remotely hosted HTTP MCP server.

**2026 note:** MCP specification `2026-07-28` introduces a stateless core, multi-round-trip interactions, routing changes, and authorization hardening. For new remote deployments, prefer Streamable HTTP; legacy standalone SSE transport is not the recommended new default.

## Safety checklist

- [ ] No passwords, tokens, private documents, or personal data committed to Git.
- [ ] External write operations are disabled or explicitly approved when applicable.
- [ ] Failures are handled clearly rather than silently ignored.

[Course index](../../README.md) · [Previous: 10](../10/README.md) · [Next: 12](../12/README.md)
