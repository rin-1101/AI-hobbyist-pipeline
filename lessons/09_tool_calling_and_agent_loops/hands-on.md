# Hands-on — Function calling and the single-agent loop

[Overview](README.md) · [Theory](theory.md) · [Resources](resources.md)

## Build

A personal assistant with 2-3 **read-only** tools (search documents, query test SQL data, read a calendar fixture or local task list).

## Implementation workflow

1. Create a project directory and reproducible Python environment.
2. Define inputs, outputs, security boundaries, and expected errors.
3. Implement a minimal working version and run it locally.
4. Add tests for expected, edge, and failure cases.
5. Demonstrate or deploy the project as required.
6. Record benchmark results, known limitations, and next improvements.

## Required exercises

- [ ] Implement and inspect tool calls without a framework once.
- [ ] Rebuild using either OpenAI Agents SDK or Pydantic AI.
- [ ] Cap tool calls, execution time, and token budget.
- [ ] Force a human approval gate before any write/delete/email action.

## Deliverables

- [ ] Working project with setup and run instructions.
- [ ] Reproducible tests or screenshots of results.
- [ ] No secrets or private information committed to Git.
- [ ] Notes on at least one failure and how it was resolved.

## Definition of done

> You can follow a trace and explain every tool decision and effect.

[Course directory](../../README.md) · [← 8](../08_beyond_pdf_rag/README.md) · [10 →](../10_durable_agents_and_memory/README.md)
