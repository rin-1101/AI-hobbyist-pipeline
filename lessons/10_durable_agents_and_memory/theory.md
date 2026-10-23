# Theory — Lesson 10: Durable agents, state, memory, and Agent Skills

[Lesson overview](README.md) · [Hands-on project](hands-on.md) · [Resources](resources.md)

> **Crash course:** Read this first, then complete the [hands-on exercise](hands-on.md). The examples teach the concepts; they are not substitutes for running and testing the project.

## Learning goals

ephemeral conversation history vs persistent memory, context compaction, retrieval-based memory, checkpointing, resumable tasks, human-in-the-loop, workflow orchestration, reusable Agent Skills (`SKILL.md`).

## Crash course

### 1. State is what lets an agent continue

An agent that forgets everything after each request cannot reliably handle long tasks, resumptions, or human approvals. But “memory” means several different things:

- **Conversation history:** Messages supplied to the model on the current call.
- **Workflow state:** Which step is active, pending tool calls, and intermediate results.
- **Checkpoint:** A durable snapshot of workflow state for restart/resume.
- **Long-term memory:** Persisted facts or preferences retrieved across different sessions.

A typical architecture separates a **checkpointer** for individual conversation threads from a **store** for cross-thread facts.

### 2. Durable workflows and approval gates

Imagine an assistant preparing an email:

```text
draft -> validate recipients -> pause for approval
      -> approval received -> send -> record result
```

A durable graph or workflow saves state before pausing. When the user approves later, the process resumes using the same task ID. If the server restarts during the pause, the draft and pending approval are still available.

**Important:** A checkpoint is not an “exactly once” guarantee. If the process crashes immediately after sending an email but before recording success, naive replay may send twice. Give side-effectful operations an idempotency key or record their outcome transactionally when possible.

### 3. Memory needs policy

Store only what is needed, with an owner, source, update time, retention limit, and deletion mechanism. Avoid silently converting every conversation into permanent memory. A store can contain inaccurate or outdated facts; use confirmation and expiration.

**Agent Skills** are reusable instructions or workflow packages that teach an assistant *how* to perform a task. They are not identical to durable memory. An MCP server (next lesson) exposes tools/data; a skill generally describes a workflow and when to use it.

### 4. Pick a persistence strategy

In-memory checkpoints are fine for a prototype but disappear on restart. SQLite or PostgreSQL-backed state makes recovery possible. Plan for schema changes, concurrency, cancellation, replay, and interrupted tool calls. LangGraph is one framework for this; the principles work outside LangGraph too.

**Common mistakes:** storing API keys in state snapshots; unbounded message histories; treating repeated side effects as harmless; persisting data without deletion and privacy controls.

**Try it now:** Trace what should happen if the server crashes after an approved tool action but before the user receives confirmation.

## Knowledge check

- [ ] Can I explain the main idea to someone with basic Python knowledge?
- [ ] Can I draw the relevant data/control flow and identify trust boundaries?
- [ ] Can I describe when this technique is preferable to a simpler alternative?
- [ ] Can I name at least two failure modes and how I would detect them?
- [ ] Can I connect the concepts to this lesson's [hands-on deliverable](hands-on.md)?

## Continue learning

Use [resources.md](resources.md) for primary documentation, then implement the practical project in [hands-on.md](hands-on.md). See the [complete course syllabus](../../AI_Hobbyist_Roadmap_2026.md) for additional architecture and capstone ideas.

[Course directory](../../README.md) · [← Lesson 09](../09_tool_calling_and_agent_loops/README.md) · [Lesson 11 →](../11_mcp_server_deployment/README.md)
