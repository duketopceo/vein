# DESIGN.md — vein

Design contract for the vein interface. The shared principle across VEIN,
SWITCHBOARD, and VIVA: **simple on the surface, with every claim, result, and
explanation clickable down to its evidence.**

## Interaction model

Floorplan-style: overview → zoom → select → inspect. The ecosystem view shows a
small, comprehensible subgraph — never a globe of thousands of edges. Users
expand branches deliberately.

| Level | Shows | Next click reveals |
|---|---|---|
| Ecosystem | Stage clusters (extraction, processing, energy, equipment, logistics, customers) | Companies and facilities in the stage |
| Entity | Company, mine, refinery, utility, port, commodity | Ownership, geography, activities, identifiers |
| Relationship | Typed edge with epistemic label | Exact evidence, dates, qualifications, conflicting sources |
| Financials | Revenue, margins, cash flow, debt, capex, segments | Period, currency, original disclosure, calculation |
| Recent changes | Outage, acquisition, contract, earnings, policy | Source document and affected graph facts |

A synchronized table view mirrors whatever the graph shows — visual
exploration is never the only retrieval path.

## Epistemic rendering

Relationship certainty is shown as explicit labels, never a bare line:

- **documented** — primary source establishes this exact relationship
- **historical** — was true in a bounded past period
- **industry exposure** — sector-level linkage, not facility-specific
- **candidate** — model- or community-suggested, awaiting evidence
- **disputed** — sources conflict; both shown

No model-generated "94% confidence" badge unless the score has a defensible
calibration method.

## Freshness

Five timestamps stay distinct everywhere they surface: source published,
event occurred, period covered, system retrieved/checked, relationship
effective/ceased. Different object types carry different refresh policies —
quotes, earnings, ownership, contracts, and community discussion never share
one expiration.

## Honesty states

Every data cell resolves to one of: value + provenance, `unavailable`,
`delayed`, `not licensed`, or `candidate`. Missing is a first-class rendered
state, not an absence.

## UI stack

Rune (`anomalyco/rune`, pinned rev in `Cargo.toml`) + `rune-kit` components.
Token-driven theming via `rune-kit`'s `Kit` — no per-screen ad-hoc styling.
Headless rendering (`rune` supports PNG dump + element-tree dump) is the UI
verification path in CI-style checks.
