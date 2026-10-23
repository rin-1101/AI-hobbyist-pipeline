# Hands-on — 15: Production-like deployment and operation

[Lesson overview](README.md) · [Theory](theory.md) · [Resources](resources.md)

## Project brief

An integrated deployment: UI + FastAPI + agent runtime + RAG store + MCP server + persistence + tracing.

## Suggested implementation workflow

1. **Prepare:** Create a local project folder and virtual environment; record dependencies and model/runtime versions.
2. **Design:** Draw a minimal data-flow diagram, define inputs/outputs, and identify secrets or permissions.
3. **Build:** Implement the smallest end-to-end version of the project brief.
4. **Test:** Create success, failure, and edge-case scenarios; retain reproducible input/output examples.
5. **Deploy or demonstrate:** Run the project according to the lesson requirements; preserve a repeatable run command.
6. **Document:** Capture measurements, known limitations, and your solution to one debugging issue.

## Required tasks

- [ ] Containerize services and pin compatible dependency versions.
- [ ] Configure healthchecks, restart policies, resource limits and data volumes.
- [ ] Keep MCP and databases **private by default**; expose only necessary authenticated entry points.
- [ ] Deploy on a personal Linux server/VPS or private LAN; use a reverse proxy with HTTPS for public traffic.
- [ ] Consider Cloudflare Tunnel + Access for controlled remote access; a tunnel alone does not replace application authorization.
- [ ] Verify restart, backup/restore, upgrade, and rollback; run smoke tests from a second device.

## Deliverables

- [ ] Working code with a short setup guide (in a separate project repository or local folder).
- [ ] Reproducible run/deployment instructions, including any environment variables **by name only**.
- [ ] Evidence of tests or sample outputs; remove API keys and sensitive data.
- [ ] Short comparison of at least one design alternative or limitation.
- [ ] Learning notes: what succeeded, what failed, and what to improve.

## Definition of done

> A fresh machine with your instructions and permitted secrets can reproduce the stack.

## Safety checklist

- [ ] No passwords, tokens, private documents, or personal data committed to Git.
- [ ] External write operations are disabled or explicitly approved when applicable.
- [ ] Failures are handled clearly rather than silently ignored.

[Course index](../../README.md) · [Previous: 14](../14/README.md) · [Next: 16](../16/README.md)
