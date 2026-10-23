# Hands-on — Evaluations, traces, red teaming, and security

[Overview](README.md) · [Theory](theory.md) · [Resources](resources.md)

## Build

A quality dashboard / test suite with Langfuse (or equivalent), pytest and an intentionally adversarial input set.

## Implementation workflow

1. Create a project directory and reproducible Python environment.
2. Define inputs, outputs, security boundaries, and expected errors.
3. Implement a minimal working version and run it locally.
4. Add tests for expected, edge, and failure cases.
5. Demonstrate or deploy the project as required.
6. Record benchmark results, known limitations, and next improvements.

## Required exercises

- [ ] Build **50+** test cases including normal, no-answer, stale-data and hostile-input cases.
- [ ] Trace model calls, retrieval, tool execution, failures and costs; redact sensitive data.
- [ ] Compare at least 2 changes against a fixed eval baseline.
- [ ] Follow **OWASP GenAI LLM Top 10 (2026)** and test prompt injection via retrieved documents and MCP tool results.
- [ ] Never trust natural-language model output as an authorization check; enforce permissions in code.

## Deliverables

- [ ] Working project with setup and run instructions.
- [ ] Reproducible tests or screenshots of results.
- [ ] No secrets or private information committed to Git.
- [ ] Notes on at least one failure and how it was resolved.

## Definition of done

> A regression test can catch a quality or security failure before redeployment.

[Course directory](../../README.md) · [← 13](../13_agent_interfaces_and_multimodal/README.md) · [15 →](../15_production_deployment/README.md)
