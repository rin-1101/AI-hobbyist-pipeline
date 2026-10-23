# Hands-on — Your first deployable AI service

[Overview](README.md) · [Theory](theory.md) · [Resources](resources.md)

## Build

A minimal web chat interface backed by `POST /chat` or a streaming endpoint.

## Implementation workflow

1. Create a project directory and reproducible Python environment.
2. Define inputs, outputs, security boundaries, and expected errors.
3. Implement a minimal working version and run it locally.
4. Add tests for expected, edge, and failure cases.
5. Demonstrate or deploy the project as required.
6. Record benchmark results, known limitations, and next improvements.

## Required exercises

- [ ] Add `/health` and `/ready` checks.
- [ ] Create a Docker image and `compose.yaml`.
- [ ] Deploy the app to your own laptop or LAN; open it from another device if your network permits.
- [ ] Keep API keys server-side, never in browser JavaScript or Git.

## Deliverables

- [ ] Working project with setup and run instructions.
- [ ] Reproducible tests or screenshots of results.
- [ ] No secrets or private information committed to Git.
- [ ] Notes on at least one failure and how it was resolved.

## Definition of done

> `docker compose up -d --build` launches a usable app after a clean restart.

[Course directory](../../README.md) · [← 3](../03_local_models/README.md) · [5 →](../05_document_ingestion_and_embeddings/README.md)
