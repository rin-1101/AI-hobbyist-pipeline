#### Week 15 - Production-like deployment and operation
**Understand:** multi-service Compose, configuration vs secrets, auth, TLS, reverse proxies, private networks, persistent volumes, backups, migrations, health probes, structured logs, audit logs, CI/CD, rollback, rate limiting.

**Build:** An integrated deployment: UI + FastAPI + agent runtime + RAG store + MCP server + persistence + tracing.

**Do:**
- [ ] Containerize services and pin compatible dependency versions.
- [ ] Configure healthchecks, restart policies, resource limits and data volumes.
- [ ] Keep MCP and databases **private by default**; expose only necessary authenticated entry points.
- [ ] Deploy on a personal Linux server/VPS or private LAN; use a reverse proxy with HTTPS for public traffic.
- [ ] Consider Cloudflare Tunnel + Access for controlled remote access; a tunnel alone does not replace application authorization.
- [ ] Verify restart, backup/restore, upgrade, and rollback; run smoke tests from a second device.

**Exit check:** A fresh machine with your instructions and permitted secrets can reproduce the stack.

> **Phase:** Production & Publishing | **Week:** 15 of 16 | **Pace:** approx. 6–10 hours

---

## Lesson workflow

1. Read the **Understand** topics and visit the [official resources](../../AI_Hobbyist_Roadmap_2026.md#7-official-learning-resources-verified-october-2026).
2. Build the **Build** project in a separate Git repository or a local working directory.
3. Complete the **Do** checklist and retain screenshots, tests, or benchmark results as evidence.
4. Meet the **Exit check** before moving to the next lesson.

## Your learning notes

- **What I learned:** _Add your notes._
- **What I built:** _Link to your code or deployment._
- **Biggest blocker:** _Record the problem and the fix._
- **Evidence:** _Link to tests, screenshots, logs, or benchmark runs._

---

[← Course home](../../README.md) · [← Week 14](../14-evals-tracing-and-security/README.md) · [Week 16 →](../16-capstone-and-publishing/README.md)
