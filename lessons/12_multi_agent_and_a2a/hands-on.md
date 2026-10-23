# Hands-on — Multi-agent patterns and agent communication

[Overview](README.md) · [Theory](theory.md) · [Resources](resources.md)

## Build

A **Research Agent** delegates to a **Document Agent** and a **Data Agent**, which return sourced results for the parent to synthesize.

## Implementation workflow

1. Create a project directory and reproducible Python environment.
2. Define inputs, outputs, security boundaries, and expected errors.
3. Implement a minimal working version and run it locally.
4. Add tests for expected, edge, and failure cases.
5. Demonstrate or deploy the project as required.
6. Record benchmark results, known limitations, and next improvements.

## Required exercises

- [ ] Implement a two-agent handoff locally first.
- [ ] Compare with the equivalent single agent; retain multiple agents only if helpful.
- [ ] Stretch: expose one agent via the **A2A protocol** and invoke it from a separate process.
- [ ] Log the reason for delegation, result and failure handling.

## Deliverables

- [ ] Working project with setup and run instructions.
- [ ] Reproducible tests or screenshots of results.
- [ ] No secrets or private information committed to Git.
- [ ] Notes on at least one failure and how it was resolved.

## Definition of done

> You know MCP connects agents to **tools/data**, while A2A connects **agents to other agents**.

[Course directory](../../README.md) · [← 11](../11_mcp_server_deployment/README.md) · [13 →](../13_agent_interfaces_and_multimodal/README.md)
