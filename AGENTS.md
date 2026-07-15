# AGENTS.md

## Repository mission

Implement the Investment Operating System specifications as a staged, evidence-first research platform. Do not expand scope beyond the current milestone without documenting the decision.

## Reading order

1. `README.md`
2. `docs/00-project-vision.md`
3. `docs/01-investment-operating-system.md`
4. `docs/02-earnings-research-agent.md`
5. `docs/03-playbook-framework.md`
6. `docs/04-prediction-validation.md`
7. `docs/06-learning-engine.md`
8. `docs/07-agent-organization.md`
9. `docs/08-knowledge-graph.md`
10. `docs/09-data-and-storage.md`
11. `docs/10-testing-and-quality.md`
12. `docs/05-development-roadmap.md`

## Implementation priorities

Build the TSM earnings-call vertical slice first. Do not begin portfolio automation, autonomous trading, or a large UI before the source, transcript, expectation, prediction, checkpoint, and validation loop works end to end.

## Required engineering behavior

- Use typed Python.
- Keep jobs idempotent and resumable.
- Validate YAML and JSON against repository schemas.
- Preserve source provenance and checksums.
- Keep exact numbers traceable to evidence.
- Never hard-code company research rules into a global prompt; load YAML playbooks.
- Never let a model invent consensus estimates.
- Published predictions are immutable.
- Learning creates proposals; it does not directly mutate core rules.
- Add tests and documentation with every implementation change.

## Harness workflow

For changes spanning multiple independent scopes, use an Orchestrator and bounded Workers. Each Worker must return status, files changed, tests run, evidence or references used, uncertainties, and remaining work.

## Completion report

Every development task must report:

- scope completed;
- files changed;
- tests and verification results;
- known limitations;
- migrations or configuration required;
- follow-up issues.
