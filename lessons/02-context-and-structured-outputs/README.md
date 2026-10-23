#### Week 2 - Context engineering, structured outputs, and deterministic boundaries
**Understand:** prompt contracts, Pydantic schemas, JSON validation, few-shot examples, constrained output, context selection, prompt caching, idempotency, and prompt versioning.

**Build:** A natural-language task extractor that returns validated structured data (`title`, `priority`, `due_date`, `confidence`) without executing tasks.

**Do:**
- [ ] Define Pydantic output models and reject invalid results.
- [ ] Test ambiguous and adversarial inputs.
- [ ] Compare long-vs-short prompts and document the tradeoffs.
- [ ] Add golden-case automated tests (minimum 15).

**Exit check:** Your app never trusts unvalidated AI-generated JSON as an instruction.

> **Phase:** LLM Foundations | **Week:** 2 of 16 | **Pace:** approx. 6–10 hours

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

[← Course home](../../README.md) · [← Week 1](../01-llm-apis-and-inference/README.md) · [Week 3 →](../03-local-models/README.md)
