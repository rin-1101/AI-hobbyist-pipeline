# Hands-on — Beyond simple PDF RAG

[Overview](README.md) · [Theory](theory.md) · [Resources](resources.md)

## Build

A router that can retrieve from **documents** or a **read-only SQLite/PostgreSQL dataset** with parameterized or tightly validated queries.

## Implementation workflow

1. Create a project directory and reproducible Python environment.
2. Define inputs, outputs, security boundaries, and expected errors.
3. Implement a minimal working version and run it locally.
4. Add tests for expected, edge, and failure cases.
5. Demonstrate or deploy the project as required.
6. Record benchmark results, known limitations, and next improvements.

## Required exercises

- [ ] Use a restricted database user; never allow generic SQL execution against a real production database.
- [ ] Show the source path (document citation or query/data reference) with each answer.
- [ ] Experiment with one of: table-aware RAG, OCR images, graph-based retrieval, or multi-hop questions.
- [ ] Add a refusal/fallback for questions outside available data.

## Deliverables

- [ ] Working project with setup and run instructions.
- [ ] Reproducible tests or screenshots of results.
- [ ] No secrets or private information committed to Git.
- [ ] Notes on at least one failure and how it was resolved.

## Definition of done

> You understand when RAG, SQL, or a plain deterministic API is the best answer.

[Course directory](../../README.md) · [← 7](../07_advanced_rag_and_evaluation/README.md) · [9 →](../09_tool_calling_and_agent_loops/README.md)
