# Hands-on — Context engineering, structured outputs, and deterministic boundaries

[Overview](README.md) · [Theory](theory.md) · [Resources](resources.md)

## Build

A natural-language task extractor that returns validated structured data (`title`, `priority`, `due_date`, `confidence`) without executing tasks.

## Implementation workflow

1. Create a project directory and reproducible Python environment.
2. Define inputs, outputs, security boundaries, and expected errors.
3. Implement a minimal working version and run it locally.
4. Add tests for expected, edge, and failure cases.
5. Demonstrate or deploy the project as required.
6. Record benchmark results, known limitations, and next improvements.

## Required exercises

- [ ] Define Pydantic output models and reject invalid results.
- [ ] Test ambiguous and adversarial inputs.
- [ ] Compare long-vs-short prompts and document the tradeoffs.
- [ ] Add golden-case automated tests (minimum 15).

## Deliverables

- [ ] Working project with setup and run instructions.
- [ ] Reproducible tests or screenshots of results.
- [ ] No secrets or private information committed to Git.
- [ ] Notes on at least one failure and how it was resolved.

## Definition of done

> Your app never trusts unvalidated AI-generated JSON as an instruction.

[Course directory](../../README.md) · [← 1](../01_llm_apis_and_inference/README.md) · [3 →](../03_local_models/README.md)
