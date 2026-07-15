# Agent Organization and Contracts

## Organization

```text
Chief Investment Officer Agent
├── Research Director
│   ├── Source Discovery Worker
│   ├── Transcript Worker
│   ├── Financial Worker
│   ├── Consensus Worker
│   ├── Company / Industry Specialist
│   └── Supply-Chain Worker
├── Independent Review Director
│   ├── Bull Reviewer
│   ├── Bear Reviewer
│   ├── Evidence Auditor
│   └── Prediction Compiler
├── Validation Director
│   ├── Checkpoint Scheduler
│   ├── Outcome Collector
│   ├── Prediction Reviewer
│   └── Error Attribution Worker
└── Learning Director
    ├── Signal Weight Analyst
    ├── Playbook Proposal Worker
    └── Alpha Memory Curator
```

## Orchestrator responsibilities

- Resolve company, event, period, and research objective.
- Load company and industry YAML playbooks.
- Load prior unresolved watch items and predictions.
- Build an explicit task graph and assign minimal context.
- Enforce source and evidence requirements.
- Reject unsupported precise numbers and conclusions.
- Track run state and support resumability.
- Compile final output only after review gates pass.

## Worker input contract

```json
{
  "task_id": "task-001",
  "role": "financial_worker",
  "objective": "Extract Q3 guidance and compare it with the expectation matrix.",
  "allowed_sources": ["source-11", "source-12"],
  "playbook_refs": ["company.TSM@0.1.0", "industry.foundry@0.1.0"],
  "required_outputs": ["metrics", "claims", "unknowns"],
  "prohibited_actions": ["invent_consensus", "modify_playbook"]
}
```

## Worker output contract

```json
{
  "task_id": "task-001",
  "status": "completed",
  "claims": [],
  "metrics": [],
  "evidence_ids": [],
  "counter_evidence_ids": [],
  "unknowns": [],
  "confidence": 0.82,
  "verification": [],
  "files_changed": []
}
```

## Context isolation

Workers receive only the context necessary for their scope. The Bear Reviewer should not inherit the Bull review's conclusion before producing an independent critique. The Prediction Reviewer must retrieve the immutable original prediction rather than a rewritten report summary.

## Review gates

1. Evidence audit
2. Numeric consistency check
3. Expectation-gap check
4. Company-playbook coverage check
5. Counter-thesis check
6. Prediction falsifiability check
7. Research quality score

## Failure behavior

When evidence is missing, workers return `unknown` with a requested source type. They must never fabricate a transcript, speaker identity, consensus estimate, or exact metric.
