# Hands-on — 05: Document ingestion and embedding fundamentals

[Lesson overview](README.md) · [Theory](theory.md) · [Resources](resources.md)

## Project brief

A pipeline that extracts 20-100 permitted PDFs/Markdown/DOCX files using Docling, creates chunks, and stores source metadata.

## Suggested implementation workflow

1. **Prepare:** Create a local project folder and virtual environment; record dependencies and model/runtime versions.
2. **Design:** Draw a minimal data-flow diagram, define inputs/outputs, and identify secrets or permissions.
3. **Build:** Implement the smallest end-to-end version of the project brief.
4. **Test:** Create success, failure, and edge-case scenarios; retain reproducible input/output examples.
5. **Deploy or demonstrate:** Run the project according to the lesson requirements; preserve a repeatable run command.
6. **Document:** Capture measurements, known limitations, and your solution to one debugging issue.

## Required tasks

- [ ] Preserve source filename/page/section and a stable document ID.
- [ ] Compare two chunking methods, including heading-aware chunking.
- [ ] Make re-ingestion idempotent (no duplicate chunks).
- [ ] Test malformed or scanned documents and record extraction failures.

## Deliverables

- [ ] Working code with a short setup guide (in a separate project repository or local folder).
- [ ] Reproducible run/deployment instructions, including any environment variables **by name only**.
- [ ] Evidence of tests or sample outputs; remove API keys and sensitive data.
- [ ] Short comparison of at least one design alternative or limitation.
- [ ] Learning notes: what succeeded, what failed, and what to improve.

## Definition of done

> Every retrievable chunk can be traced to an original document.

## Safety checklist

- [ ] No passwords, tokens, private documents, or personal data committed to Git.
- [ ] External write operations are disabled or explicitly approved when applicable.
- [ ] Failures are handled clearly rather than silently ignored.

[Course index](../../README.md) · [Previous: 04](../04/README.md) · [Next: 06](../06/README.md)
