# Investment Knowledge Graph

## Goal

Represent how macro events, industries, technologies, companies, products, customers, suppliers, equipment, materials, financial metrics, and valuation drivers connect. The graph supports causal research, source reuse, and supply-chain transmission without treating every relationship as equally certain.

## Core node types

- MacroEvent
- Industry
- Technology
- Company
- Product
- CustomerSegment
- Supplier
- Competitor
- Equipment
- Material
- Geography
- Regulation
- FinancialMetric
- ValuationDriver
- ManagementPerson
- ResearchClaim

## Core edge types

- PRODUCES
- USES_TECHNOLOGY
- SUPPLIES
- BUYS_FROM
- COMPETES_WITH
- SUBSTITUTES_FOR
- DEPENDS_ON
- CAPACITY_CONSTRAINS
- PRICE_AFFECTS
- COST_AFFECTS
- REVENUE_EXPOSED_TO
- MARGIN_EXPOSED_TO
- CAPEX_EXPOSED_TO
- REGULATED_BY
- VALIDATED_BY
- CONTRADICTED_BY

## Edge properties

Every relationship stores:

```yaml
edge_id: edge-001
from: company.TSM
to: technology.CoWoS
relation: PRODUCES
confidence: 0.97
evidence_ids:
  - source-claim-101
valid_from: 2025-01-01
valid_to: null
last_verified_at: 2026-07-15
regime: ai_accelerator_expansion
notes: Capacity and product definitions can change over time.
```

## Causal paths

The reasoning engine may propose paths such as:

```text
Hyperscaler AI CapEx
→ accelerator demand
→ advanced packaging demand
→ packaging equipment utilization
→ supplier orders
→ revenue / margin impact
```

A proposed path must preserve evidence and confidence at each edge. Overall confidence cannot exceed the weakest material edge without an explicit justification.

## Temporal behavior

Relationships are time-bounded. A supplier relationship, technology generation, or customer concentration may become stale. The graph must support effective dates and periodic revalidation.

## Graph update governance

- New factual edges require evidence.
- Inferred edges are labeled as inferred.
- Material edge changes generate review proposals.
- Conflicting evidence is retained rather than overwritten.
- Deleted or expired relationships remain auditable.

## Initial MVP graph

Implement only the nodes and edges needed for the first TSM earnings workflow:

- TSMC
- advanced nodes
- advanced packaging
- AI accelerators
- overseas fabs
- major CapEx categories
- margin drivers
- equipment, testing, substrate, PCB, power, and cooling categories

Do not attempt a universal ontology before the vertical slice is working.
