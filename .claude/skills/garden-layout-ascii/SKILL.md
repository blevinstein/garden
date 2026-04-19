---
name: garden-layout-ascii
description: Create or update ASCII-art garden planting layouts in the garden repo—one file per raised bed and greenhouse, with plants placed on a fixed-inch grid (default 6"). Use when updating `layout/interior-*.md`, placing plants on a grid, converting a sketch into a repo-checkable layout, or when the user wants a layout diagram.
---

# garden-layout-ascii

## Repository

| | |
|--|--|
| **Remote** | `https://github.com/blevinstein/garden` |
| **Local checkout** | `~/dev/garden` |

Season content lives under **`~/dev/garden/<YYYY>/`**. Layout files under **`layout/`**; raster references under **`sketches/`**. Follow **`~/dev/garden/CONVENTIONS.md`** for naming and rules.

## Scope

- Read the user's **raster sketch(es)** in `sketches/` (bed layout) plus any explicit plant coordinates the user gives.
- Write or update **`layout/interior-<id>.md`** (one file per enclosure: e.g. `interior-ps1.md`, `interior-greenhouse.md`). No whole-property site diagram is required unless asked.
- Maintain **`layout/beds-legend.md`**: each letter → common name (and variety if needed).
- Use **`CROPS.md`** and **`PLAN.md`** for counts, spacing, and bed labels. If the sketch and plan disagree, ask the user which is authoritative before drawing; don't silently reconcile.

## Grid conventions

- **Units:** inches, matching `layout/README.md` / `PLAN.md`.
- **Grid spacing:** default **6"**. Override only if a bed needs finer placement (e.g. 3"); prefer a finer grid over off-grid plants.
- **Intersections, not cells.** Plants sit on grid intersections (the `.` positions). Cells between intersections are implicit.
- **Origin & axes:** `(0,0)` at **bottom-left**. `x` runs along the **long axis** (increasing rightward). `y` runs along the **short axis** (increasing upward). Highest `y` row appears at the **top** of the diagram.
- **North:** top of the diagram, matching `layout/README.md`. Note orientation in prose if the bed is rotated relative to property north.
- **Bed dimensions:** must be multiples of the grid spacing. A 72" × 36" bed on a 6" grid has `(72/6)+1 = 13` columns × `(36/6)+1 = 7` rows of intersections.

## Rendering rules

Use this exact character discipline so files diff cleanly and the agent can re-read its own output reliably.

- **Empty intersection:** ASCII period `.`
- **Occupied intersection:** single **uppercase** letter matching `beds-legend.md`
- **Column separator:** one ASCII space between glyphs on the same row (so each intersection occupies 2 chars: glyph + space, except the last in the row which is just the glyph)
- **Row prefix:** `y=NN  ` (left-padded so all row prefixes in a file align; two spaces between the label and the first glyph)
- **Column axis line** beneath the grid: `x=0` aligned under the first glyph, `x=<W>` aligned under the last glyph
- **Header line** above the grid, one blank line separating:
  ```
  <BED_ID>  <W>" x <H>",  <G>" grid,  (0,0) = bottom-left
  ```
  where `<BED_ID>` is the bed label (e.g. `PS2`), `<W>`/`<H>` are bed dimensions in inches, `<G>` is grid spacing.
- **No cell borders.** Do not draw `+---+` boxes; the dot grid is the diagram.
- **No trailing whitespace.** End each row after its last glyph.
- **Off-grid plants:** if a plant coordinate is not a multiple of `<G>`, either (a) tighten the grid for that bed, or (b) snap to the nearest intersection and note the true offset in prose under the diagram. Never silently round without noting it.
- **Collisions:** two plants on the same intersection means either the plan is wrong or the grid is too coarse. Surface the conflict; do not pick a winner.

## File layout

Save as `~/dev/garden/<YYYY>/layout/interior-<id>.md`. Suggested body:

```markdown
# <BED_ID> interior

<one-line description: location, cover, sun exposure if useful>

## Planting

\`\`\`
<header line>

<grid>

<x-axis line>
\`\`\`

## Plant list

| Symbol | Plant | Positions (x, y) in inches | Count |
|--------|-------|----------------------------|-------|
| K | kale | (12,12), (30,12), ... | 8 |
| L | lemon balm | (18,12) | 1 |

## Notes

<optional: drip/timer, covers, spacing rationale, deviations from CROPS.md>
```

Keep the plant-list table in sync with the grid: every symbol in the grid appears in the table, and the count matches.

## Rendering template

For a **72" × 36" bed on a 6" grid** (PS1/PS2/FS1/FS2 in the 2026 season), the empty template is:

```
<BED_ID>  72" x 36",  6" grid,  (0,0) = bottom-left

y=36  . . . . . . . . . . . . .
y=30  . . . . . . . . . . . . .
y=24  . . . . . . . . . . . . .
y=18  . . . . . . . . . . . . .
y=12  . . . . . . . . . . . . .
y= 6  . . . . . . . . . . . . .
y= 0  . . . . . . . . . . . . .
      x=0                  x=72
```

Each grid row is 31 characters wide: 6-char `y=NN  ` prefix + 13 glyphs separated by single spaces. The last glyph sits at column 30, so the `2` of `x=72` lands directly beneath it.

To place a plant at `(x, y)`:
- Column index = `x / G` (0-based from the left)
- Row index from the bottom of the grid = `y / G`; from the top = `(H/G) - (y/G)`
- The glyph sits at character position `6 + 2*(x/G)` on the matching row (assuming the `y=NN  ` prefix is 6 chars wide for 2-digit `y`).

## Worked example: PS2

```
PS2  72" x 36",  6" grid,  (0,0) = bottom-left

y=36  . . . . . . . . . . . . .
y=30  . . K . . K . . K . . K .
y=24  . . . . . . . . . . . . .
y=18  . . . . . . . . . . . . .
y=12  . . . L . . . . K . . K .
y= 6  . . . . . . . . . . . . .
y= 0  . . . . . . . . . . . . .
      x=0                  x=72
```

| Symbol | Plant | Positions (x, y) | Count |
|--------|-------|------------------|-------|
| K | kale | (12,30), (30,30), (48,30), (66,30), (48,12), (66,12) | 6 |
| L | lemon balm | (18,12) | 1 |

Note how `L` at `x=18` sits between the `x=12` and `x=24` columns — it's on a 6" grid intersection that the kale pattern skips. That's the value of the grid: offsets are explicit and checkable.

## Workflow

1. Confirm the season `<YYYY>` and read `layout/README.md` for bed dimensions, units, and north convention.
2. For each bed to diagram:
   a. Collect plant positions. Ask the user for explicit `(x, y)` tuples if the sketch is ambiguous — do not guess silently.
   b. Verify every `(x, y)` is a multiple of the grid spacing. If not, either tighten the grid or flag the offset.
   c. Check for collisions and for counts matching `CROPS.md` / `PLAN.md`. If they disagree, ask which is authoritative.
3. Draft the grid using the rendering rules above. Start from the empty template for the matching bed size.
4. Write `layout/interior-<id>.md` with the grid, plant-list table, and any notes.
5. **Read the file back** with the Read tool to verify the grid renders as intended (correct row/column alignment, right glyphs at right intersections). Fix any drift before finishing.
6. Update `layout/beds-legend.md` with any new symbols.
7. Update `layout/README.md` if file extensions, units, or naming changed (e.g. moving from `interior-*.svg` to `interior-*.md`).
8. Tell the user the paths you wrote so they can commit.

## Common pitfalls

- **Row alignment drift.** Editing a middle row without matching spaces on neighbouring rows — always re-read the file after editing.
- **Wrong origin.** Placing `y=0` at the top. Highest `y` is at the top; `y=0` is the bottom row.
- **Silent rounding.** Snapping `(21, 12)` to `(18, 12)` without saying so. Flag it.
- **Fake reconciliation.** Sketch says 6 kale; `CROPS.md` says 8; don't split the difference. Ask.
- **Cell borders.** Tempting but noisy; stick with the dot grid.
