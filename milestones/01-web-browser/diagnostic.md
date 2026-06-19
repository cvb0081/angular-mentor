# A1 Diagnostic — How the web & browser work

**Run:** 2026-06-19

## Questions & answers

| # | Subtopic | Your answer | Correct | Result |
|---|----------|-------------|---------|--------|
| 1 | S1 HTTP lifecycle | DNS → TCP/TLS → request → response → render | A | pass |
| 2 | S1 HTTP lifecycle | Use your cached copy; unchanged | A | pass |
| 3 | S2 DNS | The IP address for a hostname | A | pass |
| 4 | S3 Browser's job | Executing the server's database queries | A | pass |
| 5 | S4 DOM | "don't know" | A | fail |
| 6 | S5 Rendering pipeline | "no idea" | A | fail |
| 7 | S5 Rendering pipeline | "no idea" | A | fail |
| 8 | S6 Reflow/repaint | "no idea" | A | fail |
| 9 | S6 Reflow/repaint | "no idea" | A | fail |
| 10 | S7 Event loop | "no idea" | A | fail |

**Score:** 4 / 10.

## Per-subtopic verdict

| Subtopic | Verdict |
|----------|---------|
| S1 Client–server & HTTP lifecycle | mastered |
| S2 DNS | mastered |
| S3 Browser's job | mastered |
| S4 DOM | gap |
| S5 Rendering pipeline | gap |
| S6 Reflow/repaint | gap |
| S7 Event loop | gap |

**Pattern:** Network/server side is solid (expected for a backend engineer). Everything that happens *inside* the browser — DOM, rendering, reflow, event loop — is the gap. This is the high-value half of A1 and directly underpins how Angular renders and updates the UI.

## Generated A1 study plan

Mapping: mastered → one-line recap · partial → targeted section · gap → full teaching + drill target.

- **Recap only (mastered):**
  - S1 HTTP lifecycle, S2 DNS, S3 browser-vs-server boundary — one-paragraph recap, then move on.

- **Module covers (full teaching, in this order):**
  1. **S4 — The DOM:** what the DOM actually is (live object tree, not the HTML text), nodes vs elements, how JS reads/mutates it, why DOM updates are expensive. *Foundation for everything Angular does to the view.*
  2. **S5 — Rendering pipeline:** parse → DOM + CSSOM → render tree (visible nodes only) → layout → paint → composite. Walk one concrete example end to end.
  3. **S6 — Reflow vs repaint:** which changes trigger layout vs paint-only; layout thrashing from interleaved read/write (the `offsetHeight` trap). *Sets up Angular change-detection performance later.*
  4. **S7 — Event loop:** call stack, macrotasks vs microtasks (promise callbacks), where rendering and `requestAnimationFrame` fit. *Sets up async + zone.js intuition later.*

- **Mini-project (aimed at S4–S6):** a tiny vanilla-JS page that renders a list from a JS array into the DOM, lets you add/remove items by mutating the DOM, and uses browser DevTools' Performance/Rendering panel to *see* layout vs paint happen. Goal: feel the DOM and the pipeline directly, no framework.

- **Debug drill (aimed at top gap S5/S6):** a provided snippet that causes layout thrashing by reading `offsetHeight` inside a loop while writing styles. You profile it in DevTools, identify the forced reflows, and fix it by batching reads then writes.

**Next:** execute beats 3–5 (module → mini-project → drill) per this plan in the next cycle.
