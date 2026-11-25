# Lusion

**URL:** https://lusion.co · **Category:** creative studio / portfolio · **Industry:** digital production studio · **Provenance:** canonical knowledge, recorded 2026-11-25 · **Verify live:** current reel/works (studios update constantly), WebGL behaviour on your hardware

## Why it is worth studying

Lusion is the award-circuit reference for WebGL-first studio portfolios — real-time 3D as the site's material (not decoration), playful physics, and the specific craft of making an immersive site that still loads, still navigates and still communicates. It is the study object for the [motion-led and 3D styles](../../visual-styles/interface-styles.md) §4.10–4.12, and for the loading/performance discipline heavy sites must observe ([../../frontend-engineering/performance.md](../../frontend-engineering/performance.md)).

## Visual direction

Experimental real-time: WebGL scenes as backgrounds and heroes, particles/physics simulation, dark grounds with precise light, type kept small and functional so the simulation speaks. The frontier style, executed with production discipline.

## Typography

Minimal utilitarian type over the 3D work: small grotesque/mono labels, restrained scale — the deliberate inversion of type-led sites. Where type animates, it follows the scene's physics rather than UI conventions.

## Colour system

Dark grounds, neutral UI, colour supplied by the rendered scenes themselves (lit materials, particles). The lesson: in immersive work, the palette lives in the lighting rig, not in CSS tokens — though the UI chrome still obeys contrast rules.

## Composition and layout

The scene IS the layout: UI floats over simulation space; content sections arrive as camera/scene transitions. Conventional grids exist only for project-index surfaces.

## Navigation

Minimal, persistent, scene-aware; project index as the conventional fallback surface — the two-layer pattern (immersive face + practical index) is the key architecture lesson ([../../motion-and-interaction/scroll-experiences.md](../../motion-and-interaction/scroll-experiences.md) §5.4).

## Interesting sections

- **The live hero:** interactive particle/physics scene that responds to input — the "the site is alive" moment, with real interaction (not passive).
- **Works index:** the practical, grid-based surface — proof that immersion and usability can be layered.
- **Project detail transitions:** scene-to-scene continuity (shared-element thinking at WebGL scale).

## Interaction and motion

Continuous simulation (paused when hidden), pointer-reactive scenes, scene transitions as page transitions. The motion budget is spent where it defines the site — everywhere else stays still ([../../motion-and-interaction/animation-libraries.md](../../motion-and-interaction/animation-libraries.md) one-context discipline).

## Imagery and visual assets

The real-time scenes themselves; project stills/videos for the index. Asset strategy: everything heavy is streamed, everything critical is instant.

## Distinctive details

The loading experience (styled, informative, honest — a brand moment, not a spinner); physics that respond naturally; the graceful low-power behaviour; the index's plain usability.

## What makes it effective

Demonstration: a studio selling real-time craft shows real-time craft, working smoothly, as the site itself. The medium is the proof.

## What to learn (and what to leave)

**Learn:** WebGL as the site's material (with budgets); the immersive-face/practical-index architecture; loading as a designed moment; simulation pauses and fallbacks. **Leave:** immersion for surfaces whose users are task-orientated (dashboards, docs), and simulation without a static or reduced-motion story.

## Suitable project types

Creative studios, award-class campaign sites, game-adjacent brands, immersive product launches.

## Related references and patterns

[Igloo](igloo.md) (immersion peer), [Apple](apple.md) (scroll storytelling peer), [Vercel](vercel.md) (the sober opposite); patterns: [../patterns.md](../patterns.md) §immersive faces, §loading moments, §scene transitions.

## What to verify live

Current works and scene style (studios refresh constantly); performance on your own hardware — this site is also a *test object* for WebGL budgeting.
