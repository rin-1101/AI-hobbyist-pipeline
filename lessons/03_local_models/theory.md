# Theory — Lesson 03: Local models and inference servers

[Lesson overview](README.md) · [Hands-on project](hands-on.md) · [Resources](resources.md)

> **Crash course:** Read this first, then complete the [hands-on exercise](hands-on.md). The examples teach the concepts; they are not substitutes for running and testing the project.

## Learning goals

open-weight models, licenses, quantization, CPU/GPU/RAM/VRAM constraints, context length, tokens/second, latency vs throughput, model download sizes.

## Crash course

### 1. What changes when inference runs locally?

With a hosted API, the provider manages GPUs, model loading, and scaling. With **local inference**, you manage the model weights, memory requirements, updates, performance, and availability. The app can still call a familiar HTTP interface.

```text
App -> model adapter -> Ollama / llama.cpp / vLLM -> model
                    -> hosted API (alternate backend)
```

A model adapter gives the rest of your app one stable interface, regardless of where inference runs.

### 2. Hardware and model vocabulary

- **Parameters:** Learned numeric weights. More parameters often raise memory needs, but size alone does not establish quality.
- **Quantization:** Store weights at lower numerical precision (such as 4-bit instead of 16-bit) to reduce memory use, often with some quality/performance trade-off.
- **VRAM:** GPU memory holds model weights and working data. Context length and concurrent requests also consume memory.
- **Tokens per second:** Generation throughput; distinguish it from prompt-processing time and initial model load time.
- **Context length:** A larger configured context consumes additional memory and does not guarantee good long-range reasoning.
- **License:** “Open-weight” does not automatically mean unrestricted commercial use.

Rough intuition: an 8-billion-parameter model needs about 16 GB just for weights at 16-bit precision, before overhead; 4-bit quantization can substantially reduce the weight footprint. Actual runtime memory depends on implementation and context.

### 3. Example: test a local API

With Ollama running and a suitable model already downloaded, you can call its HTTP endpoint:

```bash
curl http://localhost:11434/api/generate   -d '{"model":"YOUR_INSTALLED_MODEL","prompt":"Explain RAG in one sentence","stream":false}'
```

Replace the placeholder with a model actually installed on your machine. Your application should expose settings such as `MODEL_BACKEND` and `MODEL_NAME`, not scatter provider-specific calls across the codebase.

### 4. Choose using a benchmark, not a brand name

Use the same 10 prompts, comparable output lengths, and quality rubric across backends. Measure success rate, first-response latency, total latency, memory use, and energy/cost where practical. Run a warm-up so model loading does not distort every timing.

**Common mistakes:** downloading a model larger than available RAM/VRAM; claiming private deployment while still sending content to a remote embedding or telemetry service; benchmarking only one happy-path prompt.

**Try it now:** Explain how quantization might allow a model to fit your laptop yet still reduce answer quality.

## Knowledge check

- [ ] Can I explain the main idea to someone with basic Python knowledge?
- [ ] Can I draw the relevant data/control flow and identify trust boundaries?
- [ ] Can I describe when this technique is preferable to a simpler alternative?
- [ ] Can I name at least two failure modes and how I would detect them?
- [ ] Can I connect the concepts to this lesson's [hands-on deliverable](hands-on.md)?

## Continue learning

Use [resources.md](resources.md) for primary documentation, then implement the practical project in [hands-on.md](hands-on.md). See the [complete course syllabus](../../AI_Hobbyist_Roadmap_2026.md) for additional architecture and capstone ideas.

[Course directory](../../README.md) · [← Lesson 02](../02_context_and_structured_outputs/README.md) · [Lesson 04 →](../04_deployable_ai_service/README.md)
