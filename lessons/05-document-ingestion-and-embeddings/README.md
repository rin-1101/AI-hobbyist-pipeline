#### Week 5 - Document ingestion and embedding fundamentals
**Understand:** embeddings, semantic similarity, data parsing, chunk sizes/overlap, document structure, metadata, provenance, OCR, deduplication, content hashing, incremental ingestion.

**Build:** A pipeline that extracts 20-100 permitted PDFs/Markdown/DOCX files using Docling, creates chunks, and stores source metadata.

**Do:**
- [ ] Preserve source filename/page/section and a stable document ID.
- [ ] Compare two chunking methods, including heading-aware chunking.
- [ ] Make re-ingestion idempotent (no duplicate chunks).
- [ ] Test malformed or scanned documents and record extraction failures.

**Exit check:** Every retrievable chunk can be traced to an original document.

> **Phase:** Retrieval & Knowledge | **Week:** 5 of 16 | **Pace:** approx. 6–10 hours

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

[← Course home](../../README.md) · [← Week 4](../04-deployable-ai-service/README.md) · [Week 6 →](../06-basic-rag/README.md)
