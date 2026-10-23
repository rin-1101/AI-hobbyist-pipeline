# Theory — Lesson 09: Function calling and the single-agent loop

[Lesson overview](README.md) · [Hands-on project](hands-on.md) · [Resources](resources.md)

> **Crash course:** Read this first, then complete the [hands-on exercise](hands-on.md). The examples teach the concepts; they are not substitutes for running and testing the project.

## Learning goals

tool definitions and schemas, planning vs execution, tool selection, bounded loops, retries, budgets, action observation, side effects, deterministic workflow vs autonomous agent.

## Crash course

### 1. The difference between a chat model and an agent

A normal chat endpoint receives a prompt and returns an answer. An **agent** is application code that allows a model to select and use **tools**, observe the results, and decide the next step. The model proposes actions; your program decides what is actually allowed to execute.

```text
user -> model -> proposed tool + arguments
                    |
                 validate
                    |
              run allowed tool
                    |
              result -> model -> answer or next tool
```

A tool is often a typed function such as `lookup_order(order_id)`, not permission to run arbitrary Python or shell commands.

### 2. Function calling is a protocol between model and code

Describe each tool with a name, purpose, and argument schema. The model returns a structured tool-call request. Your orchestrator must validate it, dispatch the function, and return a **tool result message** to the model. A tool definition does not automatically give the model access to your environment.

Sketch of an agent loop:

```python
for step in range(MAX_STEPS):
    response = ask_model(messages, available_tools)
    if response.has_final_answer:
        break
    for call in response.tool_calls:
        args = validate_arguments(call)
        result = run_allowlisted_tool(call.name, args)
        messages.append(tool_result_message(call, result))
else:
    raise RuntimeError("Agent exceeded its step budget")
```

The functions above are pseudocode; SDK-specific response shapes vary.

### 3. Bound the loop

Set budgets for **maximum steps, time, tokens, and money**. Log tool inputs and outputs with secrets redacted. Prefer read-only tools first. For actions such as sending emails, moving money, changing files, or deleting records, require explicit permission and a human confirmation step.

Tool results may contain adversarial content. For example, a webpage returned by a search tool can include instructions aimed at the agent. Such instructions are untrusted evidence—not a new system directive.

### 4. When *not* to use an agent

If the workflow is fixed (“parse file, validate schema, save record”), ordinary deterministic code is often simpler, cheaper, safer, and more testable. Use agents where tool choice or intermediate reasoning genuinely benefits from model judgment.

**Common mistakes:** infinite tool loops; executing unchecked tool arguments; retrying state-changing calls without idempotency; confusing reasoning text with authorization.

**Try it now:** Design a read-only tool and a write-capable tool for the same app. Which one requires additional safeguards, and why?

## Knowledge check

- [ ] Can I explain the main idea to someone with basic Python knowledge?
- [ ] Can I draw the relevant data/control flow and identify trust boundaries?
- [ ] Can I describe when this technique is preferable to a simpler alternative?
- [ ] Can I name at least two failure modes and how I would detect them?
- [ ] Can I connect the concepts to this lesson's [hands-on deliverable](hands-on.md)?

## Continue learning

Use [resources.md](resources.md) for primary documentation, then implement the practical project in [hands-on.md](hands-on.md). See the [complete course syllabus](../../AI_Hobbyist_Roadmap_2026.md) for additional architecture and capstone ideas.

[Course directory](../../README.md) · [← Lesson 08](../08_beyond_pdf_rag/README.md) · [Lesson 10 →](../10_durable_agents_and_memory/README.md)
