# Hands-on — 16: Capstone, benchmark, and publish

[Lesson overview](README.md) · [Theory](theory.md) · [Resources](resources.md)

## Project brief

Finalize Personal AI Workbench or a capstone from Section 5.

## Suggested implementation workflow

1. **Prepare:** Create a local project folder and virtual environment; record dependencies and model/runtime versions.
2. **Design:** Draw a minimal data-flow diagram, define inputs/outputs, and identify secrets or permissions.
3. **Build:** Implement the smallest end-to-end version of the project brief.
4. **Test:** Create success, failure, and edge-case scenarios; retain reproducible input/output examples.
5. **Deploy or demonstrate:** Run the project according to the lesson requirements; preserve a repeatable run command.
6. **Document:** Capture measurements, known limitations, and your solution to one debugging issue.

## Required tasks

- [ ] Run ingestion end-to-end and demonstrate sourced RAG answers.
- [ ] Demonstrate an agent using your MCP server in a controlled workflow.
- [ ] Demonstrate an approval gate, a refused unauthorized action, and agent recovery after restart.
- [ ] Include a deployment walkthrough, architecture diagram, 50-case evaluation report and screenshots.
- [ ] Tag a Git release (e.g., `v1.0.0`) and publish a sanitized portfolio demo if allowed.

## Deliverables

- [ ] Working code with a short setup guide (in a separate project repository or local folder).
- [ ] Reproducible run/deployment instructions, including any environment variables **by name only**.
- [ ] Evidence of tests or sample outputs; remove API keys and sensitive data.
- [ ] Short comparison of at least one design alternative or limitation.
- [ ] Learning notes: what succeeded, what failed, and what to improve.

## Definition of done

> Another developer can install, test and deploy your project from its documentation.

## Safety checklist

- [ ] No passwords, tokens, private documents, or personal data committed to Git.
- [ ] External write operations are disabled or explicitly approved when applicable.
- [ ] Failures are handled clearly rather than silently ignored.

[Course index](../../README.md) · [Previous: 15](../15/README.md) · Course complete!
