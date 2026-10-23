# Hands-on — 06: Basic Retrieval-Augmented Generation (RAG)

[Lesson overview](README.md) · [Theory](theory.md) · [Resources](resources.md)

## Project brief

`/ask` API + chat UI that answers questions over your document collection and cites specific source files/pages.

## Suggested implementation workflow

1. **Prepare:** Create a local project folder and virtual environment; record dependencies and model/runtime versions.
2. **Design:** Draw a minimal data-flow diagram, define inputs/outputs, and identify secrets or permissions.
3. **Build:** Implement the smallest end-to-end version of the project brief.
4. **Test:** Create success, failure, and edge-case scenarios; retain reproducible input/output examples.
5. **Deploy or demonstrate:** Run the project according to the lesson requirements; preserve a repeatable run command.
6. **Document:** Capture measurements, known limitations, and your solution to one debugging issue.

## Required tasks

- [ ] Store/retrieve chunks in Qdrant or pgvector.
- [ ] Compare `LLM alone` vs `vector retrieval + LLM` on 20 questions.
- [ ] Return citations and an explicit "insufficient evidence" answer when retrieval is poor.
- [ ] Deploy the RAG API and vector database with persistent volumes.

## Deliverables

- [ ] Working code with a short setup guide (in a separate project repository or local folder).
- [ ] Reproducible run/deployment instructions, including any environment variables **by name only**.
- [ ] Evidence of tests or sample outputs; remove API keys and sensitive data.
- [ ] Short comparison of at least one design alternative or limitation.
- [ ] Learning notes: what succeeded, what failed, and what to improve.

## Definition of done

> The system cites actual retrieved material; nonexistent sources are never fabricated.

## Safety checklist

- [ ] No passwords, tokens, private documents, or personal data committed to Git.
- [ ] External write operations are disabled or explicitly approved when applicable.
- [ ] Failures are handled clearly rather than silently ignored.

[Course index](../../README.md) · [Previous: 05](../05/README.md) · [Next: 07](../07/README.md)
