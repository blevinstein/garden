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
- [`2026/SCHEDULE.md`](2026/SCHEDULE.md) — rolling ~3-month task schedule (regenerated; dated header).
- `2026/layout/` — one ASCII file per bed/greenhouse plus `beds-legend.md`; `sketches/` holds source rasters (do not delete).

## Working conventions

- **Markdown only** for structured content; tables are fine in `CROPS.md` / `CARE.md`.
- **Irrigation lives in prose** (`PLAN.md` + `CARE.md`), never in the ASCII layouts — layouts stay focused on plant positions.
- Follow `CONVENTIONS.md` exactly for where each kind of content belongs; keep the same content in one place and link to it rather than duplicating.
- **Git:** commit and push to `main` (no review process) after meaningful updates so the plan of record keeps history.

## Skills

Several `/garden-*` skills exist for common tasks: `garden-plan-of-record` (PLAN/CROPS/CARE), `garden-layout-ascii` (layouts), `garden-calendar-schedule` (SCHEDULE.md), and `garden-irrigation-plan` (irrigation/emitter sizing). Prefer them when they fit the request.
