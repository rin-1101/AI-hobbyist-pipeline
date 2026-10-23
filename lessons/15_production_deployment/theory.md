# Theory — Lesson 15: Production-like deployment and operation

[Lesson overview](README.md) · [Hands-on project](hands-on.md) · [Resources](resources.md)

> **Crash course:** Read this first, then complete the [hands-on exercise](hands-on.md). The examples teach the concepts; they are not substitutes for running and testing the project.

## Learning goals

multi-service Compose, configuration vs secrets, auth, TLS, reverse proxies, private networks, persistent volumes, backups, migrations, health probes, structured logs, audit logs, CI/CD, rollback, rate limiting.

## Crash course

### 1. Deployment is a system property

A working Python process is not the same as a deployable service. A deployed AI application must start reliably, recover after failure, protect data, expose observability, and support controlled updates.

```text
client -> TLS/reverse proxy -> authenticated API
                                  |-> LLM provider / local inference
                                  |-> vector DB
                                  +-> persistent metadata store
```

Docker Compose is a practical learning environment for multi-service apps; managed infrastructure or Kubernetes may make sense later but are not prerequisites.

### 2. Containers, networking, and persistence

A **Dockerfile** builds an image; **Compose** defines running services, networks, environment variables, health checks, and volumes. Persistent data belongs in durable volumes or managed databases, not in the container's writable layer. A restart policy can bring services back after crashes; it is not a substitute for monitoring or backups.

Distinguish **liveness** (“process is alive”) from **readiness** (“can currently serve requests”). Configure app startup to tolerate slow database initialization and handle temporary provider outages.

### 3. Safe exposure

- Bind locally during development; deliberately decide which ports are accessible on the LAN or internet.
- Terminate HTTPS at a trusted reverse proxy; configure TLS certificates and forwarded headers correctly.
- Require authentication and per-user authorization; restrict who can query which documents and use which tools.
- Load secrets from a secret store or protected environment, not images or Git.
- Apply request limits, tool allowlists, and logging redaction.

“Only on the internal network” does not remove the need for authorization or transport security.

### 4. CI/CD and release discipline

```text
commit -> lint/tests -> build image -> scan/check
       -> deploy -> smoke tests -> monitor -> rollback if needed
```

Pin dependency versions or use lockfiles. Record the exact image version so you can roll back. Define an upgrade path for both code and persistent database schemas. Back up documents, metadata, and indexes according to what can be rebuilt.

### 5. What to monitor

Track uptime, error rate, request volume, queue depth, p95 latency, per-request cost, retrieval failures, model-provider outages, disk use, and vector DB health. Use alerts that describe actionable conditions, not simply “some logs exist.”

**Common mistakes:** storing data only inside containers; publishing development admin endpoints; restarting services without a recovery test; deploying unreviewed dependency changes.

**Try it now:** Write a three-step response plan for an API that stays online but suddenly cannot reach its vector database.

## Knowledge check

- [ ] Can I explain the main idea to someone with basic Python knowledge?
- [ ] Can I draw the relevant data/control flow and identify trust boundaries?
- [ ] Can I describe when this technique is preferable to a simpler alternative?
- [ ] Can I name at least two failure modes and how I would detect them?
- [ ] Can I connect the concepts to this lesson's [hands-on deliverable](hands-on.md)?

## Continue learning

Use [resources.md](resources.md) for primary documentation, then implement the practical project in [hands-on.md](hands-on.md). See the [complete course syllabus](../../AI_Hobbyist_Roadmap_2026.md) for additional architecture and capstone ideas.

[Course directory](../../README.md) · [← Lesson 14](../14_evals_tracing_and_security/README.md) · [Lesson 16 →](../16_capstone_and_publishing/README.md)
