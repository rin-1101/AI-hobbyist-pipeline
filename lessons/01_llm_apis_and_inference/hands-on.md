# Hands-on — APIs, inference, and the model mental model

[Overview](README.md) · [Theory](theory.md) · [Resources](resources.md)

## Build

`ai-cli`, a terminal app that submits a prompt to a provider and records response time, token use where available, and errors.

## Implementation workflow

1. Create a project directory and reproducible Python environment.
2. Define inputs, outputs, security boundaries, and expected errors.
3. Implement a minimal working version and run it locally.
4. Add tests for expected, edge, and failure cases.
5. Demonstrate or deploy the project as required.
6. Record benchmark results, known limitations, and next improvements.

## Required exercises

- [ ] Make a successful SDK call without using a framework.
- [ ] Compare answers for five prompts across two available models.
- [ ] Implement timeouts, exception handling, and an explicit cost/spend limit for hosted APIs.
- [ ] Write down cases where the LLM confidently gives a wrong answer.

## Deliverables

- [ ] Working project with setup and run instructions.
- [ ] Reproducible tests or screenshots of results.
- [ ] No secrets or private information committed to Git.
- [ ] Notes on at least one failure and how it was resolved.

## Definition of done

> You can explain what runs locally, what runs at the provider, and what data leaves your device.

[Course directory](../../README.md) · [2 →](../02_context_and_structured_outputs/README.md)
