# Investment Operating System (IOS)

> Build an AI investment research organization, not another AI chatbot.

## Vision

Most AI investment assistants stop after summarizing information. **Investment Operating System (IOS)** is designed to continuously:

- research evidence;
- understand market expectations;
- form falsifiable conclusions and predictions;
- create future validation checkpoints;
- learn from prediction errors;
- improve company and industry playbooks over time.

The goal is not merely to produce more reports. The goal is to build an AI research organization whose research quality improves every quarter.

## Core research loop

```text
Expectation
    ↓
Evidence
    ↓
Reasoning
    ↓
Prediction
    ↓
Checkpoint
    ↓
Validation
    ↓
Error attribution
    ↓
Playbook and signal-weight update
```

## Core principles

1. **Evidence before opinion** — important claims must be traceable to original sources.
2. **Expectation before analysis** — a result is not a surprise unless it is compared with what the market expected.
3. **Reasoning before conclusion** — revenue, margin, and CapEx changes must be decomposed by cause.
4. **Prediction before hindsight** — conclusions must be converted into immutable, falsifiable Prediction Cards.
5. **Independent validation** — the research agent must not grade its own work without a separate reviewer.
6. **Unknown is acceptable** — insufficient evidence must be labeled rather than guessed.
7. **Playbooks are versioned knowledge** — company and industry research rules live outside hard-coded prompts.

## System architecture

```text
Investment Operating System
├── Source & Evidence Layer
├── Research Engine
├── Company / Industry Playbooks
├── Knowledge Graph
├── Market Expectation Engine
├── Causal Reasoning Engine
├── Debate & Review Engine
├── Prediction & Checkpoint Engine
├── Learning / Alpha Memory Engine
└── Portfolio Decision Layer
```

## Initial scope

The first vertical slice is an **Earnings Call Research Agent** that can:

- discover official investor-relations materials;
- download presentations, reports, webcasts, audio, and transcripts;
- use Whisper when no transcript is available;
- separate prepared remarks from analyst Q&A;
- load company-specific research playbooks;
- compare actual results with pre-event expectations;
- identify changes that may affect EPS, valuation, or the supply chain;
- create Prediction Cards and future checkpoints;
- validate prior predictions and update research weights.

## Repository layout

```text
docs/                  Product, architecture, and research specifications
agents/                Orchestrator and worker contracts
playbooks/             Versioned company and industry playbooks
knowledge/             Company DNA, industry DNA, and graph schemas
prediction/            Prediction ledger, checkpoints, and validation
portfolio/             Portfolio and risk decision specifications
src/                   Application code (after specifications stabilize)
tests/                 Unit, integration, and research-quality tests
```

## Documentation map

Start with:

1. [`docs/00-project-vision.md`](docs/00-project-vision.md)
2. [`docs/01-investment-operating-system.md`](docs/01-investment-operating-system.md)
3. [`docs/02-earnings-research-agent.md`](docs/02-earnings-research-agent.md)
4. [`docs/03-playbook-framework.md`](docs/03-playbook-framework.md)
5. [`docs/04-prediction-validation.md`](docs/04-prediction-validation.md)
6. [`docs/05-development-roadmap.md`](docs/05-development-roadmap.md)

## Success criteria

IOS is successful only when it can demonstrate that:

- predictions are defined before outcomes are known;
- checkpoints are executed automatically;
- errors are attributed to data, consensus, causality, timing, valuation, or external shocks;
- signal weights and playbooks improve from evidence;
- research accuracy and usefulness improve over repeated quarters.

## Project status

**Specification-first / pre-MVP.** The immediate goal is to implement one complete, testable earnings-call workflow before expanding into portfolio automation or autonomous trading.
