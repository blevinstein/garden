# Layout legend — 2026 interior diagrams

Canonical **bed and greenhouse** drawings are **per-enclosure** SVGs in this folder (no whole-property site plan). Pair with [`../PLAN.md`](../PLAN.md) and [`../CROPS.md`](../CROPS.md).

## Files

| File | Interior | Zone | Contents (schematic) |
|------|----------|------|----------------------|
| [`interior-fs2.svg`](interior-fs2.svg) | 6 × 3 ft | 2 | Brussels sprouts; oregano corner TBD |
| [`interior-fs1.svg`](interior-fs1.svg) | 6 × 3 ft | 2 | Yellow + green onions (15 positions); oregano TBD |
| [`interior-ps2.svg`](interior-ps2.svg) | 6 × 3 ft | 2 | Kale + lemon balm |
| [`interior-ps1.svg`](interior-ps1.svg) | 6 × 3 ft | 2 | Six strawberries |
| [`interior-greenhouse.svg`](interior-greenhouse.svg) | 6 × 4 ft | 1 | Tomato (vertical), peppers, jalapeño, sweet potato |

## SVG units

- **1 SVG unit = 1 inch** on the interior rectangle (**72×36** for beds, **72×48** for greenhouse), plus a small margin for titles and notes.
- **North** is the **top** edge of each interior (labeled on drawing).

## Drip / irrigation (each file)

| Element | Meaning |
|---------|---------|
| **M** (blue FS/PS, green GH) | Manifold / tee where 1/4″ run enters the box (corner is schematic). |
| **Brown lines** | 1/4″ tubing (schematic path, not literal routing). |
| **Aqua / green dots** | Emitter locations at plant positions. |
| **Footer text** | Target **GPH** and **timer zone** per [`PLAN.md`](../PLAN.md). |

**Zone 2** raised beds share one timer in the plan; **Zone 1** is the greenhouse. Program run times in `PLAN.md` / `CARE.md`, not on these diagrams.

## Adjusting

- Move plant circles and emitter stubs when you finalize spacing; keep **`<g id="plants">`** and **`<g id="irrigation">`** separate per [CONVENTIONS.md](../../CONVENTIONS.md).
- Site context (where each box sits on the lot) stays in [`../sketches/`](../sketches/) and narrative `PLAN.md` only.
