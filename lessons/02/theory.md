# Theory — 02: Context engineering, structured outputs, and deterministic boundaries

[Lesson overview](README.md) · [Hands-on](hands-on.md) · [Resources](resources.md)

## Learning objectives

prompt contracts, Pydantic schemas, JSON validation, few-shot examples, constrained output, context selection, prompt caching, idempotency, and prompt versioning.

## Core concepts to study

1. **prompt contracts** — Define the idea in your own words, explain when you would use it, and identify one failure mode or trade-off.
2. **Pydantic schemas** — Define the idea in your own words, explain when you would use it, and identify one failure mode or trade-off.
3. **JSON validation** — Define the idea in your own words, explain when you would use it, and identify one failure mode or trade-off.
4. **few-shot examples** — Define the idea in your own words, explain when you would use it, and identify one failure mode or trade-off.
5. **constrained output** — Define the idea in your own words, explain when you would use it, and identify one failure mode or trade-off.
6. **context selection** — Define the idea in your own words, explain when you would use it, and identify one failure mode or trade-off.
7. **prompt caching** — Define the idea in your own words, explain when you would use it, and identify one failure mode or trade-off.
8. **idempotency** — Define the idea in your own words, explain when you would use it, and identify one failure mode or trade-off.
9. **and prompt versioning** — Define the idea in your own words, explain when you would use it, and identify one failure mode or trade-off.

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

[Course index](../../README.md) · [Previous: 01](../01/README.md) · [Next: 03](../03/README.md)
