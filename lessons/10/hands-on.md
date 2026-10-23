# Hands-on — 10: Durable agents, state, memory, and Agent Skills

[Lesson overview](README.md) · [Theory](theory.md) · [Resources](resources.md)

## Project brief

Add task history, an approval queue, and resumable execution. Consider LangGraph when explicit state transitions are important.

## Suggested implementation workflow

1. **Prepare:** Create a local project folder and virtual environment; record dependencies and model/runtime versions.
2. **Design:** Draw a minimal data-flow diagram, define inputs/outputs, and identify secrets or permissions.
3. **Build:** Implement the smallest end-to-end version of the project brief.
4. **Test:** Create success, failure, and edge-case scenarios; retain reproducible input/output examples.
5. **Deploy or demonstrate:** Run the project according to the lesson requirements; preserve a repeatable run command.
6. **Document:** Capture measurements, known limitations, and your solution to one debugging issue.

## Required tasks

- [ ] Save execution/checkpoint state in persistent storage.
- [ ] Stop and restart the service mid-task; recover without repeating side effects.
- [ ] Implement one portable Agent Skill for a repeatable low-risk task.
- [ ] Test a bad memory entry and a malicious/untrusted skill instruction.

## Deliverables

- [ ] Working code with a short setup guide (in a separate project repository or local folder).
- [ ] Reproducible run/deployment instructions, including any environment variables **by name only**.
- [ ] Evidence of tests or sample outputs; remove API keys and sensitive data.
- [ ] Short comparison of at least one design alternative or limitation.
- [ ] Learning notes: what succeeded, what failed, and what to improve.

## Definition of done

> A failed task can resume safely and an audit trail explains its actions.

## Safety checklist

- [ ] No passwords, tokens, private documents, or personal data committed to Git.
- [ ] External write operations are disabled or explicitly approved when applicable.
- [ ] Failures are handled clearly rather than silently ignored.

[Course index](../../README.md) · [Previous: 09](../09/README.md) · [Next: 11](../11/README.md)
