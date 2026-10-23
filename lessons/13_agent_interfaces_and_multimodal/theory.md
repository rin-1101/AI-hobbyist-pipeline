# Theory — Lesson 13: Agent user interfaces and multimodal experiments

[Lesson overview](README.md) · [Hands-on project](hands-on.md) · [Resources](resources.md)

> **Crash course:** Read this first, then complete the [hands-on exercise](hands-on.md). The examples teach the concepts; they are not substitutes for running and testing the project.

## Learning goals

event streaming, progressive updates, approval dialogs, shared state, AG-UI (agent-to-app interaction), A2UI (declarative agent-generated UI), image/audio input, realtime voice, browser/computer use.

## Crash course

### 1. An AI experience is more than a chat bubble

For users, **latency, control, feedback, and accessibility** can matter as much as raw model quality. An AI UI should clearly indicate what is processing, what evidence was used, what actions are proposed, and whether a task is waiting for approval.

### 2. Streaming and state

A model can emit text chunks incrementally. An agent might also emit events such as “tool started,” “tool completed,” “approval requested,” or “final answer ready.” Your frontend should distinguish these event types rather than printing internal tool traces as if they were answers.

```text
backend event stream -> UI state reducer
                      -> progress / streamed text / approval / result
```

Event IDs and explicit states help with reconnects and rendering. A UI should not show a workflow as “done” until the backend actually confirms completion.

### 3. Protocols worth recognizing

- **AG-UI:** A protocol for exchanging agent activity and interaction events with frontends. It can reduce bespoke wiring between agent backends and user interfaces.
- **A2UI:** A declarative approach to agent-suggested interface content. Treat generated UI descriptions as untrusted structured data and render only approved components.
- **Multimodal models:** Models that can accept or produce more than text, such as images or audio. Your app must still handle file-size limits, privacy, and uncertain perception.

These concepts solve different problems: agent-to-UI events, UI descriptions, and media understanding.

### 4. Designing for weaker devices

If a browser is slow or lacks reliable modern animation APIs, show a static or low-motion fallback, avoid large client bundles, and render a short text status when streaming is not supported. Buttons should remain tappable while content updates. For expensive visual previews, make loading explicit and avoid blocking the core task.

Accessibility basics include focus management, keyboard navigation, readable contrast, and a clear textual description of status changes. Human approval should be explicit and reversible when feasible.

### 5. Example: a document research panel

Display retrieved sources alongside the draft answer. Show a distinct “Searching…” state, then evidence, then the final answer. If the assistant suggests a write action, render a confirmation card with the exact target and intended change.

**Common mistakes:** conflating progress events with authoritative completion; rendering arbitrary model-supplied HTML; flashing constant animation; hiding errors behind perpetual loading indicators.

**Try it now:** Sketch three UI states for an agent that must ask permission before posting a message.

## Knowledge check

- [ ] Can I explain the main idea to someone with basic Python knowledge?
- [ ] Can I draw the relevant data/control flow and identify trust boundaries?
- [ ] Can I describe when this technique is preferable to a simpler alternative?
- [ ] Can I name at least two failure modes and how I would detect them?
- [ ] Can I connect the concepts to this lesson's [hands-on deliverable](hands-on.md)?

## Continue learning

Use [resources.md](resources.md) for primary documentation, then implement the practical project in [hands-on.md](hands-on.md). See the [complete course syllabus](../../AI_Hobbyist_Roadmap_2026.md) for additional architecture and capstone ideas.

[Course directory](../../README.md) · [← Lesson 12](../12_multi_agent_and_a2a/README.md) · [Lesson 14 →](../14_evals_tracing_and_security/README.md)
