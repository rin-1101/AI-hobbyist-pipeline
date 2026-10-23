# Hands-on — Document ingestion and embedding fundamentals

[Overview](README.md) · [Theory](theory.md) · [Resources](resources.md)

## Build

A pipeline that extracts 20-100 permitted PDFs/Markdown/DOCX files using Docling, creates chunks, and stores source metadata.

## Implementation workflow

1. Create a project directory and reproducible Python environment.
2. Define inputs, outputs, security boundaries, and expected errors.
3. Implement a minimal working version and run it locally.
4. Add tests for expected, edge, and failure cases.
5. Demonstrate or deploy the project as required.
6. Record benchmark results, known limitations, and next improvements.

## Required exercises

- [ ] Preserve source filename/page/section and a stable document ID.
- [ ] Compare two chunking methods, including heading-aware chunking.
- [ ] Make re-ingestion idempotent (no duplicate chunks).
- [ ] Test malformed or scanned documents and record extraction failures.

## Deliverables

- [ ] Working project with setup and run instructions.
- [ ] Reproducible tests or screenshots of results.
- [ ] No secrets or private information committed to Git.
- [ ] Notes on at least one failure and how it was resolved.

## Definition of done

> Every retrievable chunk can be traced to an original document.

[Course directory](../../README.md) · [← 4](../04_deployable_ai_service/README.md) · [6 →](../06_basic_rag/README.md)
