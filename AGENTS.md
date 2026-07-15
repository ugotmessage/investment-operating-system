# AGENTS.md

## Mission

Implement the Investment Operating System as a specification-first, evidence-driven research platform. Do not reduce the project to transcript scraping or generic LLM summarization.

## Required reading order

1. `README.md`
2. `docs/00-project-vision.md`
3. `docs/01-investment-operating-system.md`
4. `docs/02-earnings-research-agent.md`
5. `docs/03-playbook-framework.md`
6. `docs/04-prediction-validation.md`
7. `docs/06-learning-engine.md`
8. `docs/07-data-contracts.md`
9. `docs/08-agent-contracts.md`
10. `docs/09-testing-and-quality-gates.md`
11. `docs/05-development-roadmap.md`

## Non-negotiable rules

- Load company and industry YAML playbooks before analysis.
- Separate facts, management claims, consensus, inference, speculation, and unknowns.
- Never invent consensus estimates, exact figures, quotes, speakers, or timestamps.
- Every important claim must retain source provenance.
- Every falsifiable conclusion must create an immutable Prediction Card and checkpoints.
- The originating researcher must not be the sole prediction reviewer.
- Learning produces versioned proposals; it does not silently rewrite prompts or playbooks.
- Keep the MVP narrow: one complete TSM earnings workflow before broad platform expansion.
- Use deterministic code for extraction, calculations, dates, validation rules, and state transitions; use LLMs for classification and synthesis only where justified.
- Make all jobs idempotent, resumable, observable, and testable.

## Development workflow

For every phase:

1. restate the acceptance criteria;
2. inspect existing contracts and schemas;
3. implement the smallest complete vertical slice;
4. add unit and integration tests;
5. run tests and record results;
6. update documentation when behavior changes;
7. do not begin the next phase until the current exit criteria are met.

## Definition of done

A feature is not complete merely because it produces prose. It is complete only when inputs, outputs, provenance, failure states, tests, and validation behavior are defined and verified.
