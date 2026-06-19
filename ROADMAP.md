# Angular Zero→Senior Roadmap

Curated from `research/` on 2026-06-19. Each milestone runs: **module → mini-project → debug drill**. Mini-projects feed the capstone where possible.

Modern-first spine: standalone components + signals + new control flow + typed reactive forms as the baseline. RxJS for async/streams; NgRx as full treatment when a service isn't enough. Legacy NgModules / `*ngIf` treated as read-only "you'll see this in old code" context.

## How to read this
- `[ ]` not started · `[~]` in progress · `[x]` done
- Detailed per-milestone plans are written just-in-time when we reach each one (not all upfront).
- Scope is frontend-only; all data comes from a mock API (json-server / in-memory / static JSON).

## Bands

### A. Frontend Foundations
- [~] **A1. How the web & browser work** — request lifecycle, DOM, rendering. *Outcome: explain what happens from URL to pixels.*
- [ ] **A2. HTML + semantic structure & forms** — semantic markup, forms, a11y basics. *Outcome: hand-write an accessible semantic form.*
- [ ] **A3. CSS essentials** — box model, flexbox, grid, responsive design. *Outcome: build a responsive layout without a framework.*
- [ ] **A4. Modern JavaScript + DOM** — ES modules, async/await, fetch, DOM APIs. *Outcome: fetch and render data with vanilla JS.*
- [ ] **A5. TypeScript for frontend** — types, interfaces, generics, strict mode. *Outcome: model an API response with strict types.*

### B. Angular Core
- [ ] **B1. Angular setup & project anatomy** — CLI, standalone bootstrap, file structure. *Outcome: scaffold and run an app, explain each generated file.*
- [ ] **B2. Components & templates** — anatomy, data binding, new control flow (`@if`/`@for`/`@switch`). *Outcome: build a multi-component UI from mock data.*
- [ ] **B3. Signals** — `signal`/`computed`/`effect`, inputs-as-signals. *Outcome: build reactive UI state with signals only.*
- [ ] **B4. Directives & pipes** — built-in + custom. *Outcome: write a custom attribute directive and a custom pipe.*
- [ ] **B5. Component communication** — inputs/outputs, view/content children. *Outcome: build a parent↔child interactive widget.*
- [ ] **B6. Dependency Injection & services** — `providedIn`, injection, service-as-state. **Capstone domain chosen here.** *Outcome: extract state into an injectable service.*

### C. Angular Advanced
- [ ] **C1. Routing** — routes, params, guards, lazy loading, resolvers. *Outcome: multi-route app with a guarded lazy area.*
- [ ] **C2. Forms (typed reactive)** — reactive forms, validators, CVA, dynamic forms. *Outcome: complex validated form with a custom control.*
- [ ] **C3. HTTP & mock API** — `HttpClient`, interceptors, json-server/in-memory. *Outcome: full CRUD against a mock API with an interceptor.*
- [ ] **C4. RxJS** — observables, operators, combination, signals↔RxJS bridging (`toSignal`/`toObservable`). *Outcome: build a debounced search/stream feature.*
- [ ] **C5. State management (NgRx — full treatment)** — signal stores vs services vs NgRx; build a real NgRx feature and know when to escalate. *Outcome: app state managed with NgRx, with a written justification.*

### D. Senior & Ecosystem
- [ ] **D1. Change detection & performance** — OnPush, lazy loading, image optimization, hydration. *Outcome: profile and speed up a slow view.*
- [ ] **D2. Testing** — unit (Jest/Karma), component harness, e2e. *Outcome: meaningful test suite for a feature.*
- [ ] **D3. SSR / hybrid rendering** — `@angular/ssr`, hydration. *Outcome: server-render the capstone.*
- [ ] **D4. Security** — XSS, CSRF, trusted types, safe HTTP. *Outcome: audit and harden the app.*
- [ ] **D5. Internationalization (i18n)** — `@angular/localize`, locales, translation workflow. *Outcome: ship the capstone in two locales.*
- [ ] **D6. Animations** — Angular animations, transitions, triggers. *Outcome: add meaningful motion to a capstone flow.*
- [ ] **D7. Architecture & scalability** — feature structure, libraries, patterns. *Outcome: document the capstone's architecture like a senior would.*
- [ ] **D8. Deployment** — build environments, deploy the capstone. *Outcome: a live, shareable app.*

## Capstone
Real evolving app on a mock API. Domain chosen at **B6** (or earlier if it clearly helps). Mini-projects from Bands B–D feed into it. Tracked in `capstone/`.
