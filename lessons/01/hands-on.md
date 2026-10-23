# Hands-on — 01: APIs, inference, and the model mental model

[Lesson overview](README.md) · [Theory](theory.md) · [Resources](resources.md)

## Project brief

`ai-cli`, a terminal app that submits a prompt to a provider and records response time, token use where available, and errors.

## Suggested implementation workflow

1. **Prepare:** Create a local project folder and virtual environment; record dependencies and model/runtime versions.
2. **Design:** Draw a minimal data-flow diagram, define inputs/outputs, and identify secrets or permissions.
3. **Build:** Implement the smallest end-to-end version of the project brief.
4. **Test:** Create success, failure, and edge-case scenarios; retain reproducible input/output examples.
5. **Deploy or demonstrate:** Run the project according to the lesson requirements; preserve a repeatable run command.
6. **Document:** Capture measurements, known limitations, and your solution to one debugging issue.

## Required tasks

- [ ] Make a successful SDK call without using a framework.
- [ ] Compare answers for five prompts across two available models.
- [ ] Implement timeouts, exception handling, and an explicit cost/spend limit for hosted APIs.
- [ ] Write down cases where the LLM confidently gives a wrong answer.

## Deliverables

- [ ] Working code with a short setup guide (in a separate project repository or local folder).
- [ ] Reproducible run/deployment instructions, including any environment variables **by name only**.
- [ ] Evidence of tests or sample outputs; remove API keys and sensitive data.
- [ ] Short comparison of at least one design alternative or limitation.
- [ ] Learning notes: what succeeded, what failed, and what to improve.

## Definition of done

> You can explain what runs locally, what runs at the provider, and what data leaves your device.

## Safety checklist

- [ ] No passwords, tokens, private documents, or personal data committed to Git.
- [ ] External write operations are disabled or explicitly approved when applicable.
- [ ] Failures are handled clearly rather than silently ignored.

[Course index](../../README.md) · [Next: 02](../02/README.md)
