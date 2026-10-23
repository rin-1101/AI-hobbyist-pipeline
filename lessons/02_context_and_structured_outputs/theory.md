# Theory — Lesson 02: Context engineering, structured outputs, and deterministic boundaries

[Lesson overview](README.md) · [Hands-on project](hands-on.md) · [Resources](resources.md)

> **Crash course:** Read this first, then complete the [hands-on exercise](hands-on.md). The examples teach the concepts; they are not substitutes for running and testing the project.

## Learning goals

prompt contracts, Pydantic schemas, JSON validation, few-shot examples, constrained output, context selection, prompt caching, idempotency, and prompt versioning.

## Crash course

### 1. A prompt is an interface, not a guarantee

A useful LLM application defines a **contract**: the input it accepts, the output shape it expects, and the programmatic checks applied before anything else happens. “Return JSON” is only an instruction; **schema validation** is the enforcement mechanism.

Suppose your app extracts tasks from text:

```json
{"title":"Email the team","priority":"high",
 "due_date":"2026-11-02","confidence":0.86}
```

The model can omit fields, invent a date, or return “urgent-ish” instead of a valid priority. Your code should reject or repair invalid results under a bounded retry policy.

### 2. Core ideas

- **Structured outputs:** Ask the model for a specific schema. Use native constrained-output modes when the selected provider supports them.
- **Pydantic:** Validate types and constraints *after* the response arrives.
- **Few-shot examples:** Show representative valid inputs and outputs, especially edge cases.
- **Context engineering:** Give the model only relevant instructions, documents, and user information, with clear source boundaries.
- **Prompt versioning:** Treat prompts like code: version them, test them, and record which version produced an output.
- **Idempotency:** Repeating a request should not accidentally repeat a side effect such as creating the same task twice.

For example, Pydantic can enforce the expected shape:

```python
from datetime import date
from typing import Literal
from pydantic import BaseModel, Field

class Task(BaseModel):
    title: str = Field(min_length=1)
    priority: Literal["low", "medium", "high"]
    due_date: date | None = None
    confidence: float = Field(ge=0.0, le=1.0)
```

Parsing into `Task` catches malformed fields. It cannot prove the due date was correctly inferred from the original message; that needs a semantic test or user confirmation.

### 3. Separate inference from execution

A safe design has two steps:

```text
user text -> model extraction -> schema validation
          -> business-rule validation -> user confirmation
          -> deterministic create_task() function
```

A confidence score is a model-produced estimate, **not** a calibrated probability unless you validate it empirically. For missing or ambiguous due dates, preserve `null` or request clarification rather than inventing one.

**Common mistakes:** putting credentials in prompts; treating valid JSON as truthful; allowing model-generated data to invoke arbitrary operations; changing prompts without regression tests.

**Try it now:** Give your extractor “Remind me sometime next week.” Decide which fields it can safely populate and which should remain uncertain.

## Knowledge check

- [ ] Can I explain the main idea to someone with basic Python knowledge?
- [ ] Can I draw the relevant data/control flow and identify trust boundaries?
- [ ] Can I describe when this technique is preferable to a simpler alternative?
- [ ] Can I name at least two failure modes and how I would detect them?
- [ ] Can I connect the concepts to this lesson's [hands-on deliverable](hands-on.md)?

## Continue learning

Use [resources.md](resources.md) for primary documentation, then implement the practical project in [hands-on.md](hands-on.md). See the [complete course syllabus](../../AI_Hobbyist_Roadmap_2026.md) for additional architecture and capstone ideas.

[Course directory](../../README.md) · [← Lesson 01](../01_llm_apis_and_inference/README.md) · [Lesson 03 →](../03_local_models/README.md)
