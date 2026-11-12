# vein

> Global-market intelligence: search a company, commodity, facility, industry, or economic event and see how that part of the economy connects — with every claim, result, and explanation clickable down to its evidence.

## Stack

- Rust workspace — one local binary: embedded service + UI
- [Rune](https://github.com/anomalyco/rune) (GPU-rendered UI, pinned dev rev) + `rune-kit` components
- SQLite for records, filesystem artifact store for source documents
- OpenRouter for model calls (never evidence), Sonar for web-grounded discovery, `last30days` adapter for community leads

## Local Setup

```bash
# clone
git clone https://github.com/duketopceo/vein
cd vein

# toolchain: Rust 1.99.1 (see rust-toolchain.toml once crates land)
rustup show

# env vars
cp .env.example .env
# fill in .env (OPENROUTER_API_KEY at minimum)

# run — no crates yet; first runnable slice lands with plan unit U1
cargo build --workspace
```

## Deploy

Local-first desktop app. No hosted deploy; a server-side data service is a later option for licensing and scheduled refresh (see `docs/BRIEF.md`).

## Docs

- `docs/BRIEF.md` — product and architecture brief (source of truth for scope)
- `docs/plans/` — ce-plan implementation plans
- `ROADMAP.md` — phased delivery and release gates
- `DESIGN.md` — interaction and evidence design contract
- See `AGENTS.md` for agent context.
