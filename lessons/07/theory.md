# Theory — 07: Advanced RAG, reranking, and retrieval evaluation

[Lesson overview](README.md) · [Hands-on](hands-on.md) · [Resources](resources.md)

## Learning objectives

dense vs sparse retrieval (BM25), hybrid search, rank fusion, reranking, metadata filtering, query expansion, multi-query retrieval, parent-child chunks, retrieval precision/recall, nDCG, groundedness.

## Core concepts to study

1. **dense vs sparse retrieval (BM25)** — Define the idea in your own words, explain when you would use it, and identify one failure mode or trade-off.
2. **hybrid search** — Define the idea in your own words, explain when you would use it, and identify one failure mode or trade-off.
3. **rank fusion** — Define the idea in your own words, explain when you would use it, and identify one failure mode or trade-off.
4. **reranking** — Define the idea in your own words, explain when you would use it, and identify one failure mode or trade-off.
5. **metadata filtering** — Define the idea in your own words, explain when you would use it, and identify one failure mode or trade-off.
6. **query expansion** — Define the idea in your own words, explain when you would use it, and identify one failure mode or trade-off.
7. **multi-query retrieval** — Define the idea in your own words, explain when you would use it, and identify one failure mode or trade-off.
8. **parent-child chunks** — Define the idea in your own words, explain when you would use it, and identify one failure mode or trade-off.
9. **retrieval precision/recall** — Define the idea in your own words, explain when you would use it, and identify one failure mode or trade-off.
10. **nDCG** — Define the idea in your own words, explain when you would use it, and identify one failure mode or trade-off.
11. **groundedness** — Define the idea in your own words, explain when you would use it, and identify one failure mode or trade-off.

## Architecture and design questions

1. What problem does this lesson's technique solve better than a simple deterministic script?
2. Where does information enter and leave the system? Which components are trusted?
3. What happens if a model is wrong, times out, or becomes unavailable?
4. How would you measure whether your implementation works?
5. What would change if you had to run the project locally or deploy it for another user?

## Quick understanding check

- [ ] Explain the major concepts without reading the glossary.
- [ ] Sketch the request/data flow for the project.
- [ ] Name two realistic implementation trade-offs.
- [ ] Explain how to test the exit criteria in the lesson overview.

## Further reading

See [resources.md](resources.md), and the [complete syllabus](../../AI_Hobbyist_Roadmap_2026.md).

[Course index](../../README.md) · [Previous: 06](../06/README.md) · [Next: 08](../08/README.md)
