# Hands-on — Basic Retrieval-Augmented Generation (RAG)

[Overview](README.md) · [Theory](theory.md) · [Resources](resources.md)

## Build

`/ask` API + chat UI that answers questions over your document collection and cites specific source files/pages.

## Implementation workflow

1. Create a project directory and reproducible Python environment.
2. Define inputs, outputs, security boundaries, and expected errors.
3. Implement a minimal working version and run it locally.
4. Add tests for expected, edge, and failure cases.
5. Demonstrate or deploy the project as required.
6. Record benchmark results, known limitations, and next improvements.

## Required exercises

- [ ] Store/retrieve chunks in Qdrant or pgvector.
- [ ] Compare `LLM alone` vs `vector retrieval + LLM` on 20 questions.
- [ ] Return citations and an explicit "insufficient evidence" answer when retrieval is poor.
- [ ] Deploy the RAG API and vector database with persistent volumes.

## Deliverables

- [ ] Working project with setup and run instructions.
- [ ] Reproducible tests or screenshots of results.
- [ ] No secrets or private information committed to Git.
- [ ] Notes on at least one failure and how it was resolved.

## Definition of done

> The system cites actual retrieved material; nonexistent sources are never fabricated.

[Course directory](../../README.md) · [← 5](../05_document_ingestion_and_embeddings/README.md) · [7 →](../07_advanced_rag_and_evaluation/README.md)
