# Hands-on — 14: Evaluations, traces, red teaming, and security

[Lesson overview](README.md) · [Theory](theory.md) · [Resources](resources.md)

## Project brief

A quality dashboard / test suite with Langfuse (or equivalent), pytest and an intentionally adversarial input set.

## Suggested implementation workflow

1. **Prepare:** Create a local project folder and virtual environment; record dependencies and model/runtime versions.
2. **Design:** Draw a minimal data-flow diagram, define inputs/outputs, and identify secrets or permissions.
3. **Build:** Implement the smallest end-to-end version of the project brief.
4. **Test:** Create success, failure, and edge-case scenarios; retain reproducible input/output examples.
5. **Deploy or demonstrate:** Run the project according to the lesson requirements; preserve a repeatable run command.
6. **Document:** Capture measurements, known limitations, and your solution to one debugging issue.

## Required tasks

- [ ] Build **50+** test cases including normal, no-answer, stale-data and hostile-input cases.
- [ ] Trace model calls, retrieval, tool execution, failures and costs; redact sensitive data.
- [ ] Compare at least 2 changes against a fixed eval baseline.
- [ ] Follow **OWASP GenAI LLM Top 10 (2026)** and test prompt injection via retrieved documents and MCP tool results.
- [ ] Never trust natural-language model output as an authorization check; enforce permissions in code.

## Deliverables

- [ ] Working code with a short setup guide (in a separate project repository or local folder).
- [ ] Reproducible run/deployment instructions, including any environment variables **by name only**.
- [ ] Evidence of tests or sample outputs; remove API keys and sensitive data.
- [ ] Short comparison of at least one design alternative or limitation.
- [ ] Learning notes: what succeeded, what failed, and what to improve.

## Definition of done

> A regression test can catch a quality or security failure before redeployment.

## Safety checklist

- [ ] No passwords, tokens, private documents, or personal data committed to Git.
- [ ] External write operations are disabled or explicitly approved when applicable.
- [ ] Failures are handled clearly rather than silently ignored.

[Course index](../../README.md) · [Previous: 13](../13/README.md) · [Next: 15](../15/README.md)
