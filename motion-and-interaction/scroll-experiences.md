# Scroll Experiences

## 1. What is it?

The craft of scroll-driven interface behaviour: everything a page does as the user scrolls, from honest, tiny reveals to cinematic scroll-driven scenes — plus the rules that separate the honest versions from scroll-jacking. It covers the platform capability (CSS scroll-driven animations), the library approaches (GSAP ScrollTrigger, Lenis, Motion scroll utilities), scroll composition patterns (pinning, scrubbed scenes, parallax, horizontal scroll, sticky storytelling), performance mechanics, and accessibility obligations. The general motion theory is [Motion principles](motion-principles.md); library selection is [Animation libraries](animation-libraries.md).

## 2. Why does it matter?

Scroll is the one input every web user performs constantly, and it is the most abused: scroll-jacking (hijacking the wheel for a choreography), permanent parallax, and pinned sections that trap users are the commonest complaints about "animated" sites — and the reason many teams ban motion outright. Yet scroll-driven storytelling is also the web's most distinctive narrative capability when done honestly: content reveals in reading order, scenes scrub with the user's own hand, and long products explain themselves progressively. This file exists so agents can build the second kind reliably and recognise the first kind on sight.

## 3. Core principles

**Principle 1 — The user owns the scroll.** Native scrolling, keyboard scrolling and touch physics are the platform contract. An honest scroll experience *responds to* scroll position; it never delays, redirects or consumes scroll events for its own choreography. A user must always be able to reach the footer by dragging the scrollbar.

**Principle 2 — Reveals serve reading order.** The default scroll behaviour worth building is content appearing as it enters the viewport, sequenced by reading order, once — then staying visible. Reveals that replay on every scroll-up are noise; content that never appears without JavaScript is a defect (the static story must exist — [Motion principles](motion-principles.md) §5).

**Principle 3 — Scrubbed scenes map progress to the user's hand.** Cinematic scroll scenes (a product assembling, a story chapter pinned while stages advance) work because *the user's scroll position is the timeline*. Progress maps to scroll; users can go back and forward freely; the scene is a rendering of position, not an autoplay video chained to the wheel.

**Principle 4 — Motion-reduced users get the story, not the skeleton.** Under `prefers-reduced-motion`: reveals become instant, parallax flattens, scrubbed scenes become static chapter layouts (all stages visible), smooth scroll disables. Nothing informational may live only in the scroll choreography.

**Principle 5 — Scroll effects are a performance budget.** Scroll handlers run on every frame; anything un-throttled (layout reads/writes per scroll event) janks immediately. Effects must run on the compositor (transform/opacity), read scroll via rAF-synced sources, and pause when off-screen.

## 4. How it works — the platform and the libraries

**CSS scroll-driven animations (baseline, modern browsers).** Native progress-driven animation: `animation-timeline: view()` for reveal-on-scroll and `animation-timeline: scroll()` for progress bars/parallax — no JavaScript, compositor-run, degrades gracefully (unsupported browsers show the static layout). The default choice for reveals and simple scrubbed effects. https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_scroll-driven_animations [search-verified, accessed 2026-11-25]

**GSAP ScrollTrigger (orchestration).** The toolkit for scenes CSS cannot express: pinning, complex timelines scrubbed to scroll, split-text choreography, section-based scene management. Combine with Lenis for smooth scroll where the experience justifies it (rAF-synced). Use: `scrollTrigger: { trigger, start, end, scrub: true }` for scrubbed scenes; `once: true` for reveals.

**Lenis (smooth scroll).** Inertial scrolling that stays native-compatible (it does not intercept scroll, it smooths it). Honest-use rules: disable for `prefers-reduced-motion`; consider disabling on touch (native momentum already exists); never combine with wheel-hijacking patterns. [Animation libraries](animation-libraries.md) §4.4 carries the selection criteria.

**Motion scroll utilities (React).** `useScroll`/`useTransform` for scroll-linked values in React components — parallax offsets, progress-driven styles inside the component model.

**IntersectionObserver (reveals).** The dependency-free reveal mechanism: observe entries, add a class, animate via CSS transition; `once` semantics for one-time reveals; works without any library.

## 5. Practical application — the patterns

**5.1 Reveal on enter (the workhorse).** Elements fade/rise once as they enter (8–24 px rise, 300–500 ms, 30–80 ms stagger in reading order). Build: IntersectionObserver + CSS class, or CSS `view()` timeline. Rule: appears once, stays visible, content exists without JS (start visible, animate only when the observer is attached — the no-JS default is the static story).

**5.2 Parallax (the restrained one).** Background layers moving slower than foreground, depth through differential rates (10–20% differential, conventional). Build: CSS `view()` timeline or Motion `useTransform`. Rules: decorative layers only — never move text the user is reading relative to its container; flat under reduced motion; one or two layers, not five.

**5.3 Pinned storytelling (the cinematic one).** A section pins (`position: sticky` or ScrollTrigger pin) while stages of a scene advance with scroll progress — product features demonstrated in sequence, a narrative unfolding. Rules: the pinned section's height defines the scene's duration explicitly; stages map to clear scroll ranges; the user can scroll back through stages; a static all-stages layout under reduced motion; escape is always one wheel-flick away (never trap).

**5.4 Horizontal scroll (the deliberate one).** Vertical wheel driving horizontal movement — for galleries, timelines and process sequences. Rules: an honest implementation maps *virtual* progress to horizontal translation of a track while native page scroll continues; keyboard users get horizontal scroll affordances (focusable track, arrow keys); on touch, native horizontal swipe works; provide a static horizontal-scroll container fallback (overflow-x) under reduced motion.

**5.5 Progress indicators.** Reading progress bars, section indicators, scroll-linked counters — the cheapest honest scroll value. Build: CSS `scroll()` timeline, one element, compositor-safe.

**5.6 Sticky composition (no JavaScript).** Sticky headers/cards/stacking cards (`position: sticky`) — the zero-dependency scroll pattern family; stacking-card effects via sticky + z-index; check stacking contexts ([../ui-ux/frontend-implementation.md](../ui-ux/frontend-implementation.md)).

**5.7 Scroll snapping.** `scroll-snap-type` for carousel-like or section-step interfaces — native, interruptible, accessible by construction. Use for genuine step-sets (onboarding, image galleries), never for whole-page section locking on content sites.

## 6. Decision framework

| Goal | First choice | Upgrade when |
| --- | --- | --- |
| Content reveals in reading order | IntersectionObserver + CSS (or `view()` timeline) | Complex stagger choreography → GSAP |
| Progress bar / scroll counter | CSS `scroll()` timeline | Never — CSS is sufficient |
| Subtle depth (parallax) | CSS `view()` timeline, 10–20% differential | Scroll-linked React state → Motion utilities |
| Pinned story scene | `position: sticky` + CSS | Multi-stage scrubbed timelines → GSAP ScrollTrigger |
| Smooth inertial feel | Nothing (native) | Justified campaign experience → Lenis (honest-use rules) |
| Horizontal process sequence | Native overflow-x + scroll-snap | Scroll-scrubbed horizontal cinema → GSAP + Lenis |
| Section step-set | CSS scroll-snap | Never trap full-page scroll on content sites |

## 7. Examples

**Example 1 — an honest product story.** A hardware landing page: hero settles on load (the dealt moment, not scroll-driven); features reveal in reading order (IntersectionObserver, once); one pinned scene shows the product assembling in four stages as a sticky stage scrubs scroll progress (GSAP, scrub, 1,200 px of scroll driving four stage states); a thin progress bar (CSS `scroll()`); parallax on one decorative layer at 15% differential. Reduced motion: reveals instant, the pinned scene renders as a static four-panel section, parallax flat, no smooth scroll. Keyboard: full native scroll; the scene is decoration over complete content.

**Example 2 — the scroll-jack audit.** A competitor site traps the wheel: each section takes three wheel ticks to pass because a library consumes scroll to drive an autoplaying animation; the scrollbar reaches the footer but the wheel never does; on touch, flicks are ignored mid-animation. The audit finding: every check in the honesty test (§3 principle 1) fails. Rebuild applies the same choreography scrubbed to scroll — the visual result is near-identical, the user's control is total, and abandonment on the page measurably drops.

## 8. Common mistakes

- **Scroll-jacking** — consuming wheel events for autoplay choreography; the defining scroll sin (principle 1).
- **Reveal-on-every-scroll** — re-animating content each time it re-enters; once is the rule.
- **Content missing without JavaScript** — initial `opacity: 0` set in CSS with the observer as the only reveal path; no-JS users (and crawlers) get nothing.
- **Parallax on text** — moving what the user is reading; depth belongs to decorative layers.
- **Janky handlers** — per-scroll-event layout reads/writes; rAF-synced, compositor-only effects or none.
- **Pinning without escape** — trapped sections, invisible scene ends, scroll distance unrelated to content.
- **Reduced-motion theatre** — a blanket `display: none` on animated elements instead of a static restage; information vanishes rather than flattens.
- **Smooth scroll for its own sake** — Lenis on documentation, dashboards and forms.

## 9. Evaluation checklist

- [ ] The scrollbar reaches the footer with native wheel/keyboard; no scroll consumption.
- [ ] Reveals fire once, serve reading order, and content is complete without JavaScript.
- [ ] Scrubbed scenes map progress to scroll bidirectionally; going back works.
- [ ] Pinned sections have explicit scroll ranges and are escapable in one gesture.
- [ ] Parallax touches only decorative layers; text never moves relative to its container.
- [ ] Horizontal patterns keep native touch swipes and keyboard affordances.
- [ ] `prefers-reduced-motion`: instant reveals, static scene layouts, no smooth scroll, no parallax.
- [ ] Effects animate transform/opacity only; 60 fps holds while scrolling on a mid-range device.
- [ ] Off-screen scenes pause; no per-scroll-event layout thrash.

## 10. Related topics

- [Motion principles](motion-principles.md) — the governing craft layer.
- [Animation libraries](animation-libraries.md) — GSAP, Lenis, Motion selection detail.
- [Frontend implementation](../ui-ux/frontend-implementation.md) — CSS layer mechanics (stacking contexts, transforms).
- [Performance](../frontend-engineering/performance.md) — the frame budget scroll effects must meet.
- [Layout and composition](../layout/grid-systems.md) — the structure scroll choreography moves through.
- [Accessibility testing](../accessibility/accessibility-testing.md) — where reduced-motion and keyboard checks live in a QA pass.

## 11. References

- MDN, "CSS scroll-driven animations" — the platform capability and its syntax. https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_scroll-driven_animations [search-verified, accessed 2026-11-25]
- GSAP ScrollTrigger documentation — scrub, pinning and scene management. https://gsap.com/docs/v3/Plugins/ScrollTrigger/ [search-verified, accessed 2026-11-25]
- Lenis documentation and repository — the smooth-scroll model and its rAF sync. https://github.com/darkroomengineering/lenis [accessed 2026-11-25]
- MDN, IntersectionObserver API. https://developer.mozilla.org/en-US/docs/Web/API/Intersection_Observer_API [search-verified, accessed 2026-11-25]
- W3C, WCAG 2.2 — 2.2.2 (Pause, Stop, Hide), 2.3.3 (Animation from Interactions), 1.4.10 (Reflow) bound all scroll behaviour. [canonical]
- The honesty test (§3 principle 1) and pattern budgets are this library's synthesis of professional practice.
