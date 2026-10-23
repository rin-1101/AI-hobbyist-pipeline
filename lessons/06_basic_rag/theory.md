# Theory — Lesson 06: Basic Retrieval-Augmented Generation (RAG)

[Lesson overview](README.md) · [Hands-on project](hands-on.md) · [Resources](resources.md)

> **Crash course:** Read this first, then complete the [hands-on exercise](hands-on.md). The examples teach the concepts; they are not substitutes for running and testing the project.

## Learning goals

embedding index, vector search, nearest neighbors, cosine similarity, retrieval top-k, context packing, answer grounding, citations, abstention.

## Crash course

### 1. RAG is “search, then answer”

A basic Retrieval-Augmented Generation system connects an LLM to evidence at **question time**.

```text
question -> embed/query -> retrieve top-k relevant chunks
         -> assemble cited context -> LLM -> grounded answer
```

The model's internal knowledge remains available, but your application should prioritize retrieved evidence for questions about your documents. RAG does not automatically fine-tune or retrain the model.

### 2. The two stages

**Retrieval:** Vector search finds chunks similar to the question. Parameters include top-k, metadata filters, and similarity thresholds. Retrieval quality determines whether the model even sees the needed fact.

**Generation:** The app sends those chunks with a clear instruction: answer from supplied evidence, cite identifiers, and say when evidence is insufficient. Attach citations to source IDs from your retrieval system, not citations invented by the model.

Example context:

```text
[SRC-17 | handbook.pdf | p. 8]
Employees can submit leave requests up to 30 days in advance.

Question: When can I submit a leave request?
```

A grounded answer points to **SRC-17**. If the document says nothing about approvals, the system should not invent an approval policy.

### 3. Guardrails for a first implementation

- Keep source metadata and enforce document-level authorization before results reach the model.
- Limit context size and order results intentionally.
- Detect empty/weak retrieval and return “I couldn't verify that from the available documents.”
- Treat retrieved text as **data**, not system instructions. A malicious PDF might say “ignore earlier rules”; your app must not grant it authority.
- Handle document changes: stale indexes produce stale answers.

### 4. Measure the right things

Create 20 factual questions from known source passages. Record whether retrieval found the evidence (**retrieval recall**) and whether the final answer used it correctly (**answer grounding**). Compare “model only” and “RAG” versions, including questions the collection cannot answer.

**Common mistakes:** picking arbitrary chunk sizes and never testing them; providing links to unrelated files; relying on semantic similarity as proof of factual correctness; leaking another user's documents.

**Try it now:** Write a question that your document collection intentionally cannot answer. What should the system return?

## Knowledge check

- [ ] Can I explain the main idea to someone with basic Python knowledge?
- [ ] Can I draw the relevant data/control flow and identify trust boundaries?
- [ ] Can I describe when this technique is preferable to a simpler alternative?
- [ ] Can I name at least two failure modes and how I would detect them?
- [ ] Can I connect the concepts to this lesson's [hands-on deliverable](hands-on.md)?

## Continue learning

Use [resources.md](resources.md) for primary documentation, then implement the practical project in [hands-on.md](hands-on.md). See the [complete course syllabus](../../AI_Hobbyist_Roadmap_2026.md) for additional architecture and capstone ideas.

[Course directory](../../README.md) · [← Lesson 05](../05_document_ingestion_and_embeddings/README.md) · [Lesson 07 →](../07_advanced_rag_and_evaluation/README.md)
