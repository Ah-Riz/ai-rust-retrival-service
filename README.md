# ai-rust-retrieval-service

Minimal Rust HTTP API (Axum + Tokio) for a local semantic retrieval service. Phase 1: health check only.

## Prerequisites

- Rust toolchain (`rustc`, `cargo`)

## Setup

```bash
cp .env.example .env
```

Defaults: `HOST=127.0.0.1`, `PORT=8080`.

## Run

```bash
cargo run
```

## Verify

```bash
curl -i http://127.0.0.1:8080/health
```

Expect HTTP 200 and:

```json
{"status":"ok"}
```

## Quality checks

```bash
cargo fmt
cargo fmt --check
cargo clippy
```

## Out of scope (later phases)

Python embeddings service, PostgreSQL/pgvector, ingest, and query APIs.