# Meal Planner

Weekly Telugu meal planning for a household of 4. Monday to Saturday,
one dry and one wet each day.

```
meal-planner/
├── README.md
├── rules.md              the ruleset
├── dishes.md             master dish list, fixed anchors, dry/wet split
├── current-week.md       the in-progress week (rule 24)
├── cook-message.txt      this week in Hindi for the cook, WhatsApp-ready
└── weeks/
    ├── TEMPLATE.md       copy this for a new week
    ├── 2026-08-17.md
    ├── 2026-08-24.md     one file per completed week
    ├── 2026-08-31.md
    ├── 2026-09-07.md     plan only, unconfirmed
    ├── 2026-10-05.md     partial
    └── 2026-10-12.md     plan only, unconfirmed
```

## Weekly routine

"Do this week's meal plan" should be enough. Claude has no memory between
sessions; this folder is the memory, so read it directly — nothing to paste.

1. **Read** `rules.md`, `dishes.md`, `current-week.md` and the last two files in
   `weeks/`.
2. **Close out last week.** Ask what actually got cooked and any swaps, mark
   rows `cooked`, then move `current-week.md` to `weeks/YYYY-MM-DD.md` (its
   Monday). No answer → rows read `unconfirmed`, the whole plan counts as
   eaten, and say so.
3. **Plan the week** into `current-week.md` from last week's bank. Link each
   dish to its recipe video from `dishes.md`.
4. **Show the cook message in English** in chat (format below) and wait for
   approval. A correction that sounds standing ("never", "every Saturday")
   goes into `rules.md` / `dishes.md` straight away; if unclear, ask once.
5. **Write `cook-message.txt` in Hindi**, line for line from the approved
   English.
6. **Draft it in WhatsApp** to Kamal (below). Send only after the user says
   send, and confirm it shows Delivered.
7. **Commit and push** — `git add -A && git commit && git push`. Remote is the private repo `kowshiksiva5/meal-planner`.

## Once the week is done

Mark the days that actually got cooked as `cooked`. If something was swapped
mid-week, edit the row to what really happened — a plan that doesn't match the
kitchen is worse than no record at all. If it isn't done by then, step 2 of the
next routine does it.

## Learnings

- Use names the household knows: Telugu, English in brackets (aratikaya, not
  "raw banana fry"). The cook gets Hindi names.
- The cook makes simple home food. No cashew-heavy or restaurant-rich curries
  (rule 16). New dishes only when asked, and keep them simple.
- Chicken quantity isn't planned — it's told to the cook on the day.
- Roti is 200 g a day, none on the ghee roast day.
- The user picks recipe videos, Hindi where possible. Store each link on its
  dish in `dishes.md` so later weeks reuse it.
- Corrections come short and dictated ("Sat also andhra chicken fry"). Apply
  them and confirm in a line; save questions for real forks.

## Adding a dish

Add it to the right table in `dishes.md`, linked to its recipe video if there
is one. Note whether it's dry or wet, whether it works with roti, and flag it
if it's sour or curd-based — those drive the pairing rules.

## Sending to the cook

Kamal (WhatsApp: "Kamal Cook bhaiya") reads Hindi only.

**Message format** (`cook-message.txt`):

- Devanagari. WhatsApp `*bold*` day headings, one block per day.
- 🥘 dry, 🍲 wet, 🍗 chicken, 🥚 egg, 🍚 base. `▶️ <link>` under each dish that
  has a video.
- Top lines: the dates, "rice every day, roti 200 g except Wednesday", "cook
  once, serve at lunch and dinner", "▶️ = video".
- No chicken quantities.

**Drafting it** — WhatsApp Web in Edge Beta, driven with AppleScript
`execute (active tab of window id N) javascript`:

1. Open a new Edge Beta window on `https://web.whatsapp.com` and keep its
   window id. Wait for `#side` to exist (chats take ~20 s to load).
2. Search: set `#side input[aria-label="Search or start a new chat"]` with the
   native value setter plus an `input` event. Open the chat by dispatching
   mousedown, mouseup and click on the result's `[role=gridcell]`.
3. Before every write, check the first line of `#main header` is
   `Kamal Cook bhaiya` — the user may switch chats in that window.
4. The compose box is a Lexical editor. Clear it: select its contents with a
   Range, then in a separate call dispatch `beforeinput` with
   `deleteContentBackward` (`execCommand('delete')` does nothing). Insert:
   dispatch a `paste` ClipboardEvent whose DataTransfer holds the text
   (base64 the file to carry Devanagari through AppleScript). Never send
   keystrokes — Enter sends.
5. Diff the compose box's `<p>` lines against the file. On the user's go,
   click `#main footer button[aria-label="Send"]` and check the last row has
   the `Delivered` label.
