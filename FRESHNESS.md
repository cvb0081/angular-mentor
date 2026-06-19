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
