# Hands-on — 08: Beyond simple PDF RAG

[Lesson overview](README.md) · [Theory](theory.md) · [Resources](resources.md)

## Project brief

A router that can retrieve from **documents** or a **read-only SQLite/PostgreSQL dataset** with parameterized or tightly validated queries.

## Suggested implementation workflow

1. **Prepare:** Create a local project folder and virtual environment; record dependencies and model/runtime versions.
2. **Design:** Draw a minimal data-flow diagram, define inputs/outputs, and identify secrets or permissions.
3. **Build:** Implement the smallest end-to-end version of the project brief.
4. **Test:** Create success, failure, and edge-case scenarios; retain reproducible input/output examples.
5. **Deploy or demonstrate:** Run the project according to the lesson requirements; preserve a repeatable run command.
6. **Document:** Capture measurements, known limitations, and your solution to one debugging issue.

## Required tasks

- [ ] Use a restricted database user; never allow generic SQL execution against a real production database.
- [ ] Show the source path (document citation or query/data reference) with each answer.
- [ ] Experiment with one of: table-aware RAG, OCR images, graph-based retrieval, or multi-hop questions.
- [ ] Add a refusal/fallback for questions outside available data.

## Deliverables

- [ ] Working code with a short setup guide (in a separate project repository or local folder).
- [ ] Reproducible run/deployment instructions, including any environment variables **by name only**.
- [ ] Evidence of tests or sample outputs; remove API keys and sensitive data.
- [ ] Short comparison of at least one design alternative or limitation.
- [ ] Learning notes: what succeeded, what failed, and what to improve.

## Definition of done

> You understand when RAG, SQL, or a plain deterministic API is the best answer.

### Phase C - Agents, MCP, and interoperability (Weeks 9-12)

## Safety checklist

- [ ] No passwords, tokens, private documents, or personal data committed to Git.
- [ ] External write operations are disabled or explicitly approved when applicable.
- [ ] Failures are handled clearly rather than silently ignored.

[Course index](../../README.md) · [Previous: 07](../07/README.md) · [Next: 09](../09/README.md)
