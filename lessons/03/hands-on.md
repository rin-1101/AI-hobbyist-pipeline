# Hands-on — 03: Local models and inference servers

[Lesson overview](README.md) · [Theory](theory.md) · [Resources](resources.md)

## Project brief

A model selector that switches between a hosted model and a small local Ollama model using a stable application interface.

## Suggested implementation workflow

1. **Prepare:** Create a local project folder and virtual environment; record dependencies and model/runtime versions.
2. **Design:** Draw a minimal data-flow diagram, define inputs/outputs, and identify secrets or permissions.
3. **Build:** Implement the smallest end-to-end version of the project brief.
4. **Test:** Create success, failure, and edge-case scenarios; retain reproducible input/output examples.
5. **Deploy or demonstrate:** Run the project according to the lesson requirements; preserve a repeatable run command.
6. **Document:** Capture measurements, known limitations, and your solution to one debugging issue.

## Required tasks

- [ ] Run a model with Ollama and call its local HTTP API.
- [ ] Benchmark 10 identical tasks across local/cloud models.
- [ ] Document data privacy, quality, speed, and running costs.
- [ ] Stretch: test llama.cpp; explore vLLM only if hardware permits.

## Deliverables

- [ ] Working code with a short setup guide (in a separate project repository or local folder).
- [ ] Reproducible run/deployment instructions, including any environment variables **by name only**.
- [ ] Evidence of tests or sample outputs; remove API keys and sensitive data.
- [ ] Short comparison of at least one design alternative or limitation.
- [ ] Learning notes: what succeeded, what failed, and what to improve.

## Definition of done

> The application can change its model without rewriting core business logic.

## Safety checklist

- [ ] No passwords, tokens, private documents, or personal data committed to Git.
- [ ] External write operations are disabled or explicitly approved when applicable.
- [ ] Failures are handled clearly rather than silently ignored.

[Course index](../../README.md) · [Previous: 02](../02/README.md) · [Next: 04](../04/README.md)
