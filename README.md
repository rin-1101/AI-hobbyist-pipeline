# AI Hobbyist Pipeline

A **16-week, project-based AI engineering learning path** for hobbyists who want to build and deploy real AI applications—not just experiment with prompts. Start with model APIs and local inference, then progress through RAG, AI agents, MCP servers, multi-agent protocols, evaluations, and production deployment.

**Audience:** Python developers and curious builders · **Pace:** 6–10 hours/week · **Approach:** Build → Test → Deploy → Document.

## Getting started

1. Start with [Lesson 01](lessons/01-llm-apis-and-inference/README.md).
2. For each lesson, study the concepts, build the mini-project, finish the checklist, and pass the exit check.
3. Commit your work and record your lessons learned. Advance only once you can demonstrate the outcome.
4. Read the [complete syllabus and technology reference](AI_Hobbyist_Roadmap_2026.md) for background, architecture, stack choices, security guidance, and source links.

## Lesson directory

| Week | Lesson | Phase |
|---|---|---|
| 01 | [APIs, inference, and the model mental model](lessons/01-llm-apis-and-inference/README.md) | LLM Foundations |
| 02 | [Context engineering, structured outputs, and deterministic boundaries](lessons/02-context-and-structured-outputs/README.md) | LLM Foundations |
| 03 | [Local models and inference servers](lessons/03-local-models/README.md) | LLM Foundations |
| 04 | [Your first deployable AI service](lessons/04-deployable-ai-service/README.md) | LLM Foundations |
| 05 | [Document ingestion and embedding fundamentals](lessons/05-document-ingestion-and-embeddings/README.md) | Retrieval & Knowledge |
| 06 | [Basic Retrieval-Augmented Generation (RAG)](lessons/06-basic-rag/README.md) | Retrieval & Knowledge |
| 07 | [Advanced RAG, reranking, and retrieval evaluation](lessons/07-advanced-rag-and-evaluation/README.md) | Retrieval & Knowledge |
| 08 | [Beyond simple PDF RAG](lessons/08-beyond-pdf-rag/README.md) | Retrieval & Knowledge |
| 09 | [Function calling and the single-agent loop](lessons/09-tool-calling-and-agent-loops/README.md) | Agents & Protocols |
| 10 | [Durable agents, state, memory, and Agent Skills](lessons/10-durable-agents-and-memory/README.md) | Agents & Protocols |
| 11 | [Build and deploy your own MCP server](lessons/11-mcp-server-deployment/README.md) | Agents & Protocols |
| 12 | [Multi-agent patterns and agent communication](lessons/12-multi-agent-and-a2a/README.md) | Agents & Protocols |
| 13 | [Agent user interfaces and multimodal experiments](lessons/13-agent-interfaces-and-multimodal/README.md) | Production & Publishing |
| 14 | [Evaluations, traces, red teaming, and security](lessons/14-evals-tracing-and-security/README.md) | Production & Publishing |
| 15 | [Production-like deployment and operation](lessons/15-production-deployment/README.md) | Production & Publishing |
| 16 | [Capstone, benchmark, and publish](lessons/16-capstone-and-publishing/README.md) | Production & Publishing |

## Learning outcomes

- Build applications using hosted and **local LLMs**.
- Develop **retrieval-augmented generation (RAG)** apps grounded in documents and data.
- Create **agents**, reusable tools, and **MCP servers**.
- Explore **multi-agent workflows**, A2A, streaming interfaces, and multimodal systems.
- Apply **evaluation, security, observability, Docker, and deployment** fundamentals.

## Repository structure

```text
.
├── README.md                         # Course introduction and lesson directory
├── AI_Hobbyist_Roadmap_2026.md      # Full curriculum and technology reference
└── lessons/
    ├── 01-llm-apis-and-inference/README.md
    ├── 02-context-and-structured-outputs/README.md
    ├── ...
    └── 16-capstone-and-publishing/README.md
```

## Recommended capstone

Build a **Personal AI Workbench** that combines a RAG knowledge base, an agent with controlled tools, your own MCP server, a web frontend, automated evaluations, and a Docker Compose deployment. See the [capstone ideas](AI_Hobbyist_Roadmap_2026.md#5-capstone-ideas) for alternatives.

> The lesson folders are **learning guides**, not completed project implementations. Build and version your exercise code as you work through the course.
