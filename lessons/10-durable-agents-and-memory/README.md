#### Week 10 - Durable agents, state, memory, and Agent Skills
**Understand:** ephemeral conversation history vs persistent memory, context compaction, retrieval-based memory, checkpointing, resumable tasks, human-in-the-loop, workflow orchestration, reusable Agent Skills (`SKILL.md`).

**Build:** Add task history, an approval queue, and resumable execution. Consider LangGraph when explicit state transitions are important.

**Do:**
- [ ] Save execution/checkpoint state in persistent storage.
- [ ] Stop and restart the service mid-task; recover without repeating side effects.
- [ ] Implement one portable Agent Skill for a repeatable low-risk task.
- [ ] Test a bad memory entry and a malicious/untrusted skill instruction.

**Exit check:** A failed task can resume safely and an audit trail explains its actions.

> **Phase:** Agents & Protocols | **Week:** 10 of 16 | **Pace:** approx. 6–10 hours

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

[← Course home](../../README.md) · [← Week 9](../09-tool-calling-and-agent-loops/README.md) · [Week 11 →](../11-mcp-server-deployment/README.md)
