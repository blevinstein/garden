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
  CROPS.md          # Crop list: variety, quantity, seeds vs starts, bed assignment, spacing notes
  CARE.md           # Water, fertilizer, pruning/training, pests, harvest, preservation
  SCHEDULE.md       # Rolling ~3-month task schedule (regenerated; dated header)
  layout/
    README.md       # Units, north arrow policy, how files relate (optional but recommended)
    interior-*.svg  # One SVG per raised bed + greenhouse: interior dims, plants, drip (¼″ + emitters)
    beds-legend.md  # Symbol → plant; drip line styles, emitter legend, timer/zone notes
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
- Which layout files are canonical (`layout/interior-*.svg` + `beds-legend.md`; no whole-lot SVG required)
- Open questions and decisions log (dated bullets are fine)

## Layout (`layout/` + `sketches/`)

- **Sketches:** User-supplied rasters in `sketches/` are the visual reference; preserve them. Sketches may be **bed/planting only**, **drip/tubing only**, or **combined** (tubing is often planned per bed before planting).
- **SVG:** Each file is **one enclosure** (one raised bed interior or greenhouse floor) at **true interior dimensions** (inches or cm—state in `layout/README.md` or `PLAN.md`).
- **Letters/symbols:** Use a short code per plant type in the diagram; define codes in `beds-legend.md`.
- **Spacing inside each bed** should match the plan (rows, in-row spacing, counts). Lot position is optional sketch-only.
- Use stable group `id`s (e.g. `<g id="plants">`, `<g id="irrigation">` per file).

### Drip irrigation (diagram)

- **Hardware assumption:** **1/4 inch** drip tubing to most beds; **one emitter at each plant base** (or each planned plant position). **Multiple timers** run separate circuits—diagrams should show **which timer feeds which bed or zone** (stroke color or dash pattern per circuit, plus labels).
- **SVG structure:** Keep plants and irrigation in **separate groups** (e.g. beds/plants vs `<g id="irrigation">`). Tubing may be **schematic** (readable polylines; not literal 1/4" line width). Emitter positions align with plant markers.
- **Legend:** Extend `beds-legend.md` with a **Drip / irrigation** subsection (line styles, emitter symbol, timer names). Optional **timer → beds** table in the legend if the SVG is busy.

## Schedule (`SCHEDULE.md`)

- Start with: **Generated:** ISO date and what it was based on (e.g. “CROPS.md + frost dates from PLAN.md”).
- **Near term (about 4 weeks):** weekly task lists.
- **Rest of ~3 months:** weekly or biweekly buckets; use **monthly** sections only when detail would be noise.
- Tie tasks to crops/beds where helpful; avoid duplicating long care prose by pointing to `CARE.md`.

## Git

Commit and push to main (no review process) after meaningful updates so the plan of record has history.
