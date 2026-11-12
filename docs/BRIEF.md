# VEIN — product and architecture brief

Codename: **VEIN** — global-market intelligence.

Shared design principle across VEIN, SWITCHBOARD, and VIVA: **simple on the
surface, with every claim, result, and explanation clickable down to its
evidence.**

## The actual product

VEIN is not a mining tool. A mine is an excellent demonstration, but the same
interface accepts a company, commodity, facility, industry, country, or
economic event.

The experience starts with one search box:

> "Map the global quartz-to-semiconductor chain. Show public-company exposure,
> energy inputs, equipment suppliers, and what changed recently."

The result initially shows a small, comprehensible ecosystem — not a globe
covered in thousands of connections. Users expand the interesting branches.

## Click into everything

| Level | What appears | What the next click reveals |
|---|---|---|
| Ecosystem | Extraction, processing, energy, equipment, logistics, customers | Companies and facilities in each stage |
| Entity | Company, mine, refinery, utility, port, commodity | Ownership, geography, activities, identifiers |
| Relationship | Supplies, owns, operates, transports, purchases | Exact evidence, dates, qualifications, conflicting sources |
| Financials | Revenue, margins, cash flow, debt, capex, segments | Reporting period, currency, original disclosure, calculation |
| Recent changes | Outage, acquisition, contract, earnings, policy | Source document and the specific graph facts affected |

The most important click is on the connection between two things. Clicking
"Company A supplies Facility B" must answer *how do you know, when was that
true, and does the source establish that exact relationship?*

Use a Floorplan-style interaction: overview, zoom, select, inspect. Keep a
synchronized table available so visual exploration never becomes the only way
to retrieve the data.

## Separate economic relationships

The graph needs typed relationships, not generic "related to" lines:

- Ownership and operation.
- Documented supplier/customer contracts.
- Physical flows and processing stages.
- Utility service territories and power-purchase agreements.
- Industry-level exposure.
- Analyst-generated hypotheses.

Do not render those as equally certain. A manufacturer selling milling
equipment globally does not prove it supplied a particular mill; a nearby
power station does not prove it powers a particular mine.

Start with explicit labels such as **documented**, **historical**,
**industry exposure**, **candidate**, and **disputed**. Avoid a
model-generated "94% confidence" badge unless the score has a defensible
calibration method.

## OpenRouter, Sonar, recent research

These are three different components, not three interchangeable sources of
truth.

| Component | Proposed responsibility | Boundary |
|---|---|---|
| **OpenRouter** | Model selection for extraction, classification, synthesis, and verification | A model response is not financial or relationship evidence |
| **Sonar** | Web-grounded discovery, recent developments, source discovery | Preserve underlying sources; independently verify important claims |
| **`last30days` adapter** | Recent discussion, emerging topics, terminology, leads | Treat community discussion as discovery, not audited fact |
| **Structured financial feeds** | Financial statements, quotes, corporate actions, identifiers | Display coverage, reporting periods, delays, and redistribution limits |
| **Primary-source ingestion** | Filings, exchange notices, company announcements, regulatory documents | Ground material facts in the original record |

For Sonar, design a direct connection and allow an OpenRouter route only after
verifying that the selected route preserves the response fields and citations
the product requires. For `last30days`, wrap its structured outputs behind an
adapter rather than making its internal scripts the foundation of the data
model.

## Freshness without false precision

"Researched today" is not the same as "true today." Store separate timestamps
for:

- When the source was published.
- When the underlying event occurred.
- The period covered by a financial figure.
- When the system retrieved and last checked it.
- When a relationship became effective or ceased to apply.

Use different refresh policies for different objects. Quotes, earnings,
ownership, supply contracts, and community discussion should not share one
expiration setting.

The recent-research layer should propose changes to established facts, not
silently overwrite them. A useful feature is **"What changed since my last
visit?"**, with additions, removals, disputed relationships, and revised
financial data shown separately.

## Global coverage, honest gaps

Design the identifier model globally from day one: legal entity, security,
listing, exchange, share class, currency, and fiscal calendar must be separate
concepts. A company with multiple listings should not become multiple
suppliers in the ecosystem.

Launch with global search and an explicit coverage matrix, rather than
claiming equally complete financials everywhere. Show **unavailable**,
**delayed**, and **not licensed** instead of filling gaps with generated
numbers.

Public-company financials also need a scope label: **consolidated company**,
**reported segment**, or **facility-specific disclosure**. Do not imply that
the parent company's entire revenue comes from the selected mine.

## First useful release

Build one complete vertical slice:

**Search → bounded ecosystem → company table → relationship evidence →
recent changes.**

Use quartz/semiconductors as one test case and a substantially different
ecosystem — such as agricultural inputs or electricity infrastructure — as
the second. Passing both helps establish that VEIN is a global-markets
product rather than a mining demo with a generic search box.

The release gate should require every displayed factual edge and financial
cell to have provenance, date context, and a visible missing-data state.

## Shared engineering, limited coupling

A small shared foundation makes sense, but domain-specific records stay
separate. Shared primitives across the three products: evidence reference,
version identity, execution events, inspectable derivation.

A reasonable starting implementation is a local-first service,
SQLite-backed records, a filesystem artifact store, and a web interface.
For VEIN, add a server-side data service when licensing, scheduled refresh,
or shared datasets require it.
