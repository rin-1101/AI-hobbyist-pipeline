# Theory — 03: Local models and inference servers

[Lesson overview](README.md) · [Hands-on](hands-on.md) · [Resources](resources.md)

## Learning objectives

open-weight models, licenses, quantization, CPU/GPU/RAM/VRAM constraints, context length, tokens/second, latency vs throughput, model download sizes.

## Core concepts to study

1. **open-weight models** — Define the idea in your own words, explain when you would use it, and identify one failure mode or trade-off.
2. **licenses** — Define the idea in your own words, explain when you would use it, and identify one failure mode or trade-off.
3. **quantization** — Define the idea in your own words, explain when you would use it, and identify one failure mode or trade-off.
4. **CPU/GPU/RAM/VRAM constraints** — Define the idea in your own words, explain when you would use it, and identify one failure mode or trade-off.
5. **context length** — Define the idea in your own words, explain when you would use it, and identify one failure mode or trade-off.
6. **tokens/second** — Define the idea in your own words, explain when you would use it, and identify one failure mode or trade-off.
7. **latency vs throughput** — Define the idea in your own words, explain when you would use it, and identify one failure mode or trade-off.
8. **model download sizes** — Define the idea in your own words, explain when you would use it, and identify one failure mode or trade-off.

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

[Course index](../../README.md) · [Previous: 02](../02/README.md) · [Next: 04](../04/README.md)
