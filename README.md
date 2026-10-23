# AI Hobbyist Engineering Roadmap (2026 Edition)

> Updated: 2026-10-23 | Track: Python-first, project-based | Suggested pace: 16 weeks, 6-10 hours/week
>
> Outcome: Design, build, test, deploy, and maintain AI applications that use local/cloud models, RAG, agents, MCP servers, and optional multi-agent protocols.

## 0. How to use this syllabus

**Build one project progressively instead of 16 throwaway demos.** The main project is **Personal AI Workbench**: a private AI web application that answers questions about a permitted collection of documents, performs read-only tools, connects to your own MCP server, and runs reliably in Docker.

- Mark `[x]` after **demonstrating** the result, not just watching a tutorial.
- Commit each week's output to Git/Gitea, with a short `README.md`, screenshots where useful, and a `CHANGELOG.md` entry.
- Save a small evaluation dataset. Rerun it whenever you change a prompt, model, embedding, or retriever.
- Use **public or synthetic data** for experiments. Never point exploratory agents at confidential systems or production databases.
- One main agent framework, one main vector database, and one UI are enough. Learn the concepts before swapping libraries.

### Prerequisites

- Python (comfortable with functions/classes), packages and virtual environments; Git, JSON, HTTP, REST basics; SQL helpful.
- Docker and Docker Compose; an editor (VS Code is fine).
- A modern compatible Python version (3.12/3.13 is a sensible default; verify support before choosing 3.14 for every library), `uv` or another environment manager.
- Node.js only if using a React/Next.js interface or JavaScript-based tools.
- A small API budget **or** a computer that can run a small local model. A dedicated GPU helps but is optional.

### Recommended core stack (pick one per row)

| Layer | Recommended starting choice | Alternative / later |
|---|---|---|
| Language and backend | Python + FastAPI + Pydantic | TypeScript + Next.js |
| Environment | `uv`, Git, pytest | pip/venv, Poetry |
| LLM access | OpenAI Responses API or another provider SDK | Ollama's local API; LiteLLM gateway |
| Local model runtime | Ollama | llama.cpp, vLLM for higher-throughput serving |
| Agent loop | OpenAI Agents SDK **or** Pydantic AI | LangGraph for explicit durable state graphs; Google ADK |
| Ingestion | Docling | Unstructured, format-specific parsers |
| RAG retrieval | Qdrant | PostgreSQL + pgvector, Chroma |
| Agent context/memory | PostgreSQL + explicit session state | LangGraph checkpoints/stores |
| MCP | Official MCP Python SDK v2 | Official TypeScript SDK |
| Evals/traces | pytest + Langfuse | Arize Phoenix, Pydantic Evals, promptfoo |
| UI | Streamlit (fast) | Next.js/React, CopilotKit/AG-UI |
| Deployment | Docker Compose on a laptop, LAN server, or Linux VPS | Cloud Run/Render/Railway, Kubernetes much later |
| Private access | VPN / LAN; reverse proxy with authentication | Cloudflare Tunnel + Access or other zero-trust gate |

> These are complementary choices, not a shopping list: do not install all of them in week 1.

## 1. Full 16-week curriculum

### Phase A - LLM application fundamentals (Weeks 1-4)

#### Week 1 - APIs, inference, and the model mental model
**Understand:** tokens, context windows, sampling settings, model limitations, system/developer/user roles, model/provider boundaries, latency, cost, local vs hosted inference.

**Build:** `ai-cli`, a terminal app that submits a prompt to a provider and records response time, token use where available, and errors.

**Do:**
- [ ] Make a successful SDK call without using a framework.
- [ ] Compare answers for five prompts across two available models.
- [ ] Implement timeouts, exception handling, and an explicit cost/spend limit for hosted APIs.
- [ ] Write down cases where the LLM confidently gives a wrong answer.

**Exit check:** You can explain what runs locally, what runs at the provider, and what data leaves your device.

#### Week 2 - Context engineering, structured outputs, and deterministic boundaries
**Understand:** prompt contracts, Pydantic schemas, JSON validation, few-shot examples, constrained output, context selection, prompt caching, idempotency, and prompt versioning.

**Build:** A natural-language task extractor that returns validated structured data (`title`, `priority`, `due_date`, `confidence`) without executing tasks.

**Do:**
- [ ] Define Pydantic output models and reject invalid results.
- [ ] Test ambiguous and adversarial inputs.
- [ ] Compare long-vs-short prompts and document the tradeoffs.
- [ ] Add golden-case automated tests (minimum 15).

**Exit check:** Your app never trusts unvalidated AI-generated JSON as an instruction.

#### Week 3 - Local models and inference servers
**Understand:** open-weight models, licenses, quantization, CPU/GPU/RAM/VRAM constraints, context length, tokens/second, latency vs throughput, model download sizes.

**Build:** A model selector that switches between a hosted model and a small local Ollama model using a stable application interface.

**Do:**
- [ ] Run a model with Ollama and call its local HTTP API.
- [ ] Benchmark 10 identical tasks across local/cloud models.
- [ ] Document data privacy, quality, speed, and running costs.
- [ ] Stretch: test llama.cpp; explore vLLM only if hardware permits.

**Exit check:** The application can change its model without rewriting core business logic.

#### Week 4 - Your first deployable AI service
**Understand:** FastAPI endpoints, streaming, HTTP errors, environment variables, Dockerfiles, health checks, logs, and simple UI integration.

**Build:** A minimal web chat interface backed by `POST /chat` or a streaming endpoint.

**Do:**
- [ ] Add `/health` and `/ready` checks.
- [ ] Create a Docker image and `compose.yaml`.
- [ ] Deploy the app to your own laptop or LAN; open it from another device if your network permits.
- [ ] Keep API keys server-side, never in browser JavaScript or Git.

**Exit check:** `docker compose up -d --build` launches a usable app after a clean restart.

### Phase B - Retrieval and knowledge systems (Weeks 5-8)

#### Week 5 - Document ingestion and embedding fundamentals
**Understand:** embeddings, semantic similarity, data parsing, chunk sizes/overlap, document structure, metadata, provenance, OCR, deduplication, content hashing, incremental ingestion.

**Build:** A pipeline that extracts 20-100 permitted PDFs/Markdown/DOCX files using Docling, creates chunks, and stores source metadata.

**Do:**
- [ ] Preserve source filename/page/section and a stable document ID.
- [ ] Compare two chunking methods, including heading-aware chunking.
- [ ] Make re-ingestion idempotent (no duplicate chunks).
- [ ] Test malformed or scanned documents and record extraction failures.

**Exit check:** Every retrievable chunk can be traced to an original document.

#### Week 6 - Basic Retrieval-Augmented Generation (RAG)
**Understand:** embedding index, vector search, nearest neighbors, cosine similarity, retrieval top-k, context packing, answer grounding, citations, abstention.

**Build:** `/ask` API + chat UI that answers questions over your document collection and cites specific source files/pages.

**Do:**
- [ ] Store/retrieve chunks in Qdrant or pgvector.
- [ ] Compare `LLM alone` vs `vector retrieval + LLM` on 20 questions.
- [ ] Return citations and an explicit "insufficient evidence" answer when retrieval is poor.
- [ ] Deploy the RAG API and vector database with persistent volumes.

**Exit check:** The system cites actual retrieved material; nonexistent sources are never fabricated.

#### Week 7 - Advanced RAG, reranking, and retrieval evaluation
**Understand:** dense vs sparse retrieval (BM25), hybrid search, rank fusion, reranking, metadata filtering, query expansion, multi-query retrieval, parent-child chunks, retrieval precision/recall, nDCG, groundedness.

**Build:** Improve Week 6's system using **hybrid retrieval + a reranker**.

**Do:**
- [ ] Add exact-term retrieval so IDs and error codes remain searchable.
- [ ] Compare 3 pipelines: dense-only, hybrid, hybrid + reranking.
- [ ] Build at least 30 query/expected-source evaluation cases.
- [ ] Record quality, p50/p95 latency, and cost across the alternatives.

**Exit check:** You can justify whether more complex retrieval actually improves your own test data.

#### Week 8 - Beyond simple PDF RAG
**Understand:** text-to-SQL safety, structured data retrieval, document/table/figure processing, routing data sources, GraphRAG, multimodal RAG and their tradeoffs.

**Build:** A router that can retrieve from **documents** or a **read-only SQLite/PostgreSQL dataset** with parameterized or tightly validated queries.

**Do:**
- [ ] Use a restricted database user; never allow generic SQL execution against a real production database.
- [ ] Show the source path (document citation or query/data reference) with each answer.
- [ ] Experiment with one of: table-aware RAG, OCR images, graph-based retrieval, or multi-hop questions.
- [ ] Add a refusal/fallback for questions outside available data.

**Exit check:** You understand when RAG, SQL, or a plain deterministic API is the best answer.

### Phase C - Agents, MCP, and interoperability (Weeks 9-12)

#### Week 9 - Function calling and the single-agent loop
**Understand:** tool definitions and schemas, planning vs execution, tool selection, bounded loops, retries, budgets, action observation, side effects, deterministic workflow vs autonomous agent.

**Build:** A personal assistant with 2-3 **read-only** tools (search documents, query test SQL data, read a calendar fixture or local task list).

**Do:**
- [ ] Implement and inspect tool calls without a framework once.
- [ ] Rebuild using either OpenAI Agents SDK or Pydantic AI.
- [ ] Cap tool calls, execution time, and token budget.
- [ ] Force a human approval gate before any write/delete/email action.

**Exit check:** You can follow a trace and explain every tool decision and effect.

#### Week 10 - Durable agents, state, memory, and Agent Skills
**Understand:** ephemeral conversation history vs persistent memory, context compaction, retrieval-based memory, checkpointing, resumable tasks, human-in-the-loop, workflow orchestration, reusable Agent Skills (`SKILL.md`).

**Build:** Add task history, an approval queue, and resumable execution. Consider LangGraph when explicit state transitions are important.

**Do:**
- [ ] Save execution/checkpoint state in persistent storage.
- [ ] Stop and restart the service mid-task; recover without repeating side effects.
- [ ] Implement one portable Agent Skill for a repeatable low-risk task.
- [ ] Test a bad memory entry and a malicious/untrusted skill instruction.

**Exit check:** A failed task can resume safely and an audit trail explains its actions.

#### Week 11 - Build and deploy your own MCP server
**Understand:** MCP **tools vs resources vs prompts**, MCP clients/hosts/servers, local stdio, remote Streamable HTTP, JSON-RPC, authentication, consent, network boundaries and least privilege.

**Build:** `personal-knowledge-mcp`: a small MCP server exposing `search_notes`, `get_note`, and optionally `list_collections` to authorized clients.

**Do:**
- [ ] Use the **official MCP Python SDK v2** (follow its current API, not old v1 tutorial snippets).
- [ ] Start with local `stdio` and test with an MCP Inspector or compatible client.
- [ ] Expose the same *read-only* capabilities over Streamable HTTP as a service with a `/mcp` endpoint.
- [ ] Dockerize the remote server; protect it with appropriate authentication/authorization before allowing remote access.
- [ ] Test input validation, denial of unauthorized requests, and minimal credentials.
- [ ] Make it usable by at least one real MCP-capable client, preferably two.

**Exit check:** You understand why a local stdio MCP server is deployed differently from a remotely hosted HTTP MCP server.

**2026 note:** MCP specification `2026-07-28` introduces a stateless core, multi-round-trip interactions, routing changes, and authorization hardening. For new remote deployments, prefer Streamable HTTP; legacy standalone SSE transport is not the recommended new default.

#### Week 12 - Multi-agent patterns and agent communication
**Understand:** single-agent vs multi-agent tradeoffs; supervisor, delegation, handoff, parallel specialists, communication contracts, failure isolation; A2A Agent Cards, Tasks, and Artifacts.

**Build:** A **Research Agent** delegates to a **Document Agent** and a **Data Agent**, which return sourced results for the parent to synthesize.

**Do:**
- [ ] Implement a two-agent handoff locally first.
- [ ] Compare with the equivalent single agent; retain multiple agents only if helpful.
- [ ] Stretch: expose one agent via the **A2A protocol** and invoke it from a separate process.
- [ ] Log the reason for delegation, result and failure handling.

**Exit check:** You know MCP connects agents to **tools/data**, while A2A connects **agents to other agents**.

### Phase D - Experiences, quality, security, deployment (Weeks 13-16)

#### Week 13 - Agent user interfaces and multimodal experiments
**Understand:** event streaming, progressive updates, approval dialogs, shared state, AG-UI (agent-to-app interaction), A2UI (declarative agent-generated UI), image/audio input, realtime voice, browser/computer use.

**Build:** An agent console with streaming answers, cited retrieval, tool-call timeline, explicit approvals, and status/error states.

**Do:**
- [ ] Implement streaming tool/progress events in UI.
- [ ] Experiment with **AG-UI 1.0** or a compatible frontend adapter (optional).
- [ ] Experiment with one modality: receipt/photo understanding, voice input, or an agent-driven UI widget.
- [ ] Stretch: Playwright browser interaction in a sandbox with confirmation before external actions.

**Exit check:** Users can tell what the AI is doing and can stop/approve consequential operations.

#### Week 14 - Evaluations, traces, red teaming, and security
**Understand:** offline/online evals, golden datasets, regression testing, answer relevance, faithfulness, retrieval recall@k, tool-call success, latency/cost budgets, observability, prompt injection, data exfiltration and excessive agency.

**Build:** A quality dashboard / test suite with Langfuse (or equivalent), pytest and an intentionally adversarial input set.

**Do:**
- [ ] Build **50+** test cases including normal, no-answer, stale-data and hostile-input cases.
- [ ] Trace model calls, retrieval, tool execution, failures and costs; redact sensitive data.
- [ ] Compare at least 2 changes against a fixed eval baseline.
- [ ] Follow **OWASP GenAI LLM Top 10 (2026)** and test prompt injection via retrieved documents and MCP tool results.
- [ ] Never trust natural-language model output as an authorization check; enforce permissions in code.

**Exit check:** A regression test can catch a quality or security failure before redeployment.

#### Week 15 - Production-like deployment and operation
**Understand:** multi-service Compose, configuration vs secrets, auth, TLS, reverse proxies, private networks, persistent volumes, backups, migrations, health probes, structured logs, audit logs, CI/CD, rollback, rate limiting.

**Build:** An integrated deployment: UI + FastAPI + agent runtime + RAG store + MCP server + persistence + tracing.

**Do:**
- [ ] Containerize services and pin compatible dependency versions.
- [ ] Configure healthchecks, restart policies, resource limits and data volumes.
- [ ] Keep MCP and databases **private by default**; expose only necessary authenticated entry points.
- [ ] Deploy on a personal Linux server/VPS or private LAN; use a reverse proxy with HTTPS for public traffic.
- [ ] Consider Cloudflare Tunnel + Access for controlled remote access; a tunnel alone does not replace application authorization.
- [ ] Verify restart, backup/restore, upgrade, and rollback; run smoke tests from a second device.

**Exit check:** A fresh machine with your instructions and permitted secrets can reproduce the stack.

#### Week 16 - Capstone, benchmark, and publish
**Understand:** system tradeoffs, dependency risk, cost management, operational runbooks, reproducibility, portfolio storytelling.

**Build:** Finalize Personal AI Workbench or a capstone from Section 5.

**Do:**
- [ ] Run ingestion end-to-end and demonstrate sourced RAG answers.
- [ ] Demonstrate an agent using your MCP server in a controlled workflow.
- [ ] Demonstrate an approval gate, a refused unauthorized action, and agent recovery after restart.
- [ ] Include a deployment walkthrough, architecture diagram, 50-case evaluation report and screenshots.
- [ ] Tag a Git release (e.g., `v1.0.0`) and publish a sanitized portfolio demo if allowed.

**Exit check:** Another developer can install, test and deploy your project from its documentation.

## 2. Reference architecture

```text
User / Browser
     |
     v
Web UI (Streamlit / Next.js / AG-UI optional)
     |
     v
FastAPI Gateway (authentication, rate limits, audit logs)
     |
     v
Agent Orchestrator (Agents SDK / Pydantic AI / LangGraph)
     |-------------> LLM Provider / Ollama / vLLM
     |-------------> Session + Checkpoint Store (PostgreSQL)
     |-------------> RAG Search API ----------------------+
     |                                                     |
     |                                                Vector DB
     |                                                (Qdrant/pgvector)
     |                                                     ^
     |                                                Embeddings
     |                                                     ^
     |                                           Docling + Chunking
     |                                                     ^
     |                                               Allowed Documents
     |
     +-------------> MCP Client --> MCP Server --> Safe tools/read-only APIs
     |
     +-------------> Optional A2A Client --> Specialist Agent Service

Across the system: evaluation suite, tracing, metrics, logs, secrets, backups.
Deployment: separate Docker Compose services; private internal networking.
```

### Separate deployment exercises

| Service | Minimum deployable unit | Acceptance test | Deployment hazard |
|---|---|---|---|
| RAG | FastAPI `/ingest` and `/ask` + persisted Qdrant volume | Query source-cited answer after restart; duplicate ingestion is safe | Data leakage, duplicate/stale indexes, unsupported citations |
| Agent | API endpoint + workflow state + bounded tools | Stop service mid-run; resume safely; approval is required for write action | Repeated side effects, unlimited tool loops, long-running failures |
| Local MCP | `stdio` server launched by an MCP client | Client discovers and calls one read-only tool | Local file/process permissions and malicious instructions |
| Remote MCP | Streamable HTTP `/mcp` behind auth | Authorized client works; unauthorized one fails | Public unauthenticated tool exposure, token forwarding, SSRF |
| Full stack | Compose with UI, API, model access, DB, MCP, observability | Cold boot, healthcheck, backup/restore, remote HTTPS login | Secrets, migrations, resource limits, no rollback |

## 3. The 2026 technology radar

Prioritize concepts first. These tools/protocols are worth exploring **after** the core exercises:

| Topic | Why learn it | Suggested experiment | Priority |
|---|---|---|---|
| MCP 2026-07-28 / Python SDK v2 | Portable tools/resources/prompts and modern remote transport | Ship one stdio and one authenticated HTTP MCP endpoint | Core |
| OpenAI Responses API / Agents SDK; Pydantic AI | Modern model tools, structured outputs, code-first agents | Implement one agent two ways | Core |
| LangGraph durable state | Reliable long-running workflows, checkpoints, approvals | Resume after process restart | Core for complex agents |
| Hybrid RAG / rerank / retrieval evals | Better retrieval precision/recall | Benchmark dense vs hybrid vs reranked | Core |
| Langfuse or Phoenix | AI traces, prompt experiments, quality monitoring | Debug a bad tool decision using a trace | Core |
| A2A | Interoperable agent-to-agent communication | Deploy a specialist agent with an Agent Card | Intermediate |
| Agent Skills (`SKILL.md`) | Reusable, on-demand task expertise | Package a documentation/checklist workflow | Intermediate |
| AG-UI 1.0 | Structured live events between agent and frontend | Show tool timeline and approvals in React | Intermediate |
| A2UI | Safe declarative UI generated by an agent | Generate a simple dashboard card/form from agent output | Optional |
| Multimodal RAG | Retrieve information from scans, charts, images, audio | Ask a question about a figure in a document | Intermediate |
| Ollama / llama.cpp | Practical local inference, privacy and model swapping | Run a small model offline | Core |
| vLLM | Higher-throughput self-hosted serving with standard APIs | Serve an open-weight model on a suitable GPU | Advanced |
| LiteLLM Gateway | Multi-provider routing, budgets and fallbacks | Route two providers with spending limits | Intermediate |
| Computer/browser use + Playwright | Agents interacting with interfaces | Automate a test website with approval and sandbox | Advanced |
| LoRA/QLoRA, PEFT | Lightweight model adaptation | Fine-tune a small model on *permitted* data | Advanced optional |
| GraphRAG / knowledge graphs | Structured entity-relation retrieval | Compare graph vs standard RAG on multi-hop questions | Advanced optional |
| Real-time voice / TTS / ASR | Interactive spoken experiences | Add voice input/output to a safe read-only assistant | Optional |
| n8n / Dify / Flowise | Low-code automation and rapid workflow prototyping | Trigger a RAG summarization job from a test event | Optional |

**Latest protocol distinction:**
- **MCP:** agent/application <-> tools, prompts, and resources.
- **A2A:** an agent/application <-> another independently hosted agent.
- **AG-UI:** user interface <-> agent runtime events/state/interactions.
- **A2UI:** agent describes portable UI components for a client renderer.
- **Agent Skills:** reusable instructions/scripts/resources for how to carry out a task; not the same as an MCP service.

## 4. Working habits and quality gates

For every project or feature, complete this mini-cycle:

1. **Define** 5-10 explicit acceptance tests and failure cases.
2. **Prototype** a simple deterministic approach first (plain Python or API call).
3. **Add AI** only where variability or natural language is useful.
4. **Evaluate** correctness, sources, tool safety, latency and cost.
5. **Trace** unexpected tool decisions and retrieval mistakes.
6. **Secure** untrusted inputs, permissions, secrets and network access.
7. **Deploy** in containers; validate restart and failure recovery.
8. **Document** decisions, changed files, test results, and known limitations.

### Graduation criteria (minimum)

- [ ] A versioned, deployable web app with containerized backend and documented setup.
- [ ] RAG from at least 20 permitted documents, with citations and refusal when evidence is missing.
- [ ] A benchmark set of at least 50 realistic questions/actions, with regression results.
- [ ] One model-driven agent with at least two tools and a maximum tool/step budget.
- [ ] One tested MCP server (stdio + optionally authenticated Streamable HTTP).
- [ ] A visible, enforced human-approval step for consequential side effects.
- [ ] Persistent app/agent state, structured logs/traces, and failure recovery.
- [ ] Healthchecks, authentication, backups, no committed secrets, and a repeatable deployment.

## 5. Capstone ideas

### A. Personal Knowledge Copilot (recommended first)
- Upload your own notes/manuals/PDFs; ask grounded questions and get source citations.
- Use an agent to search a local read-only task database and summarize relevant results.
- Expose search via your own MCP server; optionally connect another agent via A2A.
- Deploy on your home network with an authenticated UI.

### B. Home-lab Operations Assistant
- Collect Docker container status, disk alerts and application logs in read-only mode.
- Agent summarizes incidents and suggests a recovery plan.
- A human approves any restart or system-changing command.
- Add local-only deployment, audit logs and rollback.

### C. AI Game Master / RPG Companion
- Build a game-world RAG index of lore, quests and characters.
- Use multiple agents for narrator, rules and inventory with persisted game state.
- Optional voice input, image understanding and agent-generated UI cards.
- Keep game rules and inventory changes deterministic and validated.

### D. Developer Documentation Assistant
- Ingest an **authorized** Git/Gitea wiki or a sample public repository.
- Agent explains architecture and proposes task documentation updates.
- MCP server exposes read-only repository search; all write/push actions require explicit approval.
- Add evaluation cases for stale documentation and unauthorized data requests.

## 6. Suggested project repository

```text
ai-hobbyist-workbench/
  README.md
  ROADMAP.md
  CHANGELOG.md
  .env.example
  .gitignore
  pyproject.toml
  uv.lock                    # if using uv
  compose.yaml
  compose.production.yaml
  Dockerfile
  docs/
    architecture.md
    deployment.md
    security.md
    decisions/
  apps/
    api/                      # FastAPI routes and auth
    ui/                       # Streamlit or Next.js
    agent/                    # tool loop, workflow, approvals
    rag/                      # parsers, chunking, retrieval, rerank
    mcp_server/               # MCP protocol adapter and allowed tools
  skills/
    doc-summary/SKILL.md
  data/
    sample/                   # synthetic or permitted examples only
  evals/
    cases.jsonl
    benchmark.py
  tests/
    test_api.py
    test_rag.py
    test_agent.py
    test_mcp.py
  scripts/
    ingest.py
    backup.sh
    smoke_test.py
```

Keep secrets, tokens, private data, large model weights and local vector indexes out of Git. Use an explicit backup/restore procedure for persistent data.

## 7. Official learning resources (verified October 2026)

### Foundations, models, and agents
- OpenAI Responses / tools: https://developers.openai.com/api/docs/guides/tools
- OpenAI Agents SDK: https://developers.openai.com/api/docs/guides/agents/sdk
- Pydantic AI: https://pydantic.dev/docs/ai/overview/
- LangChain/LangGraph learning: https://docs.langchain.com/oss/python/learn
- LangGraph persistence: https://langchain-ai.github.io/langgraph/concepts/durable_execution/
- Ollama local API: https://github.com/ollama/ollama/blob/main/docs/api/introduction.mdx
- vLLM serving: https://docs.vllm.ai/en/latest/serving/openai_compatible_server/
- LiteLLM Gateway: https://docs.litellm.ai/docs/simple_proxy

### RAG and evaluations
- Docling: https://docling-project.github.io/docling/
- Qdrant hybrid retrieval: https://qdrant.tech/documentation/search-tuning/hybrid-search/
- Qdrant reranking: https://qdrant.tech/documentation/tutorials-basics/reranking-hybrid-search/
- Langfuse: https://langfuse.com/docs
- Langfuse evaluations: https://langfuse.com/docs/evaluation/overview

### Protocols, agents, and UX
- MCP 2026-07-28 release: https://blog.modelcontextprotocol.io/posts/2026-07-28/
- MCP Python SDK v2: https://py.sdk.modelcontextprotocol.io/
- MCP server transport guidance: https://py.sdk.modelcontextprotocol.io/run/
- A2A protocol: https://a2a-protocol.org/latest/
- A2A core concepts: https://a2a-protocol.org/latest/topics/key-concepts/
- Agent Skills open standard: https://agentskills.io/specification
- AG-UI protocol: https://www.copilotkit.ai/ag-ui
- AG-UI 1.0 (September 30, 2026): https://www.copilotkit.ai/blog/ag-ui-1.0
- A2UI: https://a2ui.org/

### Deploy and secure
- Docker Compose: https://docs.docker.com/compose/
- Compose production guidance: https://docs.docker.com/compose/how-tos/production/
- Cloudflare Access self-hosted applications: https://developers.cloudflare.com/cloudflare-one/access-controls/applications/http-apps/
- OWASP GenAI LLM Top 10 (2026): https://genai.owasp.org/initiative/owasp-top-10-for-llm-and-genai/

---

## 8. Optional fast-track (if you already know Python, SQL, REST, Docker)

- **Week 1:** Combine curriculum Weeks 1-4 into one deployable LLM chat API.
- **Weeks 2-3:** Implement and deploy RAG, then hybrid retrieval and citations.
- **Weeks 4-5:** Build tool calling, a single agent, approvals and persisted state.
- **Weeks 6-7:** Build and deploy MCP (local stdio + authenticated remote HTTP).
- **Week 8:** Add multi-agent experiment / A2A and streaming UI.
- **Week 9:** Add 50-case evals, traces, OWASP tests and reliability hardening.
- **Week 10:** Containerize the integrated capstone, document and demo it.

**What not to rush:** authentication, private-data handling, tool permissions, evaluation and restart/recovery tests.