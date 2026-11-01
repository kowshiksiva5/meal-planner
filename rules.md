# Rules

---

## Structure

1. Six days, Monday to Saturday. Sunday is off the plan.
2. One dry and one wet a day, two dishes only. Cooked once, served at both
   meals.
3. Rice and roti every day. Some people eat rice at both meals, some eat roti
   at one, so the day's dishes must work with roti too. Thin wets (pappu
   aside) need a dry that carries the roti. (From 12 Oct 2026.) Roti is
   200 g a day, every day except the ghee roast day. (From 19 Oct 2026.)

## Fixed anchors

4. Midweek — chicken ghee roast only, with bagara rice and no roti. Wednesday
   by default, Thursday when shifted. No second dish.
5. Saturday — Andhra chicken fry only, with bagara rice + roti. (From
   19 Oct 2026.)
5a. Chicken on both days is a bone-in + boneless mix, about 2:1 bone-in.
   (From 12 Oct 2026.)
6. Friday — egg bhurji plus paneer butter masala. (From 19 Oct 2026, when
   kaju paneer was dropped.)

## Rotation

7. Nothing repeats across consecutive weeks. The fixed anchors (chicken, and
   Friday's paneer butter masala) are the only exception.
8. Check the previous week's log and exclude all of it — including anything
   that ran twice.
9. When the dry list runs short, pull from the widened list in `dishes.md`
   rather than repeating.

## Pappu

10. Once a week only.
11. Rotate the type — tomato, palak, mango. Never the same one twice in a row.

## Pairing

12. No two sour or curd-based dishes in the same week. Majjiga charu,
    majjiga pulusu, sambar and the pulusus all count as one category.
13. Retired 12 Oct 2026. Majjiga charu no longer travels with the ghee
    roast; the roast now goes with bagara rice (see rule 17).
14. Sambar pairs with chicken, not on its own day.
15. Don't put two fries on the same plate.
16. No cashew-heavy curries. The cook doesn't make them. (From 19 Oct 2026;
    replaces the old rich-wets rule.)
17. Bagara rice is already flavoured, so it doesn't need a charu beside it.
    Onion-lemon salad if the plate feels dry.
18. Don't double an ingredient across the week — e.g. drumstick in two
    dishes, chole and bobbarlu together, or egg on two days.

## Working method

19. Plan one week at a time. No multi-week grids.
20. Every unused dish goes into a bank, listed at the end of each week's plan.
21. Claude has no memory between sessions. The `weeks/` folder is the memory —
    read the last two weeks before planning a new one.
22. If a week is partly cooked already, plan only the remaining days and treat
    what's been eaten as used up.
23. No curry repeats in the immediately following week. The fixed anchors are
    the only exception.
24. The in-progress week lives in `current-week.md` at the repo root, not in
    `weeks/`. It moves into `weeks/` when the next week is planned; days not
    confirmed read `unconfirmed` and count as eaten.

