# Data and Storage Architecture

## MVP technology

Use SQLite for the first vertical slice, with repository interfaces designed for migration to PostgreSQL. Raw documents and media remain in object/file storage; structured metadata and normalized records live in the database.

## Core tables

- companies
- industries
- events
- research_runs
- sources
- source_versions
- documents
- transcript_segments
- speakers
- questions
- answers
- metrics
- guidance
- expectations
- claims
- claim_evidence
- playbook_versions
- knowledge_nodes
- knowledge_edges
- predictions
- checkpoints
- checkpoint_results
- validation_reviews
- error_attributions
- learning_proposals
- signal_weights
- management_credibility
- alpha_memory

## Immutability

Published Prediction Cards are append-only. Corrections create a new record linked to the original but never replace the original statement, criteria, confidence, or content hash.

## Provenance

Every derived object stores:

- research run ID;
- source IDs;
- parser and model versions;
- playbook versions;
- creation timestamp;
- confidence;
- whether it was programmatic, model-generated, human-authored, or reviewed.

## Source versioning

Sources store URL, retrieval timestamp, MIME type, checksum, source rank, access status, and content location. Changed source content creates a new version instead of silently replacing the prior copy.

## Job state

Long-running jobs use durable states: pending, running, blocked, failed_retryable, failed_terminal, completed, and superseded. Each stage is idempotent and can resume without duplicating unchanged artifacts.

## Retention and access

- Never commit copyrighted full transcripts or licensed reports to the public repository.
- Keep credentials and private source tokens outside the repository.
- Store only permitted extracts and evidence references.
- Support deletion and source-access revocation while retaining non-content audit metadata when legally allowed.
