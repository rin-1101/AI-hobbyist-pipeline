# Hands-on — 09: Function calling and the single-agent loop

[Lesson overview](README.md) · [Theory](theory.md) · [Resources](resources.md)

## Project brief

A personal assistant with 2-3 **read-only** tools (search documents, query test SQL data, read a calendar fixture or local task list).

## Suggested implementation workflow

1. **Prepare:** Create a local project folder and virtual environment; record dependencies and model/runtime versions.
2. **Design:** Draw a minimal data-flow diagram, define inputs/outputs, and identify secrets or permissions.
3. **Build:** Implement the smallest end-to-end version of the project brief.
4. **Test:** Create success, failure, and edge-case scenarios; retain reproducible input/output examples.
5. **Deploy or demonstrate:** Run the project according to the lesson requirements; preserve a repeatable run command.
6. **Document:** Capture measurements, known limitations, and your solution to one debugging issue.

## Required tasks

- [ ] Implement and inspect tool calls without a framework once.
- [ ] Rebuild using either OpenAI Agents SDK or Pydantic AI.
- [ ] Cap tool calls, execution time, and token budget.
- [ ] Force a human approval gate before any write/delete/email action.

## Deliverables

- [ ] Working code with a short setup guide (in a separate project repository or local folder).
- [ ] Reproducible run/deployment instructions, including any environment variables **by name only**.
- [ ] Evidence of tests or sample outputs; remove API keys and sensitive data.
- [ ] Short comparison of at least one design alternative or limitation.
- [ ] Learning notes: what succeeded, what failed, and what to improve.

## Definition of done

> You can follow a trace and explain every tool decision and effect.

## Safety checklist

- [ ] No passwords, tokens, private documents, or personal data committed to Git.
- [ ] External write operations are disabled or explicitly approved when applicable.
- [ ] Failures are handled clearly rather than silently ignored.

[Course index](../../README.md) · [Previous: 08](../08/README.md) · [Next: 10](../10/README.md)
