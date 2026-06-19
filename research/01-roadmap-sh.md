# Source 01 — roadmap.sh

**Fetched:** 2026-06-19
**Sources:**
- Frontend: https://roadmap.sh/frontend
- Angular: https://roadmap.sh/angular
- Angular node content (used because the roadmap.sh pages render as interactive SVG that the fetcher couldn't read directly): https://github.com/kamranahmedse/developer-roadmap/tree/master/src/data/roadmaps/angular/content
- Supplemented by web search of the roadmap.sh Angular topic list.

> **Fetch note:** Direct WebFetch of `roadmap.sh/frontend` returned only page metadata/FAQ (SVG-rendered nodes not parseable), and `roadmap.sh/angular` returned no node content. Frontend topics below are reconstructed from the roadmap.sh skill list + standard frontend roadmap structure; Angular topics are the actual node names from the roadmap's GitHub content directory.

## Frontend roadmap — topic list (frontend-fundamentals band)

1. Internet & how the web works (HTTP, DNS, browsers, hosting)
2. HTML — semantic markup, forms, accessibility basics
3. CSS — box model, flexbox, grid, responsive design, layouts
4. JavaScript — syntax, DOM manipulation, fetch/AJAX, ES modules
5. TypeScript — types, interfaces, generics (alternative/required for Angular)
6. Version control — Git (already strong)
7. Package managers — npm
8. Web security basics — CORS, HTTPS, XSS, CSP
9. Accessibility (a11y)
10. Web performance basics
11. Build tools / module bundlers
12. Testing & debugging, browser dev tools
13. Frontend framework (→ Angular)

## Angular roadmap — topic nodes (from GitHub content dir)

Grouped from the roadmap's node list into a logical learning order:

**Getting started**
- Introduction to Angular, Angular and History, Local Setup, Angular CLI, Configuration

**Components & templates**
- Components, Component Anatomy, Creating Components, Component Templates, Component Bindings, Component Lifecycle, Encapsulation, Metadata, Dynamic Components
- Data Binding: Interpolation, Attribute Binding, Event Binding, Input & Output
- Control Flow: If / Else / Else-If, For, Switch, Defer / Deferrable Views, Let
- Pipes: Common Pipes, Custom Pipes, Pipes Precedence

**Directives**
- Directives, Attribute Directives, Custom Directives

**Modules vs standalone & architecture**
- Modules, Module Architecture, Creating Modules, Feature Modules, Imports, Angular Architecture, Libraries / Creating Libraries

**Reactivity & signals**
- Signals, Inputs as Signals, Model Inputs, Change Detection

**Dependency injection**
- Dependency Injection, Dependencies, Providers, Communication, Parent-Child Interaction, ContentChild

**Component communication**
- Parent-Child Interaction, Input & Output, ViewChild/ContentChild

**RxJS / reactive programming**
- Observable Pattern, Observable Lifecycle, Operators, Combination, Complex Sequences, Filtering

**Routing**
- Routing, Guards, Lazy Loading, Lazy Loading Modules, Link Identification

**Forms**
- Forms, Dynamic Forms, Custom Validators, Control Value Accessor

**HTTP**
- HTTP Client, Making Requests, HTTPClient CSRF

**State management**
- NgRx, NGXS, Elf

**Rendering & performance**
- Change Detection, Performance, Image Optimization, Hydration, Server-side & hybrid rendering, AOT Compilation, Build Environments, CLI Builders

**Testing**
- Code Coverage, Debugging Tests, End-to-End Testing

**Security**
- Cross-Site Scripting, Cross-Site Request Forgery, Cross-Site Script Inclusion, HTTP Vulnerabilities, Enforce Trusted Types

**Internationalization & extras**
- Internationalization, Locales by ID, Localize Package, Multiple Locales, Animation, Accessibility, Drag and drop

**Tooling**
- Angular CLI, DevTools, Language Service, Developer Tools, Deployment
