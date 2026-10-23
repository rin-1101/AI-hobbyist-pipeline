# Hands-on — 04: Your first deployable AI service

[Lesson overview](README.md) · [Theory](theory.md) · [Resources](resources.md)

## Project brief

A minimal web chat interface backed by `POST /chat` or a streaming endpoint.

## Suggested implementation workflow

1. **Prepare:** Create a local project folder and virtual environment; record dependencies and model/runtime versions.
2. **Design:** Draw a minimal data-flow diagram, define inputs/outputs, and identify secrets or permissions.
3. **Build:** Implement the smallest end-to-end version of the project brief.
4. **Test:** Create success, failure, and edge-case scenarios; retain reproducible input/output examples.
5. **Deploy or demonstrate:** Run the project according to the lesson requirements; preserve a repeatable run command.
6. **Document:** Capture measurements, known limitations, and your solution to one debugging issue.

## Required tasks

- [ ] Add `/health` and `/ready` checks.
- [ ] Create a Docker image and `compose.yaml`.
- [ ] Deploy the app to your own laptop or LAN; open it from another device if your network permits.
- [ ] Keep API keys server-side, never in browser JavaScript or Git.

## Deliverables

- [ ] Working code with a short setup guide (in a separate project repository or local folder).
- [ ] Reproducible run/deployment instructions, including any environment variables **by name only**.
- [ ] Evidence of tests or sample outputs; remove API keys and sensitive data.
- [ ] Short comparison of at least one design alternative or limitation.
- [ ] Learning notes: what succeeded, what failed, and what to improve.

## Definition of done

> `docker compose up -d --build` launches a usable app after a clean restart.

### Phase B - Retrieval and knowledge systems (Weeks 5-8)

## Safety checklist

- [ ] No passwords, tokens, private documents, or personal data committed to Git.
- [ ] External write operations are disabled or explicitly approved when applicable.
- [ ] Failures are handled clearly rather than silently ignored.

[Course index](../../README.md) · [Previous: 03](../03/README.md) · [Next: 05](../05/README.md)
