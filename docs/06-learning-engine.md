# Learning and Research Evolution Engine

## Purpose

The Learning Engine converts validated outcomes into controlled improvements. Its objective is not to make the Agent change itself after every mistake. Its objective is to accumulate evidence about which research signals, management statements, causal models, and checkpoints are useful.

## Two separate pipelines

```text
Research Pipeline
Evidence → Analysis → Prediction → Publication

Learning Pipeline
Checkpoint → Outcome → Independent Review → Error Attribution
→ Learning Proposal → Human/CIO Approval → Versioned Update
```

The research process must never grade and rewrite itself in one uncontrolled step.

## Learning objects

### Signal performance

Track performance by company, industry, topic, prediction type, and horizon. Examples:

- absolute CapEx guidance;
- CapEx driver quality;
- management supply wording;
- gross-margin guidance;
- customer inventory commentary;
- analyst consensus revisions.

Each signal record should contain sample size, directional accuracy, calibration, average lead time, false-positive rate, and last update date.

### Management credibility

Credibility is topic-specific, not one score per executive or company. Track separately:

- revenue guidance accuracy;
- margin guidance accuracy;
- CapEx guidance accuracy;
- product schedule accuracy;
- demand-language accuracy;
- optimistic or conservative bias.

### Alpha Memory

Alpha Memory stores reusable lessons rather than raw document summaries. Each memory must contain:

- context and market regime;
- original prediction and outcome;
- useful signal or failed assumption;
- applicable companies or industries;
- evidence and confidence;
- expiration or revalidation date.

### Research-process metrics

Measure:

- unsupported-claim rate;
- citation completeness;
- prediction definition quality;
- checkpoint completion rate;
- confidence calibration;
- directional, magnitude, timing, and causal accuracy;
- repeat-error rate;
- playbook proposal acceptance rate.

## Learning proposal

The Learning Engine may propose changes but may not silently apply material methodology changes.

```yaml
proposal_id: LP-TSM-2027-001
kind: signal_weight_update
target: company.TSM.research_priorities.capex_absolute
old_value: 0.80
proposed_value: 0.45
reason: CapEx headline value showed low predictive power; driver classification was materially stronger.
evidence:
  sample_size: 12
  directional_accuracy_old: 0.42
  directional_accuracy_related_driver: 0.79
confidence: 0.84
review_required: true
status: proposed
```

Supported proposal types:

- add, remove, or reframe a research question;
- change a signal weight;
- change management credibility by topic;
- adjust checkpoint timing;
- add a causal edge to the knowledge graph;
- add an interpretation trap or counter-thesis;
- modify a validation criterion.

## Approval and rollback

Every accepted update must record:

- prior version;
- new version;
- approving reviewer;
- evidence set;
- effective date;
- rollback condition.

Playbook files and model configuration must remain version controlled. A proposed change based on a very small sample, a single market regime, or an external shock should normally remain experimental.

## Confidence calibration

Predictions grouped near 70% confidence should be correct approximately 70% of the time under the chosen scoring definition. The system should report calibration curves by prediction type and company. Overconfidence is an error category and must influence future confidence generation.

## Research evolution cadence

- Event-level: validate exact event predictions.
- Quarterly: update unresolved questions and management credibility.
- Semiannual: review signal weights and checkpoint timing.
- Annual: review company and industry playbook structure, regime changes, and stale Alpha Memory.

## Safety rails

The Learning Engine must not:

- alter immutable historical predictions;
- delete failed predictions;
- optimize only for short-term stock-price direction;
- treat one successful trade as proof of causality;
- overwrite core evidence rules;
- automatically apply major changes without review;
- learn from outcome data that was unavailable at the prediction timestamp as if it were original evidence.
