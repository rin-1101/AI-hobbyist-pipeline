#### Week 14 - Evaluations, traces, red teaming, and security
**Understand:** offline/online evals, golden datasets, regression testing, answer relevance, faithfulness, retrieval recall@k, tool-call success, latency/cost budgets, observability, prompt injection, data exfiltration and excessive agency.

**Build:** A quality dashboard / test suite with Langfuse (or equivalent), pytest and an intentionally adversarial input set.

**Do:**
- [ ] Build **50+** test cases including normal, no-answer, stale-data and hostile-input cases.
- [ ] Trace model calls, retrieval, tool execution, failures and costs; redact sensitive data.
- [ ] Compare at least 2 changes against a fixed eval baseline.
- [ ] Follow **OWASP GenAI LLM Top 10 (2026)** and test prompt injection via retrieved documents and MCP tool results.
- [ ] Never trust natural-language model output as an authorization check; enforce permissions in code.

**Exit check:** A regression test can catch a quality or security failure before redeployment.

> **Phase:** Production & Publishing | **Week:** 14 of 16 | **Pace:** approx. 6–10 hours

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

[← Course home](../../README.md) · [← Week 13](../13-agent-interfaces-and-multimodal/README.md) · [Week 15 →](../15-production-deployment/README.md)
