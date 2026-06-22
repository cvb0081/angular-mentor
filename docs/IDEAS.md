# Ideas / Backlog

Parked ideas, not yet scoped into ROADMAP. Captured to not forget.

## I1 — Extract a reusable "learn-anything-with-AI" method into its own open-source repo

**Date captured:** 2026-06-19

**Idea:** Everything we build in angular-mentor — the five-beat milestone loop (diagnostic quiz → tailored study plan → module → mini-project → debug drill), the refresher/recall spaced-repetition mode, the ROADMAP/PROGRESS/FRESHNESS tracking system, the mentor stance — is **not Angular-specific**. It's a general method for going Zero-to-Senior in any language/framework with an AI mentor.

Goal: distill that method (templates, process, the CLAUDE.md mentor contract, the freshness/spaced-repetition mechanics) into a standalone, framework-agnostic toolkit. Later split into its own public repo to help others learn in the age of AI.

**To brainstorm later:**
- Name (working ideas: none yet — needs a session)
- Scope: what's the portable core vs. what stays Angular-specific?
- Format: template repo? CLI/skill? plain markdown scaffolding + a CLAUDE.md template?
- How a learner picks their domain/roadmap source and seeds milestones
- License (MIT likely for max reuse)

**How to spin out as a separate repo when ready:** see ROADMAP/this note — use `git subtree split` or `git filter-repo` on the extracted folder to keep history (details discussed in chat).

**Status:** scaffolded → tracked in [issue #2](https://github.com/cvb0081/angular-mentor/issues/2). Folder `learn-with-ai/` exists with README + skeleton; fill incrementally, spin out via Option A later.
