# Repository conventions

## Repository paths

| Item | Value |
|------|--------|
| Git remote | `https://github.com/blevinstein/garden` |
| Default clone location | `~/dev/garden` |

## Soil test (`SOIL.md` at repo root)

- **Location:** `SOIL.md` in the **repository root** (not under `<YYYY>/`).
- **Purpose:** Long-lived reference to lab results (typically years apart, not every season). Each season’s `PLAN.md` should link to it with a relative path: [`SOIL.md`](../SOIL.md) from inside `<YYYY>/`.
- **If you re-test:** Update the root file in place (or replace with a dated archive + new summary—your choice), rather than copying soil data into each year folder.

## Per-season layout (`<YYYY>/`)

All season content lives under **`<YYYY>/`** where `<YYYY>` is the calendar year for that growing season.

```
<YYYY>/
  PLAN.md           # Plan of record: goals, constraints, frost/zone, infrastructure, decisions
  CROPS.md          # Crop list: variety, quantity, bed assignment, spacing notes
  CARE.md           # Water, fertilizer, pruning/training, pests, harvest, preservation
  SCHEDULE.md       # Rolling ~3-month task schedule (regenerated; dated header)
  layout/
    README.md       # Units, north-arrow policy, grid spacing, how files relate
    interior-*.md   # One ASCII file per raised bed + greenhouse: interior dims + plant grid
    beds-legend.md  # Per-bed symbol → plant; grid conventions
  sketches/
    ...             # Raster sketches (PNG/JPG); source for the ASCII layouts; do not delete
```

## Markdown only

Use Markdown for structured content. Tables in `CROPS.md` / `CARE.md` are fine.

## Plan of record (`PLAN.md`)

Should state or link:

- Hardiness zone and **last spring / first fall frost** (source and dates)
- Property constraints (sun, water, time budget, organic/synthetic preferences)
- Infrastructure: trellises, row cover, irrigation
- Which layout files are canonical (`layout/interior-*.md` + `beds-legend.md`; no whole-lot diagram required)
- Open questions and decisions log (dated bullets are fine)

## Layout (`layout/` + `sketches/`)

- **Sketches:** User-supplied rasters in `sketches/` are the visual reference; preserve them. Sketches may be bed/planting only, drip/tubing only, or combined.
- **ASCII diagrams:** Each `interior-*.md` file is **one enclosure** (one raised bed interior or greenhouse floor) at **true interior dimensions** (inches). Plants sit on grid intersections of a fixed grid spacing (typically 6"). The `garden-layout-ascii` skill documents the rendering rules; `layout/README.md` and `layout/beds-legend.md` document the conventions for this season.
- **Letters/symbols:** Use a short (single uppercase letter) code per plant type per diagram; define codes in each `interior-*.md` file and summarize across beds in `beds-legend.md`. The same letter may denote different plants in different beds — each file is self-contained.
- **Spacing inside each bed** should match the plan (rows, in-row spacing, counts). Lot position is optional sketch-only.
- **Drip / irrigation** belongs in prose (`PLAN.md` + `CARE.md`), **not** in the ASCII layouts. Zone assignments, emitter rates (GPH), run times, and schedule all live in `PLAN.md` / `CARE.md`; layouts stay focused on plant positions.

## Schedule (`SCHEDULE.md`)

- Start with: **Generated:** ISO date and what it was based on (e.g. “CROPS.md + frost dates from PLAN.md”).
- **Near term (about 4 weeks):** weekly task lists.
- **Rest of ~3 months:** weekly or biweekly buckets; use **monthly** sections only when detail would be noise.
- Tie tasks to crops/beds where helpful; avoid duplicating long care prose by pointing to `CARE.md`.

## Git

Commit and push to main (no review process) after meaningful updates so the plan of record has history.
