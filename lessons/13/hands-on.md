# Hands-on — 13: Agent user interfaces and multimodal experiments

[Lesson overview](README.md) · [Theory](theory.md) · [Resources](resources.md)

## Project brief

An agent console with streaming answers, cited retrieval, tool-call timeline, explicit approvals, and status/error states.

## Suggested implementation workflow

1. **Prepare:** Create a local project folder and virtual environment; record dependencies and model/runtime versions.
2. **Design:** Draw a minimal data-flow diagram, define inputs/outputs, and identify secrets or permissions.
3. **Build:** Implement the smallest end-to-end version of the project brief.
4. **Test:** Create success, failure, and edge-case scenarios; retain reproducible input/output examples.
5. **Deploy or demonstrate:** Run the project according to the lesson requirements; preserve a repeatable run command.
6. **Document:** Capture measurements, known limitations, and your solution to one debugging issue.

## Required tasks

- [ ] Implement streaming tool/progress events in UI.
- [ ] Experiment with **AG-UI 1.0** or a compatible frontend adapter (optional).
- [ ] Experiment with one modality: receipt/photo understanding, voice input, or an agent-driven UI widget.
- [ ] Stretch: Playwright browser interaction in a sandbox with confirmation before external actions.

## Deliverables

- [ ] Working code with a short setup guide (in a separate project repository or local folder).
- [ ] Reproducible run/deployment instructions, including any environment variables **by name only**.
- [ ] Evidence of tests or sample outputs; remove API keys and sensitive data.
- [ ] Short comparison of at least one design alternative or limitation.
- [ ] Learning notes: what succeeded, what failed, and what to improve.

## Definition of done

> Users can tell what the AI is doing and can stop/approve consequential operations.

## Safety checklist

- [ ] No passwords, tokens, private documents, or personal data committed to Git.
- [ ] External write operations are disabled or explicitly approved when applicable.
- [ ] Failures are handled clearly rather than silently ignored.

[Course index](../../README.md) · [Previous: 12](../12/README.md) · [Next: 14](../14/README.md)
