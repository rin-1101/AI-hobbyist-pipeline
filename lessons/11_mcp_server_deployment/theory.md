# Theory — Lesson 11: Build and deploy your own MCP server

[Lesson overview](README.md) · [Hands-on project](hands-on.md) · [Resources](resources.md)

> **Crash course:** Read this first, then complete the [hands-on exercise](hands-on.md). The examples teach the concepts; they are not substitutes for running and testing the project.

## Learning goals

MCP **tools vs resources vs prompts**, MCP clients/hosts/servers, local stdio, remote Streamable HTTP, JSON-RPC, authentication, consent, network boundaries and least privilege.

## Crash course

### 1. What MCP standardizes

**Model Context Protocol (MCP)** is an interoperability layer through which AI applications discover and use external capabilities. Instead of custom-integrating each tool into every agent, an MCP **server** publishes capabilities through a shared protocol.

```text
AI host application
    |-- MCP client ---- local MCP server (stdio)
    +-- MCP client ---- remote MCP server (Streamable HTTP)
```

The **host** is the assistant application. It uses one or more **clients** to communicate with **servers**. An MCP server need not run a language model itself.

### 2. Tools, resources, and prompts

- **Tool:** A callable operation, such as looking up a document or creating a draft. It may have side effects.
- **Resource:** Data that a client can read, identified by a URI and possibly offered as context.
- **Prompt:** A reusable, server-provided prompt template or workflow starting point.

MCP uses structured protocol messages and typed schemas; in common implementations JSON-RPC carries operations across the transport.

### 3. Local vs remote deployment

**stdio:** The host launches a local subprocess and exchanges messages via its standard input/output. It is suitable for laptop tools; log to stderr to avoid corrupting the protocol stream.

**Streamable HTTP:** The server listens on an HTTP endpoint such as `/mcp`. Use this for remote deployment. Put it behind authentication, TLS, rate limits, origin/host protections, and appropriate network policy. Legacy SSE transports exist, but Streamable HTTP is recommended for new deployments.

The current v2 Python SDK exposes `MCPServer`. A minimal **read-only** demonstration is:

```python
from mcp.server import MCPServer

mcp = MCPServer("HobbyNotes")

@mcp.tool()
def search_notes(query: str) -> str:
    """Search a small sample note index."""
    return f"Example result for: {query}"

if __name__ == "__main__":
    mcp.run(transport="streamable-http", port=3001)
```

This uses a placeholder tool; replace the function body with a real, permission-checked lookup. For a locally launched server, use `mcp.run()` to select stdio.

### 4. Deployment boundaries and security

The model choosing a tool does **not** confer authorization. The server must independently validate arguments, authenticate callers, authorize data access, and avoid returning secrets. A remotely deployed MCP server is a network service: test DNS-rebinding/Host-header behavior, reverse-proxy headers, TLS, and access scopes against the documentation for your SDK version.

**Common mistakes:** copying older v1 SDK imports into v2 projects; treating resources like executable tools; exposing the HTTP endpoint without authentication; logging protocol messages to stdout under stdio; mounting the whole filesystem when only one folder is needed.

**Try it now:** Explain the difference between an MCP tool and an ordinary REST endpoint. Which components make it discoverable to an MCP-aware host?

## Knowledge check

- [ ] Can I explain the main idea to someone with basic Python knowledge?
- [ ] Can I draw the relevant data/control flow and identify trust boundaries?
- [ ] Can I describe when this technique is preferable to a simpler alternative?
- [ ] Can I name at least two failure modes and how I would detect them?
- [ ] Can I connect the concepts to this lesson's [hands-on deliverable](hands-on.md)?

## Continue learning

Use [resources.md](resources.md) for primary documentation, then implement the practical project in [hands-on.md](hands-on.md). See the [complete course syllabus](../../AI_Hobbyist_Roadmap_2026.md) for additional architecture and capstone ideas.

[Course directory](../../README.md) · [← Lesson 10](../10_durable_agents_and_memory/README.md) · [Lesson 12 →](../12_multi_agent_and_a2a/README.md)
