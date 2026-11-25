# Motion Principles

## 1. What is it?

The theory layer for interface motion: what animation is *for* in a frontend, the classical animation principles that transfer to UI, the timing laws (Fitts's law, Hick's law, Doherty threshold) that set interaction budgets, and the construction rules — easing, duration, choreography, interruption, reduced motion — that turn those ideas into CSS and JavaScript. The library's existing interaction layer ([../ui-ux/interaction-design.md](../ui-ux/interaction-design.md)) covers feedback timing, latency perception and reduced motion at the interaction-design level; this file is the motion-craft companion for agents building animated interfaces, with the library catalogue in [Animation libraries](animation-libraries.md) and scroll-specific craft in [Scroll experiences](scroll-experiences.md).

## 2. Why does it matter?

Motion is the most expensive design material on the web and the least reversible: it ships in milliseconds of user time and kilobytes of attention, and bad motion — slow, constant, decorative, blocking — actively degrades products. Yet motion done well is also the clearest signal of craft: it explains where elements come from, what just changed, and what is possible. Agents default to two failure modes: no motion at all (interfaces feel dead and state changes go unnoticed) or motion everywhere (scroll-jacking, perpetual loops, staggered-everything). The principles here exist to make motion *purposeful, hierarchical, interruptible and accessible* — the four properties every good interface animation system shares.

## 3. Core principles

**Principle 1 — Motion explains, it does not decorate.** Every animation answers a user question: where did this come from (entrance), what changed (transition), what can I do (affordance), is the system working (feedback). An animation with no answer is decoration and is cut.

**Principle 2 — Hierarchy: one hero, few supporting, many quiet.** A page budgets its motion like its type scale: one signature moment (the hero entrance, a dealt scroll scene), a handful of supporting transitions (state changes, reveals), and quiet micro-interactions everywhere (hover, focus, press). Everything animated at the same weight is nothing animated at all.

**Principle 3 — Motion obeys physical intuition.** Objects accelerate in, decelerate out (ease-out for entrances, ease-in for exits, ease-in-out for state moves); nothing teleports; nothing hovers without cause. Physical coherence is why users can *read* an animation without thinking.

**Principle 4 — Interruptible and reversible.** Real users click early, leave mid-transition and change direction. Every animation must be interruptible (CSS transitions are; JS timelines must be built to retarget) and its state must be consistent from any interruption point.

**Principle 5 — The accessibility floor is absolute.** `prefers-reduced-motion` renders the same information statically ([../ui-ux/interaction-design.md](../ui-ux/interaction-design.md) §5.3); nothing essential is conveyed by motion alone; nothing loops indefinitely without a pause control (WCAG 2.2.2). Motion is an enhancement layer over a complete static experience.

## 4. The classical principles, translated

The twelve principles of Disney-era animation (Thomas and Johnston, 1981) transfer to UI selectively — the ones that map, and the ones that do not:

| Principle | UI translation | Use |
| --- | --- | --- |
| Timing | Duration scales with distance and importance; 150–400 ms for micro-transitions (conventional); ~1 s for hero entrances | Every animation |
| Slow in, slow out | Ease-out entrances, ease-in exits, ease-in-out moves; avoid linear (mechanical) and strong overshoot (comedic) except deliberately | Every animation |
| Anticipation | A slight pre-move before a big action (button dips before modal opens) | Signature moments |
| Follow-through | Settling motion after the main move — elements ease past and return | Card entrances, dealt moments |
| Squash and stretch | Volume-preserving deformation | Rarely; playful brands only, and never on text |
| Secondary action | Supporting motion that reinforces the main one (a card lifts while its image zooms 1.02) | Hover states, hero moments |
| Exaggeration | Amplified motion for emphasis | Marketing moments; never on dense UI |
| Arcs | Motion follows curved paths, not straight lines | Element entrances at scale |
| Solid drawing | Consistent form/weight in 3D work | 3D scenes ([Interface styles](../visual-styles/interface-styles.md)) |
| Appeal | The motion has character | Brand moments |

What does **not** transfer: frame-by-frame pose animation (UI motion is parametric), and full theatrical staging (interfaces must stay legible first).

## 5. The timing laws

- **Fitts's law** — time to acquire a target grows with distance and shrinks with size. Motion implication: moving targets and shrinking hit areas cost users time; animated navs must not move targets mid-acquisition. Full treatment and math: standard HCI literature (MacKenzie's formulation is the anchor). **Review question:** does any animation move or resize a target the user is reaching for?
- **Hick's law** — decision time grows with the number and entropy of choices. Motion implication: animated option showers (everything flying in at once) increase perceived choice count; stagger arrivals in reading order instead. **Review question:** does the entrance choreography match the reading order and de-emphasise secondary options?
- **Doherty threshold** — system response under ~400 ms keeps users engaged and productive (the 1982 IBM finding); above it, perceived performance work (progress indication, optimistic UI, skeleton states) bridges the gap. Motion implication: feedback animations under 400 ms make a fast system feel instant; the full latency budget table lives in [../ui-ux/interaction-design.md](../ui-ux/interaction-design.md) §5.6. **Review question:** does every action over 400 ms have designed bridging feedback?

## 6. How it works — construction rules

**Duration bands (conventional, not laws):** 100–150 ms hover/press feedback; 200–300 ms small transitions (toggles, dropdowns); 300–500 ms modals, page transitions, larger moves; 600–1000 ms hero entrances and dealt moments; anything longer must be scroll-driven or user-controlled.

**Easing vocabulary:** one primary ease-out (cubic-bezier(0.16, 1, 0.3, 1) family or the framework's equivalent) for entrances; one ease-in for exits; ease-in-out for state moves; `linear` only for continuous loops (spinners, progress). Overshoot springs for playful brands, sparingly. Encode the vocabulary as tokens ([../design-systems/design-tokens.md](../design-systems/design-tokens.md)) — one ease and one duration per band beats bespoke curves everywhere.

**Choreography:** entrances stagger in reading order (30–80 ms offsets, conventional); related elements move as a group; exits are faster than entrances; nothing animates in the first paint of content users came to read (the hero's entrance is the exception — it is the page's one moment).

**Origin awareness:** elements animate *from where they logically came* — a modal from its trigger button (shared-element transition), a page from the clicked card, a menu from its burger. Origin-aware motion is the difference between choreography and noise.

**Staggering:** reveals sequenced, not simultaneous; **rubber banding:** overscroll resistance on scrollable edges (platform-native convention; do not re-implement poorly). **Interruptibility:** CSS transitions/transforms handle interruption by design; JS-driven timelines use frameworks with retargeting (Motion, GSAP) rather than hand-rolled tweens.

## 7. Practical application

**A component motion system.** Tokens: `--duration-fast: 150ms`, `--duration-base: 250ms`, `--duration-slow: 450ms`, `--ease-out`, `--ease-in`, `--ease-inout`; every interactive component gets hover (lift 1–2 px or brightness), focus-visible (ring, instant), active (press: scale 0.98 or translate), and entrance (opacity + 8–12 px rise on the fast token). This base layer alone lifts a product's perceived quality more than any hero animation.

**The dealt moment.** Each page carries one deliberate motion statement — a hero entrance with line-by-line type rise, one scroll-driven scene, one interactive flourish. It is designed, budgeted and tested at the same priority as layout. Two moments on a long page; never zero on a marketing surface.

**Reduced motion.** A single media query collapses the system: entrances become instant or opacity-only, loops stop, parallax flattens, and the page's story must survive. Test it as a first-class viewport ([../ui-ux/interaction-design.md](../ui-ux/interaction-design.md) §5.3).

**Performance.** Animate only `transform` and `opacity` (compositor-friendly); avoid animating layout properties (`width`, `top`, `margin`) and expensive filters; `will-change` sparingly; measure on mid-range devices ([../frontend-engineering/performance.md](../frontend-engineering/performance.md)); long-running canvases pause off-screen.

## 8. Decision framework

For each proposed animation, four questions in order:

1. **What does it explain?** No answer → cut. (Purpose)
2. **What weight is it?** Hero / supporting / quiet — assign one; if all three exist on the page, the budget is set. (Hierarchy)
3. **What happens when the user interrupts it?** Must be a defined, safe state. (Interruption)
4. **What does it look like with motion off?** Must carry the same information statically. (Accessibility)

Then the implementation filter: compositor-only properties, duration from the token bands, easing from the vocabulary, and a reduced-motion story.

## 9. Examples

**Example 1 — a settings page, motion system only.** No hero moment (task-focused surface): toggles animate state on the fast token, sections collapse/expand on the base token, saving feedback appears on the fast token, and everything respects reduced motion. Total animation code: tokens plus ~15 rules. The page feels responsive and crafted without a single decorative animation.

**Example 2 — a campaign page with hierarchy.** Hero: headline lines rise staggered on load (~900 ms, dealt once). Supporting: cards reveal on scroll with 60 ms staggers (scroll-triggered, not scroll-jacked — [Scroll experiences](scroll-experiences.md)). Quiet: hover lifts, underline draws, buttons press. One deal, three weights, no overlap in purpose; `prefers-reduced-motion` renders the full content statically and the campaign still works as a page.

**Example 3 — interrupting a transition.** A user opens a filter panel and immediately clicks a facet before the 350 ms open finishes. The panel's transition (CSS transition on transform/opacity) retargets naturally; its scroll position stays valid; the facet click lands. A hand-rolled JS timeline that cannot retarget would have swallowed the click — the reason principle 4 mandates interruptible construction.

## 10. Common mistakes

- **Motion without purpose** — decorative loops, "because it looks alive"; the first question answers it.
- **Flat hierarchy** — everything staggered, everything bouncing; no single moment reads.
- **Linear or wrong-direction easing** — mechanical entrances; ease-out is the default direction of life.
- **Slow everything** — 600 ms hovers; users perceive sluggishness, not elegance.
- **Scroll-jacking** — stealing scroll control for a choreography the user did not ask to watch ([Scroll experiences](scroll-experiences.md) governs the honest version).
- **Non-interruptible timelines** — hand-rolled tweens that eat clicks; build on transitions or retargeting frameworks.
- **Reduced motion as an afterthought** — a last-week media query that hides content instead of restaging it.
- **Animating layout** — width/top/margin animations jank on real devices; transform/opacity only.
- **Moving targets** — animations that move what the user is reaching for (Fitts's law violation).

## 11. Evaluation checklist

- [ ] Every animation states what it explains; decorative-only animation is removed.
- [ ] The page's motion hierarchy is countable: one hero moment, few supporting, quiet micro-layer.
- [ ] Durations come from the token bands; easing from the token vocabulary.
- [ ] Entrances stagger in reading order; exits are faster than entrances.
- [ ] Major elements animate from their logical origin.
- [ ] Every animation is interruptible and lands in a consistent state.
- [ ] `prefers-reduced-motion` renders the complete static story; nothing essential is motion-only.
- [ ] No indefinite loop lacks a pause; nothing loops longer than 5 s without control.
- [ ] Only transform/opacity are animated; 60 fps holds on a mid-range device.
- [ ] No animation moves or resizes a target the user is acquiring.

## 12. Related topics

- [Interaction design](../ui-ux/interaction-design.md) — feedback timing, latency budgets, reduced-motion detail, interruptible motion.
- [Animation libraries](animation-libraries.md) — GSAP, Motion, Lenis, Lottie, Rive, Three.js: what each is for.
- [Scroll experiences](scroll-experiences.md) — scroll-driven animation craft and its accessibility.
- [Microinteractions](microinteractions.md) — the quiet layer, including sound.
- [Design tokens](../design-systems/design-tokens.md) — encoding the duration/easing vocabulary.
- [Design laws](../ux-psychology/design-laws.md) — Doherty threshold context and the peak-end rule's motion implication.
- [Interface styles](../visual-styles/interface-styles.md) — the motion-led style's full pattern.

## 13. References

- Thomas, F. and Johnston, O. (1981), *The Illusion of Life: Disney Animation* — the twelve principles. [canonical]
- MacKenzie, I. S. (1992), "Fitts' law as a research and design tool in human-computer interaction" — the formulation used here. [canonical]
- Doherty, W. J. and Thadhani, A. J. (1982), "The Economic Value of Rapid Response Time" (IBM) — the ~400 ms threshold. Cited via perf practice literature. [canonical]
- W3C, WCAG 2.2, Success Criterion 2.2.2 (Pause, Stop, Hide) — the looping-motion rule. https://www.w3.org/WAI/WCAG22/Understanding/pause-stop-hide.html [search-verified, accessed 2026-11-25]
- MDN, `prefers-reduced-motion` — the accessibility mechanism. https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-reduced-motion [search-verified, accessed 2026-11-25]
- Val Head, *Designing Interface Animation* (Rosenfeld, 2016) — the purpose/hierarchy framing in professional practice. [canonical]
- Duration bands and choreography offsets are stated as professional conventions of this library, not sourced laws.
