# Testing Strategy and Checklist
Version: 0.1
Status: Initial checklist; commands depend on repository setup

## Testing principles
- Tests must verify behavior, not merely that code compiles.
- Keep evaluation data small, public, and reproducible.
- Never use confidential or personal documents as test fixtures.
- Record commands and actual outcomes.
- Do not claim test coverage or performance without evidence.

## 1. Setup and health
- [ ] A clean clone can follow the README to configure and start the system.
- [ ] Rust service health endpoint returns the documented response.
- [ ] Python service health endpoint works if a separate service exists.
- [ ] Missing configuration fails with a useful error.
- [ ] An unavailable dependency is reported clearly.

## 2. Input validation
- [ ] Empty document is rejected or handled according to documented rules.
- [ ] Oversized request is rejected safely.
- [ ] Malformed request returns the documented 4xx response.
- [ ] Invalid top-k value is rejected or bounded.
- [ ] Unsupported file type is rejected with a useful message.
- [ ] Repeated ingestion has documented, tested behavior.

## 3. Ingestion and chunking
- [ ] Chunk boundaries and overlap are deterministic for fixed settings.
- [ ] Source metadata is retained.
- [ ] Empty or whitespace-only content is handled.
- [ ] Embedding failures do not leave inconsistent records.
- [ ] Model/version mismatch is detected or prevented.
- [ ] Database errors are handled without leaking credentials.

## 4. Retrieval quality
- [ ] Known queries retrieve expected source IDs.
- [ ] No-result queries return a predictable response.
- [ ] Similarity scores and ranking direction are documented.
- [ ] Recall@k is measured on a labelled query set.
- [ ] MRR or another ranking metric is measured when the dataset supports it.
- [ ] Evaluation set and model parameters are versioned.

## 5. Answer generation (only if included)
- [ ] Answers include source references.
- [ ] Unsupported questions do not produce fabricated source claims.
- [ ] Provider timeout and rate-limit behavior is handled.
- [ ] Prompt injection contained in retrieved documents is treated as untrusted input.
- [ ] Secrets and private document content are not emitted in logs.

## 6. Rust/API behavior
- [ ] Invalid requests return stable, documented error shapes.
- [ ] Downstream timeout does not hang requests indefinitely.
- [ ] Concurrent requests do not corrupt shared state.
- [ ] Graceful shutdown works.
- [ ] Logs include request IDs but exclude secrets.
- [ ] CORS and exposed endpoints are configured deliberately if deployed.

## 7. Integration and resilience
- [ ] End-to-end ingestion-to-query flow passes.
- [ ] Database restart behavior is understood and tested.
- [ ] Downstream service failure returns a controlled error.
- [ ] Retry behavior is bounded; no uncontrolled retry loop.
- [ ] Duplicate submissions behave consistently.

## 8. Performance
- [ ] Benchmark dataset and environment are documented.
- [ ] Warm-up and measurement procedure are documented.
- [ ] p50 and p95 latency are recorded.
- [ ] Throughput and concurrency are recorded.
- [ ] Memory usage is recorded where practical.
- [ ] Baseline and optimized versions use comparable conditions.
- [ ] Performance claims are limited to what the benchmark actually measures.

## 9. Release gate
- [ ] Formatter passes.
- [ ] Linter passes.
- [ ] Unit tests pass.
- [ ] Integration tests pass.
- [ ] Clean-clone setup is verified.
- [ ] Known limitations are documented.
- [ ] No secrets are committed.
- [ ] `audit.md` is updated with evidence.

## Results log
| Date | Command / scenario | Environment | Result | Notes |
|---|---|---|---|---|
| Not run | Not run | Not recorded | Not run | No repository has been inspected yet |
