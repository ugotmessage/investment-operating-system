# Development Roadmap

## Delivery strategy

Build one complete vertical slice before adding broad platform features. The first milestone is a testable earnings-call workflow for one company and one quarter.

## Phase 0 — Specification baseline

Deliverables:

- repository documentation structure;
- core data contracts;
- evidence and citation rules;
- company playbook schema;
- Prediction Card schema;
- acceptance tests.

Exit criteria:

- Agent can read the docs in order and identify MVP scope without guessing.

## Phase 1 — Source ingestion MVP

Deliverables:

- Python project skeleton;
- company YAML configuration;
- official IR discovery;
- PDF, HTML, webcast, and audio downloader;
- source manifest and checksums;
- ffmpeg audio extraction;
- retry, deduplication, and resumability.

First target: TSM / one selected earnings period.

## Phase 2 — Transcript intelligence

Deliverables:

- faster-whisper or WhisperX integration;
- timestamps;
- speaker diarization where available;
- financial terminology correction;
- prepared remarks and Q&A segmentation;
- structured analyst question and management answer records.

## Phase 3 — Research and expectation engine

Deliverables:

- company and industry playbook loader;
- prior-guidance extraction;
- expectation matrix;
- financial metric and guidance extraction;
- historical wording comparison;
- evidence-linked Bull, Bear, and Unknown analysis;
- Markdown, JSON, and Telegram outputs.

## Phase 4 — Prediction and checkpoint engine

Deliverables:

- immutable Prediction Ledger;
- automatic checkpoint compiler;
- scheduler;
- outcome-source collection;
- independent validation reviewer;
- direction, magnitude, timing, and causal scoring;
- error attribution.

## Phase 5 — Controlled learning

Deliverables:

- topic-specific management credibility;
- signal-weight history;
- versioned playbook proposals;
- approval and rollback workflow;
- Alpha Memory queries;
- 30-, 90-, 180-, and 365-day validation reports.

## Phase 6 — Multi-company and industry graph

Deliverables:

- multiple company configurations;
- industry playbooks;
- knowledge graph for company, product, customer, supplier, equipment, and materials;
- supply-chain transmission analysis;
- cross-company evidence reuse with source provenance.

## Phase 7 — Portfolio layer

Only after research and validation are stable:

- portfolio exposure mapping;
- thesis overlap and correlation;
- position-sizing suggestions;
- catalyst and invalidation monitoring;
- risk-manager and CIO review.

Autonomous order execution remains out of scope until separately designed and approved.

## Engineering standards

- Typed Python interfaces
- SQLite for MVP, migration path to PostgreSQL
- Idempotent and resumable jobs
- Structured logs
- Unit and integration tests
- Golden test fixtures for transcript and metric extraction
- No unsupported exact financial number in final outputs
- No automatic core-prompt mutation

## MVP definition of done

1. A command runs one TSM earnings period end to end.
2. Official sources are versioned and auditable.
3. Missing transcript is generated from audio with timestamps.
4. Prepared remarks and Q&A are separated.
5. A company-specific playbook drives the questions asked.
6. Actual results are compared with a pre-event expectation matrix.
7. Conclusions contain evidence and counter-evidence.
8. At least one immutable Prediction Card is created.
9. At least one checkpoint can later be executed and scored.
10. The same job can safely resume after interruption.
