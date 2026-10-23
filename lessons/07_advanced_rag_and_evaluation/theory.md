# Theory — Lesson 07: Advanced RAG, reranking, and retrieval evaluation

[Lesson overview](README.md) · [Hands-on project](hands-on.md) · [Resources](resources.md)

> **Crash course:** Read this first, then complete the [hands-on exercise](hands-on.md). The examples teach the concepts; they are not substitutes for running and testing the project.

## Learning goals

dense vs sparse retrieval (BM25), hybrid search, rank fusion, reranking, metadata filtering, query expansion, multi-query retrieval, parent-child chunks, retrieval precision/recall, nDCG, groundedness.

## Crash course

### 1. Why basic vector search can miss

Dense embeddings work well for meaning but may overlook exact product IDs, error codes, rare names, or numbers. **Sparse/keyword retrieval**, often BM25, rewards literal term matches. **Hybrid search** combines both so each compensates for the other's weaknesses.

```text
                 +-> dense vector results ----+
user query ------|                            +-> fuse -> rerank -> context
                 +-> BM25 keyword results ---+
```

**Metadata filtering** narrows results by user, document type, date, project, or source; it is often a security requirement, not just a relevance trick.

### 2. Fusion vs reranking

A fusion method combines ranked lists. **Reciprocal Rank Fusion (RRF)** uses positions rather than raw similarity scores:

```text
RRF(document) = sum(1 / (k + rank_in_each_result_list))
```

Where `k` is a smoothing constant and rank starts at a consistent index. A document ranked highly by both retrievers rises in the combined list.

A **reranker** then scores a smaller candidate set more carefully using both the question and passage, often improving relevance at additional compute cost. Retrieve widely, rerank narrowly.

### 3. Build an evaluation set before tuning

For each test question record which chunk(s) contain the answer. Useful measures:

- **Recall@k:** In how many questions did the top-k results contain at least one relevant passage?
- **MRR:** How early did the first relevant result appear, averaged over questions?
- **Precision@k:** What proportion of returned chunks are relevant?
- **Answer faithfulness:** Did generated claims follow the retrieved evidence?

Use separate development and evaluation questions so you do not tune purely to the test set. Include “no answer exists,” contradictory documents, and exact identifier questions.

### 4. Worked comparison

Query: “Which release fixed error E-1047?” Dense search might retrieve general release notes about errors; BM25 can find **E-1047** exactly. Fusion raises the exact-match page; reranking checks whether it says “fixed” versus “still investigating.”

**Common mistakes:** comparing raw cosine scores with BM25 scores directly; tuning solely on generated answer fluency; reranking all documents; failing to apply permission filters at retrieval time.

**Try it now:** Describe a query where keyword search will likely outperform embeddings, and another where the reverse is true.

## Knowledge check

- [ ] Can I explain the main idea to someone with basic Python knowledge?
- [ ] Can I draw the relevant data/control flow and identify trust boundaries?
- [ ] Can I describe when this technique is preferable to a simpler alternative?
- [ ] Can I name at least two failure modes and how I would detect them?
- [ ] Can I connect the concepts to this lesson's [hands-on deliverable](hands-on.md)?

## Continue learning

Use [resources.md](resources.md) for primary documentation, then implement the practical project in [hands-on.md](hands-on.md). See the [complete course syllabus](../../AI_Hobbyist_Roadmap_2026.md) for additional architecture and capstone ideas.

[Course directory](../../README.md) · [← Lesson 06](../06_basic_rag/README.md) · [Lesson 08 →](../08_beyond_pdf_rag/README.md)
