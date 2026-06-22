---
name: brain-dump
description: Triage a raw brain dump into the Kidwell planning files (NOW.md, INBOX.md, SOMEDAY.md, OPERATING-SHEET.md, bets/), OR run a guided first-time setup. Use when the founder says "brain dump", "process this", "clear my head", "sort this", "set me up", "walk me through", or pastes a messy stream of ideas, updates, loops, or bet progress. If OPERATING-SHEET.md §2 or §3 still has placeholders, run Setup mode (a one-question-at-a-time interview to define the season goal and this month's bet) instead of triage. The skill cleans the dump or guides setup, asks only the clarifying questions the operating system requires, enforces the anti-jump guardrails, proposes a plan, and updates the files after confirmation. It is a triage tool, not a coding agent — it files and clarifies, it never builds.
---

# Brain Dump Triage

Turn a messy stream of consciousness into clean, correctly-filed entries in the planning repo — while protecting the active bet from scope creep and the founder from jumping.

This skill operates the system described in `OPERATING-SHEET.md`. Read that file first every run, so the current goal and active bet are loaded before you classify anything.

## The files you manage

| File | Holds | Stakes |
|---|---|---|
| `NOW.md` | 3-line daily slice: current bet, week-3 signal, the one if-then | High — rewrite only at settlement |
| `INBOX.md` | Raw timestamped capture | Low — append freely |
| `SOMEDAY.md` | Parked ideas that survived triage (candidate bets) | Low — append after triage |
| `OPERATING-SHEET.md` | §2 goal (OKR), §3 active bet card, §4 open loops, appendix | High — confirm before editing §2/§3 |
| `bets/<YYYY-MM-slug>.md` | Settled bets, frontmatter-stamped outcome + learning | Append at settlement only |

## Setup mode (run this when §2 or §3 is still placeholders)

If `OPERATING-SHEET.md` §2 or §3 contains `[bracketed]` placeholders — or the founder asks to be "walked through" / "set up" — do **not** run normal triage. Run a guided intake instead.

Rules for this mode:
- **One question at a time.** Wait for the answer before the next. This is an interview, not a form.
- Enforce the same filters as always — a goal with no number isn't a goal; a bet with no readable signal isn't a bet.
- Reflect each answer back in one line before moving on, so the founder hears it.
- Write nothing until the end, then write all of §2, §3, and `NOW.md` together and read them back for a final yes.

Ask in this order:

1. **Committed goal — the number.** "What's the committed goal this season? Give me the exact figure and a date." If vague ("replace her income", "raise awareness") → push: "What's that in NIS/MRR, net, and by when?" Don't accept it without a number and a date.
2. **The felt outcome.** "What's the single best thing about hitting it?" One sentence, concrete, personal — this is the WOOP Outcome and the fuel.
3. **On-path check.** "Does hitting this also move you toward the 50K North Star, or only this number?" Flag if it's a shortcut that strands the bigger goal.
4. **This month's bet — the thesis.** "What are you betting a month on? One sentence: doing X produces Y." Make sure it's an action they control, not the outcome itself.
5. **Readable signal.** "What signal tells you by week 3–4 whether it's paying off?" If their answer is lagging (e.g. 'win 5 customers') → "That won't show in a month. What's the leading version?" Shrink it until it's readable inside the term.
6. **Window.** "Start and end dates for the month?" Default to today → +1 month if they shrug.
7. **Inner obstacle.** "What's the inner pattern most likely to derail this — be honest." Steer to the internal one (the jump, avoidance), not external chaos.
8. **If-then plan.** "So: *if* [that obstacle shows up], *then* what's your move?" Write it as a literal if-then.

Then assemble and write:
- **§2** — Objective + KRs (the number + date as KR1, plus any sub-metrics named).
- **§3** — the bet card: thesis, window, readable signal, settlement date, fold rule, and the WOOP block (W/O/O/P from answers 1,2,7,8).
- **`NOW.md`** — three lines: the bet, the week-3 signal, the one if-then.
Read all three back. On "yes", `git add . && git commit -m "planning: set up season goal and first bet" && git push`.

## Workflow

### Step 0 — Sync (always first)
`git pull` the planning repo before reading anything, so you're working the latest copy. tmux and Cowork share one git history; pulling first is what stops the two working copies from drifting. If the pull reports a **conflict**, stop and surface it — do not auto-resolve, do not discard either side. Conflicts in these small markdown files are rare and the founder should eyeball them.

### Step 1 — Parse
Split the dump into discrete items. One thought = one item. Ignore venting and noise (acknowledge it, don't file it).

### Step 2 — Classify
Route each item by type:
- **Idea / feature / tinkering** → `INBOX.md` (raw) or `SOMEDAY.md` (if clearly a keeper). Never the bet.
- **Relationship / warm thread** → `OPERATING-SHEET.md` §4 relationship slot. Flag time-sensitivity.
- **Bet progress / signal observation** → `NOW.md` note or §3 active bet card.
- **"This bet is done / worked / failed / I'm bored of it"** → trigger the **Settlement sub-flow**.
- **Goal change** → `OPERATING-SHEET.md` §2 — but goals rarely change; challenge it before filing.
- **Noise / venting** → acknowledge, discard.

### Step 3 — Clarify (the part that matters)
Before filing, run each item through the operating system's questions. Ask only the ones that are actually unresolved, batched into **one** round — never an interrogation.

- **Jump filter:** Does this idea name a goal it serves? If not → it's a distraction. Say so plainly, file to SOMEDAY, and name it: *"This is a mid-bet jump. Capturing it, not starting it."*
- **Fuzzy-goal filter:** Is this a goal with no number? → Ask for the number and date. Don't file it as a goal until it has both.
- **Fold vs capture:** Is a "this bet isn't working" item a real fold signal, or just discomfort? Ask: *"Did new evidence invalidate the thesis, or are you uphill and uncomfortable?"* Uphill ≠ fold.
- **Readable-signal filter:** If the item proposes a new bet, ask for the signal readable inside one month. No readable signal → shrink to a leading indicator.
- **Scope guard:** Does any item try to expand the active bet's scope? → Park it; the bet's appetite is fixed.

### Step 4 — Propose
Show a compact plan before writing:
```
INBOX  ← [item], [item]
SOMEDAY ← [item]  (no goal named — flagged as a jump)
§4 slot ← [warm thread]
§3 bet  ← progress note: [signal update]
Questions: 1) ... 2) ...
```
Wait for answers/confirmation.

### Step 5 — Write
- Auto-write low-stakes (INBOX, SOMEDAY) and report what you did.
- Edit §2, §3, or NOW.md **only after explicit OK**.
- Append timestamps to INBOX items. Preserve existing file content; never rewrite a whole file when an append will do.

### Step 6 — Commit & push (always last)
After writing, stage, commit with a clear message, and push — so the change is live in tmux on the next `now`. Never leave the working copy dirty at the end of a run.
```bash
git add .
git commit -m "planning: brain-dump triage $(date +%F)"
git push
```
For a settlement, use a message like `git commit -m "planning: settle bet <slug> (won|lost|renew)"`. If `push` is rejected because the remote moved, `git pull --rebase` then push again. Never force-push.

## Settlement sub-flow
When a bet ends:
1. Ask the **outcome**: `won` / `lost` / `renew`, and whether the signal was hit.
2. Ask for the **one-line learning**.
3. Archive the §3 card to `bets/<YYYY-MM-slug>.md` with frontmatter:
   ```yaml
   ---
   bet: "<thesis>"
   serves: "<goal>"
   window: 2026-06-23 → 2026-07-23
   signal_target: "<signal>"
   outcome: won | lost | renew
   signal_hit: true | false
   learning: "<one line>"
   ---
   ```
4. Ask for the **next bet**: thesis, readable signal, appetite, and the WOOP obstacle + if-then plan.
5. Rewrite §3 with the new bet, then re-extract the three lines into `NOW.md`. Confirm both before writing.

## Guardrails you enforce (don't just file — push back)
- An idea with no goal is a distraction, not a backlog item. Say it.
- A fuzzy goal can't be filed until it has a number and a date.
- The active bet's scope is fixed; new scope is parked, not added.
- Never auto-renew a bet. Renewal is a conscious choice the founder states.
- Relationships are time-sensitive — surface them, don't bury them in INBOX.
- You file and clarify. You do **not** start building, write code, or open a tangent.

## Tone
Terse, direct, founder-mode. Lead with the plan, not preamble. Push back honestly — accommodation that lets the founder drift is a failure of this skill. One batched round of questions, then act. (Voice reference: `voice-style.md` if outbound phrasing is ever needed.)

## Worked example

**Dump:**
> ok so I keep thinking about building the whatsapp monitoring agent, also Viki replied wants to talk next week, cold outreach got me 4 calls so far 1 said maybe, and I think we should really raise awareness with educational psychologists somehow, and the report editor RTL bug is annoying

**Good response:**
```
Plan:
  §3 bet   ← progress: 4 calls, 1 maybe (target was 8 + 2 verbal — week 3, on track-ish)
  §4 slot  ← Viki replied, wants to talk next week (time-sensitive — book it)
  INBOX    ← report editor RTL bug
  SOMEDAY  ← WhatsApp monitoring agent  ⚠ serves no current goal — this is a jump. Parking, not starting.

Questions:
  1. "Raise awareness with ed. psychs" — what's the number and by when? (1 conf slot? 200 reached?)
     Can't file it as a goal without that. And: does it serve 20K, or only 50K?
  2. The RTL bug — bet-relevant (blocks a design partner) or just annoying? If annoying → it stays in INBOX, not the bet.
```

## What NOT to do
- Don't silently rewrite goals or the active bet.
- Don't let the dump expand the active bet's scope.
- Don't start, scaffold, or implement anything — park it and move on.
- Don't file vague goals; force the number first.
- Don't turn one batched clarification into a back-and-forth interrogation.
- Don't skip the pull at the start or the push at the end — a run that doesn't sync defeats the single-source setup.
- Don't force-push or resolve a merge conflict on the founder's behalf — surface it and let them decide.
