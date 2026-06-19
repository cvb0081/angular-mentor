# Source 02 — Official Angular docs (angular.dev)

**Fetched:** 2026-06-19
**Sources:**
- https://angular.dev/overview
- https://angular.dev/roadmap (official project roadmap, for direction/recency)

## Recommended learning order (from the official "In-depth Guides")

**Introduction phase**
1. What is Angular? — framework overview
2. Installation / setup
3. Essentials — core concepts intro
4. Start coding! — hands-on first tutorial

**Core concepts (in the order docs present them)**
1. **Signals** — fine-grained reactivity model + compile-time optimizations (docs lead with this now)
2. **Components** — encapsulated, reusable units
3. **Templates** — view layer & data binding
4. **Directives** — extending HTML
5. **Dependency Injection** — sharing code/services across the app
6. **Routing** — navigation, guards, lazy-loading, data resolution
7. **Forms** — form participation & validation
8. **HTTP Client** — server communication

**Advanced topics**
- Server-side & hybrid rendering (SSR / `@angular/ssr`)
- Testing
- Angular Aria (accessibility)
- Internationalization
- Animations
- Drag and drop

**Developer support tooling**
- Angular CLI
- DevTools
- Language Service

## Notable: the official docs now lead with Signals and standalone components

Modern Angular (current docs) emphasizes:
- **Standalone components** as the default (NgModules de-emphasized).
- **Signals** for reactivity, alongside RxJS for async streams.
- **New control flow** syntax (`@if`, `@for`, `@switch`, `@defer`) over the old structural directives.

This matters for calibration: teach the modern path (standalone + signals + new control flow) as the primary, treat NgModules / legacy `*ngIf` as "you'll see this in older code" context.
