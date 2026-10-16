# Active Task
Task ID: T-002
Status: Done
Goal: Minimal Rust HTTP API with config, health endpoint, .env.example, and README
start steps.
## Context
Phase 0 is done (see `audit.md`). No Python or Postgres in this task.
## Requirements
- Create a Rust Axum + Tokio service under `ai-rust-retrieval-service/`.
- Load `HOST` and `PORT` from environment (sensible defaults, e.g. `127.0.0.1:8080`).
- Expose `GET /health` returning JSON like `{"status":"ok"}` and HTTP 200.
- Add `.env.example` with placeholders only (no real secrets).
- Add `README.md` with exact commands to run and curl the health check.
- Add Rust format/lint commands documented in README (`cargo fmt`, `cargo clippy`).
- Do not add Python, Postgres, embeddings, or ingest/query APIs yet.
- Do not commit secrets.
## Deliverables
1. Compiling Cargo project with health route.
2. `.env.example`
3. `README.md` with setup + verify steps
4. Short note in `audit.md` that Phase 1 skeleton was verified (commands + results)
## Acceptance criteria
- [x] `cargo run` starts the server
- [x] `curl` to `/health` returns 200 and ok JSON
- [x] `cargo fmt --check` and `cargo clippy` documented (and run if possible)
- [x] No Python/DB code in this change
- [x] `audit.md` updated with evidence
## Reference files
- `prd.md` (MVP: documented local setup, health)
- `implementation_plan.md` Phase 1
- `audit.md`
ai_rust_retrieval_service