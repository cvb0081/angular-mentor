# Refresher / Recall Mode Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Stand up the mentor-driven, spaced-repetition refresher system: a `FRESHNESS.md` tracker plus the durable behavior documented in `CLAUDE.md`, closing issue #1.

**Architecture:** No code/runtime — the feature is a markdown data file (`FRESHNESS.md`) plus mentor behavior rules written into `CLAUDE.md`. "Tests" are content-verification checks. Because no milestone is `[x]` yet, correctness is proven by a worked example embedded in `FRESHNESS.md` rather than a live session.

**Tech Stack:** Markdown. Git. `gh` for closing the issue.

## Global Constraints

- **Trigger:** conversational ("refresh me" / "start a refresher"); mentor reads `FRESHNESS.md`, runs the session, rewrites the row.
- **Eligibility:** only completed milestones (`[x]` in `ROADMAP.md`). Seeded into `FRESHNESS.md` at `interval = 1`, `next_due = today` when a milestone flips to `[x]`.
- **Selection:** most overdue (largest `today − next_due`); ties → oldest `last_practiced`; if none overdue, offer soonest-due.
- **Interval update:** pass → `× 2` · partial → unchanged · fail → reset to `1`. Then `next_due = today + interval`.
- **Session:** escalating MCQ → applied task → debug fix; stop early on a stumble. fail = stumble at MCQ · partial = clear MCQ, stumble later · pass = clear all attempted.
- **Granularity:** milestone-level only (no subtopic freshness). No notifications. No automated tooling. No SM-2 ease factor.
- **Commit footer:** end every commit with `Co-Authored-By: Claude Opus 4.8 (1M context) <noreply@anthropic.com>`.

---

### Task 1: Create `FRESHNESS.md`

**Files:**
- Create: `FRESHNESS.md`

**Interfaces:**
- Produces: the freshness table (single source of truth for scheduling) and a worked example demonstrating the interval math.

- [ ] **Step 1: Write `FRESHNESS.md`**

```markdown
# Freshness Tracker

Spaced-repetition freshness for **completed** milestones (`[x]` in `ROADMAP.md`). Updated by refresher sessions. Mechanic: `docs/superpowers/specs/2026-06-19-refresher-recall-mode-design.md`.

A row is added when a milestone is marked `[x]` (seeded at interval 1, due immediately). Selection picks the most overdue row. After a session: pass → interval × 2 · partial → unchanged · fail → reset to 1; then `next due = last practiced + interval`.

| Topic | Last practiced | Last result | Interval (days) | Next due |
|-------|----------------|-------------|-----------------|----------|

_No completed milestones yet — table fills as milestones reach `[x]`._

---

## Worked example (not live data)

Demonstrates one full cycle, to be deleted once real rows exist.

1. **A1 completed** on 2026-06-25 → seed row:

   | A1 Web & browser | 2026-06-25 | seeded | 1 | 2026-06-25 |

2. **Refresher on 2026-06-28** (A1 is 3 days overdue, picked). Learner **passes** all stages → interval `1 × 2 = 2`:

   | A1 Web & browser | 2026-06-28 | pass | 2 | 2026-06-30 |

3. **Refresher on 2026-07-02** (2 days overdue). Learner stumbles on the debug stage → **partial**, interval unchanged (2):

   | A1 Web & browser | 2026-07-02 | partial | 2 | 2026-07-04 |

4. **Refresher on 2026-07-05**. Learner fails the MCQ stage → **fail**, interval resets to 1:

   | A1 Web & browser | 2026-07-05 | fail | 1 | 2026-07-06 |
```

- [ ] **Step 2: Verify**

Confirm `FRESHNESS.md` exists, has the live table with the 5 column headers (`Topic | Last practiced | Last result | Interval (days) | Next due`), the empty-state note, and a worked example showing all three result transitions (pass ×2, partial unchanged, fail reset-to-1).

- [ ] **Step 3: Commit**

```bash
git add FRESHNESS.md
git commit -m "Add FRESHNESS.md freshness tracker (issue #1)

Co-Authored-By: Claude Opus 4.8 (1M context) <noreply@anthropic.com>"
```

---

### Task 2: Document refresher mode in `CLAUDE.md`

**Files:**
- Modify: `CLAUDE.md` (add a "Refresher / recall mode" section; extend the repo map; add seeding to the session-end routine)

**Interfaces:**
- Consumes: `FRESHNESS.md` from Task 1.
- Produces: the durable mentor behavior so any future session runs the mode consistently.

- [ ] **Step 1: Add `FRESHNESS.md` to the repo map in `CLAUDE.md`**

In the `## Repo map` list, add this line directly after the `PROGRESS.md` line:

```markdown
- `FRESHNESS.md` — spaced-repetition freshness for completed milestones; drives refresher mode.
```

- [ ] **Step 2: Add the refresher-mode section to `CLAUDE.md`**

Insert this section immediately before `## Mentor stance (for Claude)`:

```markdown
## Refresher / recall mode

Keeps completed topics warm. Triggered when the learner says "refresh me" / "start a refresher".

When triggered:
1. Read `FRESHNESS.md`. Eligible topics = rows present (only `[x]` milestones get rows).
2. **Select** the most overdue topic (largest `today − next due`); ties → oldest last practiced; if none overdue, offer the soonest-due and say it isn't due yet.
3. Run an **escalating drill**, stopping early on a clear stumble:
   - **MCQ** — 3–5 knowledge-check questions (diagnostic style).
   - **Applied task** — only if MCQ passed.
   - **Debug / broken-snippet fix** — only if the task went well.
4. **Score:** stumble at MCQ → `fail` · clear MCQ, stumble later → `partial` · clear all attempted → `pass`.
5. **Update** the topic's `FRESHNESS.md` row: pass → interval × 2 · partial → unchanged · fail → reset to 1; set `next due = today + interval`, `last practiced = today`, `last result =` the result. Append a one-line `PROGRESS.md` entry (date, topic, result).

**Seeding:** whenever a milestone is marked `[x]` in `ROADMAP.md`, add its row to `FRESHNESS.md` with `last result = seeded`, `interval = 1`, `next due = today`.
```

- [ ] **Step 3: Add seeding to the session-end routine in `CLAUDE.md`**

In `## Mentor stance (for Claude)`, change the bullet `- Keep \`PROGRESS.md\` updated at the end of each session.` to:

```markdown
- Keep `PROGRESS.md` updated at the end of each session; when a milestone is marked `[x]`, seed its row in `FRESHNESS.md`.
```

- [ ] **Step 4: Verify**

Confirm `CLAUDE.md` contains a `## Refresher / recall mode` heading, the repo map references `FRESHNESS.md`, the section lists the 5-step trigger flow and the seeding rule, and the mentor-stance bullet now mentions seeding `FRESHNESS.md`.

- [ ] **Step 5: Commit**

```bash
git add CLAUDE.md
git commit -m "Document refresher/recall mode behavior in CLAUDE.md (issue #1)

Co-Authored-By: Claude Opus 4.8 (1M context) <noreply@anthropic.com>"
```

---

### Task 3: Log, push, and close issue #1

**Files:**
- Modify: `PROGRESS.md`

**Interfaces:**
- Consumes: completed `FRESHNESS.md` + `CLAUDE.md` changes.
- Produces: log entry; remote updated; issue #1 closed.

- [ ] **Step 1: Append a `PROGRESS.md` entry**

```markdown
## 2026-06-19 — Refresher/recall mode built
- **Did:** Designed and implemented refresher mode — `FRESHNESS.md` tracker + spaced-repetition behavior in `CLAUDE.md`. Closed issue #1.
- **Clicked:** Spaced-repetition scheduling (interval ×2 / reset-to-1) and the escalating MCQ→task→debug drill.
- **Debugged:** —
- **Resume note:** Built a self-directed spaced-repetition skill-retention system.
```

- [ ] **Step 2: Commit and push**

```bash
git add PROGRESS.md
git commit -m "Log refresher mode completion

Co-Authored-By: Claude Opus 4.8 (1M context) <noreply@anthropic.com>"
git push
```

- [ ] **Step 3: Close issue #1**

```bash
gh issue close 1 --repo cvb0081/angular-mentor --comment "Implemented as a mentor-driven markdown system: FRESHNESS.md tracker (spaced repetition, interval x2 / reset-to-1) + refresher behavior documented in CLAUDE.md. Design: docs/superpowers/specs/2026-06-19-refresher-recall-mode-design.md. Activates once milestones reach [x]."
```

- [ ] **Step 4: Verify**

Confirm `git status` is clean, `git log origin/main..HEAD --oneline` is empty (all pushed), and `gh issue view 1 --repo cvb0081/angular-mentor --json state -q .state` returns `CLOSED`.

---

## Self-Review

**Spec coverage:**
- Trigger & runtime model → CLAUDE.md section, Task 2. ✓
- Eligibility (`[x]` only) + seeding → CLAUDE.md section + seeding bullet, Task 2; FRESHNESS.md note, Task 1. ✓
- Selection (most overdue, tie-break, none-overdue fallback) → CLAUDE.md step 2, Task 2. ✓
- Interval update table (×2 / unchanged / reset-1) → FRESHNESS.md header + worked example (Task 1) + CLAUDE.md step 5 (Task 2). ✓
- `FRESHNESS.md` format (5 columns) → Task 1. ✓
- Escalating session flow + result mapping → CLAUDE.md steps 3–4, Task 2. ✓
- PROGRESS.md append per session → CLAUDE.md step 5 (behavior) + Task 3 (this build's own log). ✓
- Out-of-scope items (no tooling/notifications/subtopic/SM-2) → respected; nothing added. ✓
- "Verify via worked example" (spec next step) → Task 1 worked example. ✓
- Issue #1 closure → Task 3. ✓

**Placeholder scan:** No TODO/TBD/“implement later”. All file content given verbatim. The worked-example dates are illustrative sample data (explicitly labeled "not live data"), not placeholders.

**Type consistency:** Column set `Topic | Last practiced | Last result | Interval (days) | Next due` identical in Task 1 and referenced consistently in Task 2. Result values `pass/partial/fail/seeded` consistent across tasks. Interval rule (×2 / unchanged / reset-to-1) stated identically in Global Constraints, Task 1, and Task 2.
