# Repository conventions

## Repository paths

Paths in this document are **relative to the repository root** of your checkout (any directory name or location).

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
  CARE.md           # Water, fertilizer, pruning/training, harvest, preservation
  PESTS.md          # Pest observations and control protocols (dated log + perennial reference)
  WEATHER.md        # Significant weather events with sources; correlate with crop outcomes
  SCHEDULE.md       # Rolling ~3-month task schedule (regenerated; dated header)
  observations/
    README.md       # Pattern + what belongs here vs. PESTS/WEATHER/SCHEDULE
    YYYY-MM-DD-*.md # One dated field note per file; links to photos in ../photos/
  photos/
    YYYY-MM-DD-*.* # Dated photos referenced from observations and schedule
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

## Pests (`PESTS.md`)

- **Purpose:** Year-over-year pest reference. Each season's file documents perennial problems (what to expect on the Front Range), control protocols, and a dated observation log so next year's approach can be calibrated against what worked.
- **What goes here:** Pest identification, control protocols, observation tables (date / location / severity / outcome), and notes on timing (e.g. when Nosema bait is most effective, when to expect peak aphid pressure).
- **What stays in `CARE.md`:** Brief per-plant pest notes (e.g. "inspect Brussels for cabbage worms weekly") and cross-references to `PESTS.md`. Don't duplicate full protocols in both files.
- **What goes in `SCHEDULE.md`:** Time-sensitive tasks ("apply Nolo Bait this week", "check cherry for aphids"). Link to `PESTS.md` for the protocol detail.
- **Cross-season pattern:** If a pest is observed consistently across years, note it under the perennial pest section with a year-tagged row in the observation table. This makes it easy to see whether populations are earlier, later, or more severe than prior years.

## Observations (`observations/`)

- **Purpose:** Dated field notes about a specific plant or bed on a specific day — problems noticed, actions taken or planned, next check-in. One file per observation, named `YYYY-MM-DD-<subject>.md`. Photos live in `photos/` and are referenced by relative link.
- **Scope:** Keep the note narrow and factual. If an observation forces a change, cross-link to (and update) the affected canonical file: `PLAN.md` decisions log or open questions, `CARE.md` sections, `SCHEDULE.md` near-term tasks. Don't restate the plan here.
- **What belongs elsewhere:** Pest sightings tied to the perennial pest log → `PESTS.md`. Weather events themselves → `WEATHER.md` (an observation of a plant's *response* to weather can live here and link to the weather entry).
- **Longevity:** Observations are historical — leave old files in place rather than editing them; write a new dated file for a follow-up.

## Schedule (`SCHEDULE.md`)

- Start with: **Generated:** ISO date and what it was based on (e.g. “CROPS.md + frost dates from PLAN.md”).
- **Near term (about 4 weeks):** weekly task lists.
- **Rest of ~3 months:** weekly or biweekly buckets; use **monthly** sections only when detail would be noise.
- Tie tasks to crops/beds where helpful; avoid duplicating long care prose by pointing to `CARE.md`.

## Git

Commit and push to main (no review process) after meaningful updates so the plan of record has history.
