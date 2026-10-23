# Hands-on — Agent user interfaces and multimodal experiments

[Overview](README.md) · [Theory](theory.md) · [Resources](resources.md)

## Build

An agent console with streaming answers, cited retrieval, tool-call timeline, explicit approvals, and status/error states.

## Implementation workflow

1. Create a project directory and reproducible Python environment.
2. Define inputs, outputs, security boundaries, and expected errors.
3. Implement a minimal working version and run it locally.
4. Add tests for expected, edge, and failure cases.
5. Demonstrate or deploy the project as required.
6. Record benchmark results, known limitations, and next improvements.

## Required exercises

- [ ] Implement streaming tool/progress events in UI.
- [ ] Experiment with **AG-UI 1.0** or a compatible frontend adapter (optional).
- [ ] Experiment with one modality: receipt/photo understanding, voice input, or an agent-driven UI widget.
- [ ] Stretch: Playwright browser interaction in a sandbox with confirmation before external actions.

## Deliverables

- [ ] Working project with setup and run instructions.
- [ ] Reproducible tests or screenshots of results.
- [ ] No secrets or private information committed to Git.
- [ ] Notes on at least one failure and how it was resolved.

## Definition of done

> Users can tell what the AI is doing and can stop/approve consequential operations.

[Course directory](../../README.md) · [← 12](../12_multi_agent_and_a2a/README.md) · [14 →](../14_evals_tracing_and_security/README.md)
