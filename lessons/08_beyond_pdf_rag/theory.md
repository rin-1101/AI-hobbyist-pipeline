# Theory — Lesson 08: Beyond simple PDF RAG

[Lesson overview](README.md) · [Hands-on project](hands-on.md) · [Resources](resources.md)

> **Crash course:** Read this first, then complete the [hands-on exercise](hands-on.md). The examples teach the concepts; they are not substitutes for running and testing the project.

## Learning goals

text-to-SQL safety, structured data retrieval, document/table/figure processing, routing data sources, GraphRAG, multimodal RAG and their tradeoffs.

## Crash course

### 1. Documents are only one kind of knowledge

“RAG” is a *pattern*—fetch external evidence before answering—not a requirement to search PDFs. Real applications mix structured databases, graphs, images, APIs, and text indexes.

```text
question -> router
             |-> vector/keyword documents
             |-> approved SQL query
             |-> knowledge graph
             +-> image/document parser
          -> combine evidence -> answer
```

The hard part becomes deciding **which source is authoritative**, joining results safely, and preserving provenance.

### 2. Text-to-SQL is not unrestricted database access

An LLM can help translate a question into SQL, but it may invent columns, join tables incorrectly, or generate dangerous statements. Prefer a curated **semantic layer** with known metrics, allowed tables, and tested query templates.

A safer flow:

1. Classify the user question.
2. Retrieve approved schema descriptions and business definitions.
3. Generate a **read-only, parameterized** query or choose an approved template.
4. Validate tables, columns, access rights, row limits, and execution cost.
5. Run under a restricted database account; inspect results before summarizing.

A query executing successfully does **not** prove it measures the right business concept.

### 3. When graphs help

A **knowledge graph** represents entities and relationships such as `Person -> works_on -> Project`. Graph traversal is useful for multi-hop questions (“Which teams own services that depend on X?”). GraphRAG approaches combine relationship-based retrieval with text evidence. You do not need a graph database for every RAG app.

### 4. Multimodal ingestion

Charts, scanned forms, screenshots, and diagrams may contain key information absent from extracted text. A vision model or specialized parser can interpret them, but preserve the original image reference and capture uncertainty. For important numbers in charts, validate against source data when possible.

**Common mistakes:** allowing write-capable generated SQL; assuming a correct answer format implies a correct join; blending conflicting data sources without timestamps; losing image/page citations.

**Try it now:** For “How many active customers used a coupon last month?”, explain why a database query may be more reliable than vector search over marketing reports.

## Knowledge check

- [ ] Can I explain the main idea to someone with basic Python knowledge?
- [ ] Can I draw the relevant data/control flow and identify trust boundaries?
- [ ] Can I describe when this technique is preferable to a simpler alternative?
- [ ] Can I name at least two failure modes and how I would detect them?
- [ ] Can I connect the concepts to this lesson's [hands-on deliverable](hands-on.md)?

## Continue learning

Use [resources.md](resources.md) for primary documentation, then implement the practical project in [hands-on.md](hands-on.md). See the [complete course syllabus](../../AI_Hobbyist_Roadmap_2026.md) for additional architecture and capstone ideas.

[Course directory](../../README.md) · [← Lesson 07](../07_advanced_rag_and_evaluation/README.md) · [Lesson 09 →](../09_tool_calling_and_agent_loops/README.md)
