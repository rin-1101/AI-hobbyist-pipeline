# Hands-on — 02: Context engineering, structured outputs, and deterministic boundaries

[Lesson overview](README.md) · [Theory](theory.md) · [Resources](resources.md)

## Project brief

A natural-language task extractor that returns validated structured data (`title`, `priority`, `due_date`, `confidence`) without executing tasks.

## Suggested implementation workflow

1. **Prepare:** Create a local project folder and virtual environment; record dependencies and model/runtime versions.
2. **Design:** Draw a minimal data-flow diagram, define inputs/outputs, and identify secrets or permissions.
3. **Build:** Implement the smallest end-to-end version of the project brief.
4. **Test:** Create success, failure, and edge-case scenarios; retain reproducible input/output examples.
5. **Deploy or demonstrate:** Run the project according to the lesson requirements; preserve a repeatable run command.
6. **Document:** Capture measurements, known limitations, and your solution to one debugging issue.

## Required tasks

- [ ] Define Pydantic output models and reject invalid results.
- [ ] Test ambiguous and adversarial inputs.
- [ ] Compare long-vs-short prompts and document the tradeoffs.
- [ ] Add golden-case automated tests (minimum 15).

## Deliverables

- [ ] Working code with a short setup guide (in a separate project repository or local folder).
- [ ] Reproducible run/deployment instructions, including any environment variables **by name only**.
- [ ] Evidence of tests or sample outputs; remove API keys and sensitive data.
- [ ] Short comparison of at least one design alternative or limitation.
- [ ] Learning notes: what succeeded, what failed, and what to improve.

## Definition of done

> Your app never trusts unvalidated AI-generated JSON as an instruction.

## Safety checklist

- [ ] No passwords, tokens, private documents, or personal data committed to Git.
- [ ] External write operations are disabled or explicitly approved when applicable.
- [ ] Failures are handled clearly rather than silently ignored.

[Course index](../../README.md) · [Previous: 01](../01/README.md) · [Next: 03](../03/README.md)
