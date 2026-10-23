# Theory — Lesson 05: Document ingestion and embedding fundamentals

[Lesson overview](README.md) · [Hands-on project](hands-on.md) · [Resources](resources.md)

> **Crash course:** Read this first, then complete the [hands-on exercise](hands-on.md). The examples teach the concepts; they are not substitutes for running and testing the project.

## Learning goals

embeddings, semantic similarity, data parsing, chunk sizes/overlap, document structure, metadata, provenance, OCR, deduplication, content hashing, incremental ingestion.

## Crash course

### 1. RAG begins with reliable ingestion

Before documents can answer questions, they must be transformed into searchable, traceable pieces.

```text
PDF / DOCX / Markdown -> parser -> clean text + structure
  -> chunks + metadata -> embedding model -> vector index
```

The parser can lose tables, headings, page numbers, reading order, or footnotes. **OCR** can recover text from scans, but introduces recognition errors. Inspect representative documents rather than assuming every extraction succeeded.

### 2. What an embedding represents

An **embedding** is a numeric vector representing aspects of text meaning. Similar passages often appear near each other in vector space. It is not a factual summary, and nearby vectors do not prove two statements are equally true. A vector index stores embeddings so nearest-neighbor search can run efficiently.

Keep the embedding model consistent between indexed documents and queries. Switching embedding models generally requires re-embedding indexed content.

### 3. Chunking is a retrieval design decision

If chunks are too large, each search result may contain noise and waste context. If too small, important relationships are split apart. Try at least two strategies:

- **Fixed-size:** A bounded number of tokens with optional overlap. Simple but may cut tables and paragraphs in half.
- **Structure-aware:** Split on headings, sections, or paragraphs and retain parent section information. Often more interpretable, but depends on parsing quality.

For every chunk store **document ID, source path, section/page, chunk index, permissions, and ingestion version**. This enables citations, deletion, and access control later.

### 4. Idempotent ingestion

A pipeline should handle a file being uploaded twice without duplicating its chunks. Compute a stable hash from normalized content or source bytes, record model/chunker versions, and replace outdated chunks when a document changes.

```text
file hash unchanged? -> skip
file changed? -> parse -> replace old chunks -> update index
```

When handling private documents, apply access labels **before indexing and searching**, not merely when generating the final response.

**Common mistakes:** treating OCR errors as ground truth; indexing files without source metadata; mixing incompatible embedding dimensions; storing the same document repeatedly; silently dropping failed pages.

**Try it now:** Compare how you would chunk a contract with numbered clauses versus a page of meeting notes.

## Knowledge check

- [ ] Can I explain the main idea to someone with basic Python knowledge?
- [ ] Can I draw the relevant data/control flow and identify trust boundaries?
- [ ] Can I describe when this technique is preferable to a simpler alternative?
- [ ] Can I name at least two failure modes and how I would detect them?
- [ ] Can I connect the concepts to this lesson's [hands-on deliverable](hands-on.md)?

## Continue learning

Use [resources.md](resources.md) for primary documentation, then implement the practical project in [hands-on.md](hands-on.md). See the [complete course syllabus](../../AI_Hobbyist_Roadmap_2026.md) for additional architecture and capstone ideas.

[Course directory](../../README.md) · [← Lesson 04](../04_deployable_ai_service/README.md) · [Lesson 06 →](../06_basic_rag/README.md)
