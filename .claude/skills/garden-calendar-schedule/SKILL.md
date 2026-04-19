---
name: garden-calendar-schedule
description: Regenerate or create the rolling approximately-three-month garden task schedule (SCHEDULE.md) in the garden git repo from PLAN.md and CROPS.md—action-first, minimal duplication; weekly or date-range near term, coarser buckets further out, frost-driven indoor/outdoor timing. Use when the user asks for a seasonal calendar, what to do this week, next three months of tasks, or to refresh SCHEDULE.md.
---

# garden-calendar-schedule

## Repository

| | |
|--|--|
| **Remote** | `https://github.com/blevinstein/garden` |
| **Local checkout** | `~/dev/garden` |

Work in **`~/dev/garden/<YYYY>/`**. Obey **`~/dev/garden/CONVENTIONS.md`**.

## Scope

- Read **`PLAN.md`** (frost dates, zone, constraints) and **`CROPS.md`** (what is growing, seed vs transplant).
- Write or replace **`SCHEDULE.md`** with a **rolling ~3-month** view from **today’s date** (or a date the user specifies).
- **Structure:**
  - Header: **Generated:** ISO date; note inputs (e.g. “from PLAN.md + CROPS.md, frost dates as stated in PLAN.md”).
  - **Near term:** Prefer **date-range** sections (e.g. pre-trip, travel, first week back) when many calendar weeks would be **no-ops**; use **Week of …** sections when tasks genuinely change week to week.
  - **Remainder of the 3-month window:** weekly, biweekly, or **monthly** buckets—whichever keeps the file short without hiding real deadlines.
- Reference **`CARE.md`** for recurring care (fertilize, prune) without pasting long prose—point to sections.

Out of scope: editing **`PLAN.md` / `CROPS.md` / `CARE.md`** except when a contradiction must be fixed to make the schedule sane (prefer flagging the user); primary narrative edits belong to **`garden-plan-of-record`**. Layout work belongs to **`garden-layout-ascii`**.

## Rules

- **Frost dates** must come from `PLAN.md` or explicit user message—do not guess.
- **Action-first (default tone):** The schedule is a **to-do list for people**, not a second copy of the plan. Include only tasks for the homeowner or an **explicit** helper (neighbor, sitter). When automated systems cover a stretch and **nothing** is required, say so in one line (e.g. “Nothing required unless …”) instead of filling weeks with reminders.
- **No no-op sections:** Do not create headings whose only content is “while away, no tasks,” purely informational restatement of the drip program, or “optional” filler unless the user asked for contingency checks. Collapse quiet periods; keep optional neighbor/sitter items in **one** compact bullet.
- **No duplicate reference material:** Do not paste zone/bed/crop summary tables or long irrigation narratives that already live in **`PLAN.md`** / **`CROPS.md`** / **`CARE.md`**—link to the right section instead.
- Tasks should be actionable when present (verb + object + crop/bed when useful).
- If the season folder or `SCHEDULE.md` is missing, create the folder/files per `CONVENTIONS.md` after confirming the year.

## Workflow

1. Identify `<YYYY>` and read `PLAN.md`, `CROPS.md`, and `CARE.md` if present.
2. Build the schedule from recorded frost dates and crop methods (direct sow vs transplant).
3. Draft sections, then **prune**: remove rows that only duplicate `PLAN.md`/`CROPS.md`, remove empty weeks in favor of date ranges, and merge redundant optional checks.
4. Rewrite `SCHEDULE.md` with the agreed structure and a fresh **Generated** line.
5. Tell the user the file path for an easy commit.
