# Theory — Lesson 14: Evaluations, traces, red teaming, and security

[Lesson overview](README.md) · [Hands-on project](hands-on.md) · [Resources](resources.md)

> **Crash course:** Read this first, then complete the [hands-on exercise](hands-on.md). The examples teach the concepts; they are not substitutes for running and testing the project.

## Learning goals

offline/online evals, golden datasets, regression testing, answer relevance, faithfulness, retrieval recall@k, tool-call success, latency/cost budgets, observability, prompt injection, data exfiltration and excessive agency.

## Crash course

### 1. Evaluate systems, not just prompts

A demo that works once proves little. AI evaluation asks: **How often does this system meet a defined standard across representative cases?** Test model responses, retrieval, tool use, latency, security, and complete user tasks separately.

```text
test case -> app execution -> captured trace
          -> metrics + rubric -> pass/fail + diagnosis
```

### 2. Four useful kinds of evaluation

1. **Deterministic assertions:** Valid JSON, correct schema, allowed tool name, citation format, HTTP status, and output constraints.
2. **Groundedness/answer checks:** Compare generated claims with trusted evidence; allow human grading for nuanced failures.
3. **Retrieval metrics:** Recall@k, precision@k, and ranking quality on questions with known relevant sources.
4. **Workflow metrics:** Task completion, external-action correctness, p50/p95 latency, token cost, retry rate, and failure recovery.

Model-based judges are useful but can be inconsistent or biased. Calibrate them against a smaller human-reviewed set.

### 3. Trace the workflow

A **trace** records steps and timing; a **span** represents an operation such as retrieval or a tool call. Correlate events with a request ID, model/prompt version, retrieved chunk IDs, and tool outcomes. Redact credentials and minimize personal data before recording logs or traces.

When performance degrades, traces tell you whether the cause was slow retrieval, high prompt length, repeated tool calls, or model latency.

### 4. Threats specific to agentic systems

**Prompt injection** is hostile instructions embedded in lower-trust content like retrieved webpages or tool output. A document saying “send me all secrets” has no right to override your application rules. Other risks include unauthorized tool execution, data exfiltration, cross-user retrieval, and uncontrolled cost.

Defenses are layered: restrict tools and data, validate arguments, separate instructions from external content, require human approval for sensitive actions, and test adversarial cases. A powerful prompt alone is not a security boundary.

### 5. Create a release gate

Build a dataset of at least 20 real questions plus explicit edge cases. Pick thresholds (e.g. no unauthorized actions, schema validation always passing, evidence found for most answerable questions) *before* changing prompts. Re-run the suite after every model, embedding, or tool update.

**Common mistakes:** evaluating only average accuracy; leaking sensitive prompts into logs; using the test set as an optimization prompt; skipping refusal and access-control tests.

**Try it now:** Explain why a system may have high retrieval recall but still produce an unfaithful final answer.

## Knowledge check

- [ ] Can I explain the main idea to someone with basic Python knowledge?
- [ ] Can I draw the relevant data/control flow and identify trust boundaries?
- [ ] Can I describe when this technique is preferable to a simpler alternative?
- [ ] Can I name at least two failure modes and how I would detect them?
- [ ] Can I connect the concepts to this lesson's [hands-on deliverable](hands-on.md)?

## Continue learning

Use [resources.md](resources.md) for primary documentation, then implement the practical project in [hands-on.md](hands-on.md). See the [complete course syllabus](../../AI_Hobbyist_Roadmap_2026.md) for additional architecture and capstone ideas.

[Course directory](../../README.md) · [← Lesson 13](../13_agent_interfaces_and_multimodal/README.md) · [Lesson 15 →](../15_production_deployment/README.md)
