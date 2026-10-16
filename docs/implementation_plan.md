# Implementation Plan
Version: 0.1
Status: Planned
Source of truth: `prd.md`

## Working rules
- Work in small phases. Do not implement multiple phases in one unreviewed change.
- Inspect the existing repository before creating or replacing files.
- Do not invent completed work. Mark items complete only after running the relevant checks.
- Record decisions and deviations in `audit.md`.
- Use `task_today.md` as the single active task brief.
- If blocked, record the issue in `bugs.md` before attempting broad changes.

## Phase 0 — Repository and environment discovery
- [ ] Inspect repository structure, Git status, current language/framework versions, and existing conventions.
- [ ] Identify available Rust, Python, Docker, and PostgreSQL tooling.
- [ ] Record existing code and reusable components; do not overwrite them blindly.
- [ ] Confirm project name and license.
- [ ] Create or update this plan only after repository facts are known.

Acceptance: a short environment report exists and no existing work has been overwritten.

## Phase 1 — Minimal project skeleton
- [ ] Create a Rust API service with configuration and a health endpoint.
- [ ] Create a Python service only if the chosen model workflow requires a separate process.
- [ ] Add environment-variable examples with placeholders only.
- [ ] Add formatting/lint commands for Rust and Python.
- [ ] Add initial README with exact local setup steps.

Acceptance: services start locally and health checks pass.

## Phase 2 — Data model and storage
- [ ] Define document/source and chunk metadata.
- [ ] Choose PostgreSQL + pgvector or document a justified alternative.
- [ ] Add schema/migrations and deterministic seed/sample data.
- [ ] Define how embedding model/version metadata is recorded.
- [ ] Add validation for duplicate ingestion and invalid records.

Acceptance: schema can be created from a clean environment; persistence tests pass.

## Phase 3 — Ingestion and embeddings
- [ ] Implement text input validation.
- [ ] Implement deterministic chunking with documented parameters.
- [ ] Implement embedding generation behind a clear interface.
- [ ] Store chunks, vectors, and source metadata.
- [ ] Add tests for empty input, long input, malformed input, and repeated ingestion.

Acceptance: sample corpus ingests reproducibly and failures return useful errors.

## Phase 4 — Retrieval API
- [ ] Implement query validation and top-k bounds.
- [ ] Generate query embeddings using the same compatible model/version.
- [ ] Retrieve and rank chunks.
- [ ] Return source IDs, snippets, scores, and relevant metadata.
- [ ] Define behavior for empty results and service unavailability.
- [ ] Add unit and integration tests.

Acceptance: known test queries return expected relevant sources within agreed evaluation criteria.

## Phase 5 — Optional answer generation
- [ ] Decide whether answer generation adds value within the time budget.
- [ ] If included, add a provider/model abstraction and explicit configuration.
- [ ] Require answers to be grounded in retrieved sources.
- [ ] Handle insufficient evidence and provider errors.
- [ ] Add tests for unsupported questions and citation presence.

Acceptance: answer behavior is tested; otherwise document retrieval-only scope.

## Phase 6 — Quality, security, and observability
- [ ] Add structured logs and request IDs.
- [ ] Ensure secrets are never logged or committed.
- [ ] Add payload limits and safe input validation.
- [ ] Add health/readiness checks.
- [ ] Add tests for expected failures and service timeouts.
- [ ] Add CI for formatting, linting, and tests where feasible.

Acceptance: checks run from documented commands and common failures are understandable.

## Phase 7 — Evaluation and performance
- [ ] Create a small evaluation dataset with queries and expected source IDs.
- [ ] Calculate retrieval metrics such as Recall@k and MRR where appropriate.
- [ ] Add repeatable load tests.
- [ ] Report p50/p95 latency, throughput, and memory use where measurable.
- [ ] Record hardware, versions, parameters, and test methodology.
- [ ] Compare Rust gateway overhead against a clearly defined baseline only if the comparison is fair.

Acceptance: results can be reproduced; no unmeasured performance claims.

## Phase 8 — Portfolio polish
- [ ] Finalize architecture diagram.
- [ ] Document trade-offs, limitations, and future work.
- [ ] Add example requests and responses.
- [ ] Provide one-command local startup where practical.
- [ ] Verify a clean-clone setup.
- [ ] Create a short demo and a technical write-up.
- [ ] Review the project against the PRD and update `audit.md`.

Acceptance: an unfamiliar engineer can understand, run, test, and evaluate the project.

## Definition of done for every task
- [ ] Requirements met.
- [ ] Relevant tests added or updated.
- [ ] Formatting/lint checks run.
- [ ] Tests actually executed; results recorded.
- [ ] Docs updated.
- [ ] No secrets or unrelated changes.
- [ ] `audit.md` reflects actual state.
