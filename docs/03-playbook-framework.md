# Company and Industry Playbook Framework

## Purpose

A transcript does not explain itself. Each company and industry must have a versioned playbook describing what matters, why it matters, how to validate it, and which signals have historically been useful.

Playbooks must be loaded at runtime and must not be hard-coded into a single system prompt.

## Playbook schema

```yaml
id: company.TSM
version: 0.1.0
company: TSMC
industry: semiconductor_foundry
updated_at: 2026-07-15

research_priorities:
  - id: ai_demand_visibility
    weight: 1.0
    why_it_matters: Forward demand and utilization for advanced nodes and packaging.
    evidence:
      - management_guidance
      - customer_capex
      - capacity_and_lead_time
    invalidation:
      - customer_digesting_inventory
      - shortened_visibility

  - id: gross_margin_quality
    weight: 1.0
    decompositions:
      - pricing
      - node_mix
      - ramp_dilution
      - utilization
      - overseas_fab_cost
      - foreign_exchange
```

## Required sections

Each company playbook should define:

- Business model and economic engine
- Revenue, margin, cash-flow, and valuation drivers
- Key products, customers, suppliers, technologies, and competitors
- Top research questions
- Company-specific KPI definitions
- Management vocabulary and historical wording
- Typical accounting or interpretation traps
- Bull, Base, and Bear transmission paths
- Evidence required for each conclusion
- Invalidation conditions
- Historical mistakes and lessons
- Signal weights and their update history

## Example: TSMC priorities

- AI demand visibility and supply tightness
- Pricing power versus process-mix effects
- Gross-margin quality and dilution causes
- CapEx quality rather than CapEx headline value
- Advanced packaging capacity and bottlenecks
- N2 ramp, yield, and cost curve
- Overseas-fab dilution and subsidies
- Mature-node utilization and competition

Questions include:

- Is CapEx increasing because of effective capacity or higher construction cost?
- Is margin dilution caused by a healthy new-node ramp or weakening pricing power?
- Does packaging expansion benefit equipment, testing, substrate, and PCB suppliers equally?
- Has management shortened demand visibility or changed supply language?

## Example: NVIDIA priorities

- Product roadmap execution
- Rack-scale system readiness
- Networking and interconnect mix
- Supply constraints by component
- Training versus inference demand
- Customer concentration and expansion
- Gross-margin path
- China and export-control exposure

The analysis must not focus merely on whether revenue reached a record.

## Runtime behavior

Before research begins, the Orchestrator must:

1. load the company playbook;
2. load the parent industry playbook;
3. retrieve prior-quarter unresolved watch items;
4. rank questions by current signal weight;
5. add newly discovered topics without silently overwriting the playbook;
6. record the playbook version used by the report.

## Updating a playbook

A playbook update must include:

- triggering evidence or validation result;
- old and new rule or weight;
- reason for change;
- effective date;
- reviewer approval state;
- rollback path.

A single prediction error must not automatically rewrite the entire methodology.
