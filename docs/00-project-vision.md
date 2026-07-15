# Project Vision

## Problem

Most AI investment tools summarize documents but do not preserve the assumptions behind a conclusion, define how it will be tested, or learn from later outcomes. They can produce fluent reports while repeating the same research mistakes every quarter.

## Product goal

Build an AI investment research organization that can:

1. collect and normalize primary evidence;
2. understand what the market expected before an event;
3. apply company- and industry-specific research playbooks;
4. form causal, falsifiable investment conclusions;
5. create future validation checkpoints automatically;
6. attribute errors and update its research process;
7. preserve an auditable history of predictions and learning.

## Non-goals for the MVP

- Autonomous trading
- High-frequency execution
- Full portfolio optimization
- A large web dashboard
- Scraping paywalled research without permission
- Allowing an LLM to invent consensus estimates or exact financial figures

## North-star questions

Every research output must answer:

1. What is the market missing?
2. What changed relative to expectations?
3. What can change forward EPS?
4. What can change the valuation multiple?
5. What is probably noise?
6. What evidence would invalidate the thesis?

## Product principles

- Primary sources have the highest authority.
- Facts, management claims, consensus, inference, and speculation must be separated.
- Every important conclusion must have evidence.
- Every testable conclusion must become a Prediction Card.
- Predictions are immutable after publication; later evidence is appended.
- Validation must be performed by an independent reviewer process.
- Self-improvement modifies versioned playbooks and signal weights, not arbitrary core prompts.
