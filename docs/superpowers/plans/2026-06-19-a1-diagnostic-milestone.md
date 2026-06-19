# A1 Diagnostic + 5-Beat Milestone Loop — Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Adopt the 5-beat milestone loop project-wide, then run milestone A1's diagnostic and generate A1's tailored study plan.

**Architecture:** Doc-and-interactive-quiz work, not code. Tasks update the loop docs, scaffold the A1 milestone folder, deliver a 10-question knowledge-check quiz via the multiple-choice question UI (a user-input gate), score it, and write `diagnostic.md` (answers + per-subtopic verdicts + generated plan). "Tests" are artifact verification checks. Frequent commits.

**Tech Stack:** Markdown docs. AskUserQuestion for the quiz. Git.

## Global Constraints

- **5-beat loop:** every milestone runs `diagnostic quiz → tailored study plan → module → mini-project → debug drill`. This supersedes the old 3-beat loop in `CLAUDE.md` and `docs/superpowers/specs/2026-06-19-angular-mentorship-system-design.md`.
- **Quiz type:** knowledge-check multiple-choice (real right/wrong questions), ~1–2 per subtopic, 6–12 total per milestone. Mentor scores inline; no automated scoring tooling, no new dependencies.
- **Verdict scale:** each subtopic scored `mastered` / `partial` / `gap`.
- **Plan mapping:** `mastered` → skip or one-line recap · `partial` → short targeted section · `gap` → full teaching + mini-project/drill aimed here.
- **Results record:** `milestones/NN-topic/diagnostic.md`, format compatible with the future refresher mode (issue #1).
- **A1 milestone folder:** `milestones/01-web-browser/`.
- **Scope boundary:** this plan ends at A1's generated study plan. It does NOT teach the module, build the mini-project, or the drill.
- **Commit footer:** end every commit with `Co-Authored-By: Claude Opus 4.8 (1M context) <noreply@anthropic.com>`.

---

### Task 1: Adopt the 5-beat loop in the docs

**Files:**
- Modify: `CLAUDE.md` (the "How this works" three-beat list)
- Modify: `docs/superpowers/specs/2026-06-19-angular-mentorship-system-design.md` (the "Milestone anatomy" section)

**Interfaces:**
- Produces: the canonical 5-beat loop description that Task 3's diagnostic instantiates.

- [ ] **Step 1: Update `CLAUDE.md`**

Replace the three numbered beats under "## How this works" with five:

```markdown
Each milestone runs five beats:
1. **Diagnostic quiz** — knowledge-check MCQs across the milestone's subtopics; results stored in `milestones/NN-topic/diagnostic.md`.
2. **Tailored study plan** — generated from the quiz: skip mastered subtopics, drill the gaps.
3. **Module** — teach the gap/partial concepts with small examples.
4. **Mini-project** — learner builds something focused with it.
5. **Challenge/debug drill** — learner fixes/extends broken or half-built code, aimed at the gaps.
```

- [ ] **Step 2: Update the design spec**

In `docs/superpowers/specs/2026-06-19-angular-mentorship-system-design.md`, under "## Milestone anatomy — the learning loop", add a note directly under the heading:

```markdown
> **Updated 2026-06-19:** loop expanded to 5 beats — a **diagnostic quiz** and a **tailored study plan** now precede the three beats below. See `2026-06-19-a1-diagnostic-milestone-design.md`.
```

- [ ] **Step 3: Verify**

Confirm `CLAUDE.md` lists 5 numbered beats and contains "Diagnostic quiz", and the design spec contains the "Updated 2026-06-19" note.

- [ ] **Step 4: Commit**

```bash
git add CLAUDE.md docs/superpowers/specs/2026-06-19-angular-mentorship-system-design.md
git commit -m "Adopt 5-beat milestone loop (diagnostic + tailored plan)

Co-Authored-By: Claude Opus 4.8 (1M context) <noreply@anthropic.com>"
```

---

### Task 2: Scaffold the A1 milestone folder

**Files:**
- Create: `milestones/01-web-browser/README.md`

**Interfaces:**
- Produces: the `milestones/01-web-browser/` folder that Task 3 writes `diagnostic.md` into.

- [ ] **Step 1: Create `milestones/01-web-browser/README.md`**

```markdown
# A1 — How the web & browser work

First milestone. Outcome: explain what happens from URL to pixels.

## Subtopics
1. Client–server model & HTTP request lifecycle
2. DNS resolution
3. The browser's job
4. The DOM
5. Rendering pipeline (parse → render tree → layout → paint → composite)
6. Reflow / repaint triggers
7. Event loop basics

## Files
- `diagnostic.md` — diagnostic quiz results + generated study plan (the 5-beat loop's first two beats).

Module, mini-project, and debug drill are added here after the diagnostic generates the plan.
```

- [ ] **Step 2: Verify**

Confirm `milestones/01-web-browser/README.md` exists and lists the 7 subtopics.

- [ ] **Step 3: Commit**

```bash
git add milestones/01-web-browser/README.md
git commit -m "Scaffold A1 milestone folder

Co-Authored-By: Claude Opus 4.8 (1M context) <noreply@anthropic.com>"
```

---

### Task 3: Run the A1 diagnostic and write `diagnostic.md`

**Files:**
- Create: `milestones/01-web-browser/diagnostic.md`

**Interfaces:**
- Consumes: the subtopic list from Task 2.
- Produces: `diagnostic.md` with answers, per-subtopic verdicts, and the generated A1 study plan that the next cycle (module/mini-project/drill) consumes.

**The quiz (answer key — do NOT reveal correct answers while asking):**

> Subtopic → Question → options (correct marked `*`).

1. **(S1 HTTP lifecycle)** What's the correct order after pressing Enter on a URL?
   - A* DNS lookup → TCP/TLS handshake → HTTP request → response → parse & render
   - B HTTP request → DNS lookup → render → TCP handshake
   - C TLS handshake → render → DNS lookup → HTTP request
2. **(S1 HTTP lifecycle)** An HTTP response status of `304 Not Modified` means:
   - A* Use your cached copy; the resource hasn't changed
   - B The resource was permanently deleted
   - C The server redirected you elsewhere
3. **(S2 DNS)** DNS resolution primarily returns:
   - A* The IP address for a hostname
   - B The HTML of the page
   - C The TLS certificate
4. **(S3 Browser job)** Which is NOT the browser engine's job?
   - A* Executing the server's database queries
   - B Parsing HTML and CSS
   - C Running JavaScript and painting pixels
5. **(S4 DOM)** The DOM is best described as:
   - A* An in-memory tree of objects representing the parsed HTML, manipulable by JS
   - B The raw HTML text file on disk
   - C The CSS stylesheet
6. **(S5 Rendering pipeline)** Correct rendering pipeline order?
   - A* Parse HTML→DOM & CSS→CSSOM → render tree → layout → paint → composite
   - B Paint → layout → render tree → composite
   - C Layout → paint → DOM → CSSOM
7. **(S5 Rendering pipeline)** The render tree contains:
   - A* Only visible nodes with their computed styles
   - B Every DOM node, including `display:none` ones
   - C Only text nodes
8. **(S6 Reflow/repaint)** Which change forces a **layout/reflow** (not just a repaint)?
   - A* Changing an element's width or height
   - B Changing only its text color
   - C Changing only its `box-shadow` color
9. **(S6 Reflow/repaint)** Reading `el.offsetHeight` right after writing a style can cause:
   - A* A forced synchronous layout ("layout thrashing")
   - B A new network request
   - C Nothing at all, reads are always free
10. **(S7 Event loop)** After the current synchronous task finishes, the event loop runs:
    - A* All queued microtasks (e.g. promise callbacks) before the next macrotask
    - B The next macrotask immediately, microtasks last
    - C Rendering always first, before any JS

**Subtopic → question map:** S1→Q1,Q2 · S2→Q3 · S3→Q4 · S4→Q5 · S5→Q6,Q7 · S6→Q8,Q9 · S7→Q10.

- [ ] **Step 1: Ask Q1–Q4 (first AskUserQuestion batch)**

Deliver Q1–Q4 verbatim (options A/B/C as labels, do not mark the correct one). Record the learner's selected letters.

- [ ] **Step 2: Ask Q5–Q8 (second batch)**

Deliver Q5–Q8 the same way. Record answers.

- [ ] **Step 3: Ask Q9–Q10 (third batch)**

Deliver Q9–Q10. Record answers.

- [ ] **Step 4: Score and compute verdicts**

For each question mark pass/fail against the answer key. Then per subtopic:
- both/all questions correct → `mastered`
- some correct → `partial`
- none correct → `gap`
(Single-question subtopics: correct → `mastered`, wrong → `gap`.)

- [ ] **Step 5: Write `milestones/01-web-browser/diagnostic.md`**

Use this exact structure, filling the answer-dependent parts from Steps 1–4 (no blanks left):

```markdown
# A1 Diagnostic — How the web & browser work

**Run:** 2026-06-19

## Questions & answers

| # | Subtopic | Your answer | Correct | Result |
|---|----------|-------------|---------|--------|
| 1 | S1 HTTP lifecycle | <letter> | A | pass/fail |
| ... | ... | ... | ... | ... |
| 10 | S7 Event loop | <letter> | A | pass/fail |

(Fill all 10 rows with the real recorded answers.)

## Per-subtopic verdict

| Subtopic | Verdict |
|----------|---------|
| S1 Client–server & HTTP lifecycle | mastered/partial/gap |
| S2 DNS | mastered/partial/gap |
| S3 Browser's job | mastered/partial/gap |
| S4 DOM | mastered/partial/gap |
| S5 Rendering pipeline | mastered/partial/gap |
| S6 Reflow/repaint | mastered/partial/gap |
| S7 Event loop | mastered/partial/gap |

## Generated A1 study plan

Mapping: mastered → one-line recap · partial → targeted section · gap → full teaching + drill target.

- **Module covers:** <list the partial+gap subtopics, each with depth>
- **Recap only:** <list mastered subtopics>
- **Mini-project:** <a small browser/DOM/rendering exercise aimed at the gap subtopics>
- **Debug drill:** <a broken-code fix aimed at the top gap subtopic>
```

The "Generated A1 study plan" prose must name the actual gap/partial/mastered subtopics from the verdict table — not placeholders.

- [ ] **Step 6: Verify**

Confirm `diagnostic.md` exists, the answers table has all 10 rows filled with real letters and pass/fail, the verdict table covers all 7 subtopics, and the study plan names specific subtopics (no `<...>` placeholders remain).

- [ ] **Step 7: Commit**

```bash
git add milestones/01-web-browser/diagnostic.md
git commit -m "Run A1 diagnostic and generate tailored study plan

Co-Authored-By: Claude Opus 4.8 (1M context) <noreply@anthropic.com>"
```

---

### Task 4: Mark A1 in progress, log, and push

**Files:**
- Modify: `ROADMAP.md` (A1 checkbox)
- Modify: `PROGRESS.md`

**Interfaces:**
- Consumes: completed `diagnostic.md`.
- Produces: updated roadmap state + log; remote updated.

- [ ] **Step 1: Mark A1 in progress in `ROADMAP.md`**

Change the A1 line from `- [ ] **A1.` to `- [~] **A1.` (diagnostic done, module/project/drill remain).

- [ ] **Step 2: Append a `PROGRESS.md` entry**

```markdown
## 2026-06-19 — A1 diagnostic
- **Did:** Adopted the 5-beat milestone loop; ran A1 diagnostic (10 MCQs) and generated the tailored A1 study plan.
- **Clicked:** <fill: subtopics that scored mastered>
- **Debugged:** —
- **Resume note:** Baseline-tested web/browser fundamentals and produced a gap-targeted study plan.
```

Fill the "Clicked" line with the mastered subtopics from the diagnostic.

- [ ] **Step 3: Commit and push**

```bash
git add ROADMAP.md PROGRESS.md
git commit -m "Mark A1 in progress; log diagnostic completion

Co-Authored-By: Claude Opus 4.8 (1M context) <noreply@anthropic.com>"
git push
```

- [ ] **Step 4: Verify**

Confirm `git status` is clean and `git log origin/main..HEAD --oneline` is empty (all pushed).

---

## Self-Review

**Spec coverage:**
- 5-beat loop adopted project-wide → Task 1. ✓
- Diagnostic = knowledge-check MCQ, ~1–2/subtopic, 6–12 total → Task 3 (10 Qs across 7 subtopics). ✓
- Verdict scale mastered/partial/gap → Task 3 Step 4. ✓
- `milestones/NN-topic/diagnostic.md` format (header, Q&A, verdicts, plan) → Task 3 Step 5. ✓
- Plan mapping (mastered/partial/gap → depth) → Global Constraints + Task 3 Step 5. ✓
- A1 folder `milestones/01-web-browser/`, 7 subtopics → Task 2. ✓
- A1 flow: create folder → run quiz → write diagnostic → (module/project/drill deferred) → Tasks 2–4 + scope boundary. ✓
- Refresher-mode compatibility (issue #1) → diagnostic.md is the freshness baseline, noted in Task 2 README + spec. ✓

**Placeholder scan:** The `<...>` tokens in Task 3 Step 5 and Task 4 Step 2 are answer-dependent fields filled at execution from real quiz data; verification steps (Task 3 Step 6, presence of mastered subtopics) enforce no placeholder survives. No stray TODO/TBD elsewhere.

**Type consistency:** Subtopic labels S1–S7 used identically in the quiz map, verdict table, and study plan. Folder `milestones/01-web-browser/` and file `diagnostic.md` named consistently across Tasks 2–4. Verdict values `mastered/partial/gap` consistent throughout.
