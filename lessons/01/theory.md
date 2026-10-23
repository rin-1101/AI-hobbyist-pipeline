# Theory — 01: APIs, inference, and the model mental model

[Lesson overview](README.md) · [Hands-on](hands-on.md) · [Resources](resources.md)

## Learning objectives

tokens, context windows, sampling settings, model limitations, system/developer/user roles, model/provider boundaries, latency, cost, local vs hosted inference.

## Core concepts to study

1. **tokens** — Define the idea in your own words, explain when you would use it, and identify one failure mode or trade-off.
2. **context windows** — Define the idea in your own words, explain when you would use it, and identify one failure mode or trade-off.
3. **sampling settings** — Define the idea in your own words, explain when you would use it, and identify one failure mode or trade-off.
4. **model limitations** — Define the idea in your own words, explain when you would use it, and identify one failure mode or trade-off.
5. **system/developer/user roles** — Define the idea in your own words, explain when you would use it, and identify one failure mode or trade-off.
6. **model/provider boundaries** — Define the idea in your own words, explain when you would use it, and identify one failure mode or trade-off.
7. **latency** — Define the idea in your own words, explain when you would use it, and identify one failure mode or trade-off.
8. **cost** — Define the idea in your own words, explain when you would use it, and identify one failure mode or trade-off.
9. **local vs hosted inference** — Define the idea in your own words, explain when you would use it, and identify one failure mode or trade-off.

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

[Course index](../../README.md) · [Next: 02](../02/README.md)
