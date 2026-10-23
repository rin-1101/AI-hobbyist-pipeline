# Hands-on — Local models and inference servers

[Overview](README.md) · [Theory](theory.md) · [Resources](resources.md)

## Build

A model selector that switches between a hosted model and a small local Ollama model using a stable application interface.

## Implementation workflow

1. Create a project directory and reproducible Python environment.
2. Define inputs, outputs, security boundaries, and expected errors.
3. Implement a minimal working version and run it locally.
4. Add tests for expected, edge, and failure cases.
5. Demonstrate or deploy the project as required.
6. Record benchmark results, known limitations, and next improvements.

## Required exercises

- [ ] Run a model with Ollama and call its local HTTP API.
- [ ] Benchmark 10 identical tasks across local/cloud models.
- [ ] Document data privacy, quality, speed, and running costs.
- [ ] Stretch: test llama.cpp; explore vLLM only if hardware permits.

## Deliverables

- [ ] Working project with setup and run instructions.
- [ ] Reproducible tests or screenshots of results.
- [ ] No secrets or private information committed to Git.
- [ ] Notes on at least one failure and how it was resolved.

## Definition of done

> The application can change its model without rewriting core business logic.

[Course directory](../../README.md) · [← 2](../02_context_and_structured_outputs/README.md) · [4 →](../04_deployable_ai_service/README.md)
