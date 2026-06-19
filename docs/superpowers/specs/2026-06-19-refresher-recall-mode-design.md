# Refresher / Recall Mode — Design

**Date:** 2026-06-19
**Status:** Approved
**Implements:** GitHub issue #1

## Goal

Keep already-learned topics warm when no real-world work is exercising them. The learner triggers a refresher; the system picks the most-overdue completed topic via spaced repetition, runs an escalating recall drill, and records the result so freshness stays tracked over time.

## Trigger & runtime model

- **Trigger:** conversational — the learner says "refresh me" / "start a refresher" (or a `/refresh`-style ask).
- **No app runtime.** The mode is mentor-driven over markdown: the mentor reads `FRESHNESS.md`, selects a topic, runs the drill in-conversation, then rewrites the topic's row and appends to `PROGRESS.md`.

## Eligibility

- Only **completed** milestones (marked `[x]` in `ROADMAP.md`) are eligible.
- In-progress (`[~]`) and not-started (`[ ]`) topics never appear.
- **Seeding:** when any milestone flips to `[x]`, the mentor adds a row for it to `FRESHNESS.md` with `interval = 1` and `next_due = today` (due immediately). This seeding step is added to the milestone-completion routine.

## Selection — spaced repetition

Each topic row carries an `interval` (days) and a `next_due` date.

- **Selection rule:** among eligible topics, pick the **most overdue** — the largest `today − next_due`.
- If no topic is overdue (`today < next_due` for all), the mentor offers the **soonest-due** topic anyway, noting it isn't due yet.
- Ties broken by oldest `last_practiced`.

### Interval update (after a session)

| Session result | New interval |
|---|---|
| **pass** (all attempted stages cleared) | `interval × 2` |
| **partial** (cleared some, stumbled later) | unchanged |
| **fail** (stumbled at the first stage) | reset to `1` |

Then `next_due = today + new interval`, and `last_practiced = today`, `last result = pass/partial/fail`.

New topics start at `interval = 1` (seeded as above).

## `FRESHNESS.md` (repo root)

Single markdown table, one row per completed milestone. Human-readable and git-diffable.

```markdown
# Freshness Tracker

Spaced-repetition freshness for completed milestones. Updated by refresher sessions. See `docs/superpowers/specs/2026-06-19-refresher-recall-mode-design.md`.

| Topic | Last practiced | Last result | Interval (days) | Next due |
|-------|----------------|-------------|-----------------|----------|
| A1 Web & browser | 2026-06-20 | pass | 4 | 2026-06-24 |
```

- **Topic** — milestone ID + short name (matches `ROADMAP.md`).
- **Last practiced** — ISO date of the last refresher (or seed date).
- **Last result** — `pass` / `partial` / `fail` (or `seeded` before first session).
- **Interval (days)** — current spaced-repetition interval.
- **Next due** — ISO date `= last practiced + interval`.

## Session flow — escalating drill

Run in three escalating stages; stop early on a clear stumble:

1. **MCQ recall** — 3–5 knowledge-check multiple-choice questions on the topic (same style as milestone diagnostics).
2. **Applied task** — *only if MCQs pass* — one short hands-on task for the topic.
3. **Debug / broken-snippet fix** — *only if the task goes well* — fix or extend a small broken snippet.

**Result mapping:**
- Stumble at stage 1 (MCQ) → **fail**.
- Clear MCQ but stumble at stage 2 or 3 → **partial**.
- Clear all attempted stages → **pass**.

After the session: update the topic's `FRESHNESS.md` row per the interval table, and append a one-line entry to `PROGRESS.md` (date, topic, result).

## Components / files

- `FRESHNESS.md` (new, root) — the freshness table; single source of truth for scheduling.
- `ROADMAP.md` (read) — source of which milestones are `[x]` eligible.
- `PROGRESS.md` (append) — session log entry per refresher.
- `CLAUDE.md` (modify) — document the refresher trigger, the seeding-on-completion routine, and a pointer to this spec, so the behavior is durable across sessions.

## Out of scope (YAGNI)

- No automated script/tooling — entirely mentor-driven over markdown.
- No subtopic-level freshness (milestone granularity only); the issue's "completed + mastered subtopics" option was not chosen.
- No notifications/reminders — the learner initiates each session.
- No full SM-2 ease factor — simple ×2 / reset-to-1 scheme only.

## Next step after this spec

Invoke writing-plans to produce the implementation plan: create `FRESHNESS.md`, document the trigger + seeding routine in `CLAUDE.md`, and (since no milestone is `[x]` yet) verify the flow with a worked example rather than a live session.
