# Hands-on — 12: Multi-agent patterns and agent communication

[Lesson overview](README.md) · [Theory](theory.md) · [Resources](resources.md)

## Project brief

A **Research Agent** delegates to a **Document Agent** and a **Data Agent**, which return sourced results for the parent to synthesize.

## Suggested implementation workflow

1. **Prepare:** Create a local project folder and virtual environment; record dependencies and model/runtime versions.
2. **Design:** Draw a minimal data-flow diagram, define inputs/outputs, and identify secrets or permissions.
3. **Build:** Implement the smallest end-to-end version of the project brief.
4. **Test:** Create success, failure, and edge-case scenarios; retain reproducible input/output examples.
5. **Deploy or demonstrate:** Run the project according to the lesson requirements; preserve a repeatable run command.
6. **Document:** Capture measurements, known limitations, and your solution to one debugging issue.

## Required tasks

- [ ] Implement a two-agent handoff locally first.
- [ ] Compare with the equivalent single agent; retain multiple agents only if helpful.
- [ ] Stretch: expose one agent via the **A2A protocol** and invoke it from a separate process.
- [ ] Log the reason for delegation, result and failure handling.

## Deliverables

- [ ] Working code with a short setup guide (in a separate project repository or local folder).
- [ ] Reproducible run/deployment instructions, including any environment variables **by name only**.
- [ ] Evidence of tests or sample outputs; remove API keys and sensitive data.
- [ ] Short comparison of at least one design alternative or limitation.
- [ ] Learning notes: what succeeded, what failed, and what to improve.

## Definition of done

> You know MCP connects agents to **tools/data**, while A2A connects **agents to other agents**.

### Phase D - Experiences, quality, security, deployment (Weeks 13-16)

## Safety checklist

- [ ] No passwords, tokens, private documents, or personal data committed to Git.
- [ ] External write operations are disabled or explicitly approved when applicable.
- [ ] Failures are handled clearly rather than silently ignored.

[Course index](../../README.md) · [Previous: 11](../11/README.md) · [Next: 13](../13/README.md)
