---
name: brain-dump
description: Triage a raw brain dump into the Kidwell _planning files (NOW.md, INBOX.md, SOMEDAY.md, OPERATING-SHEET.md, bets/). Use when the founder says "brain dump", "process this", "clear my head", "sort this", or pastes a messy stream of ideas, updates, loops, or bet progress to be cleaned up and filed. The skill cleans the dump, asks only the clarifying questions the operating system requires, enforces the anti-jump guardrails, proposes a plan, and updates the files after confirmation. It is a triage tool, not a coding agent — it files and clarifies, it never builds.
---

# Brain Dump Triage

Turn a messy stream of consciousness into clean, correctly-filed entries in the `_planning/` system — while protecting the active bet from scope creep and the founder from jumping.

This skill operates the system described in `_planning/OPERATING-SHEET.md`. Read that file first every run, so the current goal and active bet are loaded before you classify anything.

## The files you manage

| File | Holds | Stakes |
|---|---|---|
| `NOW.md` | 3-line daily slice: current bet, week-3 signal, the one if-then | High — rewrite only at settlement |
| `INBOX.md` | Raw timestamped capture | Low — append freely |
| `SOMEDAY.md` | Parked ideas that survived triage (candidate bets) | Low — append after triage |
| `OPERATING-SHEET.md` | §2 goal (OKR), §3 active bet card, §4 open loops, appendix | High — confirm before editing §2/§3 |
| `bets/<YYYY-MM-slug>.md` | Settled bets, frontmatter-stamped outcome + learning | Append at settlement only |

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
git add _planning
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
