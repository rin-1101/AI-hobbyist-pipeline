# Hands-on — Production-like deployment and operation

[Overview](README.md) · [Theory](theory.md) · [Resources](resources.md)

## Build

An integrated deployment: UI + FastAPI + agent runtime + RAG store + MCP server + persistence + tracing.

## Implementation workflow

1. Create a project directory and reproducible Python environment.
2. Define inputs, outputs, security boundaries, and expected errors.
3. Implement a minimal working version and run it locally.
4. Add tests for expected, edge, and failure cases.
5. Demonstrate or deploy the project as required.
6. Record benchmark results, known limitations, and next improvements.

## Required exercises

- [ ] Containerize services and pin compatible dependency versions.
- [ ] Configure healthchecks, restart policies, resource limits and data volumes.
- [ ] Keep MCP and databases **private by default**; expose only necessary authenticated entry points.
- [ ] Deploy on a personal Linux server/VPS or private LAN; use a reverse proxy with HTTPS for public traffic.
- [ ] Consider Cloudflare Tunnel + Access for controlled remote access; a tunnel alone does not replace application authorization.
- [ ] Verify restart, backup/restore, upgrade, and rollback; run smoke tests from a second device.

## Deliverables

- [ ] Working project with setup and run instructions.
- [ ] Reproducible tests or screenshots of results.
- [ ] No secrets or private information committed to Git.
- [ ] Notes on at least one failure and how it was resolved.

## Definition of done

> A fresh machine with your instructions and permitted secrets can reproduce the stack.

[Course directory](../../README.md) · [← 14](../14_evals_tracing_and_security/README.md) · [16 →](../16_capstone_and_publishing/README.md)
