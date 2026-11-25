# Animation Libraries

## 1. What is it?

A decision-oriented catalogue of the JavaScript, CSS, canvas and WebGL animation tools a frontend agent actually chooses between, with verified maintenance status, licence, what each is genuinely good at, performance and accessibility implications, and the integration questions that decide inclusion. It covers GSAP, Motion (formerly Framer Motion), Anime.js, Lenis, React Three Fiber and Three.js, Theatre.js, Lottie, Rive, tsParticles, React Spring, and the platform baseline (CSS animation, SVG animation, Web Animations API, Canvas). The craft rules governing any of these are [Motion principles](motion-principles.md); the components and effects built on them are catalogued in [../github-resources/catalogue.md](../github-resources/catalogue.md).

## 2. Why does it matter?

Animation dependencies are the heaviest kind a frontend takes on: they run continuously, they define the feel of the product, and a wrong pick is expensive to reverse. The default failure is fashionable over-selection — shipping GSAP, Motion *and* a WebGL stack into one build because each is well known, with no one deciding which layer owns which job. This file's position: the platform (CSS + Web Animations API) owns the micro layer, one JS timeline library owns choreography, one engine owns 3D if 3D is real, and everything else is justified per need. Each library below is judged on that basis.

## 3. Core principles

**Principle 1 — One library per layer.** CSS owns the micro layer (hover, focus, simple reveals). One timeline library owns orchestrated choreography (hero entrances, scroll scenes, complex staggers). One engine owns real 3D. Adding a second library to the same layer requires a written reason.

**Principle 2 — Choose by the job, not by stars.** Stars measure attention. The selection inputs are: the motion jobs the product actually has, the framework in use, bundle/performance budget, accessibility requirements, and maintenance risk.

**Principle 3 — Every library must state its reduced-motion story.** If a library cannot pause, skip or flatten its output under `prefers-reduced-motion` without heroic effort, that is a selection factor, not a footnote.

**Principle 4 — Verify maintenance before depending.** Every entry carries its checked status (stars, licence, last push as of 2026-11-25 via the GitHub API). A library dormant for 12+ months is recorded as such — usable, but with an exit plan.

## 4. The catalogue

Format per entry: **What it is → Genuinely good at → When appropriate → Performance/access → Integration → Status (verified 2026-11-25).**

### 4.1 GSAP (GreenSock Animation Platform)

The veteran timeline library: sequencing, stagger, scroll trigger, morphing, text splitting, SVG drawing — the most complete choreography toolkit on the platform. **Good at:** complex multi-element timelines, scroll-driven scenes (ScrollTrigger), pinning, and the "dealt moments" pattern. **When:** marketing/campaign sites, any page needing orchestrated scroll choreography. **Performance:** transforms/opacity-first tooling; ScrollTrigger is well optimised; licence is now unrestricted following the 2024 Webflow acquisition (standard "no charge" plug-ins included) — verify licence terms for commercial redistribution at adoption time. **Integration:** framework-agnostic; `useGSAP` hook for React. **Status:** greensock/GSAP, 31,210★, no SPDX licence file in repo root (custom), last push 2026-11-04. https://gsap.com/ [accessed 2026-11-25]

### 4.2 Motion (formerly Framer Motion)

The React/JS animation library (`motion` package, motion.dev): declarative component API, springs, layout animations, gesture and presence handling, scroll-linked values. **Good at:** React component state animation, shared-layout transitions (origin-aware modal/card morphs), enter/exit orchestration (`AnimatePresence`). **When:** React/Next.js products where motion is part of the component system. **Performance:** hardware-accelerated by default; layout animations measure DOM (budget them); `LazyMotion` trims bundle. **Integration:** first-class React; vanilla bundle available. **Status:** motiondivision/motion, 35,534★, MIT, last push 2026-11-24. https://motion.dev/ [accessed 2026-11-25]

### 4.3 Anime.js

Lightweight timeline engine with a fresh v4 API: keyframed timelines, staggering, SVG attributes, spring easing. **Good at:** small-bundle choreography where GSAP's breadth is unneeded; SVG-heavy moments. **When:** single-page moments, sites wanting a minimal dependency. **Performance:** light (~10s of KB); transforms/opacity-first. **Integration:** framework-agnostic; v4 modular. **Status:** juliangarnier/anime, 75,041★, MIT, last push 2026-11-02. https://animejs.com/ [accessed 2026-11-25]

### 4.4 Lenis

Smooth-scroll engine ("Smooth scroll as it should be") by Darkroom Engineering: inertial scroll with raf sync, scroll-driven hooks, works with GSAP ScrollTrigger. **Good at:** the "premium scroll feel" on marketing sites — when used honestly (scroll remains native-usable, keyboard works, it is disabled for reduced motion and touch where inappropriate). **When:** campaign/portfolio sites where scroll choreography is the core experience. **Performance/access:** smooth-scroll libraries *are* the common source of scroll-jacking complaints — follow the honest-use rules in [Scroll experiences](scroll-experiences.md). **Integration:** `lenis` package; React wrapper available. **Status:** darkroomengineering/lenis, 17,459★, MIT, last push 2026-11-24. https://lenis.darkroom.engineering/ [accessed 2026-11-25]

### 4.5 Three.js and React Three Fiber

Three.js: the JavaScript 3D engine (renderer, scene, camera, materials, loaders). React Three Fiber (R3F): a React renderer over Three.js; Drei: the R3F helper kit. **Good at:** real 3D scenes, product configurators, shader-driven backgrounds, spatial storytelling. **When:** 3D is the content (hardware product pages, immersive brand moments) — not as decoration on content pages. **Performance:** the heaviest dependency in this file; budget strictly (one live WebGL context is a sane default; four is the taste-skill's ceiling), pause off-screen, provide static fallbacks, measure on integrated GPUs. **Accessibility:** WebGL scenes are decorative by default — give them `aria-hidden` and a text/story alternative; never put exclusive information in a 3D scene without an alternative. **Integration:** R3F in React apps; vanilla Three.js elsewhere; Theatre.js for authored animation (4.6). **Status:** mrdoob/three.js 119,316★ MIT (pushed 2026-11-24); pmndrs/react-three-fiber 33,923★ MIT (2026-10-21); pmndrs/drei 10,195★ MIT (2026-11-17). https://threejs.org/ [accessed 2026-11-25]

### 4.6 Theatre.js

Motion-design editor for the web: a keyframe GUI over programmatic scenes (r3f integration for 3D sequencing). **Good at:** director-quality, hand-authored animation sequences where designers tune curves visually. **When:** bespoke immersive pieces with a design-driven timeline; overkill for component motion. **Performance:** runtime is modest; authoring tool is dev-only. **Status:** theatre-js/theatre, 13,109★, Apache-2.0, **last push 2024-08-14 — dormant; adopt with an exit plan**. https://www.theatrejs.com/ [accessed 2026-11-25]

### 4.7 Lottie / lottie-web

Renders After Effects compositions (via Bodymovin export) natively — the standard for designer-authored vector animation. **Good at:** complex 2D illustration animation, onboarding moments, empty states, icon flourishes that a designer authored. **When:** a motion designer exists and works in After Effects. **Performance:** canvas/svg renderers; file size and runtime cost scale with composition complexity — budget like an image; `lottie-light` variant for simple needs. **Access:** decorative by design; provide static first frames; content-critical animation should not live only in Lottie. **Status:** airbnb/lottie-web, 32,576★, MIT, last push 2025-09-01; ecosystem (LottieFiles) active. https://airbnb.io/lottie/ [accessed 2026-11-25]

### 4.8 Rive

Interactive vector animation runtime (state machines authored in Rive's editor; web runtime rive-wasm). **Good at:** *interactive* animation — characters and UI that respond to input state (hover, press, game-like feedback); lightweight WASM runtime. **When:** brand mascots, interactive illustration, game UI; the state-machine model also suits loading/status characters. **Performance:** small runtime; assets are compact. **Status:** rive-app/rive-wasm 1,034★ MIT (pushed 2026-11-25); rive-app/rive-react 1,190★ MIT (2026-11-21). Editor is proprietary (free tier; paid plans for teams) — assets and runtime licensing need checking per project. https://rive.app/ [accessed 2026-11-25]

### 4.9 tsParticles / particles.js

Particle effects (the classic vincentgarreau/particles.js and its maintained successor tsParticles). **Good at:** configurable particle backgrounds (networks, confetti, snow). **When:** genuinely serves the atmosphere (space, data, celebration themes); recorded in [../assets/backgrounds-and-effects.md](../assets/backgrounds-and-effects.md) as a source. **Performance:** canvas-based; particle counts must be budgeted; pause off-screen. **Status:** tsparticles/tsparticles 9,127★ MIT (pushed 2026-11-25); vincentgarreau/particles.js 30,180★ MIT (2024-03-28 — the original is dormant; tsParticles is the maintained line). https://particles.js.org/ [accessed 2026-11-25]

### 4.10 React Spring

Spring-physics animation for React (`@react-spring/web`): interruption-friendly physical motion. **Good at:** gesture-driven, interruptible UI motion; drag interactions. **When:** React products with gesture-heavy interaction; note Motion (4.2) overlaps this space — pick one per project. **Status:** pmndrs/react-spring, 29,340★, MIT, last push 2026-11-24. [accessed 2026-11-25]

### 4.11 The platform baseline (default choice)

CSS transitions/animations, the Web Animations API, SVG SMIL/CSS, `scroll-driven-animations` CSS — zero dependencies, compositor-friendly, interrupted safely by the browser, and the only layer with guaranteed reduced-motion support via one media query. **Position:** the baseline owns every micro interaction and simple reveal; JS libraries are added when choreography exceeds what CSS sequences can express. MDN's scroll-driven animations guidance covers the newest baseline capability. https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_scroll-driven_animations [search-verified, accessed 2026-11-25]

## 5. How it works — the selection procedure

1. **List the motion jobs.** From the brief: micro layer (always CSS), orchestrated choreography (hero, scroll scenes), component state motion (React?), real 3D (yes/no), designer-authored assets (After Effects/Rive workflows available?), particles (atmosphere need?).
2. **Match one library per job** from the catalogue; prefer the platform when the job is small; when two libraries claim a job, prefer the one matching the framework and the smaller bundle.
3. **Budget check.** Sum the bundle and runtime costs; against the performance budget ([../frontend-engineering/performance.md](../frontend-engineering/performance.md)); cut the weakest justification.
4. **Accessibility check.** Reduced-motion handling exists for each chosen library; test all of them under the media query.
5. **Maintenance check.** Statuses above are dated; re-verify at adoption. Dormant picks (Theatre.js) get an exit plan (export timings, isolate usage).
6. **Document the decision** in the project: which layer owns which job, and why.

## 6. Decision framework

| Situation | Default choice |
| --- | --- |
| Hover/focus/simple reveals, any stack | CSS (baseline) |
| React product, component state + shared-layout transitions | Motion |
| Campaign site, scroll choreography, staggers, pinning | GSAP (+ Lenis if smooth scroll serves the experience honestly) |
| Single hero moment, minimal bundle | Anime.js or CSS |
| Real 3D product/configurator | Three.js (+ R3F/Drei in React) |
| Designer-authored 2D animation | Lottie |
| Interactive character/state-machine animation | Rive |
| Particle background (justified by theme) | tsParticles |
| Designer-tuned immersive timeline | Theatre.js (dormancy caveat) |
| Gesture-heavy React UI | React Spring or Motion — one, not both |

## 7. Examples

**Example 1 — a SaaS marketing site.** Jobs: component motion (React) + one hero choreography + one scroll scene. Pick: Motion for components; GSAP only for the scroll scene *if* CSS scroll-driven animations cannot express it (budget: ~30 KB vs 60+ KB — try CSS first). Lenis rejected: the product's own docs live on the same domain and consistent native scroll beats inertial feel for a mixed-audience site. Two dependencies at most, both justified in the decision record.

**Example 2 — a hardware product page with a configurator.** Jobs: 3D configurator (the content), component motion (React), micro layer. Pick: R3F + Drei for the configurator (one WebGL context, paused off-screen, static fallback images per colour variant), Motion for components, CSS for micro. Accessibility: the configurator's variant choices are duplicated as an accessible list — the 3D view is an enhancement, never the only channel for the product's information.

## 8. Common mistakes

- **Stacking libraries at one layer** — GSAP + Motion + react-spring in one React build; no one owns anything.
- **3D as decoration** — a Three.js background on a content page; the heaviest dependency for the weakest payoff.
- **Adopting a dormant library without an exit plan** — the maintenance check exists for exactly this.
- **Ignoring reduced motion per library** — each library needs its own flattened story; a global CSS rule does not reach canvas/WebGL.
- **Smooth scroll everywhere** — Lenis on documentation, dashboards and forms; the premium feel becomes a usability complaint.
- **Lottie for everything** — runtime cost and update friction for what a 5-line CSS transition would do.

## 9. Evaluation checklist

- [ ] Motion jobs listed before libraries chosen; one library per layer.
- [ ] Platform baseline considered first for every job.
- [ ] Bundle/runtime budget computed; weakest justification cut.
- [ ] Reduced-motion verified for each library in use.
- [ ] Maintenance status re-verified at adoption (statuses above dated 2026-11-25); dormant picks carry exit plans.
- [ ] WebGL: one context default, paused off-screen, static fallback, information never exclusive to the scene.
- [ ] Decision record written: layer → library → reason.

## 10. Related topics

- [Motion principles](motion-principles.md) — the craft layer every library implements.
- [Scroll experiences](scroll-experiences.md) — ScrollTrigger, Lenis and CSS scroll-driven animation in depth.
- [Performance](../frontend-engineering/performance.md) — the budget the selection procedure must satisfy.
- [Assets: video and motion](../assets/video-and-motion.md) — sourced motion assets (video, Lottie files) versus runtime libraries.
- [github-resources catalogue](../github-resources/catalogue.md) — the repositories behind each library, plus component libraries built on them.
- [Frontend implementation](../ui-ux/frontend-implementation.md) — the CSS layer's own motion craft.

## 11. References

- Repository statuses (stars, licence, last push) verified via the GitHub API on 2026-11-25; entries cite each project's official site. See [../references/frontend-phase-sources.md](../references/frontend-phase-sources.md) for the full verification log.
- GSAP licence notes — Webflow acquisition (2024) made standard plug-ins free; verify terms for redistribution. https://gsap.com/pricing/ [search-verified, accessed 2026-11-25]
- MDN, Web Animations API and CSS scroll-driven animations — the platform baseline. [search-verified, accessed 2026-11-25]
- W3C, WCAG 2.2 (2.2.2 Pause, Stop, Hide; 2.3.3 Animation from Interactions) — the accessibility obligations any library must satisfy. [canonical]
