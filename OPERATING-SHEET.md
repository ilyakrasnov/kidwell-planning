---
type: season-sheet
north_star: "50000 NIS MRR"
committed_goal: "20000 NIS MRR — replace second household income"
season: "2026 · Season 1"
created: 2026-06-22
review_cadence: monthly
status: active
tags: [kidwell, operating-system, goals, bets]
---

# Kidwell Operating Sheet — Season 1 · 2026

> How to use: this is the one page you open when you don't know what to do next. Swap anything in `[brackets]`. The **only mandatory ritual is the monthly settlement** — everything else is support. Read top-to-bottom when you're lost; otherwise live in §3 (this month's bet).

---

## 1. The Stack

| Level | What | Changes |
|---|---|---|
| **North Star** | 50K NIS MRR (Cloudinary-exit threshold) | Rarely. Sets bearing, not focus. |
| **Committed Goal (this season)** | **20K NIS MRR — replace my wife's income** | Each season. This is what bets ladder up to. |
| **This Month's Bet** | [Gap-Selling cold outreach → design partners] | Monthly. The thing you actually do. |

Aspirational vs committed: **50K is the summit (aspirational); 20K is the next camp (committed).** You run the system against the camp. You don't aim bets at the summit while crossing the crevasse.

---

## 2. This Season's Goal (OKR form)

**Objective:** Replace my wife's income through Kidwell, so the family's risk and her options change for real.

**Key Results** *(outcomes, not tasks — each has a number and a date):*
- **KR1** — Reach **20K NIS MRR** by `[2026-09-30]`.
- **KR2** — `[N]` paying customers at `[price]` NIS/mo.
- **KR3** — `[leading metric, e.g. 10 active design partners / X qualified pipeline]`.

**Net check:** 20K MRR must *net the household* what her income brings home, after Kidwell's costs + tax. Confirm the real number: `[gross MRR target after costs = ___]`.

**On-path check (run on every bet):** *Does this also move me toward 50K, or only toward 20K?* A shortcut to 20K via the wrong segment or unscalable pricing strands you later. Catch those.

---

## 3. This Month's Bet

> One primary bet. A second small one only if it doesn't dilute focus.

- **Window (appetite, fixed):** `[2026-06-23]` → `[2026-07-23]`
- **Serves goal:** KR `[1 / 3]`
- **Thesis:** A month of `[Gap-Selling cold outreach to private child psychologists]` produces `[enough qualified discovery calls to believe design partners are reachable]`.
- **Readable signal (by week 3–4):** `[8+ discovery calls booked, 2+ verbal interest]`
- **Settlement date:** `[2026-07-23]` → call it: **WON** (keep/scale the channel) · **LOST** (switch channel, not goal) · **RENEW** (consciously re-bet, eyes open).
- **Fold rule:** I may kill this bet early *only* by writing one line of why ("`[customer call invalidated the thesis]`"). No silent drift.

**WOOP for this bet**
- **W** — `[Land 3 design partners this quarter.]`
- **O** — `[My wife has options; the family breathes easier.]`
- **O (inner obstacle)** — `[The pull to abandon the bet mid-month and chase a fresh idea.]`
- **P** — `If the urge to jump hits mid-bet, then it goes to the inbox and I return to the bet.`

---

## 4. Open Loops (the ~10%)

Scheduled, not ambient. Fenced, not free-roaming.

- **Relationship slot** — standing `[Friday afternoon]`, half-day. Time-sensitive, compounding. *This is most of the 10%.*
  - Warm threads: `[Viki Slavin]`, `[WeCcelerate / Noam Ohayon — Leumit]`, `[Beer Sheva solo-founders group]`, `[...]`
- **Someday / Maybe (parked ideas)** — deferrable. They wait for the next betting table. They do **not** interrupt the active bet.
- **Reframe:** the 10% isn't a distraction *from* the bets — it's where next month's bets get **scouted**. It's R&D for the betting table.

Routing rule: **ideas → inbox. relationships → the slot.**

---

## 5. The Operating Loop (kept thin on purpose)

- **Capture (always-on):** idea hits → `capture "..."` → keep working. Capturing beats chasing.
  ```bash
  now()     { cat ~/kidwell/_planning/NOW.md; }
  capture() { echo "- [ ] $(date +%F) $*" >> ~/kidwell/_planning/INBOX.md; }
  ```
- **Monthly settlement (the one that matters):** anchor it to a fixed trigger — `[first SSH of the new month / 1st of month]`, not a ritual you must remember. Call the bet. Place the next.
- **Between bets (cool-down):** process INBOX, scan Someday/Maybe, pick next bet against the current **constraint**.

---

## 6. Anti-Jump Guardrails (the if-then library)

These are WOOP "P"s — pre-decided so willpower isn't required in the moment.

- **If** the urge to start something new hits mid-bet → **then** it goes to the inbox and I return.
- **If** a warm intro lands mid-bet → **then** it goes to the relationship slot, not now.
- **If** the bet feels uphill and uncomfortable → **then** I name "I'm uphill" and keep climbing (that discomfort is the work, not a signal to bail).
- **If** the bet hasn't shown its signal by week 4 → **then** I settle it honestly. No auto-renew.
- **If** an idea doesn't name a goal it serves → **then** it's a distraction. Inbox or kill.

---

## Appendix — The Frameworks (what each one is for)

**Shape Up (37signals / Ryan Singer)** — Source of the bet model. *Appetite over estimate:* fix the time, flex the scope. Work runs in fixed **cycles**; the **circuit breaker** means unfinished work defaults to dead and must be re-bet (your settlement). **No backlog** — unbet ideas evaporate and re-earn their place (your inbox isn't a debt). **Hill chart:** uphill = figuring out, downhill = executing. Free: basecamp.com/shapeup.

**OKR (Objectives & Key Results)** — The goal layer. **Objective** = the outcome; **Key Results** = 2–3 measurable signals, stated as outcomes not tasks. Distinguishes **committed** OKRs (expected to hit → your 20K) from **aspirational** ones (stretch → your 50K).

**Theory of Constraints (Goldratt)** — The bet-*selection* lens. At any moment one **bottleneck** caps the goal; bet on relieving *that*, not on whatever's interesting. Answers "this bet or that bet." Your current constraint is almost certainly validated demand.

**WOOP / MCII (Gabriele Oettingen)** — The follow-through layer, and your main lever. **W**ish, **O**utcome, **O**bstacle, **P**lan. Fuses *mental contrasting* (picture the win, then contrast it with the real inner obstacle — keeps you grounded, unlike pure visualization) with *implementation intentions* (the **if-then** plan that fires automatically at the cue). Quick, daily-able. Free: woopmylife.org.

**GTD (David Allen)** — The open-loops layer. Loops nag *because* they're not in a trusted system; **capture** them and the pull to act now quiets. **Someday/Maybe** holds deferrable ideas; the **weekly review** governs them. This is what makes the 10% safe.

**12 Week Year (Brian Moran)** — The origin instinct: compress the horizon to force urgency and execution. You shrank it further (monthly bets) and added a clean settlement so "getting pulled away" has a designated outlet instead of being a failure.

---

*Review: settle the current bet on `[date]`. Re-read §1 if you ever feel the jump coming.*
