# Layout legend — 2026 interior diagrams

Canonical **bed and greenhouse** drawings are **per-enclosure** ASCII files in this folder (no whole-property site plan). Pair with [`../PLAN.md`](../PLAN.md) and [`../CROPS.md`](../CROPS.md). Grid conventions live in the `garden-layout-ascii` skill.

## Files

| File | Interior | Drip zone | Cover | Contents |
|------|----------|-----------|-------|----------|
| [`interior-fs2.md`](interior-fs2.md) | 72" × 36" | Zone 3 | **Covered** | 4 Brussels sprouts + 10 onions |
| [`interior-fs1.md`](interior-fs1.md) | 72" × 36" | Zone 3 | Uncovered | 1 rosemary + 37 onions |
| [`interior-ps2.md`](interior-ps2.md) | 72" × 36" | Zone 3 | **Covered** | 6 kale + 1 lemon balm |
| [`interior-ps1.md`](interior-ps1.md) | 72" × 36" | Zone 3 | **Covered** | 6 strawberries |
| [`interior-greenhouse.md`](interior-greenhouse.md) | 72" × 48" | Zone 4 (daily) | Structure | 1 cherry tomato, 3 bell peppers, 1 jalapeño, 3 sweet potatoes |

Drip zone numbering matches [`../PLAN.md`](../PLAN.md#irrigation-zones): **3** boxes (all four raised beds, Sun/Wed 5:30–6:00 am); **4** greenhouse (daily 6:00–6:30 am).

## Grid conventions

- **1 character = one intersection on a 6" grid.** Every bed is rendered on 6" spacing; greenhouse and raised beds both snap to a 13-column × 7-row (or 9-row for GH) lattice.
- **Units:** inches. Interior rectangle matches real footprint (**72×36** for beds, **72×48** for greenhouse).
- **Origin (0,0) is bottom-left.** `x` runs along the long (east–west) axis, increasing rightward. `y` runs along the short (north–south) axis, increasing upward.
- **North is the top of each diagram.**
- Empty intersections are `.`; plants are a single uppercase letter.

## Symbols by bed

Symbols are scoped to each file (same letter can mean different things in different beds). The symbol table in each `interior-*.md` file is authoritative for that bed.

| Bed | Symbols |
|-----|---------|
| `interior-fs1.md` | `R` rosemary · `O` onion |
| `interior-fs2.md` | `B` Brussels sprout · `O` onion |
| `interior-ps1.md` | `S` strawberry |
| `interior-ps2.md` | `K` kale · `L` lemon balm |
| `interior-greenhouse.md` | `T` cherry tomato · `B` bell pepper · `J` jalapeño · `S` sweet potato |

## Rendering notes

- No cell borders; the dot grid *is* the diagram.
- Plants with larger footprints than 6" (rosemary, sweet potato vines, tomato branches) occupy a single intersection in the diagram but are called out in the per-file Notes section.
- Drip tubing and emitter locations are **not** drawn; they live in `PLAN.md` / `CARE.md`.
