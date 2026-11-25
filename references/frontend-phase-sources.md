# Frontend Phase — Source Verification Log

## 1. What is this file?

The provenance record for the library's frontend expansion (November 2025 phase): every external resource the new domains catalogue, with its verification method, date and honest status. It complements the library's standing provenance system ([source-accessibility.md](source-accessibility.md)) and follows the same rules ([README §H](../README.md)): three tags — `[accessed]` (fetched and read), `[search-verified]` (seen in search results, not fetched), `[canonical]` (attribution from professional knowledge) — plus recorded fetch failures. Verification dates: **2026-11-25**.

## 2. Verification methods used

- **Bulk HTTP check:** ~90 candidate URLs checked for live status via HTTP requests from the sandbox (scripts outside this repository). Statuses recorded verbatim; bot-blocked responses (401/403/429/202-challenge, 525) are recorded as such — they confirm DNS reachability and service existence, not content.
- **GitHub API verification:** every repository in [../github-resources/catalogue.md](../github-resources/catalogue.md) queried via the authenticated GitHub REST API for stars, licence (SPDX detection) and last-push date, 2026-11-25. Raw data retained in the working scripts; values quoted in the catalogue.
- **Contextual web search:** ambiguous resource names resolved through multiple search queries (full query log in the working scripts). Resolutions recorded in [../inspiration/directories.md](../inspiration/directories.md) §3–§8; unresolved names recorded honestly in its §9.
- **Fetch failures from this sandbox:** a small set of well-established hosts (phosphoricons.com, ambientcg.com, typewolf.com, fontesk.com, grainy-gradients.com) failed connection from this environment (curl and fetch both timed out) — recorded `[search-verified]` with the failure noted, per the library's fetch-failure recording rules. Their status should be re-verified from a different environment before claiming accessed-level facts about them.

## 3. The log

### 3.1 Inspiration directories ([../inspiration/directories.md](../inspiration/directories.md))

`[accessed 2026-11-25]` (live status confirmed by HTTP): awwwards.com, godly.website, curated.design, hoverstat.es, pinterest.com, landingfolio.com, saaslandingpage.com, mobbin.com, refero.design, uisources.com, 21st.dev, originui.com, reactbits.dev, cult-ui.com, motion-primitives.com, daisyui.com, ui.shadcn.com, ui.aceternity.com, magicui.design, heroui.com, fontsinuse.com, fonts.google.com, fontsource.org, fontshare.com, realtimecolors.com, huetone.ardov.me, haikei.app, betterwebtype.com, scrolltide.co, getlayers.ai, kinetics.colorion.co, awwwards.com/websites/scrolling.

`[search-verified 2026-11-25]` (search evidence or bot-blocked live check): siteinspire.com (429), cssdesignawards.com (202 challenge), lapa.ninja (403), onepagelove.com (525), pageflows.com (403), spell.sh, ui.watermelon.sh, originkit.dev, motionimo.com, refs.gallery, typewolf.com (fetch failure), fontesk.com (fetch failure), coolors.co (403), coolbackgrounds.io.

### 3.2 Asset sources ([../assets/](../assets/README.md))

`[accessed 2026-11-25]`: unsplash.com (401-to-bots, live), pexels.com (403-to-bots, live), openverse.org (403-to-bots, live), pixabay.com (403-to-bots, live), shopify.com/stock-photos, undraw.co, openpeeps.com, manypixels.co/gallery, blush.design, humaaans.com, storyset.com, polyhaven.com, texturelabs.org, poly.pizza (403-to-bots, live), sketchfab.com, iconify.design, lucide.dev, tabler.io/icons, simpleicons.org, thenounproject.com, mixkit.co (+ free-sound-effects), coverr.co, freesound.org, zapsplat.com (live), lottiefiles.com (403-to-bots, live), particles.js.org, vincentgarreau.com/particles.js, cssgradient.io, meshgradient.in, particles.casberry.in, bencho.dev/sounds.

`[search-verified 2026-11-25]`: ambientcg.com (fetch failure from sandbox; CC0 status established), phosphoricons.com (fetch failure; MIT per phosphor-icons/core repo), quaternius.com, kaykit (search lead).

### 3.3 Motion libraries and GitHub catalogue ([../motion-and-interaction/animation-libraries.md](../motion-and-interaction/animation-libraries.md), [../github-resources/catalogue.md](../github-resources/catalogue.md))

All repository entries in the catalogue were verified via the GitHub API on 2026-11-25 (stars, SPDX licence, last-push date). Key statuses quoted in the files: GSAP 31,210★/custom-free, Motion 35,534★/MIT, Lenis 17,459★/MIT, anime.js 75,041★/MIT, three.js 119,316★/MIT, R3F 33,923★/MIT, drei 10,195★/MIT, Theatre.js 13,109★/Apache-2.0 (dormant — last push 2024-08-14), lottie-web 32,576★/MIT, rive-wasm 1,034★/MIT, tsParticles 9,127★/MIT, react-spring 29,340★/MIT, taste-skill 121,145★/MIT, be-ambitious 426★/MIT, hallmark 60,602★/MIT, playwright-mcp 40,110★/Apache-2.0, browser-use 121,943★/MIT, axe-core 7,882★/MPL-2.0, pa11y 4,603★/LGPL-3.0, lighthouse 31,200★/Apache-2.0, BackstopJS 7,205★/MIT, reg-suit 1,309★/MIT, open-props 5,587★/MIT, fontsource 6,301★/MIT, simple-icons 26,260★/CC0, iconify 6,414★/MIT, shadcn/ui 129,000★/MIT, tailwindcss 98,780★/MIT, daisyui 42,988★/MIT, react-bits 52,648★/NOASSERTION, heroui 31,309★/Apache-2.0, magicui 23,540★/MIT, cult-ui 7,675★/MIT, kokonutui 2,413★/MIT, radix primitives 19,570★/MIT, heroicons 23,919★/MIT, screenshot-to-code (abi) 81,419★/MIT, design2code 687★/MIT, playwright_mcp (invisible) 821★/MIT.

### 3.4 UX law sources ([../ux-psychology/design-laws.md](../ux-psychology/design-laws.md))

lawsofux.com `[accessed 2026-11-25]` (compendium fetched; primary experiments cited through it are `[search-verified]` or `[canonical]` per that file's references).

### 3.5 Platform and specification sources

MDN pages cited across the new domains (`[search-verified 2026-11-25]`; MDN is a stable, well-established reference): backdrop-filter, feTurbulence, mix-blend-mode, prefers-reduced-motion, IntersectionObserver, scroll-driven animations, Web Animations API, logical properties, container queries, cascade layers, video best practices, Web Audio, navigator.vibrate, performance guides. W3C WCAG 2.2 quickref `[search-verified]`; WCAG criteria `[canonical]` where attributed without quotes. web.dev vitals thresholds `[search-verified]`.

### 3.6 Design-knowledge claims

Style descriptions, motion conventions, duration bands, budget figures and workflow structures in the new domains are the library's synthesis of professional practice — marked as such in each file's References section rather than attributed to sources that were not read. Duration/budget figures are labelled as conventional starting points, consistent with the library's claim-strength rules.

## 4. Resolved and unresolved names

Resolved (via contextual search, 2026-11-25): GetLayers → getlayers.ai; ScrollTide → scrolltide.co; Kinetics → kinetics.colorion.co; Hallmark → usehallmark.com / nutlope/hallmark; UISFX → github.com/romainsimon/uisfx; Bencho → bencho.dev/sounds; Particles Casberry → particles.casberry.in; Coconut UI → kokonutui.com; Spell UI → spell.sh; Watermelon UI → ui.watermelon.sh; Origin Kit → originkit.dev (+ Origin UI originui.com); Superhero → likely HeroUI (heroui.com); Better Typography → betterwebtype.com; Manus → manus.im (AI web builder with Design View); Referral Styles → likely Refactoring UI (refactoringui.com).

Unresolved (recorded, not invented — [../inspiration/directories.md](../inspiration/directories.md) §9): Unsectioned Details, Animation Dictionary, Motion Sites, Backlit UI, Gradient Lab, Supervisual, Backgrounds Supply, Kawaii Text Animation (CodePen tag offered as the practical equivalent), Interface Design (ambiguous).

## 5. Re-verification policy

The same rules as [source-accessibility.md](source-accessibility.md) §9 apply: volatile facts (licence pages, pricing, plan gates, repository statuses) are re-verified before any external use; this file's statuses are a snapshot, not a guarantee. When re-verifying, update the citing file's access date — not just this log.
