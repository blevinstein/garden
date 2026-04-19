---
name: garden-irrigation-plan
description: Plan or update the garden irrigation schedule and per-plant drip emitter sizing. Use when the user wants to set zone run times, size emitters, fit zones into an early-morning window, reconcile the plan with already-installed hardware, or update the Irrigation zones section of PLAN.md and Irrigation tuning notes in CARE.md.
---

# garden-irrigation-plan

## Repository

This skill applies to the **garden** git repository. Use the **repository root** of the open workspace (the directory that contains `CONVENTIONS.md` and per-year folders)—do not assume a fixed clone path.

Work inside **`<YYYY>/`**. Obey **`CONVENTIONS.md`** at the repository root.

## Scope

- Update **`PLAN.md` → Irrigation zones**: schedule table and per-plant emitter table.
- Update **`CARE.md` → Irrigation / Irrigation tuning**: seasonal tuning notes.
- Append a dated **decisions-log entry** in `PLAN.md` whenever schedule, run times, or emitters change.
- Keep **`CROPS.md` Zone column** in sync if zone numbering shifts.

Out of scope: layouts (`garden-layout-ascii`), task schedule (`garden-calendar-schedule`), broader plan edits (`garden-plan-of-record`).

## Inputs to gather

Ask once if missing; record in `PLAN.md` for reuse. Never guess.

1. **Zones** — how many valves and what each covers.
2. **Days per zone** — typical schedule (e.g. Sat/Wed; greenhouse daily).
3. **Clock window** — span all cycles must fit in (e.g. midnight–10am).
4. **Installed emitters** — per plant, size (GPH). Reused by default.
5. **Spare inventory** — sizes on hand (commonly ½, 1, 2 GPH).
6. **Preference** — extend run times vs. add emitters when plans conflict.

## Core formula

```
gal / plant / week  =  emitter GPH  ×  run time (hours)  ×  days per week
```

Run time is shared across all plants in a zone. Per-plant tuning is via emitter GPH (or, rarely, a second emitter on one thirsty plant).

## Weekly water reference

Peak-season targets, Front Range (Denver). Revise downward in shoulder seasons. Defer to published data or the user if available.

| Plant | Gal / plant / week |
|-------|---------------------|
| Young fruit tree (peach, cherry, oak) | 5–10 (deep; probe 12") |
| Established fruit tree | 10–20 |
| Cucumber, spaghetti squash | 3–4 |
| Hops | 3–4 |
| Morning glory | 2–3 |
| Peas | 1–2 |
| Cherry tomato (greenhouse) | 7–14 |
| Sweet potato | 5–10 |
| Bell pepper, jalapeño | 2–3 |
| Brussels sprout | 2–4 |
| Kale | 1–2 |
| Strawberry | 2–4 fruiting, 1–2 after |
| Onion | 0.5–1 |
| Lemon balm | 0.5–1 |
| Wildflowers (established) | 0.5–1 per emitter |
| Rosemary, lavender, Russian sage, Mormon tea | **dryland — no emitter** |

## Strategy

1. **Tightest plant sets the run time.** For each zone, the plant with the largest `target ÷ (GPH × days)` is the binding constraint. Example: peach at 6 gal/wk, 1 × 2 GPH, 2 days/wk → `6 / (2×2) = 1.5 hr`.
2. **Round up to 15-min.** If the result exceeds the zone's or user's clock window, either add an emitter on that plant (halves the run time) or flag the trade-off.
3. **Size every other plant's emitter** so its weekly gallons land in its target range. Low-water → ½ GPH, thirsty → 2 GPH, middle → 1 GPH if spares available, **dryland → no emitter**.
4. **Check the schedule fits** the user's clock window plus any requested buffers.
5. **Verify each plant is in range.** Flag anything outside — resize its emitter or note the trade-off.

## Workflow

1. Read `PLAN.md` Irrigation zones, `CARE.md` Irrigation tuning, and `CROPS.md` Zone column.
2. Gather any missing inputs from the user.
3. For each zone: find the tightest plant → compute run time → size remaining emitters → sanity-check.
4. Place each zone on the clock; insert buffers where requested.
5. Rewrite `PLAN.md → Irrigation zones`:
   - Intro paragraph (window, days, strategy one-liner, hardware on hand).
   - **Schedule** table: `# | Zone | Window | Days | Run time | Plants`.
   - **Emitters per plant** table: `Zone | Plant | Emitter | Gal/plant/week`.
   - Short **Notes**: reused vs new hardware, 1 GPH swaps, dryland skips.
6. Rewrite `CARE.md → Irrigation tuning` with operational bullets only (no duplicate schedule or emitter table). Cover: starting-target caveat, soil-check routine, which lever to pull first on stress (matches user preference), rain skip rule.
7. Append a decisions-log entry in `PLAN.md` (`YYYY-MM-DD: …`) summarizing window, days, run times, and emitter-sizing strategy.
8. Report the file paths changed.

## Common pitfalls

- **Invented water targets.** Use the reference table or ask; don't guess.
- **Ignoring installed hardware.** Default is to reuse; propose changes only when run time would otherwise overflow the clock window.
- **Uniform run time + uniform emitter.** Onions get flooded and Brussels go dry. Always size emitters to plants.
- **Back-to-back zones.** Leaves no room to extend one zone without cascading. Ask if a buffer is wanted.
- **Dryland in an irrigated zone.** The right answer is **no emitter**, not a small one.
- **Stale `CROPS.md` Zone column.** If zone numbers shift, update it.
- **Undocumented schedule change.** Always add a decisions-log entry — future-you needs the reasoning.
