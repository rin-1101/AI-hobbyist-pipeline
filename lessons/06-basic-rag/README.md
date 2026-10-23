#### Week 6 - Basic Retrieval-Augmented Generation (RAG)
**Understand:** embedding index, vector search, nearest neighbors, cosine similarity, retrieval top-k, context packing, answer grounding, citations, abstention.

**Build:** `/ask` API + chat UI that answers questions over your document collection and cites specific source files/pages.

**Do:**
- [ ] Store/retrieve chunks in Qdrant or pgvector.
- [ ] Compare `LLM alone` vs `vector retrieval + LLM` on 20 questions.
- [ ] Return citations and an explicit "insufficient evidence" answer when retrieval is poor.
- [ ] Deploy the RAG API and vector database with persistent volumes.

**Exit check:** The system cites actual retrieved material; nonexistent sources are never fabricated.

> **Phase:** Retrieval & Knowledge | **Week:** 6 of 16 | **Pace:** approx. 6–10 hours

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

[← Course home](../../README.md) · [← Week 5](../05-document-ingestion-and-embeddings/README.md) · [Week 7 →](../07-advanced-rag-and-evaluation/README.md)
