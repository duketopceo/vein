# AGENTS.md — vein

> This file is the agent entry point for this repo.
> Full agent context lives at: https://github.com/duketopceo/luke-agents

## What This Repo Does

vein is a local-first global-market intelligence tool. It maps how a company, commodity, facility, industry, or economic event connects — extraction, processing, energy, equipment, logistics, customers — and makes every displayed fact clickable to dated primary evidence. A model response is never evidence; claims carry provenance or an explicit missing-data state.

## Key Files

- `Cargo.toml` — workspace manifest; `members` stays empty until plan units add crates
- `docs/BRIEF.md` — product brief: scope, epistemic labels, freshness model, release gate
- `docs/plans/` — ce-plan implementation plans (Tallyline-imported)
- `ROADMAP.md` — phased delivery
- `DESIGN.md` — interaction contract (Floorplan-style explore/inspect, synchronized table)

## Current Status

- [x] Repo initialized — scaffold + plan
- [ ] In development
- [ ] Deployed
- [ ] Production traffic

## Active Issues / Known State

- Plan: `docs/plans/2026-11-12-0000-feat-vein-v1-plan.md`
- Rune pinned at `anomalyco/rune@24bd7bbb` (dev rev, pre-release — re-pin deliberately, never float)
- OpenRouter/Sonar/last30days interfaces need source-level verification — plan units U5–U6 are spikes for exactly that

## Agent Instructions (repo-specific)

- Every factual edge and financial cell rendered in UI must resolve to provenance, date context, and a visible missing-data state. No exceptions — this is the release gate.
- Never render analyst hypotheses, industry exposure, or model output with the same visual weight as documented relationships.
- Timestamps: keep published / occurred / period-covered / retrieved / effective-ceased as separate fields. Never collapse them into "freshness."
- Default: follow duketopceo/luke-agents for all standards.
