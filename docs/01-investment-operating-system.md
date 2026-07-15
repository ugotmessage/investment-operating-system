# Investment Operating System

## Research lifecycle

```text
Source discovery
→ Evidence normalization
→ Expectation matrix
→ Company playbook loading
→ Fact extraction
→ Causal analysis
→ Bull / Bear / Unknown review
→ Investment impact
→ Prediction compilation
→ Checkpoint scheduling
→ Outcome validation
→ Error attribution
→ Playbook update
```

## Layers

### Source and Evidence Layer

Collect official IR materials, filings, exchange disclosures, presentations, webcasts, audio, transcripts, financial data, and clearly labeled secondary sources. Save retrieval time, URL, source class, checksum, and local version.

### Knowledge Layer

Maintain versioned Company DNA, Industry DNA, Technology DNA, Management DNA, and a knowledge graph connecting products, customers, suppliers, equipment, materials, financial metrics, and valuation drivers.

### Research Layer

Extract facts, guidance, management claims, analyst questions, language changes, and historical comparisons. Research output must be linked to evidence.

### Market Expectation Layer

Separate company guidance, sell-side consensus, public-news expectations, price-implied expectations, and Agent scenarios. Never present an unsupported scenario as consensus.

### Reasoning Layer

Trace event → root cause → first-order impact → second-order impact → financial impact → valuation impact. Do not treat correlation as causation.

### Review Layer

Use independent Bull, Bear, Neutral, Risk, and Reviewer roles. The reviewer checks citations, unsupported leaps, missing counter-evidence, and whether conclusions are falsifiable.

### Prediction and Validation Layer

Compile testable conclusions into immutable Prediction Cards, schedule checkpoints, collect outcomes, score accuracy, and attribute errors.

### Learning Layer

Update signal weights, management credibility, research rules, and Alpha Memory through controlled, versioned changes. Core prompts must not rewrite themselves without review.

## Required classifications

Every extracted statement must be one of:

- Fact
- Management claim
- Guidance
- Market expectation
- Inference
- Speculation
- Unknown

## Publishing gate

A report cannot be published when:

- a major exact number has no source;
- no pre-event expectation matrix exists;
- a major inference has no supporting evidence;
- no counter-thesis is provided;
- a testable conclusion lacks a Prediction Card;
- confidence is high despite material unknowns.
