# Earnings Research Agent

## Objective

Build an end-to-end earnings-call workflow that does more than retrieve a transcript. It must understand what matters for the specific company, compare the event with pre-event expectations, and create testable predictions.

## Modes

```bash
python earnings_agent.py TSM --mode discover --period 2026Q2
python earnings_agent.py TSM --mode preview --period 2026Q2
python earnings_agent.py TSM --mode ingest --period 2026Q2
python earnings_agent.py TSM --mode transcribe --period 2026Q2
python earnings_agent.py TSM --mode analyze --period 2026Q2
python earnings_agent.py TSM --mode validate --period 2026Q2
python earnings_agent.py TSM --mode full --period 2026Q2
```

## Data-source priority

1. Company investor-relations website
2. Exchange and regulatory filings
3. Official webcast, replay, audio, or video
4. Official transcript or prepared remarks
5. Licensed or publicly permitted third-party transcript
6. Reputable secondary reporting

Paid or access-controlled content must not be bypassed.

## Ingestion flow

```text
IR discovery
→ source manifest
→ PDF / HTML / webcast download
→ checksum and deduplication
→ audio extraction
→ Whisper transcription when required
→ speaker and Q&A segmentation
→ financial metric extraction
→ evidence-linked analysis
```

## Transcript requirements

The processed transcript should distinguish:

- operator opening;
- prepared management remarks;
- financial review;
- guidance;
- analyst Q&A;
- closing remarks.

Each segment should preserve timestamp, speaker or uncertain speaker label, confidence, original text, and normalized text.

## Pre-event preview

Before analyzing results, build an Expectation Matrix containing:

- prior company guidance;
- publicly available consensus or estimate range;
- Bull / Base / Bear thresholds;
- key company-specific questions;
- what appears already priced in;
- unavailable or uncertain fields.

## Required analysis

The Agent must identify:

1. actual versus company guidance;
2. actual versus pre-event market expectation;
3. genuine surprises versus already-priced outcomes;
4. changes in management language across prior quarters;
5. direct, partial, or evasive answers in Q&A;
6. implications for revenue, margin, EPS, free cash flow, valuation, and supply chain;
7. evidence that would invalidate the conclusion.

## CapEx rule

CapEx increases must be decomposed into possible drivers such as effective capacity, advanced process equipment, advanced packaging, buildings and cleanrooms, overseas construction cost, inflation, maintenance, mature nodes, and purchasing timing. `CapEx up` is not automatically positive.

## Outputs

- `source_manifest.json`
- raw and cleaned transcript
- structured Q&A JSON
- metrics and guidance JSON
- expectation matrix
- evidence and claims table
- historical language diff
- full Markdown report
- Telegram summary
- Prediction Cards and checkpoint definitions

## MVP acceptance criteria

- One company and one quarter run end to end.
- Official materials are downloaded and versioned.
- Missing official transcript can be replaced with a timestamped Whisper transcript.
- Prepared remarks and Q&A are separated.
- Important exact numbers are source-linked.
- Company-specific playbook is loaded before analysis.
- At least one falsifiable prediction and checkpoint are produced.
- Re-running the workflow does not duplicate unchanged sources.
