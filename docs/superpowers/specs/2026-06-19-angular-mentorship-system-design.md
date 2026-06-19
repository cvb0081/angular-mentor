# Angular Zero→Senior Mentorship System — Design

**Date:** 2026-06-19
**Status:** Approved

## Goal

Take the user from backend-strong / frontend-weak to confidently listing **Angular** (and solid web fundamentals — HTML, CSS, JS, TypeScript) on their resume. Learning is hands-on, real-world-resembling: explore, implement, fix, debug. The repo itself tracks the journey.

## Learner profile

- **Starting point:** Strong backend / full-stack engineer. Frontend is the gap.
- **Implication:** Skip absolute-beginner programming concepts. Gap-fill frontend fundamentals (HTML/CSS, DOM, TypeScript-for-frontend, browser model) fast, then go deep on Angular.

## Scope

- **Frontend-only focus.** Capstone and exercises use a **mock API** (json-server / in-memory / static JSON). No real backend built in this project — keeps 100% of effort on Angular/frontend depth.
- Capstone domain **decided early in Phase 2**, chosen to best teach the concepts and maximize resume value.

## Two phases

### Phase 1 — Roadmap build (do first)

1. Research multiple sources: roadmap.sh (frontend + Angular tracks), official Angular docs/learning path, respected courses and blogs.
2. Present source roadmaps **side-by-side** for the user to curate (keep/drop/reorder).
3. Synthesize one **master roadmap**: an ordered list of skill milestones, calibrated for the learner profile and frontend-only scope.
4. Output committed to `ROADMAP.md` plus raw notes in `research/`.

**Method:** Research + user curates. Sourcing is current/live research, not memory-only.

### Phase 2 — The course

Work through milestones in order. Each milestone gets its **own detailed plan when reached** — not all planned upfront (keeps plans accurate to actual pace).

## Milestone anatomy — the learning loop

Each milestone runs three beats:

1. **Module** — mentor teaches the concept with small examples.
2. **Mini-project** — learner builds something focused applying it.
3. **Challenge / debug drill** — mentor hands over broken or half-built code; learner fixes/extends to drill the details.

Mini-projects feed the **capstone app** wherever possible, so the capstone grows as a real evolving application rather than throwaway exercises.

## Repo structure

```
/CLAUDE.md            Living mentor brief; evolves with learner pace & preferences
/ROADMAP.md           Master roadmap, checkbox per milestone
/PROGRESS.md          Running log: date, milestone, what clicked, what was debugged
/research/            Phase 1 source roadmaps + synthesis notes
/foundations/         HTML/CSS/TS/JS gap-fill exercises
/milestones/NN-topic/ Per-milestone module notes + mini-project + drills
/capstone/            The evolving real app
/docs/superpowers/    Specs and plans
```

## Progress tracking

- **`ROADMAP.md`** — checkboxes = the map of where we are.
- **`PROGRESS.md`** — running log per session (date, milestone, what clicked, what was debugged). Doubles as a source of resume talking points.
- **`CLAUDE.md`** — updated as the mentor learns the learner's pace and preferences, so mentoring improves over time.

## Mentor stance (encoded in CLAUDE.md)

- Favor explanation and understanding over producing finished code.
- Let the learner struggle productively; give hints before answers on drills.
- Build concepts progressively; assume earlier topics may still be new.

## Out of scope (YAGNI)

- No real backend / database.
- No deployment/devops track unless it surfaces as a curated roadmap item later.
- No upfront full-course plan — milestones planned just-in-time.

## Immediate next step after this spec

Invoke writing-plans to produce the **Phase 1 (roadmap build)** implementation plan: how the research, side-by-side presentation, curation, and synthesis into `ROADMAP.md` will run.
