# Theory — Lesson 12: Multi-agent patterns and agent communication

[Lesson overview](README.md) · [Hands-on project](hands-on.md) · [Resources](resources.md)

> **Crash course:** Read this first, then complete the [hands-on exercise](hands-on.md). The examples teach the concepts; they are not substitutes for running and testing the project.

## Learning goals

single-agent vs multi-agent tradeoffs; supervisor, delegation, handoff, parallel specialists, communication contracts, failure isolation; A2A Agent Cards, Tasks, and Artifacts.

## Crash course

### 1. Why build more than one agent?

A single agent can perform many tasks, but complex workflows may benefit from separate specialists: one researches evidence, another checks it, and a coordinator combines results. **Multi-agent design** is an architectural choice, not a requirement for advanced AI.

```text
user -> coordinator
          |-> researcher -> evidence
          |-> verifier   -> checks
          +-> writer     -> draft -> coordinator -> user
```

Each agent may have its own instructions, tools, context window, and limits. This can improve separation of concerns but adds orchestration latency, cost, and failure paths.

### 2. Patterns to know

- **Supervisor/router:** A coordinator sends work to appropriate specialists.
- **Sequential handoff:** One agent produces an artifact consumed by another.
- **Parallel workers:** Independent agents analyze separate inputs concurrently.
- **Critic/reviewer:** Another model checks claims against a rubric and evidence.
- **Deterministic workflow:** Ordinary code orders the above stages even if some stages call a model.

The most predictable starting point is a **fixed graph with one model per step**, not a free-for-all group chat.

### 3. A2A vs MCP

**Agent2Agent (A2A)** focuses on communication between agents/services: capabilities, task requests, messages, and task status. **MCP** focuses on a host accessing tools, prompts, and resources. They can complement each other: an agent might receive a task through A2A and call an MCP tool to perform part of it.

An **Agent Card** advertises what an A2A agent offers and how to contact it. Cards aid discovery; they are not proof of trust. Authenticate callers, authorize actions, and protect task data.

### 4. A worked design choice

For a research report, parallel specialists can gather information from independent categories. A verifier then checks citations. But if every specialist independently writes to the same database, race conditions and conflicting edits appear. Prefer one designated write stage, explicit inputs/outputs, and bounded retries.

Track **cost per completed task**, end-to-end latency, human review rate, and error propagation. Extra agents are worthwhile only if the quality benefit exceeds this overhead.

**Common mistakes:** vague handoff contracts; sharing confidential context indiscriminately; no owner for final output; recursive handoffs; assuming disagreement between models establishes truth.

**Try it now:** Decide whether “extract invoice, validate fields, store result” needs three agents or one model call plus deterministic validation.

## Knowledge check

- [ ] Can I explain the main idea to someone with basic Python knowledge?
- [ ] Can I draw the relevant data/control flow and identify trust boundaries?
- [ ] Can I describe when this technique is preferable to a simpler alternative?
- [ ] Can I name at least two failure modes and how I would detect them?
- [ ] Can I connect the concepts to this lesson's [hands-on deliverable](hands-on.md)?

## Continue learning

Use [resources.md](resources.md) for primary documentation, then implement the practical project in [hands-on.md](hands-on.md). See the [complete course syllabus](../../AI_Hobbyist_Roadmap_2026.md) for additional architecture and capstone ideas.

[Course directory](../../README.md) · [← Lesson 11](../11_mcp_server_deployment/README.md) · [Lesson 13 →](../13_agent_interfaces_and_multimodal/README.md)
