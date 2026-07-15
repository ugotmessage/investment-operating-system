# Core Data Contracts

## Design goals

- Preserve provenance from source to final conclusion.
- Keep immutable historical records.
- Separate deterministic values from LLM interpretations.
- Make jobs idempotent and resumable.
- Support SQLite in the MVP and PostgreSQL later.

## Core entities

### Source

```yaml
source_id: src_...
company_id: TSM
period: 2026Q2
type: earnings_release
source_class: official_ir
url: https://...
retrieved_at: 2026-07-16T14:05:00+08:00
published_at: 2026-07-16T13:30:00+08:00
local_path: data/raw/TSM/2026Q2/earnings-release.pdf
sha256: ...
license_or_access_note: public_official
status: downloaded
```

### Evidence segment

```yaml
evidence_id: ev_...
source_id: src_...
location:
  page: 8
  timestamp_start: 2523.2
  timestamp_end: 2542.1
speaker: CEO
speaker_confidence: 0.94
original_text: ...
normalized_text: ...
language: en
extraction_confidence: 0.96
```

### Claim

```yaml
claim_id: claim_...
classification: management_claim
statement: AI accelerator demand remains supply constrained.
evidence_ids: [ev_101]
created_by: transcript_analyst
confidence: 0.91
is_inference: false
```

For inferences, preserve supporting and counter-evidence:

```yaml
claim_id: claim_...
classification: inference
statement: Packaging capacity is likely to remain a revenue constraint next year.
supporting_claim_ids: [claim_101, claim_118]
counter_claim_ids: [claim_126]
confidence: 0.68
is_inference: true
```

### Metric observation

```yaml
metric_id: metric_...
name: gross_margin_guidance
period: 2026Q3
low: 66.5
high: 68.5
midpoint: 67.5
unit: percent
currency: null
source_evidence_ids: [ev_202]
extraction_method: deterministic_regex_with_review
confidence: 0.99
```

### Expectation record

```yaml
expectation_id: exp_...
metric: gross_margin_guidance
as_of: 2026-07-15T23:59:59+08:00
source_type: sell_side_consensus
value: 67.9
unit: percent
source_ids: [src_401, src_402]
confidence: 0.78
availability: available
```

### Research report

Every report stores:

- event and company;
- data cutoff time;
- playbook and prompt versions;
- source manifest hash;
- claims and predictions generated;
- quality score;
- publication state.

### Prediction Card

Use the contract in `docs/04-prediction-validation.md`. The original content and hash are immutable. Checkpoint outcomes are append-only child records.

### Validation outcome

```yaml
validation_id: val_...
prediction_id: TSM-2026Q2-CAPEX-001
checkpoint_id: cp_...
reviewed_at: 2026-10-16T10:00:00+08:00
result: partially_correct
scores:
  direction: 1.0
  magnitude: 0.5
  timing: 1.0
  causal: 0.5
outcome_evidence_ids: [ev_801, ev_802]
root_causes: [causal_error]
reviewer_agent: validation_reviewer
reviewer_version: 0.1.0
```

### Learning proposal

Use the proposal contract in `docs/06-learning-engine.md`. Proposals are separate from applied changes and must preserve approval state.

## State machines

### Source job

```text
discovered → queued → downloading → downloaded → parsed → verified
                                      ↘ failed_retryable
                                      ↘ failed_terminal
```

### Prediction

```text
draft → reviewed → published_locked → checkpoint_due → under_review
→ validated | partially_validated | unverifiable
```

### Learning proposal

```text
proposed → under_review → accepted_experimental → accepted_active
                     ↘ rejected
                     ↘ needs_more_evidence
```

## Database tables for MVP

- companies
- earnings_events
- sources
- evidence_segments
- claims
- claim_evidence
- metric_observations
- expectations
- reports
- predictions
- prediction_checkpoints
- validation_outcomes
- error_attributions
- playbook_versions
- signal_performance
- management_credibility
- learning_proposals

## Provenance invariant

A final report sentence containing an exact financial number or direct management assertion must be traceable through claim → evidence segment → source. Any sentence without that chain must be explicitly labeled interpretation or unsupported and blocked by the publishing gate.
