# learn-with-ai

> A configurable blueprint for learning any language or framework with an AI mentor. Clone it, tell it what you want to learn and what you already know, and it builds your personal Zero-to-Senior journey.

Most people "learn with AI" by asking questions until they feel productive — then forget it a week later. This template fixes that with a repeatable method you make your own. Set your target stack, your current skill level, and your goal; the AI diagnoses your gaps, builds a plan that skips what you've mastered and drills what you don't, then teaches through small projects and debug challenges instead of handing you answers. Completed topics get scheduled refreshers so knowledge stays warm. Everything's framework-agnostic — you configure it once and it adapts to whatever you're learning.

## Why this beats ad-hoc chatting

- **Structured loop** — diagnostic quiz → tailored plan → teach → build → debug drill. Progress lives in `ROADMAP.md` / `PROGRESS.md`, not chat history.
- **Active, not passive** — you build and fix real things. The AI gives hints before answers. No tutorial hell.
- **Mentor contract** — a `CLAUDE.md` that makes the AI behave like a real mentor across any project, any stack.

## Quickstart

1. Use this repo as a template (or clone it).
2. Configure it for you: run the AI-guided setup (see `SETUP.md`), or fill `CONFIG.md` by hand.
3. Start your first milestone.

## What's in here

| File / folder | Role |
|---|---|
| `CONFIG.md` | **Source of truth** — your profile, target stack, goal, capstone domain, preferences. |
| `CLAUDE.md` | Generic mentor contract; reads `CONFIG.md` for your specifics. |
| `SETUP.md` | AI-guided interview that fills `CONFIG.md` and seeds your roadmap. |
| `ROADMAP.md` | Your milestone map — one checkbox per milestone. |
| `PROGRESS.md` | Running session log. |
| `FRESHNESS.md` | Spaced-repetition tracker that drives refresher mode. |
| `milestones/` | Per-milestone notes, mini-projects, debug drills. |
| `foundations/` | Gap-fill exercises for prerequisites. |
| `capstone/` | The evolving real app you build as you learn. |
| `research/` | Source roadmaps + synthesis notes for your chosen stack. |

## Status

Early — extracted from a working Angular learning project and generalized incrementally. Files fill in as the method proves out on real journeys.
