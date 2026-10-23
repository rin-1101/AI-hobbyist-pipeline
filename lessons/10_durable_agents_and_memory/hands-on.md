# Hands-on — Durable agents, state, memory, and Agent Skills

[Overview](README.md) · [Theory](theory.md) · [Resources](resources.md)

## Build

Add task history, an approval queue, and resumable execution. Consider LangGraph when explicit state transitions are important.

## Implementation workflow

1. Create a project directory and reproducible Python environment.
2. Define inputs, outputs, security boundaries, and expected errors.
3. Implement a minimal working version and run it locally.
4. Add tests for expected, edge, and failure cases.
5. Demonstrate or deploy the project as required.
6. Record benchmark results, known limitations, and next improvements.

## Required exercises

- [ ] Save execution/checkpoint state in persistent storage.
- [ ] Stop and restart the service mid-task; recover without repeating side effects.
- [ ] Implement one portable Agent Skill for a repeatable low-risk task.
- [ ] Test a bad memory entry and a malicious/untrusted skill instruction.

## Deliverables

- [ ] Working project with setup and run instructions.
- [ ] Reproducible tests or screenshots of results.
- [ ] No secrets or private information committed to Git.
- [ ] Notes on at least one failure and how it was resolved.

## Definition of done

> A failed task can resume safely and an audit trail explains its actions.

[Course directory](../../README.md) · [← 9](../09_tool_calling_and_agent_loops/README.md) · [11 →](../11_mcp_server_deployment/README.md)
