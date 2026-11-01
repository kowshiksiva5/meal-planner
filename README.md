# Meal Planner

Weekly Telugu meal planning for a household of 4. Monday to Saturday,
one dry and one wet each day.

```
meal-planner/
├── README.md
├── rules.md              the ruleset
├── dishes.md             master dish list, fixed anchors, dry/wet split
└── weeks/
    ├── TEMPLATE.md       copy this for a new week
    └── 2026-08-24.md     one file per week, newest is current
```

## How to use it

Claude has no memory between sessions, which is what caused the repeats.
The `weeks/` folder is the fix — it's the record.

At the start of a planning session, paste in:

1. `rules.md`
2. `dishes.md`
3. The last two files from `weeks/`

Then ask for the week. Everything needed to avoid a repeat is now on the table.

## After each week

Mark the days that actually got cooked as `cooked`. If something was swapped
mid-week, edit the row to what really happened — a plan that doesn't match the
kitchen is worse than no record at all.

## Adding a dish

Add it to the right table in `dishes.md`. Note whether it's dry or wet, and
flag it if it's sour, curd-based or rich — those three drive the pairing rules.
