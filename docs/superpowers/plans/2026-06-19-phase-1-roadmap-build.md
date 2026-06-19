# Phase 1: Roadmap Build — Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Produce a curated, source-backed master `ROADMAP.md` that drives the Angular Zero→Senior course, plus the repo scaffolding to run it.

**Architecture:** This is a research-and-synthesis phase, not a coding phase. Tasks gather roadmap sources into `research/`, present them side-by-side for the user to curate, then synthesize one ordered master roadmap. "Tests" are artifact verification checks (file exists, required sections present, all required sources covered) rather than unit tests. Frequent commits per artifact.

**Tech Stack:** Markdown docs. WebSearch / WebFetch for live research. Git for versioning.

## Global Constraints

- **Learner profile:** Backend-strong / full-stack, frontend-weak. Roadmap skips beginner programming; gap-fills frontend fundamentals fast, then goes deep on Angular.
- **Scope:** Frontend-only. Capstone/exercises use a mock API (json-server / in-memory / static JSON). No real backend.
- **Sourcing method:** Live research (not memory-only), then user curates before synthesis.
- **Repo layout (target):** `/CLAUDE.md`, `/ROADMAP.md`, `/PROGRESS.md`, `/research/`, `/foundations/`, `/milestones/NN-topic/`, `/capstone/`, `/docs/superpowers/`.
- **Mentor stance:** Explanation over finished code; hints before answers; progressive concepts.
- **Commit message footer:** end every commit with `Co-Authored-By: Claude Opus 4.8 (1M context) <noreply@anthropic.com>`.
- **Capstone domain:** deferred to Phase 2 — do NOT pick it in this plan.

---

### Task 1: Scaffold repo structure

**Files:**
- Create: `PROGRESS.md`
- Create: `research/.gitkeep`
- Create: `foundations/.gitkeep`
- Create: `milestones/.gitkeep`
- Create: `capstone/.gitkeep`
- Modify: `CLAUDE.md` (add mentor stance + repo map)

**Interfaces:**
- Produces: the directory skeleton and `PROGRESS.md` log that every later task and all of Phase 2 writes into.

- [ ] **Step 1: Create the directory placeholders**

Create empty files so git tracks the dirs: `research/.gitkeep`, `foundations/.gitkeep`, `milestones/.gitkeep`, `capstone/.gitkeep`.

- [ ] **Step 2: Create `PROGRESS.md`**

```markdown
# Progress Log

Running log of the Angular Zero→Senior journey. One entry per working session.

Format per entry:

## YYYY-MM-DD — <milestone / topic>
- **Did:** what was built or studied
- **Clicked:** concepts that landed
- **Debugged:** problems hit and how they were solved
- **Resume note:** one-line skill this demonstrates

---

## 2026-06-19 — Project setup
- **Did:** Initialized repo, brainstormed mentorship design, wrote Phase 1 plan.
- **Clicked:** Project structure and learning loop (module → mini-project → drill).
- **Debugged:** —
- **Resume note:** Set up a structured, source-backed self-directed learning system.
```

- [ ] **Step 3: Update `CLAUDE.md`**

Replace the existing `## How this works` and `## Notes for Claude` sections (keep the title + Purpose) with the repo map and mentor stance:

```markdown
## Repo map

- `ROADMAP.md` — master roadmap, one checkbox per milestone. The map of where we are.
- `PROGRESS.md` — running session log; source of resume talking points.
- `research/` — Phase 1 source roadmaps + synthesis notes.
- `foundations/` — HTML/CSS/TS/JS gap-fill exercises.
- `milestones/NN-topic/` — per-milestone module notes, mini-project, and debug drills.
- `capstone/` — the evolving real app (domain chosen early in Phase 2).
- `docs/superpowers/` — specs and plans.

## How this works

Learner is backend-strong / frontend-weak. Goal: confidently put Angular + web fundamentals on the resume via hands-on work. Frontend-only scope; capstone uses a mock API.

Each milestone runs three beats:
1. **Module** — teach the concept with small examples.
2. **Mini-project** — learner builds something focused with it.
3. **Challenge/debug drill** — learner fixes/extends broken or half-built code.

Mini-projects feed the capstone where possible.

## Mentor stance (for Claude)

- Favor explanation and understanding over producing finished code.
- Let the learner struggle productively; give hints before answers on drills.
- Build concepts progressively; assume earlier topics may still be new.
- Keep `PROGRESS.md` updated at the end of each session.
- This file is living — refine it as the learner's pace and preferences become clear.
```

- [ ] **Step 4: Verify**

Confirm: all four dirs exist with `.gitkeep`, `PROGRESS.md` exists with the dated first entry, `CLAUDE.md` contains "Repo map" and "Mentor stance" headings.

- [ ] **Step 5: Commit**

```bash
git add CLAUDE.md PROGRESS.md research/.gitkeep foundations/.gitkeep milestones/.gitkeep capstone/.gitkeep
git commit -m "Scaffold repo structure and mentor brief

Co-Authored-By: Claude Opus 4.8 (1M context) <noreply@anthropic.com>"
```

---

### Task 2: Gather source roadmaps into `research/`

**Files:**
- Create: `research/01-roadmap-sh.md`
- Create: `research/02-angular-official.md`
- Create: `research/03-community-sources.md`

**Interfaces:**
- Consumes: nothing from earlier tasks.
- Produces: three raw source-summary files that Task 3 reads to build the side-by-side comparison.

- [ ] **Step 1: Research roadmap.sh**

Use WebFetch/WebSearch on roadmap.sh Frontend roadmap and roadmap.sh Angular roadmap. Capture into `research/01-roadmap-sh.md`: the ordered topic list of each, with the source URL at top and the fetch date (2026-06-19). Note which items are frontend-fundamentals vs Angular-specific.

- [ ] **Step 2: Research official Angular learning path**

Use WebFetch on the official Angular docs learning path / tutorials (angular.dev). Capture into `research/02-angular-official.md`: the official recommended learning order, key concept areas (components, templates, signals, DI, routing, forms, HTTP, RxJS, testing), with source URLs and fetch date.

- [ ] **Step 3: Research 2–3 respected community sources**

Use WebSearch for current respected Angular learning resources (well-regarded courses, syllabi, or senior-Angular skill checklists from 2025–2026). Capture into `research/03-community-sources.md`: for each source — name, URL, fetch date, and the topic list / what it emphasizes. Aim for 2–3 sources.

- [ ] **Step 4: Verify**

Confirm each of the three files exists, each lists source URL(s) and the fetch date, and each contains an ordered topic list (not just prose). If any web fetch failed, note the failure in the file and which alternative source was used instead — do not leave a file empty.

- [ ] **Step 5: Commit**

```bash
git add research/
git commit -m "Gather source roadmaps (roadmap.sh, Angular docs, community)

Co-Authored-By: Claude Opus 4.8 (1M context) <noreply@anthropic.com>"
```

---

### Task 3: Build the side-by-side comparison for curation

**Files:**
- Create: `research/04-comparison.md`

**Interfaces:**
- Consumes: `research/01-roadmap-sh.md`, `research/02-angular-official.md`, `research/03-community-sources.md`.
- Produces: a single comparison table + a proposed milestone list, presented to the user. The user's curation decisions feed Task 4.

- [ ] **Step 1: Synthesize the comparison**

In `research/04-comparison.md`, build:
1. A **topic matrix** — rows = topics aggregated across all sources; columns = each source; mark which sources include each topic and at what stage. Group rows into bands: Frontend Foundations / Angular Core / Angular Advanced / Senior & Ecosystem.
2. A **proposed milestone list** — an ordered, deduped sequence derived from the matrix, calibrated to the learner profile (compressed foundations, deep Angular). Number them and give each a one-line outcome.
3. A **curation prompt** section listing explicit decisions for the user: which proposed milestones to keep / drop / reorder, and where to set the foundations depth.

- [ ] **Step 2: Verify**

Confirm `research/04-comparison.md` has all three parts, the matrix references every source file from Task 2, and the proposed milestone list is ordered and numbered.

- [ ] **Step 3: Commit**

```bash
git add research/04-comparison.md
git commit -m "Add side-by-side roadmap comparison and proposed milestones

Co-Authored-By: Claude Opus 4.8 (1M context) <noreply@anthropic.com>"
```

- [ ] **Step 4: User curation gate (STOP)**

Present the proposed milestone list to the user. Ask them to keep / drop / reorder milestones and set foundations depth. **Wait for the user's response.** Record their decisions verbatim at the bottom of `research/04-comparison.md` under a `## Curation decisions (user)` heading, then commit:

```bash
git add research/04-comparison.md
git commit -m "Record user curation decisions

Co-Authored-By: Claude Opus 4.8 (1M context) <noreply@anthropic.com>"
```

---

### Task 4: Synthesize the master `ROADMAP.md`

**Files:**
- Create: `ROADMAP.md`

**Interfaces:**
- Consumes: `research/04-comparison.md` including the `## Curation decisions (user)` section.
- Produces: `ROADMAP.md` — the checkbox milestone map referenced by `CLAUDE.md` and all of Phase 2.

- [ ] **Step 1: Write `ROADMAP.md`**

Build from the curated milestone list. Structure:

```markdown
# Angular Zero→Senior Roadmap

Curated from `research/` on 2026-06-19. Each milestone runs: module → mini-project → debug drill. Mini-projects feed the capstone where possible.

## How to read this
- `[ ]` not started · `[~]` in progress · `[x]` done
- Detailed per-milestone plans are written just-in-time when we reach each one.

## Bands

### A. Frontend Foundations
- [ ] A1. <topic> — <one-line outcome>
- [ ] A2. ...

### B. Angular Core
- [ ] B1. ...

### C. Angular Advanced
- [ ] C1. ...

### D. Senior & Ecosystem
- [ ] D1. ...

## Capstone
Domain chosen at the start of Band B (or earlier if it helps). Tracked in `capstone/`.
```

Fill bands A–D with the actual curated milestones (replace placeholders with real topics from the curation). Every milestone gets an ID and a one-line outcome.

- [ ] **Step 2: Cross-link from `CLAUDE.md`**

Confirm `CLAUDE.md`'s repo map already points to `ROADMAP.md` (added in Task 1). No edit needed unless the line is missing — if missing, add it.

- [ ] **Step 3: Verify**

Confirm `ROADMAP.md` exists, has all four bands populated with real (non-placeholder) milestones, every milestone has an ID + checkbox + one-line outcome, and the milestone set matches the user's curation decisions from Task 3.

- [ ] **Step 4: Commit**

```bash
git add ROADMAP.md CLAUDE.md
git commit -m "Synthesize curated master roadmap

Co-Authored-By: Claude Opus 4.8 (1M context) <noreply@anthropic.com>"
```

---

### Task 5: Log progress and push

**Files:**
- Modify: `PROGRESS.md`

**Interfaces:**
- Consumes: completed `ROADMAP.md`.
- Produces: dated log entry; remote updated.

- [ ] **Step 1: Append a `PROGRESS.md` entry**

Add a dated entry recording that Phase 1 is complete and the roadmap is set:

```markdown
## 2026-06-19 — Phase 1 complete: roadmap built
- **Did:** Researched roadmap.sh / Angular docs / community sources, curated and synthesized the master roadmap.
- **Clicked:** The shape of the Angular learning path from foundations to senior.
- **Debugged:** —
- **Resume note:** Defined a source-backed Angular learning roadmap end to end.
```

- [ ] **Step 2: Commit and push**

```bash
git add PROGRESS.md
git commit -m "Log Phase 1 completion

Co-Authored-By: Claude Opus 4.8 (1M context) <noreply@anthropic.com>"
git push
```

- [ ] **Step 3: Verify**

Confirm `git status` is clean and `git log origin/main..HEAD` shows nothing (all commits pushed).

---

## Self-Review

**Spec coverage:**
- Phase 1 research from multiple sources → Task 2. ✓
- Side-by-side presentation + user curation → Task 3. ✓
- Synthesize master `ROADMAP.md` → Task 4. ✓
- Repo structure (`research/`, `foundations/`, `milestones/`, `capstone/`, `PROGRESS.md`) → Task 1. ✓
- `CLAUDE.md` mentor stance + living brief → Task 1. ✓
- Frontend-only / mock API, learner profile calibration → Global Constraints, applied in Tasks 2–4. ✓
- Capstone domain deferred to Phase 2 → Global Constraints + Task 4 note. ✓
- Phase 2 milestone plans written just-in-time → out of scope for this plan (stated in ROADMAP.md "How to read this"). ✓

**Placeholder scan:** The `<topic>` / band placeholders in Task 4 Step 1 are an intentional template filled from real curated data at execution; verification step enforces no placeholders survive. No stray TODO/TBD.

**Type consistency:** File names consistent across tasks (`research/01..04`, `ROADMAP.md`, `PROGRESS.md`, `CLAUDE.md`). Curation heading `## Curation decisions (user)` referenced identically in Tasks 3 and 4.
