# Prediction Ledger and Checkpoint Engine

## Objective

Every testable research conclusion must create a future validation plan at the moment the conclusion is published. This prevents hindsight rewriting and turns research errors into structured learning data.

## Prediction Card

```json
{
  "prediction_id": "TSM-2026Q2-CAPEX-001",
  "created_at": "2026-07-15T17:00:00+08:00",
  "company": "TSM",
  "playbook_version": "company.TSM@0.1.0",
  "type": "causal_fundamental",
  "statement": "Incremental CapEx is primarily directed to advanced process and advanced packaging capacity rather than overseas construction inflation.",
  "confidence": 0.72,
  "time_horizon": "6_months",
  "evidence_ids": ["claim_101", "claim_118"],
  "counter_evidence_ids": ["claim_126"],
  "success_criteria": [
    "Management explicitly attributes most incremental CapEx to advanced-process or packaging capacity.",
    "Subsequent capacity or equipment guidance increases."
  ],
  "failure_criteria": [
    "Management attributes most incremental CapEx to overseas construction cost.",
    "Planned effective capacity does not increase."
  ],
  "checkpoints": [
    {"kind": "event", "due_at": "2026-07-16"},
    {"kind": "next_earnings", "due_at": "2026-10-15"},
    {"kind": "six_month", "due_at": "2027-01-15"}
  ],
  "immutable": true,
  "content_hash": "sha256:..."
}
```

## Prediction types

- Event prediction
- Fundamental prediction
- Causal prediction
- Financial estimate prediction
- Consensus revision prediction
- Market-reaction prediction
- Supply-chain transmission prediction

Each type requires its own validation metric. A correct fundamental prediction and an incorrect short-term stock-price prediction must be scored separately.

## Checkpoint types

### Immediate event checkpoint

Verify disclosed facts, guidance, management answers, and immediate surprise classification.

### Operational checkpoint

Verify capacity, orders, utilization, yield, inventory, customer behavior, or product timing.

### Financial checkpoint

Verify revenue, margin, EPS, cash flow, consensus revisions, and whether investment translated into financial output.

### Market checkpoint

Measure absolute and benchmark-relative return over predefined windows. Do not use stock price alone to validate a fundamental claim.

## Outcome labels

- Correct
- Partially correct
- Wrong
- Too early
- Unverifiable
- Poorly defined
- Invalidated by external shock

## Error attribution

A wrong prediction must be assigned one or more root causes:

- Data error
- Source-quality error
- Consensus error
- Causal error
- Timing error
- Valuation error
- Market-pricing error
- Management-credibility error
- Overconfidence
- Insufficient evidence
- External shock

## Independent review

The originating research Agent must not be the sole grader. A separate Validation Reviewer must:

1. retrieve the immutable original prediction;
2. collect outcome evidence;
3. apply predefined criteria;
4. score direction, magnitude, timing, and causal accuracy separately;
5. write an error-attribution report;
6. propose, but not directly approve, playbook changes.

## Learning controls

The system may update:

- signal weights;
- management credibility by topic;
- company and industry playbook rules;
- checkpoint timing assumptions;
- common error patterns;
- Alpha Memory.

The system must not autonomously rewrite core safety or evidence rules.

## Alpha Memory queries

The long-term system should be able to answer:

- Which signals have the highest forward EPS predictive value for this company?
- Which management phrases have historically been reliable?
- Which apparent surprises were already priced in?
- Which calls were directionally correct but too early?
- Which Agent or playbook repeatedly overestimates demand?
- Which supply-chain predictions translated into orders rather than only stock-price moves?
