# Theory — Lesson 04: Your first deployable AI service

[Lesson overview](README.md) · [Hands-on project](hands-on.md) · [Resources](resources.md)

> **Crash course:** Read this first, then complete the [hands-on exercise](hands-on.md). The examples teach the concepts; they are not substitutes for running and testing the project.

## Learning goals

FastAPI endpoints, streaming, HTTP errors, environment variables, Dockerfiles, health checks, logs, and simple UI integration.

## Crash course

### 1. Turn a script into a service

A production-shaped AI app separates its web boundary from the model integration:

```text
Browser -> HTTP endpoint -> request validation -> model service
                              |                  |
                              +-> logs/errors <--+
```

**FastAPI** handles HTTP routes, input validation, and serialization. A model adapter handles API calls. A frontend should communicate with your backend, **never** directly expose a private provider API key.

### 2. Essential HTTP concepts

- `GET /health` answers whether the process is alive.
- `GET /ready` answers whether required dependencies are ready; health and readiness are not necessarily the same.
- `POST /chat` receives validated user input and returns a response.
- **Timeouts** bound how long callers wait; return useful errors instead of leaving connections hanging.
- **Streaming** emits tokens or events incrementally, improving perceived responsiveness but complicating reconnects and error reporting.
- **Status codes:** Use an appropriate 4xx for bad requests and 5xx for server failures; do not turn every error into a successful 200 response.

Minimal, provider-independent route structure:

```python
from fastapi import FastAPI
from pydantic import BaseModel

app = FastAPI()

class ChatRequest(BaseModel):
    message: str

@app.get("/health")
def health():
    return {"status": "ok"}

@app.post("/chat")
async def chat(request: ChatRequest):
    # Replace with a real async-safe model adapter.
    return {"answer": f"Received: {request.message}"}
```

This is a route demonstration, **not** a completed model integration. Add request-size limits, authentication if exposed beyond a trusted environment, and correct async handling for your provider.

### 3. Why containers help

A **Docker image** packages application code and dependencies. A **container** is a running instance. **Docker Compose** records how services start together and which ports, volumes, and environment variables they use. Rebuilding an image differs from restarting a container.

A health check should not make a paid model call. Readiness can verify configuration or an inexpensive dependency check without generating tokens.

### 4. A clean deployment test

Build the image, start it, test `/health`, call `/chat`, restart the service, and repeat. Verify no credentials are present in source control or served JavaScript. For local-only operation bind to loopback; for LAN access, configure binding, firewall, and authentication deliberately.

**Common mistakes:** baking secrets into images; relying on in-memory state; using development auto-reload in production; exposing `0.0.0.0` without access controls.

**Try it now:** Explain why a process can be “healthy” even if its model backend is unreachable.

## Knowledge check

- [ ] Can I explain the main idea to someone with basic Python knowledge?
- [ ] Can I draw the relevant data/control flow and identify trust boundaries?
- [ ] Can I describe when this technique is preferable to a simpler alternative?
- [ ] Can I name at least two failure modes and how I would detect them?
- [ ] Can I connect the concepts to this lesson's [hands-on deliverable](hands-on.md)?

## Continue learning

Use [resources.md](resources.md) for primary documentation, then implement the practical project in [hands-on.md](hands-on.md). See the [complete course syllabus](../../AI_Hobbyist_Roadmap_2026.md) for additional architecture and capstone ideas.

[Course directory](../../README.md) · [← Lesson 03](../03_local_models/README.md) · [Lesson 05 →](../05_document_ingestion_and_embeddings/README.md)
