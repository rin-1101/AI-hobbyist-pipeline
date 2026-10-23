# Theory — Lesson 01: APIs, inference, and the model mental model

[Lesson overview](README.md) · [Hands-on project](hands-on.md) · [Resources](resources.md)

> **Crash course:** Read this first, then complete the [hands-on exercise](hands-on.md). The examples teach the concepts; they are not substitutes for running and testing the project.

## Learning goals

tokens, context windows, sampling settings, model limitations, system/developer/user roles, model/provider boundaries, latency, cost, local vs hosted inference.

## Crash course

### 1. What a language model actually does

An LLM predicts the next **token** given a sequence of earlier tokens. A token is a piece of text, not necessarily a word: punctuation, whitespace, and word fragments can each count. The model does not query an authoritative fact database by default. It generates a plausible continuation based on its training and the current conversation.

An **inference request** normally follows this path:

```text
Your CLI -> SDK/HTTP -> model provider -> model inference -> response
                      (or a local model server)
```

Your program controls the input, parsing, validation, and user experience. The model supplies generated text (or other model outputs). Treat that output as *untrusted* until checked.

### 2. Four knobs that affect behavior

- **Context window:** The maximum input and output context the model can handle in one request. Large context is not perfect memory; long prompts can be costly and distract the model.
- **Sampling / temperature:** Settings influence how the model selects among candidate tokens. Lower randomness may make outputs more repeatable, but does not guarantee truth or identical results.
- **Instructions and message roles:** System/developer instructions define application behavior; user messages supply the current task. Role boundaries matter, but they do not eliminate prompt-injection risks.
- **Model choice:** Models differ in capability, latency, price, context size, data-handling policy, and tool support.

**Hallucination** means the model produces unsupported or invented information. Better prompts can reduce it; factual grounding and verification are stronger defenses.

### 3. Cost, latency, and failure modes

Hosted APIs often charge separately for input and output tokens. A rough request cost is:

```text
cost = (input_tokens / 1,000,000) * input_rate
     + (output_tokens / 1,000,000) * output_rate
```

Use the provider's current rates, not a hardcoded estimate. Record *time to first token* (for streaming), total latency, output length, and error type. Set a request timeout, an output-token limit, and a budget cap.

Hosted inference sends some request content to the provider. Local inference keeps model computation on your hardware, but you still need to audit telemetry, downloads, and any external services the application calls.

### 4. Worked example: your AI CLI

Given the prompt “Summarize this paragraph in two bullets,” run it twice with different models. Save a record containing the prompt ID, model ID, elapsed time, token usage (when available), and output. Score both for instruction-following and factual fidelity. A faster or cheaper model is useful only if it meets your quality threshold.

**Common mistakes:** assuming fluent output is factual; confusing conversation history with durable memory; hardcoding keys; comparing models with different prompts or generation limits.

**Try it now:** Explain why a prompt may fit inside the context limit yet still produce a weak answer, and identify two variables besides model size that affect response speed.

## Knowledge check

- [ ] Can I explain the main idea to someone with basic Python knowledge?
- [ ] Can I draw the relevant data/control flow and identify trust boundaries?
- [ ] Can I describe when this technique is preferable to a simpler alternative?
- [ ] Can I name at least two failure modes and how I would detect them?
- [ ] Can I connect the concepts to this lesson's [hands-on deliverable](hands-on.md)?

## Continue learning

Use [resources.md](resources.md) for primary documentation, then implement the practical project in [hands-on.md](hands-on.md). See the [complete course syllabus](../../AI_Hobbyist_Roadmap_2026.md) for additional architecture and capstone ideas.

[Course directory](../../README.md) · [Lesson 02 →](../02_context_and_structured_outputs/README.md)
