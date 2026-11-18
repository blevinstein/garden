# Agent guide

This is a garden-planning repo: narrative plans, crop lists, care notes, ASCII planting layouts, and rolling schedules — all Markdown, no code to build or test.

## Start here

- [README.md](README.md) — what the repo is and how to point an assistant at it.
- [CONVENTIONS.md](CONVENTIONS.md) — **authoritative** file layout, naming, and per-section rules. Read this before creating or moving any file.
- [SOIL.md](SOIL.md) — long-lived soil-test reference at the repo root, shared across seasons.

## Per-season content (`<YYYY>/`)

All season content lives under `<YYYY>/` (e.g. `2026/`). The current season is `2026/`:

- [`2026/PLAN.md`](2026/PLAN.md) — plan of record: goals, constraints, frost/zone, infrastructure, decisions, irrigation zones.
- [`2026/CROPS.md`](2026/CROPS.md) — crop list: variety, quantity, bed assignment, spacing.
- [`2026/CARE.md`](2026/CARE.md) — water, fertilizer, pruning, harvest, preservation, irrigation tuning.
- [`2026/PESTS.md`](2026/PESTS.md) — pest observations and control protocols (dated log + perennial reference).
- [`2026/WEATHER.md`](2026/WEATHER.md) — significant weather events with sources; correlate with crop outcomes.
- [`2026/SCHEDULE.md`](2026/SCHEDULE.md) — rolling ~3-month task schedule (regenerated; dated header).
- `2026/layout/` — one ASCII file per bed/greenhouse plus `beds-legend.md`; `sketches/` holds source rasters (do not delete).

## Working conventions

- **Markdown only** for structured content; tables are fine in `CROPS.md` / `CARE.md`.
- **Irrigation lives in prose** (`PLAN.md` + `CARE.md`), never in the ASCII layouts — layouts stay focused on plant positions.
- Follow `CONVENTIONS.md` exactly for where each kind of content belongs; keep the same content in one place and link to it rather than duplicating.
- **Git:** in interactive sessions, commit and push to `main` (no review process) after meaningful updates so the plan of record keeps history. Automated Centaur runs open pull requests instead (see below).

## Centaur (chat agent)

A chat agent answers questions and runs a weekly Saturday task prompt in the household group chat, through [centaur](https://github.com/blevinstein/centaur) and GitHub Actions. Automated runs never push to `main`: when they change files they open a pull request for review. The agent follows `CONVENTIONS.md` and has file tools only (no shell).

- Config: [`.centaur.yml`](.centaur.yml); persona: [`.centaur/persona.md`](.centaur/persona.md); scheduled prompts: `.centaur/prompts/`.
- Caller workflow: [`.github/workflows/centaur.yml`](.github/workflows/centaur.yml).

## Skills

Several `/garden-*` skills exist for common tasks: `garden-plan-of-record` (PLAN/CROPS/CARE), `garden-layout-ascii` (layouts), `garden-calendar-schedule` (SCHEDULE.md), and `garden-irrigation-plan` (irrigation/emitter sizing). Prefer them when they fit the request.
