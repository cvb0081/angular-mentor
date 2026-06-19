# Source 03 — Community sources (senior-skill emphasis)

**Fetched:** 2026-06-19

## Sources

1. **FrontendMinds — "Angular Developer Skills in 2026"**
   https://frontendminds.com/blog/angular-developer-skills-2026
2. **Medium — "Angular Interview Deep Dive: 15 Topics Senior Developers Should Master"**
   https://medium.com/@theDevBluePrint/angular-interview-deep-dive-15-topics-senior-developers-should-master-c4e09b86d1d7
3. **GreatFrontend — "Angular Interview Questions for Experienced"**
   https://www.greatfrontend.com/blog/angular-experienced-interview-questions

## What 2026 sources say a senior Angular dev must have

**Baseline (expected, not differentiators):**
- TypeScript **strict mode**
- **OnPush** change detection
- Standalone component architecture
- New control flow syntax: `@if`, `@for`, `@switch`, `@defer`
- Typed reactive forms

**Five assessment categories (FrontendMinds):**
1. Modern reactivity with **signals**
2. Component architecture with **standalone components**
3. Template syntax with **new control flow**
4. Form handling with **typed reactive forms**
5. Rendering strategy including **SSR** (`@angular/ssr`)

**Signals vs RxJS — the senior judgment call:**
- Signals → local UI state, derived/computed values.
- RxJS → async streams, effects, server interactions.
- Bridge with `toObservable` / `toSignal`.
- Knowing *when* to use which matters more than knowing the API.

**State management shift:**
- With signal APIs, many "global state" needs are now met by simple `providedIn: 'root'` services — full Redux/NgRx weight is no longer the default.

**What distinguishes seniors (vs juniors):**
- Hands-on mastery of DI, RxJS reasoning, component architecture.
- The *reasoning* behind `combineLatest` / a signal — not just syntax.
- Performance (change detection, lazy loading, hydration), testing discipline, security awareness.

## Takeaway for our roadmap

Modern-first path: standalone + signals + new control flow as the spine. RxJS taught for async/server. NgRx introduced late and framed as "when a service isn't enough." Performance, testing, SSR, and security are the senior-tier band.
