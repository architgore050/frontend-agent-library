# Backgrounds, Gradients and Effects Sources

## 1. What is it?

The verified sources for ready-made backgrounds, gradients, particle effects and animated surfaces — the atmosphere layer ([Texture and period styles](../visual-styles/texture-and-period-styles.md), [Interface styles](../visual-styles/interface-styles.md)) — plus the procedural-first rule that keeps most of these CSS/SVG-cheap rather than asset-heavy. Where a ready-made effect is genuinely the right call (complex gradients, particle systems, cinematic scenes), this file names the honest sources and their integration costs.

## 2. Why does it matter?

Backgrounds are where AI-generated frontends most visibly cheat: a purple gradient behind everything, sourced from nobody, meaning nothing. The craft position of this library is the opposite — the background system is *designed* (procedural, token-driven, style-consistent) and sourced effects are used deliberately, with licences and performance costs recorded. The sources below were verified in the research pass, including the ones the brief named ambiguously (GetLayers, Kinetics, ScrollTide, Casberry particles) — each resolved to its actual service.

## 3. The sources

### 3.1 Gradient and background generators

- **CSS Gradient — https://cssgradient.io/ [accessed 2026-11-25]** — the gradient-builder tool (visual editor + CSS output); the baseline generator.
- **Mesh Gradient — https://meshgradient.in/ [accessed 2026-11-25]** — multi-point mesh gradients (the soft multi-colour blend style); export PNG or CSS — palette-fit the stops to tokens before export.
- **Cool Backgrounds — https://coolbackgrounds.io/ [search-verified, accessed 2026-11-25]** — the multi-tool (gradients, topography, particles, images) from the Bucher/Nameeq collaboration; quick exploratory generator.
- **Haikei — https://haikei.app/ [accessed 2026-11-25]** — the SVG scene generator (waves, blobs, circles, confetti, low-poly, grid patterns); exports SVG (light, token-recolorable) or PNG. The default source for *shape-based* decorative backgrounds.

### 3.2 Particle effects

- **tsParticles — https://particles.js.org/ [accessed 2026-11-25]** — the maintained particle engine ([tsparticles/tsparticles](https://github.com/tsparticles/tsparticles), 9,127★ MIT; successor to vincentgarreau/particles.js, 30,180★ MIT, dormant since 2024). Canvas-based, highly configurable; budget particle counts and pause off-screen ([../motion-and-interaction/animation-libraries.md](../motion-and-interaction/animation-libraries.md) §4.9).
- **Casberry particles — https://particles.casberry.in/ [accessed 2026-11-25]** — "AI Particle Simulator — professional 3D swarm effects" by the Casberry agency; an AI-assisted generator for 3D particle scenes (the brief's "Particles Casberry" resolved). Status: a commercial agency tool — evaluate output licence and cost before depending on it; the open-source tsParticles line covers most web needs.

### 3.3 Cinematic template and scene libraries (AI-native)

- **GetLayers — https://www.getlayers.ai/ [accessed 2026-11-25]** — "cinematic AI sites made easy": a library of designed layers (page templates, 3D WebGL scenes, animated backgrounds, gradients) copyable as AI prompts, with docs and a Figma plugin. **The brief's "GetLayers" resolved.** Position: a strong *reference and template* source for animation-heavy marketing pages; licensing/cost of shipped layers is per-plan — verify before shipping.
- **ScrollTide — https://www.scrolltide.co/ [accessed 2026-11-25]** — "cinematic website prompts & templates": curated scroll-driven templates with copyable prompts. **The brief's "ScrollTide" resolved.** Position: scroll-choreography reference and starting points; ships templates, not a dependency — adapt rather than paste ([../motion-and-interaction/scroll-experiences.md](../motion-and-interaction/scroll-experiences.md) owns the honest patterns).

### 3.4 Motion-example galleries

- **Kinetics — https://kinetics.colorion.co/ [accessed 2026-11-25]** — "CSS & React Spring animation examples": 162+ animated UI examples with copyable snippets and AI prompts. **The brief's "Kinetics" resolved.** Position: the implementation-reference gallery for micro-motion ([Microinteractions](../motion-and-interaction/microinteractions.md)).

## 4. The comparison table

| Source | Licence/cost | Output | Position |
| --- | --- | --- | --- |
| CSS Gradient | Free tool | CSS | Baseline gradient builder |
| Mesh Gradient | Free tool | PNG/CSS | Soft mesh gradients |
| Cool Backgrounds | Free tool | PNG | Exploration |
| Haikei | Free (verify terms) | SVG/PNG | Shape scenes, token-recolorable |
| tsParticles | MIT (runtime) | Canvas | The particle default |
| Casberry particles | Commercial agency tool | 3D scenes | Evaluated lead |
| GetLayers | Per plan (verify) | Templates/prompts/scenes | Cinematic reference layer |
| ScrollTide | Per plan (verify) | Scroll templates/prompts | Scroll reference layer |
| Kinetics | Free gallery | CSS/React snippets | Micro-motion reference |

## 5. Practical workflow

1. **Design the background system first** ([../visual-styles/texture-and-period-styles.md](../visual-styles/texture-and-period-styles.md) §7 layer order): ground → atmosphere → accent moments. Most needs resolve to procedural CSS/SVG (gradients, dot grids, `feTurbulence` grain) with zero dependencies.
2. **Reach for a generator when the shape is complex** (mesh gradients, waves, blob fields): generate → recolour stops to tokens → optimise (SVG preferred over PNG) → integrate.
3. **Particles only with a justification** (theme serves it) and the runtime budget ([tsParticles: counts, off-screen pause, reduced-motion static frame](../motion-and-interaction/motion-principles.md)).
4. **Cinematic libraries are references first**: study GetLayers/ScrollTide templates for choreography vocabulary; adapt patterns into your own tokens rather than shipping foreign design wholesale.
5. **Record provenance** for any exported asset (generator URL, date) ([licensing-and-provenance.md](licensing-and-provenance.md)).

## 6. Common mistakes

- **The default purple gradient** — a generator's default palette shipped as identity ([../evaluation/ai-design-failures.md](../evaluation/ai-design-failures.md) §6); recolour every exported gradient to the project's tokens.
- **PNG where SVG works** — heavier, blurrier, unrecolorable; Haikei-class tools export SVG for a reason.
- **Particles by default** — the 2015 habit; canvas runtime on every page without a theme justification.
- **Template pasting** — shipping a cinematic template's structure and copy wholesale; references are studied, not transplanted ([../inspiration/contributing.md](../inspiration/contributing.md) anti-copying rules).
- **Unbudgeted scenes** — animated backgrounds running off-screen and on mobile at full cost.

## 7. Evaluation checklist

- [ ] Background system designed (layers, tokens) before any generator opened.
- [ ] Procedural-first rule respected; generators used for genuinely complex shapes.
- [ ] Exports recoloured to project tokens; SVG preferred over PNG.
- [ ] Particle/animated effects justified, budgeted, pausable, reduced-motion-safe.
- [ ] Cinematic sources used as references; nothing shipped wholesale without adaptation and licence check.
- [ ] Provenance recorded for exported assets.

## 8. Related topics

- [Texture and period styles](../visual-styles/texture-and-period-styles.md) — the atmosphere layer these tools feed.
- [Interface styles](../visual-styles/interface-styles.md) — the structural styles.
- [Scroll experiences](../motion-and-interaction/scroll-experiences.md) — the honest scroll patterns ScrollTide-class templates should serve.
- [Motion principles](../motion-and-interaction/motion-principles.md) — the motion budget.
- [AI image generation](image-generation.md) — Route B when no source fits.
- [Licensing and provenance](licensing-and-provenance.md) — the manifest.

## 9. References

- CSS Gradient — https://cssgradient.io/ [accessed 2026-11-25]; Mesh Gradient — https://meshgradient.in/ [accessed 2026-11-25]; Cool Backgrounds — https://coolbackgrounds.io/ [search-verified, accessed 2026-11-25]; Haikei — https://haikei.app/ [accessed 2026-11-25]
- tsParticles — https://particles.js.org/ [accessed 2026-11-25]; particles.js original — https://vincentgarreau.com/particles.js/ [accessed 2026-11-25]
- Casberry particles — https://particles.casberry.in/ [accessed 2026-11-25]
- GetLayers — https://www.getlayers.ai/ [accessed 2026-11-25, incl. docs page]; ScrollTide — https://www.scrolltide.co/ [search-verified, accessed 2026-11-25]; Kinetics — https://kinetics.colorion.co/ [search-verified, accessed 2026-11-25]
- Per-plan cost/licence items (GetLayers, ScrollTide, Casberry) are recorded as verify-before-dependency leads, not settled facts.
