# 2026 layout

## Interior diagrams (canonical)

Each raised bed and the greenhouse has its **own SVG**: true **interior** size, schematic **plant positions**, and a **drip layer** (1/4″ runs + emitter marks). There is **no** whole-property site map in this repo.

| File | Size |
|------|------|
| [`interior-fs2.svg`](interior-fs2.svg) | 6′ × 3′ |
| [`interior-fs1.svg`](interior-fs1.svg) | 6′ × 3′ |
| [`interior-ps2.svg`](interior-ps2.svg) | 6′ × 3′ |
| [`interior-ps1.svg`](interior-ps1.svg) | 6′ × 3′ |
| [`interior-greenhouse.svg`](interior-greenhouse.svg) | 6′ × 4′ |

Symbols and drip notes: [`beds-legend.md`](beds-legend.md).

## Units

**Inches:** interior width/height in each file match real **footprint** (72″ × 36″ or 72″ × 48″). North is toward the **top** of each drawing.

## Preview (optional)

```bash
magick -background white interior-fs1.svg -strip preview-fs1.png
```

Use [`../sketches/`](../sketches/) for lot context only.

## Next steps

- Name your **timers** in `beds-legend.md` when valves are fixed.  
- Add **emitter product** part numbers if you want.  
- Regenerate tubing polylines to match how you actually run lines.  
