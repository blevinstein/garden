# Repository conventions

## Per-season layout (`<YYYY>/`)

All season content lives under **`<YYYY>/`** where `<YYYY>` is the calendar year for that growing season.

```
<YYYY>/
  PLAN.md           # Plan of record: goals, constraints, frost/zone, infrastructure, decisions
  CROPS.md          # Crop list: variety, quantity, seeds vs starts, bed assignment, spacing notes
  CARE.md           # Water, fertilizer, pruning/training, pests, harvest, preservation
  SCHEDULE.md       # Rolling ~3-month task schedule (regenerated; dated header)
  layout/
    README.md       # Units, north arrow policy, how files relate (optional but recommended)
    beds.svg        # Primary planting diagram (name may vary, e.g. site.svg)
    beds-legend.md  # Letter/symbol → plant name (and variety if needed)
  sketches/
    ...             # Raster sketches (PNG/JPG); source for tracing into SVG; do not delete
```

## Markdown only

Use Markdown for structured content. Tables in `CROPS.md` / `CARE.md` are fine.

## Plan of record (`PLAN.md`)

Should state or link:

- Hardiness zone and **last spring / first fall frost** (source and dates)
- Property constraints (sun, water, time budget, organic/synthetic preferences)
- Infrastructure: trellises, row cover, irrigation
- Which layout file is canonical (`layout/beds.svg`, etc.)
- Open questions and decisions log (dated bullets are fine)

## Layout (`layout/` + `sketches/`)

- **Sketches:** User-supplied rasters in `sketches/` are the visual reference; preserve them.
- **SVG:** Draw beds at **true interior dimensions** (one unit per season: inches or cm—state in `layout/README.md` or `PLAN.md`).
- **Letters/symbols:** Use a short code per plant type in the diagram; define codes in `beds-legend.md`.
- **Bed placement on the canvas** may be approximate; **spacing inside each bed** should match the plan (rows, in-row spacing, counts).
- Group each bed in SVG with a stable `id` (e.g. `bed-a`, `bed-raised-1`).

## Schedule (`SCHEDULE.md`)

- Start with: **Generated:** ISO date and what it was based on (e.g. “CROPS.md + frost dates from PLAN.md”).
- **Near term (about 4 weeks):** weekly task lists.
- **Rest of ~3 months:** weekly or biweekly buckets; use **monthly** sections only when detail would be noise.
- Tie tasks to crops/beds where helpful; avoid duplicating long care prose by pointing to `CARE.md`.

## Git

Commit and push to main (no review process) after meaningful updates so the plan of record has history.
