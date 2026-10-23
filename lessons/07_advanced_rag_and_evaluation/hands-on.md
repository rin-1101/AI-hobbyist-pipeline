# Hands-on — Advanced RAG, reranking, and retrieval evaluation

[Overview](README.md) · [Theory](theory.md) · [Resources](resources.md)

## Build

Improve Week 6's system using **hybrid retrieval + a reranker**.

## Implementation workflow

1. Create a project directory and reproducible Python environment.
2. Define inputs, outputs, security boundaries, and expected errors.
3. Implement a minimal working version and run it locally.
4. Add tests for expected, edge, and failure cases.
5. Demonstrate or deploy the project as required.
6. Record benchmark results, known limitations, and next improvements.

## Required exercises

- [ ] Add exact-term retrieval so IDs and error codes remain searchable.
- [ ] Compare 3 pipelines: dense-only, hybrid, hybrid + reranking.
- [ ] Build at least 30 query/expected-source evaluation cases.
- [ ] Record quality, p50/p95 latency, and cost across the alternatives.

## Deliverables

- [ ] Working project with setup and run instructions.
- [ ] Reproducible tests or screenshots of results.
- [ ] No secrets or private information committed to Git.
- [ ] Notes on at least one failure and how it was resolved.

## Definition of done

> You can justify whether more complex retrieval actually improves your own test data.

[Course directory](../../README.md) · [← 6](../06_basic_rag/README.md) · [8 →](../08_beyond_pdf_rag/README.md)
