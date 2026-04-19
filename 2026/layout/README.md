# 2026 layout

## Interior diagrams (canonical)

Each raised bed and the greenhouse has its **own ASCII file** with true interior size and schematic plant positions on a 6" grid. There is **no** whole-property site map in this repo.

| File | Size |
|------|------|
| [`interior-fs2.md`](interior-fs2.md) | 6′ × 3′ (72" × 36") |
| [`interior-fs1.md`](interior-fs1.md) | 6′ × 3′ (72" × 36") |
| [`interior-ps2.md`](interior-ps2.md) | 6′ × 3′ (72" × 36") |
| [`interior-ps1.md`](interior-ps1.md) | 6′ × 3′ (72" × 36") |
| [`interior-greenhouse.md`](interior-greenhouse.md) | 6′ × 4′ (72" × 48") |

Symbols and grid notes: [`beds-legend.md`](beds-legend.md).

## Units and orientation

- **1 character = one intersection on a 6" grid.** Empty intersections are `.`; plants are a single uppercase letter (see each file's plant list).
- Interior width/height in each file match real **footprint** (72" × 36" or 72" × 48").
- `(0, 0)` is the **bottom-left** intersection. `x` runs along the long axis (increasing rightward); `y` runs along the short axis (increasing upward).
- **North is the top** of each diagram.

Use [`../sketches/`](../sketches/) for lot context and hand-drawn reference only.

## History

Earlier versions of these diagrams were SVG (`interior-*.svg` + `beds-preview.png`). The repo moved to ASCII layouts in April 2026; the SVGs were removed. See the `garden-layout-ascii` skill for the current grid conventions.
