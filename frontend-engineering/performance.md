# Performance

## 1. What is it?

The performance layer of frontend engineering: the budgets a build must meet, the mechanics that meet them (images, fonts, JavaScript, CSS, rendering), and the measurement procedure that verifies reality instead of intentions. Performance is treated here as a *design constraint* — a style or motion choice with a runtime cost is a design decision ([../visual-styles/interface-styles.md](../visual-styles/interface-styles.md), [../motion-and-interaction/motion-principles.md](../motion-and-interaction/motion-principles.md)) — and as an *engineering discipline* with numbers attached.

## 2. Why does it matter?

Performance is user experience at its most literal: every 100 ms of delay and every janky frame is felt. It is also equity — expensive devices and slow networks are not edge cases but a large share of the world's traffic — and it compounds with design ambition: the styles and motion this library encourages (blur, 3D, scroll scenes, fluid type) are exactly the ones that cost. An agent that budgets performance as seriously as hierarchy produces work that is both distinctive *and* fast; an agent that treats performance as a later QA checkbox produces beautiful pages that lose users before first paint. Google's Core Web Vitals research program gives the field its shared metrics; the budgets below are how a build operationalises them.

## 3. Core principles

**Principle 1 — Budget first, then build.** The budget (per template, not per project average) is set before scaffolding and recorded alongside the technology decision ([technology-selection.md](technology-selection.md)): page weight, JS transfer, image weight per slot, font payload, interaction latency. Late budgets are wishes, not constraints.

**Principle 2 — Ship the most static thing that works.** Rendering and asset strategy default to static ([technology-selection.md](technology-selection.md) §4.4); every dynamic layer (client hydration, runtime data fetching, runtime image processing) must justify itself.

**Principle 3 — Measure on real constraints.** Lab tools (Lighthouse) plus mid-range device and throttled network; the desktop-ultrabook-with-fast-wifi environment lies. Field data (CrUX/RUM where available) is the final authority on user-perceived performance.

**Principle 4 — The common defects have known fixes.** Image weight, font blocking, layout shift, unthrottled effects and dependency bloat cause the large majority of real-world failures; each has a standard countermeasure in §5. Performance work starts with the checklist, not with profiling esoterica.

**Principle 5 — Perceived performance is design work.** Skeletons, optimistic UI, bridging feedback and the latency ladder ([../ui-ux/interaction-design.md](../ui-ux/interaction-design.md) §5.6, Doherty threshold in [../ux-psychology/design-laws.md](../ux-psychology/design-laws.md)) make required waits feel shorter; they complement, never replace, actual speed.

## 4. How it works — the budget model

Per-template budgets (conventional starting points, tuned per project; transfer sizes assume compression):

| Budget | Target | Notes |
| --- | --- | --- |
| Total page weight (first view) | < 1 MB (content pages); < 2 MB (media-heavy) | The ~200 KB rule of thumb from a decade of performance practice has drifted upward with richer pages — set explicitly, don't drift |
| JavaScript transfer | < 200 KB (content pages); < 300–400 KB (app surfaces) | Count the framework, not the ambition |
| Largest image per slot | < 200 KB, modern format | See 5.1 |
| Fonts | ≤ 2 families, ≤ 4 files, subset, < 100 KB total | See 5.2 |
| LCP (Largest Contentful Paint) | ≤ 2.5 s on mid-range mobile | Core Web Vitals "good" threshold |
| INP (Interaction to Next Paint) | ≤ 200 ms | Replaced FID as the responsiveness vital (March 2024) |
| CLS (Cumulative Layout Shift) | ≤ 0.1 | Reserved space discipline |
| Scroll/animation frame rate | 60 fps, transform/opacity only | Verified on a mid-range device ([../motion-and-interaction/motion-principles.md](../motion-and-interaction/motion-principles.md)) |

Core Web Vitals thresholds are Google's published field metrics ("good" levels): https://web.dev/articles/vitals [search-verified, accessed 2026-11-25].

## 5. Practical application — the mechanics

**5.1 Images (the usual majority of page weight).** Modern formats (AVIF/WebP; JPEG fallback), correct intrinsic sizes, `srcset`/`sizes` for responsive delivery, explicit `width`/`height` (CLS), lazy-loading below the fold (`loading="lazy"`), high priority for the LCP image (`fetchpriority="high"`), art-directed crops as separate sources rather than CSS-scaled originals. Video: poster images, `preload="none"` unless above the fold, muted-and-looping patterns over autoplay-with-sound. Source libraries and pipeline guidance: [../assets/README.md](../assets/README.md).

**5.2 Fonts.** Self-host via [../assets/typography.md](../assets/typography.md) sources (Fontsource for packaged subsets); subset to the character ranges used; `font-display: swap` (or the `size-adjust`-tuned metrics-matching pattern) to avoid invisible text; `preload` the one or two critical files; variable fonts deliver many weights in one file. Never block first paint on a font. Details: [../typography/web-typography.md](../typography/web-typography.md).

**5.3 JavaScript.** Every dependency is a permanent tax: audit against [../motion-and-interaction/animation-libraries.md](../motion-and-interaction/animation-libraries.md) (one library per layer) and [../github-resources/catalogue.md](../github-resources/catalogue.md) (prefer the small package, not the kitchen sink); code-split per route; defer non-critical scripts; keep hydration minimal (islands/partial hydration where the stack supports it); measure with the bundle visualiser, not vibes. A script added "just for one effect" is the canonical budget leak.

**5.4 CSS.** The architecture ([css-architecture.md](css-architecture.md)) already keeps specificity and volume sane; runtime costs to avoid: animating layout properties (transform/opacity only), expensive filters (blur) at full-page scale, unthrottled scroll handlers ([../motion-and-interaction/scroll-experiences.md](../motion-and-interaction/scroll-experiences.md)), and `will-change` used as blanket insurance rather than targeted optimisation.

**5.5 Rendering stability (CLS).** Reserve space for everything async: images (dimensions), embeds (containers), ad slots (min-height), late-loading banners (avoid inserting above content), skeletons sized like their content ([../ui-ux/ui-fundamentals.md](../ui-ux/ui-fundamentals.md) states).

**5.6 Measurement procedure.** (1) Lighthouse on the built page, mobile profile. (2) Real-device pass: mid-range Android/throttled connection, core journeys. (3) DevTools performance traces for any janky interaction (long tasks, layout thrash). (4) Where available, field data (CrUX dashboard, RUM). (5) Results recorded per template against the budget table; regressions block release like visual QA blockers ([../evaluation/website-visual-qa.md](../evaluation/website-visual-qa.md)).

## 6. Decision framework

Every performance-affecting choice runs the same three-question filter:

1. **What does it cost at runtime?** (bytes, ms, frames, battery)
2. **What does it buy?** (design value, accessibility value, conversion, task success)
3. **Is there a cheaper equivalent?** (static image instead of WebGL scene; CSS instead of a library; subset instead of full font)

Buy when the value clearly exceeds the cost on the *real* device distribution; the check is documented where the cost is large (3D scenes, heavy blur, big motion libraries). The taste-skill's checker family ([skills/taste](../skills/taste/SKILL.md)) enforces several of these mechanically; the taste-skill gate runs perf checks automatically.

## 7. Examples

**Example 1 — a content page cut by 70%.** A 3.4 MB editorial page: 2.1 MB of unoptimised JPEGs, two font families at 640 KB, three analytics scripts blocking parse. Fix: AVIF + `srcset` (images → 380 KB), self-hosted subsets + swap (fonts → 88 KB), scripts → deferred and consent-gated (JS → 95 KB). LCP 4.1 s → 1.7 s on the mid-range device profile. No design change was needed — the budget made existing design decisions reviewable.

**Example 2 — the justified 3D cost.** A hardware configurator's WebGL scene costs 180 KB of libraries plus GPU runtime. The decision record: the configurator *is* the product experience (conversion-critical), so the cost is bought deliberately — one WebGL context, paused off-screen, static fallback images per variant for reduced-motion and low-end paths, load after first paint. Contrast with the same scene on a content page, where the three-question filter kills it.

## 8. Common mistakes

- **Budget as afterthought** — "we'll optimise at the end"; late optimisation is archaeology.
- **Lighthouse as the only measure** — lab scores without device/network reality; field data where it exists.
- **Unoptimised images** — the classic majority of page weight; §5.1's checklist is mechanical.
- **Blocking fonts** — invisible text and delayed paint for a subset nobody ships.
- **Dependency creep** — a library per whim; the motion layer's one-library-per-layer rule is the model.
- **Animating the wrong properties** — layout-thrashing jank on real devices that never appears in the dev environment.
- **Skeletons that lie** — placeholder shapes unrelated to content; shift and surprise instead of stability.
- **Perceived-performance theatre** — optimistic UI covering operations that genuinely fail; bridging feedback complements truth, never replaces it.

## 9. Evaluation checklist

- [ ] Budgets recorded per template before scaffolding; deviations documented.
- [ ] Images: modern format, `srcset`, intrinsic dimensions, lazy below fold, LCP priority.
- [ ] Fonts: ≤ 2 families, subset, swap, preloaded critical files, < 100 KB.
- [ ] JS budget audited; bundle visualised; one library per layer respected.
- [ ] No layout-property animation; scroll effects compositor-only and throttled.
- [ ] CLS discipline: reserved space for async content; skeletons match content.
- [ ] Lighthouse mobile pass on the built page; real-device pass on core journeys; field data where available.
- [ ] Results recorded per template; regressions block release.
- [ ] Expensive choices (3D, blur, libraries) carry documented decisions with cheaper alternatives considered.

## 10. Related topics

- [Technology selection](technology-selection.md) — where budgets are set and rendering chosen.
- [CSS architecture](css-architecture.md) — the stylesheet discipline half of runtime cost.
- [Motion principles](../motion-and-interaction/motion-principles.md) and [Scroll experiences](../motion-and-interaction/scroll-experiences.md) — the animation cost model.
- [Animation libraries](../motion-and-interaction/animation-libraries.md) — selection with bundle/runtime data.
- [Assets README](../assets/README.md) — sourcing optimised assets and the pipeline.
- [Web typography](../typography/web-typography.md) — font loading craft in detail.
- [Website visual QA](../evaluation/website-visual-qa.md) — where measurement joins the QA loop.

## 11. References

- Google, "Web Vitals" — LCP ≤ 2.5 s, INP ≤ 200 ms, CLS ≤ 0.1 thresholds and the field-data model. https://web.dev/articles/vitals [search-verified, accessed 2026-11-25]
- GoogleChrome/lighthouse — the audit tool (31,200★, Apache-2.0, pushed 2026-11-25). [accessed 2026-11-25]
- MDN performance guides — lazy loading, `fetchpriority`, `preload`, image `srcset`. https://developer.mozilla.org/en-US/docs/Web/Performance [search-verified, accessed 2026-11-25]
- web.dev, "Optimize CLS" and image optimization guides. https://web.dev [search-verified, accessed 2026-11-25]
- Budget figures are stated as conventional starting points of this library, tuned per project — not sourced laws.
