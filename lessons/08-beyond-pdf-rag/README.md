#### Week 8 - Beyond simple PDF RAG
**Understand:** text-to-SQL safety, structured data retrieval, document/table/figure processing, routing data sources, GraphRAG, multimodal RAG and their tradeoffs.

**Build:** A router that can retrieve from **documents** or a **read-only SQLite/PostgreSQL dataset** with parameterized or tightly validated queries.

**Do:**
- [ ] Use a restricted database user; never allow generic SQL execution against a real production database.
- [ ] Show the source path (document citation or query/data reference) with each answer.
- [ ] Experiment with one of: table-aware RAG, OCR images, graph-based retrieval, or multi-hop questions.
- [ ] Add a refusal/fallback for questions outside available data.

**Exit check:** You understand when RAG, SQL, or a plain deterministic API is the best answer.

> **Phase:** Retrieval & Knowledge | **Week:** 8 of 16 | **Pace:** approx. 6–10 hours

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

[← Course home](../../README.md) · [← Week 7](../07-advanced-rag-and-evaluation/README.md) · [Week 9 →](../09-tool-calling-and-agent-loops/README.md)
