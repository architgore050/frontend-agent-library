# Interface Styles

## 1. What is it?

The interface-materiality branch of the library's style vocabulary: styles whose defining material is the screen itself — depth, translucency, softness, structure, motion and data. Each entry gives the recognition cues, the product contexts where the style genuinely works, implementation techniques, suitable typography, colour and assets, and the failure modes specific to it. The classic families and the theory of style selection live in [Graphic design → Visual styles](../graphic-design/visual-styles.md); this file extends the catalogue for frontend work. Surface and period treatments are in [Texture and period styles](texture-and-period-styles.md).

## 2. Why does it matter?

"Make it modern" is not a direction. Agents that cannot name styles produce the generic AI aesthetic the library exists to prevent: default border radius, default shadow, default blue, default gradient. Naming a style converts taste into decisions a reviewer can check — a client who says "glassy" or "brutalist" or "bento" is pointing at a tradition with known techniques and known failure modes. The catalogue also prevents cargo-culting: every style here has a *where it works* clause, because the most common failure is not choosing the wrong style but applying an unfashionable-at-the-moment style everywhere regardless of product.

## 3. Core principles

**Principle 1 — Material logic before decoration.** Every style in this file imitates a material or structural logic (glass, clay, paper, blueprint, print halftone). Get the material's physics right — glass blurs and refracts what is *behind* it; clay is soft and matte; a blueprint is dimensional and precise — and the style reads as deliberate. Break the physics and it reads as costume.

**Principle 2 — One structural style per surface, one atmosphere per identity.** A product can carry a glass hero, a data-dense dashboard and an editorial blog under one typographic and colour system, but it cannot be glassy, neumorphic and brutalist at once. Mixing rules: [Graphic design → Visual styles](../graphic-design/visual-styles.md) §5.

**Principle 3 — Accessibility is not negotiable per style.** Several styles in this file fight contrast and legibility by construction (glass on busy imagery, low-contrast neumorphism, dense bento). The WCAG floors in [../accessibility/accessible-colour.md](../accessibility/accessible-colour.md) apply to every style; a style that cannot pass is adapted or rejected, not excused.

**Principle 4 — Performance is a design constraint.** Blur, 3D, generative art and motion-led styles cost GPU and battery. Budget them like any dependency: [../frontend-engineering/performance.md](../frontend-engineering/performance.md) governs how much of a style a page may carry.

## 4. The catalogue

Entry format: **Recognise → Where it works → Implement → Type, colour, assets → Mistakes.**

### 4.1 Glassmorphism

**Recognise:** translucent surfaces with backdrop blur, thin light borders (1 px white at low opacity), layered depth over colourful or image backgrounds; popularised by Apple's visionOS and macOS Big Sur era and by Dribbble exploration around 2020.
**Where it works:** immersive product surfaces over rich imagery (media players, map overlays, vision-OS-style dashboards); hero panels over gradients; luxury and entertainment brands with strong photography.
**Implement:** `backdrop-filter: blur(16px) saturate(1.4)` over a vibrant gradient or image; border `1px solid rgba(255,255,255,0.2)`; inner top highlight via gradient; layered z-depth with progressively stronger blur for background layers. Provide `@supports` fallbacks (solid translucent colour) — backdrop-filter has no effect in engines without support. For the shader-based "liquid glass" refractive variant (Apple-style edge refraction), [shuding/liquid-glass](https://github.com/shuding/liquid-glass) (MIT, see [../github-resources/catalogue.md](../github-resources/catalogue.md) §5) is the copy-paste reference implementation.
**Type, colour, assets:** high-contrast text on a darkened or lightened glass layer (WCAG still applies — tint the glass toward black or white as needed); saturated backgrounds that give the blur something to show; real photography behind the glass beats gradients.
**Mistakes:** glass on glass on glass (nothing legible behind anything); white glass on white imagery; blur without fallback; body text on heavily blurred but *busy* backgrounds; applying it to forms where every field needs crisp definition.

### 4.2 Neumorphism

**Recognise:** monochrome soft-UI — extruded and debossed shapes made of two shadows (light top-left, dark bottom-right) on a single background colour; the 2019–2020 Dribbble wave.
**Where it works:** playful control panels and concept pieces on *single-hue* backgrounds with generous sizing. Almost never the right choice for production product UI.
**Implement:** same-colour background and element; `box-shadow: -8px -8px 16px rgba(255,255,255,.6), 8px 8px 16px rgba(0,0,0,.15)`; inset variant (negative first offset) for pressed or input states.
**Type, colour, assets:** one hue family only; type must clear contrast against the shared background — the style's central tension.
**Mistakes:** the notorious one: fails WCAG contrast for boundaries and disabled states ([../accessibility/accessible-colour.md](../accessibility/accessible-colour.md)); buttons indistinguishable from background; visually exhausting at density. If a brief demands it, reserve it for decorative containers and keep controls flat and high-contrast.

### 4.3 Claymorphism

**Recognise:** puffy rounded volumes — large radii, a chunky inner highlight, soft double shadow; toy-like, friendly, matte. Emerged from 3D-illustration trends (~2021–2022).
**Where it works:** children's products, playful fintech for consumers, learning apps, mascot-led brands; anywhere warmth beats authority.
**Implement:** large `border-radius` (16–32 px), two-layer shadow (contact shadow + soft ambient), subtle inner bevel via inset highlight; pairs with clay-style 3D illustration assets (see [../assets/3d-assets.md](../assets/3d-assets.md)).
**Type, colour, assets:** rounded or soft-geometric typefaces; saturated pastel-to-vivid palettes; clay-rendered 3D characters and icons.
**Mistakes:** clay on dense data surfaces (reads as unserious); shrinking the radii to look "professional" (kills the style); overloading a page — three clay sections are charming, thirty are a toy shop.

### 4.4 Skeuomorphism

**Recognise:** interface elements imitating physical objects — stitched leather, brushed metal, paper texture, literal buttons. The pre-iOS7 paradigm (Forstall era) and current revival corners (notes apps, calendar apps imitating physical deskware).
**Where it works:** nostalgia products, note-taking and journaling apps with an analogue premise, onboarding where a physical metaphor genuinely teaches (a camera app's shutter button).
**Implement:** textured surfaces (see [Texture and period styles](texture-and-period-styles.md)), dimension shadows, material-appropriate detail (stitching, grain, specular highlights). Modern revivals are usually *restrained* skeuomorphism — one physical metaphor, flat elsewhere.
**Type, colour, assets:** period-appropriate type; realistic texture assets; warm palettes.
**Mistakes:** full skeuomorphism in 2026+ without an irony or nostalgia premise; imitating materials the product does not have; heavy texture on text-bearing surfaces.

### 4.5 Brutalism and neo-brutalism

**Recognise:** classic web brutalism (2014–2017): raw HTML honesty — default system fonts, unstyled links, harsh contrast, visible scaffolding. Neo-brutalism (the current commercial wave): hard borders (2–4 px solid black), offset block shadows (`box-shadow: 6px 6px 0 #000`), flat vivid colour blocks, chunky type, zero radius — playfully aggressive rather than raw.
**Where it works:** neo-brutalism suits developer tools, indie products, event sites, Gen-Z-facing brands that want attitude. True brutalism suits art projects and statements.
**Implement:** flat colour fills; 2–3 px borders; offset solid shadows; hover = shadow grows or element translates onto its shadow; no gradients, no blur, no soft shadows.
**Type, colour, assets:** oversized grotesque or mono type; saturated primaries or acid combinations (record the deliberate clash as a decision); halftone or sticker assets fit the vocabulary.
**Mistakes:** neo-brutalism at enterprise density (looks broken, not bold); mixing soft shadows or radii into it (incoherent); forgetting focus states — hard-border buttons need equally hard, visible focus rings ([../accessibility/accessibility-testing.md](../accessibility/accessibility-testing.md)).

### 4.6 Minimalism and maximalism (at interface scale)

**Recognise:** minimalism — few elements, generous whitespace, restrained palette, type-led; maximalism — abundance, layered colour, pattern, mixed type, deliberate density. Theory in [../foundations/principles-of-design.md](../foundations/principles-of-design.md); the interface-scale differences are about *density budgets* and *scroll behaviour*.
**Where it works:** minimalism — products where content is the hero (reading, portfolio, luxury, developer docs); maximalism — culture, music, fashion, editorial, community brands where personality is the product.
**Implement:** minimalist density budgets (see [../layout/spacing-and-proportion.md](../layout/spacing-and-proportion.md)) and one accent; maximalist grids that still keep a spacing scale, a limited palette and one typographic voice per weight class — abundance is curated, not accidental.
**Type, colour, assets:** minimalism lives or dies on typography ([../typography/web-typography.md](../typography/web-typography.md)); maximalism needs a strong art director's hand and consistent image treatment ([../imagery/image-treatment.md](../imagery/image-treatment.md)).
**Mistakes:** minimalism that is actually emptiness (no hierarchy, no content — different from minimalism); maximalism with five typefaces and seven palettes (noise, not abundance); both without a defined content priority.

### 4.7 Bento grids

**Recognise:** modular tile layouts named for Japanese lunch boxes — mixed-size rounded rectangles on a grid, each tile self-contained with its own content type and often its own background; popularised by Apple keynote summaries and portfolio trends (2022–2024).
**Where it works:** feature summaries, product overviews, portfolio and about pages, dashboards where tiles genuinely map to separate concerns.
**Implement:** CSS Grid with explicit column/row spans; consistent radius and gutters from the spacing scale; tiles own their internal padding; mixed tile backgrounds (one accent tile per composition maximum); responsive strategy = reflow spans, not shrink ([../layout/responsive-layouts.md](../layout/responsive-layouts.md)).
**Type, colour, assets:** one tile per page may carry display type or an accent ground; tiles otherwise stay quiet so composition carries the interest; small diagrams and mini-visualisations excel inside tiles ([../information-design/data-visualisation.md](../information-design/data-visualisation.md)).
**Mistakes:** bento as mandatory layout for every page (it suits *summaries*, not narrative pages); 20+ tiles (a wall, not a bento); tiles that need to be read in sequence (bento is non-linear by construction); equal-size everything (kills the rhythm).

### 4.8 Asymmetric and editorial interface layouts

**Recognise:** layouts that deliberately avoid centred symmetrical columns — offset text against full-bleed imagery, overlapping type and image, content blocks at varying scales; the web translation of editorial print design.
**Where it works:** portfolios, fashion, architecture, cultural institutions, long-form editorial products.
**Implement:** grid still rules ([../layout/grid-systems.md](../layout/grid-systems.md)) — asymmetry is *deliberate placement* on the grid, not freeform; overlapping via negative margins or grid layering with explicit z-index; text over image needs a contrast device (solid panel, scrim, or outlined type) ([../imagery/image-treatment.md](../imagery/image-treatment.md)).
**Type, colour, assets:** editorial typography pairs ([../typography/font-pairing.md](../typography/font-pairing.md)); photography-led; restrained colour so composition carries the design.
**Mistakes:** asymmetry without a grid (randomness); text over busy imagery without contrast handling; mobile adaptation that keeps desktop offsets by absolute positioning instead of reflowing.

### 4.9 Liquid and fluid interfaces

**Recognise:** organic motion — blobs, metaballs, gooey filters, draggable physics, fluid page transitions; SVG filters (feGaussianBlur + feColorMatrix contrast trick) and canvas/WebGL fluid sims; the 2024–2025 "liquid glass" wave pushed it mainstream again.
**Where it works:** creative tools, music and culture brands, immersive storytelling, AI products signalling fluidity of the medium.
**Implement:** SVG gooey filter for small elements; canvas/WebGL (WebGL2 or WebGPU fluid simulations — heavy, budget one) for hero moments; motion must be interruptible and reduced-motion safe ([../motion-and-interaction/motion-principles.md](../motion-and-interaction/motion-principles.md)).
**Type, colour, assets:** liquid typography (variable fonts animated along curves; [Texture and period styles](texture-and-period-styles.md) §kinetic) — but never at the cost of legibility; gradients that shift like fluids; render-heavy assets kept to one per page.
**Mistakes:** fluid effects on every scroll (nausea + jank); simulation running off-screen without pausing; fluid type that deforms beyond legibility; shipping the effect without a static fallback.

### 4.10 3D and isometric

**Recognise:** true 3D (perspective, camera, lighting — WebGL/Three.js scenes or rendered stills) versus isometric (fixed oblique projection, no perspective convergence — the "flat 3D" illustration and game tradition).
**Where it works:** 3D — hardware products, spatial/AR-adjacent software, games, configurators; isometric — technical explainers, maps, infrastructure and logistics brands, friendly diagram illustration.
**Implement:** rendered stills or videos of 3D are usually the right engineering answer (see [../assets/3d-assets.md](../assets/3d-assets.md)); interactive WebGL only when interaction is the point; isometric illustration as SVG or commissioned assets; CSS 3D transforms for light UI-level depth only.
**Type, colour, assets:** studio lighting in renders must match the page's lighting direction; isometric palettes are usually limited and flat.
**Mistakes:** WebGL scenes that steal the page's performance budget ([../frontend-engineering/performance.md](../frontend-engineering/performance.md)); 3D as decoration with no interaction payoff; mixing isometric and perspective 3D in one composition (reads as an error).

### 4.11 Generative art

**Recognise:** visuals produced by code — perlin-noise fields, particle systems, algorithmic pattern, unique-at-load compositions; background canvases, hero art, identity systems that generate.
**Where it works:** developer tools, data products, creative agencies, conference identities; anywhere "systems thinking" is part of the brand story.
**Implement:** canvas or WebGL with a fixed seed for reproducibility where needed; parameters exposed as design tokens (density, hue range, velocity); respect reduced motion (static frame) and pause off-screen ([../motion-and-interaction/motion-principles.md](../motion-and-interaction/motion-principles.md)).
**Type, colour, assets:** palette constraints are what make generated output look designed rather than random — constrain hue ranges and value ramps; generated art behind, never on top of, text without contrast handling.
**Mistakes:** unconstrained randomness (visual noise); full-viewport simulations on content pages; generative systems nobody can stop; art that fights the palette tokens.

### 4.12 Motion-led design

**Recognise:** pages whose identity *is* their motion — entrance choreography, scroll-driven reveals, interactive transitions; the site communicates through choreography as much as layout.
**Where it works:** award-style campaign sites, product launches, portfolios with a strong narrative; not enterprise products where users are task-orientated.
**Implement:** motion hierarchy (one hero moment, supporting transitions, quiet micro-interactions — [../motion-and-interaction/motion-principles.md](../motion-and-interaction/motion-principles.md)); scroll effects via GSAP ScrollTrigger or CSS scroll-driven animations ([../motion-and-interaction/scroll-experiences.md](../motion-and-interaction/scroll-experiences.md)); every animation interruptible; reduced-motion renders the static story.
**Type, colour, assets:** kinetic type for the hero moments; restrained palette so motion reads; assets chosen for how they *move* (video, layered stills).
**Mistakes:** motion on everything (no hierarchy); scroll-jacking (stealing scroll control); animations that block reading; performance collapse on mid-range devices.

### 4.13 Data-driven visualisation as style

**Recognise:** interfaces where live data *is* the visual — dense charts, generative dashboards, ambient displays of system state; the aesthetic is information-rich, monospaced accents, precise grids.
**Where it works:** developer tools, analytics products, finance, climate and science communication.
**Implement:** real chart craft — encodings, axes, colour semantics ([../information-design/data-visualisation.md](../information-design/data-visualisation.md)); tabular numerals for figures; dark themes common but not mandatory; update-in-place animations (numbers and bars that move truthfully).
**Type, colour, assets:** mono or low-contrast-gradient sans families; semantic colour tokens ([../colour/palette-development.md](../colour/palette-development.md)); no decorative assets — the data is the imagery.
**Mistakes:** decoration masquerading as data (sparklines of random numbers); colour as sole channel for data categories (CVD failure — [../colour/colour-accessibility.md](../colour/colour-accessibility.md)); one chart library's default theme shipped unconsidered.

### 4.14 Pixel art and ASCII aesthetics

**Recognise:** deliberately low-resolution raster look (pixel sprites, chunky dithering) or text-constituted imagery (ASCII art, terminal typography); digital-native nostalgia and hacker culture.
**Where it works:** developer tools, games and retro-styled products, indie brands with a technical-punk identity.
**Implement:** `image-rendering: pixelated` for scaled pixel assets; pixel fonts at their native multiples only (8/16/32 px) — fractional sizes destroy them; ASCII art as preformatted text or canvas render; CRT-flavour treatments optional ([Texture and period styles](texture-and-period-styles.md)).
**Type, colour, assets:** pixel typefaces (press-start-style) for display only; limited-indexed palettes; dithered gradients ([Texture and period styles](texture-and-period-styles.md) §dithering).
**Mistakes:** pixel fonts for body text (fatigue in a paragraph); resampling pixel art non-integerly (blurry); mixing high-fidelity photography with pixel art without a framing device.

## 5. How it works — choosing

The selection sequence in [Graphic design → Visual styles](../graphic-design/visual-styles.md) §6 applies; interface-scale additions:

1. **Name the material metaphor.** What does the interface imitate — glass, clay, paper, a terminal, a Swiss poster? If the answer is "nothing, it's just modern", the design has no style yet.
2. **Check the product's users and density.** Expert-dense tools tolerate less atmosphere than campaign sites; every style entry's *where it works* exists for this filter.
3. **Budget the performance cost.** Blur, 3D and simulation styles spend GPU; decide the budget before building ([../frontend-engineering/performance.md](../frontend-engineering/performance.md)).
4. **Verify the accessibility path.** Confirm the style can carry 4.5:1 text and visible states; adapt the style (tinted glass, high-contrast neumorphism variant) or move on.
5. **Commit to the vocabulary.** One structural style, its palette behaviour, its radius/shadow language, its motion character — written into tokens ([../design-systems/design-tokens.md](../design-systems/design-tokens.md)) so it survives contact with implementation.

## 6. Decision framework

| Signal in the brief | Strong candidate styles | Reject |
| --- | --- | --- |
| "Premium, calm, trustworthy" | Minimalism, editorial, restrained Swiss | Neo-brutalism, claymorphism, maximalism |
| "Developer, hacker, technical" | Terminal/mono aesthetics, pixel, neo-brutalism, data-driven | Glassmorphism, claymorphism |
| "Warm, friendly, human" | Claymorphism, organic shapes, tactile | Neo-brutalism (unless indie-attitude brief), terminal |
| "Immersive, cinematic, wow" | Glassmorphism over imagery, liquid, motion-led, 3D | Neumorphism, dense bento |
| "Complex product, many features" | Bento summaries, editorial structure, data-driven surfaces | Maximalism, heavy atmosphere styles |
| "Cultural, musical, youthful" | Maximalism, Y2K, risograph flavour, motion-led | Corporate minimalism without a twist |
| "Hardware, spatial, configurator" | 3D, isometric for explainers | Pure flat styles with no depth vocabulary |

## 7. Examples

**Example 1 — glass hero, flat product.** A media company's product page wants atmosphere without losing authority: one glass panel over a single photographic hero (video-adjacent still, saturated but darkened 20%), thin light border, interior content on solid tinted glass that passes 4.5:1; every section below is flat editorial layout in the same typographic system. The style statement is the hero; the product stays sober. This is the "one atmosphere moment" pattern most premium brands actually ship.

**Example 2 — bento feature summary with a data tile.** A developer-tool landing page uses an eight-tile bento: one accent tile with the headline promise, four feature tiles each with a micro-diagram, one live-metrics tile (true data, updating in place), one social-proof tile, one CTA tile. Equal gutters, three distinct tile sizes, one accent ground. Mobile: spans collapse to single column, order preserved by content priority. The composition reads as curated abundance — the summary style — while the product's inner pages stay conventional.

## 8. Common mistakes

- **Style without material logic** — blur and radius applied with no imitated material, producing the generic look the library exists to prevent.
- **Style at war with accessibility** — low-contrast soft styles shipped without adaptation; see the per-style mistakes and [../accessibility/accessible-colour.md](../accessibility/accessible-colour.md).
- **Style without a performance budget** — full-page blur and WebGL on content pages; jank reads as broken, not premium.
- **Mixing structural styles** — glass, clay and brutalist borders in one interface; incoherence the mixing rules exist to prevent.
- **Display styles in working surfaces** — pixel fonts in body text, clay controls in a dense settings page; the style's *where it works* clause was ignored.
- **Fashion without fit** — adopting the current trend style for a product whose users and density reject it; a style is a position about what the product is.

## 9. Evaluation checklist

- [ ] The interface's material metaphor can be named in one sentence.
- [ ] One structural style governs the surface; atmosphere moments are countable and deliberate.
- [ ] Every text/background pair in the style passes contrast, including glass and shadow states.
- [ ] Focus-visible, hover and disabled states exist in the style's own vocabulary (not defaults).
- [ ] Blur/3D/simulation cost is measured against the performance budget; fallbacks exist.
- [ ] Reduced-motion renders the style's static story completely.
- [ ] The style's typography, colour behaviour and asset language are written into tokens.
- [ ] The style matches the brief's users and density (decision framework §6 consulted).

## 10. Related topics

- [Visual styles (classic families and theory)](../graphic-design/visual-styles.md) — the base catalogue and mixing rules.
- [Texture and period styles](texture-and-period-styles.md) — the surface-treatment vocabulary that completes these styles.
- [Art direction](../graphic-design/art-direction.md) — turning a style choice into a defensible direction.
- [Moodboards](../methodology/moodboards.md) — testing the direction before production.
- [Design tokens](../design-systems/design-tokens.md) — encoding the style so it survives implementation.
- [Performance](../frontend-engineering/performance.md) — the budget constraint on atmosphere styles.
- [Motion principles](../motion-and-interaction/motion-principles.md) — the motion-led style's implementation layer.

## 11. References

- This file is a synthesis of documented style practice across design systems, style round-ups and the library's own theory files; style histories are presented as professional knowledge, not sourced claims.
- Apple Human Interface Guidelines, "Materials" — the translucency/material guidance behind glassmorphism practice. https://developer.apple.com/design/human-interface-guidelines/materials [search-verified, accessed 2026-11-25]
- MDN, `backdrop-filter` — the CSS mechanism and its support story. https://developer.mozilla.org/en-US/docs/Web/CSS/backdrop-filter [search-verified, accessed 2026-11-25]
- W3C, WCAG 2.2 — contrast and non-text contrast criteria that bound every style here. [canonical]
- Language note: style names (glassmorphism, Y2K, bento) are used as the industry uses them; where a name is contested (neo-brutalism vs web brutalism) the distinction is stated in the entry.
