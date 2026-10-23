# Theory — Lesson 16: Capstone, benchmark, and publish

[Lesson overview](README.md) · [Hands-on project](hands-on.md) · [Resources](resources.md)

> **Crash course:** Read this first, then complete the [hands-on exercise](hands-on.md). The examples teach the concepts; they are not substitutes for running and testing the project.

## Learning goals

system tradeoffs, dependency risk, cost management, operational runbooks, reproducibility, portfolio storytelling.

## Crash course

### 1. A capstone should prove decisions, not just features

Your final project should combine several lessons into a coherent **use case**. A “Personal AI Workbench” might let users upload their own notes, ask cited questions, delegate read-only tasks to an agent, call an MCP server, and manage the system through a web UI.

A minimum architecture:

```text
web app -> API + authentication
            |-> RAG ingest/search -> vector store
            |-> agent orchestrator -> permissioned tools
            |-> MCP client -> your MCP server
            +-> evaluation + logs
```

The goal is not maximal complexity. A modest app with reliable behavior and clear boundaries beats an unstable demo with every trendy framework.

### 2. Define a measurable scope

Write a one-page product brief with: users, key jobs, supported data, explicit non-goals, privacy expectations, cost limit, success criteria, and deployment target. Select one vertical slice to build first—for example, upload one Markdown document and answer one cited question. Add one capability at a time.

A useful test rubric:

- **Correctness:** Answers are supported by citations; unsupported questions produce honest uncertainty.
- **Tool safety:** Wrong arguments or unauthorized requests cannot trigger actions.
- **Reliability:** Restart restores data and workflows where persistence is required.
- **Quality:** Evaluation suite and measured latency/cost accompany the demo.
- **Usability:** Errors and approvals are understandable; the UI works on your target device.

### 3. Reproducibility is a feature

Someone else should be able to clone your code, install dependencies, set documented environment variables, load sample data, and run the app without guessing. Supply a safe `.env.example` **without real secrets**, startup commands, screenshots, architecture diagrams, and a smoke-test procedure.

Record versions of models, SDKs, embedding models, prompts, and datasets. Provide sample files that you have permission to share. If the app cannot be deployed publicly, a local demo with a reproducible setup is still valid.

### 4. Operations and storytelling

Create a runbook covering startup, shutdown, backups, restore, credential rotation, common errors, and rollback. Explain *why* you selected each major component, including what simpler alternative you considered.

In your portfolio walkthrough, lead with the user's problem, demonstrate the workflow, show one failure test and its mitigation, then discuss measured trade-offs. Be explicit about limitations rather than claiming “production-ready” without evidence.

### 5. Graduation self-review

Can you run the system from a clean checkout, answer a question with real citations, show a blocked unsafe tool call, restart without losing required data, and explain its running costs? If yes, you have an engineering artifact—not just a prompt demo.

**Try it now:** Write three measurable acceptance criteria for your capstone, including one failure or security criterion.

## Knowledge check

- [ ] Can I explain the main idea to someone with basic Python knowledge?
- [ ] Can I draw the relevant data/control flow and identify trust boundaries?
- [ ] Can I describe when this technique is preferable to a simpler alternative?
- [ ] Can I name at least two failure modes and how I would detect them?
- [ ] Can I connect the concepts to this lesson's [hands-on deliverable](hands-on.md)?

## Continue learning

Use [resources.md](resources.md) for primary documentation, then implement the practical project in [hands-on.md](hands-on.md). See the [complete course syllabus](../../AI_Hobbyist_Roadmap_2026.md) for additional architecture and capstone ideas.

[Course directory](../../README.md) · [← Lesson 15](../15_production_deployment/README.md)
