# A1 + Diagnostic-Driven Milestone Loop — Design

**Date:** 2026-06-19
**Status:** Approved

## Goal

Two things in one spec:
1. **Project-loop change:** every milestone now opens with a diagnostic questionnaire that generates a study plan tailored to the learner's actual gaps.
2. **First application:** run this for milestone **A1 — How the web & browser work**.

The mechanic is proven on A1 first; later milestones reuse it.

## Loop change (project-wide)

The milestone loop changes from 3 beats to **5 beats**:

> **diagnostic quiz → tailored study plan → module → mini-project → debug drill**

This supersedes the 3-beat loop described in `2026-06-19-angular-mentorship-system-design.md` and in `CLAUDE.md`. Both are updated to reflect the 5-beat loop.

## Diagnostic mechanics

- The mentor decomposes the milestone into **subtopics**.
- For each subtopic, the mentor asks **1–2 knowledge-check multiple-choice questions** (~6–12 total per milestone) — real questions with right/wrong answers, not self-ratings.
- Questions are delivered through the in-terminal multiple-choice question UI (AskUserQuestion).
- Each subtopic is scored from the answers as **mastered / partial / gap**:
  - **mastered** — answered correctly and confidently.
  - **partial** — mixed / partially correct.
  - **gap** — wrong or guessed.

## Results record: `milestones/NN-topic/diagnostic.md`

One file per milestone, created when the diagnostic runs. Contents:

1. **Header** — milestone ID + title, date run.
2. **Questions & answers** — each question, the options, the learner's answer, the correct answer, pass/fail.
3. **Per-subtopic verdict** — table of subtopic → mastered/partial/gap.
4. **Generated study plan** — what the module/mini-project/drill will cover, derived from the verdicts.

This file is also the **freshness baseline** that the future refresher/recall mode (GitHub issue #1) reads.

## Results → tailored study plan

The generated plan maps verdicts to depth:

- **mastered** → skipped, or a one-line recap only.
- **partial** → a short, targeted module section.
- **gap** → full teaching, and the mini-project + debug drill are aimed at these.

So the module, mini-project, and debug drill are generated from the learner's real gaps rather than being fixed content.

## A1 application

**Milestone folder:** `milestones/01-web-browser/`
**Diagnostic file:** `milestones/01-web-browser/diagnostic.md`

**A1 subtopics to diagnose:**
1. Client–server model & HTTP request lifecycle
2. DNS resolution
3. The browser's job (what a browser actually does)
4. The DOM (what it is, how it relates to HTML)
5. Rendering pipeline: parse → render tree → layout → paint → composite
6. Reflow / repaint triggers
7. Event loop basics (tasks, microtasks, rendering)

Learner is backend-strong, so subtopics 1–2 are expected to skew **mastered** and 4–7 to skew **gap/partial** — but the diagnostic decides, not the assumption.

**Flow for A1:**
1. Create `milestones/01-web-browser/` folder.
2. Run the diagnostic (6–12 MC questions across the 7 subtopics).
3. Write `diagnostic.md` with answers, verdicts, and generated plan.
4. (Module → mini-project → debug drill are executed in the *next* milestone cycle, guided by the generated plan — not part of this spec's build.)

## Scope boundary (YAGNI)

- This spec covers the **loop change + diagnostic mechanic + running A1's diagnostic and generating A1's plan.**
- It does **not** include teaching the A1 module, building the mini-project, or the debug drill — those follow once the plan exists.
- No automated scoring tooling; the mentor scores answers inline. No new dependencies.

## Out of scope

- The refresher/recall mode itself (issue #1) — only the `diagnostic.md` format is designed to be compatible with it.
- Mini-project / drill content for A1.

## Next step after this spec

Invoke writing-plans to produce the implementation plan: update docs for the 5-beat loop, scaffold `milestones/01-web-browser/`, run the A1 diagnostic, and write `diagnostic.md` with the tailored A1 plan.
