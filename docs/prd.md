# Product Requirements Document (PRD)
Version: 0.1
Status: Draft
Project: Rust-Powered AI Retrieval Service

## 1. Product summary
Build a small, production-oriented document retrieval API that demonstrates practical AI integration and reliable backend engineering. Python handles embedding/model-related work; Rust provides an API gateway and demonstrates where Rust can contribute to concurrency, reliability, and performance.

This is a portfolio project, not a claim of production-scale infrastructure.

## 2. Career objective
Demonstrate skills relevant to:
- Rust Backend Engineer
- AI Backend / LLM Application Engineer
- Applied AI Engineer (entry-level or project-oriented roles)
- Junior AI Infrastructure / Inference Engineer, where requirements fit

The repository must make the problem, architecture, tests, evaluation, and measured performance easy for a hiring manager to understand.

## 3. Problem
Teams often need to search internal documents and provide answers grounded in retrieved passages. A useful demonstration should show ingestion, embeddings, vector retrieval, source attribution, error handling, and measurable retrieval quality rather than only a chatbot UI.

## 4. Target users
- Primary: hiring managers and engineers reviewing the portfolio.
- Secondary: developers evaluating the service through its API.
- Demo users: people querying a small, non-sensitive sample document collection.

## 5. Core user journeys
1. A developer starts the system locally using documented commands.
2. A user submits a supported document for ingestion.
3. The service extracts or accepts text, chunks it, creates embeddings, and stores chunks with metadata.
4. A user submits a query.
5. The service retrieves relevant chunks and returns ranked results with source metadata.
6. If answer generation is enabled, the answer references retrieved sources and clearly handles insufficient evidence.
7. A reviewer runs automated tests and benchmark scripts and can reproduce the reported results.

## 6. MVP scope
### Must have
- A documented local development setup.
- A Rust HTTP API using Axum and Tokio, unless repository inspection identifies an existing better-fit stack.
- A Python service for embedding and/or inference, using FastAPI if a separate service is justified.
- PostgreSQL with pgvector, or a documented lightweight alternative if local setup becomes a blocker.
- Document/text ingestion with validation and useful error messages.
- Chunking and embedding pipeline.
- Similarity retrieval returning source IDs and relevant text snippets.
- Query endpoint returning ranked sources.
- Automated unit and integration tests for core paths.
- Docker-based local setup where practical.
- Reproducible evaluation and load-test scripts.
- README, architecture diagram, limitations, and benchmark methodology.

### Should have if time permits
- Basic answer generation using a configurable model/API.
- Request IDs and structured logs.
- Health/readiness endpoints.
- CI workflow.
- Small, public, non-sensitive evaluation corpus.

## 7. Out of scope
- Training a foundation model from scratch.
- Multi-tenant enterprise authentication and billing.
- Production claims about scale or security without evidence.
- Blockchain integration; it does not improve the core project goal.
- Complex autonomous agents or multi-agent orchestration.
- Kubernetes, elaborate cloud infrastructure, or premature microservices.
- Uploading private, copyrighted, confidential, or personal documents.
- Claims that Rust is faster without a fair benchmark.

## 8. Functional requirements
- FR-01: Validate requests and reject malformed inputs.
- FR-02: Ingest text/documents and retain source metadata.
- FR-03: Split text into deterministic chunks.
- FR-04: Generate embeddings consistently for ingestion and queries.
- FR-05: Retrieve top-k relevant chunks.
- FR-06: Return source attribution and ranking metadata.
- FR-07: Provide clear behavior when no relevant source is found.
- FR-08: Expose health endpoints for required services.
- FR-09: Provide reproducible test and evaluation commands.

## 9. Non-functional requirements
- Correctness: ingestion and query behavior covered by automated tests.
- Reproducibility: document model versions, parameters, environment, and commands.
- Observability: actionable errors and request-level logs without secrets.
- Performance: report measured latency/throughput; set targets only after a baseline exists.
- Maintainability: small modules, typed request/response schemas, clear configuration.
- Safety: no secrets committed; validate uploads; limit payload size; do not log full sensitive document content.

## 10. Success criteria
MVP is complete when:
- A new developer can start it using the README.
- A sample corpus can be ingested and queried end-to-end.
- Automated tests pass in a clean environment.
- Retrieval quality is evaluated on a small labelled query set.
- Load-test results include environment, dataset, concurrency, p50/p95 latency, and throughput.
- Every performance claim is backed by reproducible measurements.
- Known limitations and next steps are documented.

## 11. Key decisions / open questions
- Embedding model: TBD after checking hardware, license, and deployment constraints.
- Answer generation: optional for first milestone; retrieval-only is acceptable.
- Deployment target: local Docker first; public deployment only if secrets, costs, and abuse controls are addressed.
- File types: start with plain text/Markdown; add PDF only if it can be tested reliably.
- Rust/Python boundary: choose the simplest boundary that allows clear ownership and measurable value.

## 12. Risks
- Scope creep into a full RAG platform.
- Model/API costs or unavailable GPU resources.
- Poor retrieval evaluation due to an unrepresentative dataset.
- Rust gateway adding complexity without measurable benefit.
- Overstated performance claims.
- Deployment secrets or uploaded data mishandled.

## 13. Product principle
Ship a small, measurable, explainable system. Prefer evidence over feature count.
