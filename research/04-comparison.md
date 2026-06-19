# Side-by-side comparison & proposed milestones

**Built:** 2026-06-19 from `01-roadmap-sh.md`, `02-angular-official.md`, `03-community-sources.md`.

## Part 1 — Topic matrix

Legend: ✓ = covered · ◑ = touched/implied · — = not covered · stage in parens.

| Topic | roadmap.sh (01) | Angular docs (02) | Community/senior (03) |
|---|---|---|---|
| **— Frontend Foundations —** | | | |
| How the web works (HTTP/DNS/browser) | ✓ (early) | — | — |
| HTML semantics & forms | ✓ (early) | — | ◑ |
| CSS (box model, flexbox, grid, responsive) | ✓ (early) | — | — |
| JavaScript + DOM + fetch | ✓ (early) | — | ◑ |
| TypeScript (types, generics, **strict mode**) | ✓ (pre-Angular) | ◑ (assumed) | ✓ (baseline) |
| Accessibility (a11y) | ✓ | ✓ (Aria) | ◑ |
| Web performance basics | ✓ | ✓ | ✓ |
| Tooling: npm, CLI, dev tools | ✓ | ✓ | ◑ |
| **— Angular Core —** | | | |
| Setup / CLI / project anatomy | ✓ (early) | ✓ (intro) | ◑ |
| Components & templates | ✓ | ✓ (core) | ✓ |
| Data binding (interpolation/event/attr) | ✓ | ✓ | ✓ |
| **New control flow** (@if/@for/@switch/@defer) | ✓ | ✓ | ✓ (baseline) |
| **Standalone components** (default) | ◑ | ✓ (default) | ✓ (baseline) |
| Directives & pipes | ✓ | ✓ | ◑ |
| Component communication (in/out, view/content child) | ✓ | ✓ | ✓ |
| **Signals** (reactivity, computed, effects) | ✓ | ✓ (leads) | ✓ (top skill) |
| Dependency Injection | ✓ | ✓ (core) | ✓ (senior) |
| **— Angular Advanced —** | | | |
| RxJS (observables, operators, combination) | ✓ | ◑ | ✓ (senior) |
| Signals ↔ RxJS bridging (toSignal/toObservable) | ◑ | ✓ | ✓ (senior call) |
| Routing (guards, lazy loading, resolvers) | ✓ | ✓ (core) | ✓ |
| Forms — **typed reactive forms**, validators, CVA | ✓ | ✓ (core) | ✓ (baseline) |
| HTTP client + interceptors | ✓ | ✓ (core) | ✓ |
| State management (NgRx/NGXS/Elf, signal stores) | ✓ | ◑ | ✓ (when needed) |
| Change detection / OnPush | ✓ | ✓ | ✓ (baseline) |
| **— Senior & Ecosystem —** | | | |
| Performance (CD, lazy, image opt, hydration) | ✓ | ✓ | ✓ |
| SSR / hybrid rendering (@angular/ssr) | ◑ | ✓ | ✓ (assess area) |
| Testing (unit, coverage, e2e) | ✓ | ✓ | ✓ |
| Security (XSS, CSRF, trusted types) | ✓ | ◑ | ◑ |
| i18n, animations, libraries | ✓ | ✓ | — |
| Architecture & scalability patterns | ✓ | ◑ | ✓ (senior) |
| Deployment | ✓ | ◑ | — |

**Cross-source signal:** all three converge on a **modern-first spine** — standalone components + signals + new control flow + typed reactive forms as baseline; RxJS and NgRx framed by *when to reach for them*; performance/testing/SSR/security as the senior tier. NgModules and legacy `*ngIf` are "read-only / legacy code" context, not the primary path.

## Part 2 — Proposed milestone list

Calibrated to learner profile (backend-strong, frontend-weak): foundations compressed, Angular deep, modern-first. Each milestone = module → mini-project → debug drill.

### Band A — Frontend Foundations (compressed)
- **A1. How the web & browser work** — request lifecycle, DOM, rendering. *Outcome: explain what happens from URL to pixels.*
- **A2. HTML + semantic structure & forms** — *Outcome: hand-write an accessible semantic form.*
- **A3. CSS essentials** — box model, flexbox, grid, responsive. *Outcome: build a responsive layout without a framework.*
- **A4. Modern JavaScript + DOM** — ES modules, async/fetch, DOM APIs. *Outcome: fetch + render data with vanilla JS.*
- **A5. TypeScript for frontend** — types, interfaces, generics, strict mode. *Outcome: model an API response with strict types.*

### Band B — Angular Core
- **B1. Angular setup & project anatomy** — CLI, standalone bootstrap, file structure. *Outcome: scaffold and run an app, explain each generated file.*
- **B2. Components & templates** — anatomy, data binding, new control flow (@if/@for/@switch). *Outcome: build a multi-component UI from mock data.*
- **B3. Signals** — signal/computed/effect, inputs-as-signals. *Outcome: build reactive UI state with signals only.*
- **B4. Directives & pipes** — built-in + custom. *Outcome: write a custom attribute directive and a custom pipe.*
- **B5. Component communication** — inputs/outputs, view/content children. *Outcome: build a parent↔child interactive widget.*
- **B6. Dependency Injection & services** — providedIn, injection, service-as-state. *Outcome: extract state into an injectable service.*
- **(Capstone domain chosen here)**

### Band C — Angular Advanced
- **C1. Routing** — routes, params, guards, lazy loading, resolvers. *Outcome: multi-route app with a guarded lazy area.*
- **C2. Forms (typed reactive)** — reactive forms, validators, CVA, dynamic forms. *Outcome: complex validated form with a custom control.*
- **C3. HTTP & mock API** — HttpClient, interceptors, json-server/in-memory. *Outcome: full CRUD against a mock API with an interceptor.*
- **C4. RxJS** — observables, operators, combination, signals↔RxJS bridging. *Outcome: build a debounced search/stream feature.*
- **C5. State management** — signal stores vs services vs NgRx; when to escalate. *Outcome: refactor app state with a justified approach.*

### Band D — Senior & Ecosystem
- **D1. Change detection & performance** — OnPush, lazy, image opt, hydration. *Outcome: profile and speed up a slow view.*
- **D2. Testing** — unit (Jest/Karma), component harness, e2e. *Outcome: meaningful test suite for a feature.*
- **D3. SSR / hybrid rendering** — @angular/ssr, hydration. *Outcome: server-render the capstone.*
- **D4. Security** — XSS, CSRF, trusted types, safe HTTP. *Outcome: audit & harden the app.*
- **D5. Architecture & scalability** — feature structure, libraries, patterns. *Outcome: document the capstone's architecture like a senior would.*
- **D6. Deployment** — build envs, deploy the capstone. *Outcome: a live, shareable app.*

### Capstone
Real evolving app, mock API. Domain chosen at **B6** (or earlier if it helps). Mini-projects from B–D feed into it.

## Part 3 — Curation prompt (decisions for you)

Please decide:

1. **Foundations depth (Band A):** keep all 5 / compress to fewer (e.g. merge to "A1 web+JS" + "A2 TS+CSS") / skip any you're already solid on (you may know HTML/CSS already)?
2. **Keep / drop / reorder** any milestone in B / C / D.
3. **NgRx (C5):** full treatment, or keep light (signals/services first, NgRx only as awareness)?
4. **SSR (D3) & i18n/animations:** keep as milestones, or drop to "optional/awareness" given resume goal?
5. **When to pick the capstone domain:** at B6 as proposed, or earlier (e.g. after B1) so everything builds toward it?
6. Anything missing you want added.
