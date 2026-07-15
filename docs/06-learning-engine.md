# Controlled Learning and Self-Evolution Engine

## Purpose

The system must become better through measured research outcomes, not through uncontrolled prompt mutation. Self-evolution is a governed pipeline that converts validated prediction errors into proposed changes to weights, playbooks, checkpoint timing, and knowledge records.

## Learning loop

```text
Immutable Prediction
→ Scheduled Checkpoint
→ Outcome Evidence
→ Independent Validation
→ Error Attribution
→ Learning Proposal
→ Reviewer Approval
→ Versioned Change
→ Shadow Evaluation
→ Promotion or Rollback
```

## What may evolve

- Company-specific signal weights
- Industry-specific signal weights
- Management credibility by topic
- Question priority in a playbook
- Evidence requirements for a conclusion
- Checkpoint timing and validation metrics
- Knowledge-graph relationships and confidence
- Known failure modes and common research traps
- Agent routing and worker selection rules

## What may not evolve automatically

- Evidence and citation requirements
- Security and access-control rules
- The requirement to separate facts from inference
- Prediction immutability
- Independent validation
- Human approval requirements for material methodology changes
- Trading permissions or risk limits

## Learning proposal

Every proposed change must contain:

```yaml
proposal_id: LP-TSM-2026-001
scope: company.TSM.research_priorities.capex_quality
trigger:
  prediction_ids:
    - TSM-2026Q1-CAPEX-003
    - TSM-2026Q2-CAPEX-001
root_cause: market_pricing_error
old_value: 0.80
proposed_value: 0.58
reason: Absolute CapEx changes were less predictive than the composition of incremental CapEx.
evidence_count: 12
confidence: 0.78
risk: medium
requires_human_review: true
shadow_test_periods: 4
rollback_to: company.TSM@0.3.1
```

## Promotion rules

A proposal may be promoted only when:

1. the source predictions are immutable and fully validated;
2. outcome evidence has adequate quality;
3. sample size meets the configured threshold;
4. a separate reviewer agrees with the root cause;
5. the new rule improves shadow evaluation without materially worsening calibration;
6. the update has a version, changelog, and rollback target.

## Avoiding overfitting

The learning engine must:

- use minimum sample sizes;
- shrink small-sample weights toward industry priors;
- separate structural changes from temporary regimes;
- test changes on periods not used to create the proposal;
- avoid changing multiple related rules from one error;
- record whether gains survive after transaction costs or benchmark adjustment when market outcomes are used.

## Research performance metrics

Track by company, industry, signal, horizon, and Agent version:

- Direction accuracy
- Magnitude error
- Timing error
- Brier score and calibration
- False-positive and false-negative rates
- Citation coverage
- Unknown rate
- Overconfidence rate
- Thesis invalidation detection speed
- Consensus-estimation error
- Causal-attribution accuracy
- Benchmark-relative outcome accuracy

## Alpha Memory

Alpha Memory stores validated patterns, not raw opinions. Entries must include evidence count, regime, applicable universe, horizon, confidence, last validation date, and known exceptions.

Example:

```yaml
pattern: TSM gross-margin guidance has higher forward EPS information value than headline CapEx.
applicable_to: company.TSM
period: 2021Q1-2026Q2
observations: 22
confidence: 0.84
exceptions:
  - major FX regime changes
  - overseas-fab accounting changes
```

## Governance

- Minor metadata corrections may be auto-approved.
- Signal-weight changes require reviewer approval.
- New causal rules require human or CIO approval.
- Core methodology changes require a pull request and tests.
- Every promoted change must be reversible.
