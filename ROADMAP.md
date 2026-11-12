# ROADMAP.md — vein

Phased delivery per `docs/BRIEF.md`. Each phase ends at a verifiable gate;
nothing ships on a build alone.

## Phase 0 — Foundation (plan v1, units U1–U3)

- Rust workspace, embedded local service, Rune shell with search box
- SQLite schema: identifier model (legal entity, security, listing, exchange,
  share class, currency, fiscal calendar), evidence records, typed
  relationships with epistemic labels, five-timestamp facts
- Filesystem artifact store for source documents

**Gate:** schema migrations apply clean; evidence record round-trips with all
five timestamps.

## Phase 1 — Research slice (units U4–U7)

- Entity search + resolution; bounded ecosystem assembly
- Adapters: OpenRouter (candidate claims only), Sonar (citation-preserving
  discovery), last30days (leads only), primary-source ingestion, financial
  feed interface with coverage matrix
- Financial drill-down with scope labels (consolidated / segment /
  facility-specific)

**Gate:** quartz→semiconductor chain produces a bounded ecosystem where every
edge is documented/historical/exposure/candidate/disputed and every financial
cell carries period + provenance or an honesty state.

## Phase 2 — Inspect + change (units U8–U10)

- Floorplan-style ecosystem view + synchronized table
- Relationship evidence drawer; entity inspector
- Recent-changes layer; "what changed since my last visit"

**Gate:** the most important click — a company↔facility edge — answers how we
know, when it was true, and whether the source establishes that exact
relationship.

## Phase 3 — Second ecosystem + release (unit U11)

- Repeat the slice on a contrasting domain (agricultural inputs or electricity
  infrastructure)
- Coverage matrix published; freshness policies per object type verified

**Release gate:** every displayed factual edge and financial cell has
provenance, date context, and a visible missing-data state — on both
ecosystems.

## Explicitly deferred

- Server-side data service (until licensing/refresh demands it)
- Globe-scale visualization
- Model-generated confidence scores
- Additional ecosystems beyond the two validation cases
