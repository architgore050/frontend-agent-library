# Texture and Period Styles

## 1. What is it?

The surface-treatment and period-aesthetic branch of the style vocabulary: textures and print-era techniques (grain, halftone, dithering, duotone, risograph, collage, tactile surfaces), period aesthetics (retro-futurism, Y2K, cyberpunk), the organic-shape family, and the texture vocabulary frontend agents reach for when a design needs atmosphere — fluted glass, thermal gradients, water ripples, speckled graphite, blueprint grids, contour lines and their peers. It also covers the typographic style extensions (rebus, kinetic, experimental, modular typefaces). Interface-structural styles are in [Interface styles](interface-styles.md); the classic families in [Graphic design → Visual styles](../graphic-design/visual-styles.md); repeat-pattern craft in [Patterns and textures](../graphic-design/patterns-and-textures.md).

## 2. Why does it matter?

Surface treatment is what separates a styled page from a styled *brand*: two products can share a layout logic and still be unmistakable because one carries grain and contour lines and the other is clean glass. Textures are also the cheapest distinctiveness available — most are CSS or small SVG/CSS composites, no heavy assets — and they compose well with restrained budgets. The period styles matter because they are the vocabulary agents most often get subtly wrong: Y2K is a specific material culture with specific chrome-and-translucency cues, not "anything shiny"; risograph is a specific printing artefact, not any flat colour. Recognising the actual cues prevents the "close but off" period pastiche that reads as costume.

## 3. Core principles

**Principle 1 — Textures sit behind or around content, never through it.** A texture's job is atmosphere; body text carries no texture. If a texture competes with reading, it fails ([../accessibility/accessible-typography.md](../accessibility/accessible-typography.md) governs the floor).

**Principle 2 — One texture system per identity.** Grain or halftone or blueprint — pick the system and its parameters (density, scale, colours) once, encode as tokens, reuse. Texture soup reads as noise.

**Principle 3 — Period styles need their period's technology logic.** Each period aesthetic imitates the media technology of its time (CRT and chrome for Y2K; risograph's ink drums; cyberpunk's terminal-and-neon city). Correct period cues come from understanding the technology, not from a colour palette alone.

**Principle 4 — Texture is generated first, asset second.** Most textures in this file can be produced with CSS gradients, SVG filters (feTurbulence) or tiny repeating assets — cheaper, sharper and resolution-independent. Use photographic texture assets ([../assets/textures-and-materials.md](../assets/textures-and-materials.md)) when the surface must feel physically photographed.

## 4. The texture techniques

Entry format: **Recognise → Implement → Mistakes.** All are background/surface treatments; each composes with [Interface styles](interface-styles.md) as the page's atmosphere layer.

### 4.1 Grain and noise

**Recognise:** fine film-grain speckle over flat colour or imagery — softens digital flatness, unifies disparate assets, adds print-adjacent warmth; ubiquitous in current editorial and studio sites.
**Implement:** SVG `feTurbulence` (fractalNoise, high baseFrequency ~0.8, slight feColorMatrix desaturation) as a full-bleed overlay at 3–8% opacity, `pointer-events: none`, or a small (128–256 px) pre-rendered noise PNG tiled with `background-repeat`. Static grain only; animated grain is a video effect with a cost.
**Mistakes:** grain over body text (legibility tax); grain at visible strength (>10% opacity reads as dirty screen); animating grain on scroll; grain applied to fix a genuinely bad image treatment.

### 4.2 Halftone

**Recognise:** images or gradients reproduced as dot grids of varying size — the newspaper/comic print artefact; current use is usually display-scale (hero imagery or decorative panels), not body imagery.
**Implement:** CSS radial-gradient repeating backgrounds for pure pattern; SVG filters or pre-processed images for true halftone photography; dot size maps to luminance in authentic halftone. Colour halftone uses offset dot screens per ink — approximated with two offset dot layers in two inks.
**Mistakes:** halftone at small scales (turns to grey mush); halftone over text-bearing areas; mixing authentic (luminance-mapped) and decorative (uniform) halftone in one composition.

### 4.3 Dithering

**Recognise:** the ordered-noise technique from 1-bit and indexed-colour computing — gradients built from dot patterns instead of smooth blends; strong retro-computing signal.
**Implement:** pre-processed assets (true Bayer/ordered dithering in an image editor or via a dithering library at build time); CSS approximation via tiny repeating dot patterns; pairs with pixel aesthetics ([Interface styles](interface-styles.md) §4.14) and indexed palettes.
**Mistakes:** dithered gradients at body-text contrast cost; mixing smooth and dithered gradients in one system without intent; dithering photographic imagery at display scale (use halftone instead).

### 4.4 Duotone

**Recognise:** imagery mapped to exactly two tones — shadows to one colour, highlights to another; the classic editorial photo treatment and the reliable way to make any stock photo family consistent.
**Implement:** CSS `filter: grayscale(1)` plus a two-colour gradient `mix-blend-mode` sandwich (multiply for shadows, screen for highlights), or pre-processing; brand implementation maps the two tones to palette tokens ([../imagery/image-treatment.md](../imagery/image-treatment.md) — the family treatment).
**Mistakes:** duotone that destroys subject recognition (faces must stay readable); duotone pairs with <3:1 separation between the tones; applying it once, to one image, while the rest of the page's photos are untouched.

### 4.5 Risograph aesthetic

**Recognise:** the artefacts of risograph printing — one or two spot inks (fluorescent pink, blue, yellow are the classics), visible misregistration between ink layers, ink texture and roller streaks, halftone grain, overprint colour mixing where inks overlap.
**Where it works:** cultural events, independent publishing, music, zine-culture brands, campaigns wanting print-culture energy.
**Implement:** two-ink palette + paper ground; offset one layer 1–3 px from the other (the misregistration *is* the style); `mix-blend-mode: multiply` for the overprint effect; ink texture via grain (§4.1); halftone (§4.2) for imagery.
**Mistakes:** three or four inks (riso is a spot-colour process — the constraint is the style); perfect registration (kills it); dark saturated grounds (riso lives on light paper); treating it as "flat design with pink".

### 4.6 Collage

**Recognise:** layered cut-paper composition — torn edges, mixed photographic scraps, tape, stamps, handwritten marks; editorial-magazine and punk-print lineage.
**Where it works:** editorial features, music and culture brands, campaign moments, portfolio identity.
**Implement:** layered imagery with torn/rough-edge masks (SVG masks or pre-cut assets), slight rotations, drop shadows for physical lift; handwriting accents as font or SVG; keep a grid underneath so the collage sits in composition ([../layout/grid-systems.md](../layout/grid-systems.md)).
**Mistakes:** collage without a base grid (chaos); too many elements per composition; mixing collage layers with clean rounded-UI cards without a framing device.

### 4.7 Tactile design

**Recognise:** surfaces that imitate physical craft — paper texture, embossed edges, stitching, tape, envelope folds; warmth and materiality without full skeuomorphism ([Interface styles](interface-styles.md) §4.4).
**Where it works:** craft brands, hospitality, stationery-adjacent products, event identities.
**Implement:** paper texture assets or CSS grain, soft key-light shadows, deckle or rough edges via masks; typography that belongs to print (serif display, letterpress feel).
**Mistakes:** tactile texture under dense UI content; combining tactile warmth with terminal-cool accents (identity incoherence); texture stronger than content.

### 4.8 Retro-futurism

**Recognise:** "the future as imagined earlier" — mid-century space-age optimism (1950s–60s: boomerang shapes, starbursts, chrome, atomic patterns) or 1980s-90s techno-optimism (chrome wordmarks, grid horizons, sunset gradients).
**Where it works:** brands with a playful technological premise; campaign sites; entertainment; indie tools signalling "optimism about tools".
**Implement:** period-correct shape vocabulary (starbursts, orbital rings, perspective grids), chrome or gradient-metal type treatments, sunset gradient + horizon grid for the 80s branch; paired with modern usability underneath — the period lives in the visual layer only.
**Mistakes:** mixing mid-century and 80s cues (different periods); period styling on working UI controls; chrome text over busy backgrounds.

### 4.9 Y2K aesthetic

**Recognise:** the late-90s/early-2000s internet-and-bubble-era look — translucent aqua plastic (iMac G3 era), chrome type with lens flares, bubbly rounded forms, techno-optimist brights (cyan, silver, transparent gradients), early-web motifs (under-construction humour, marquee energy), MTV/flash-era gloss.
**Where it works:** fashion and music targeting Gen-Z nostalgia, event identities, playful consumer brands; a strong statement style.
**Implement:** translucent glossy surfaces (glassmorphism's ancestor — [Interface styles](interface-styles.md) §4.1 with bubblier radii), chrome gradient type (metallic vertical gradients + specular band), blobby organic shapes, lens-flare accents; type in rounded techno faces.
**Mistakes:** Y2K without gloss (flat pastels are not Y2K); applying it to serious infrastructure products; overusing flares (one hero moment, not twelve); ignoring that Y2K's translucency has the same contrast obligations as glass.

### 4.10 Cyberpunk

**Recognise:** high-tech-low-life visual language — neon-on-dark (cyan/magenta on near-black), glitch artefacts, terminal and HUD framing, dense city imagery, holographic accents; the Blade Runner/genre lineage rather than any single film.
**Where it works:** gaming, security and hacker-culture tools, night-economy entertainment, sci-fi adjacent products.
**Implement:** dark ground with neon accents used *sparingly* for hierarchy (neon everywhere = no hierarchy), glitch as a dealt moment not a constant ([../motion-and-interaction/motion-principles.md](../motion-and-interaction/motion-principles.md) governs the motion layer), terminal typography for data surfaces, HUD frames for imagery.
**Mistakes:** neon soup; glitch animations that never stop; neon red/blue combinations that fail CVD checks ([../colour/colour-accessibility.md](../colour/colour-accessibility.md)); cyberpunk on a children's product.

### 4.11 Organic shapes

**Recognise:** rounded, irregular, nature-adjacent forms — blobs, waves, petal contours — replacing rectangles as containers, section dividers and image masks; the friendly-geometric counterpoint to grid sharpness.
**Where it works:** wellness, education, sustainability, family products; softening data-heavy brands.
**Implement:** SVG blob paths as masks and section boundaries; consistent curvature character (one blob "handwriting"); animation via subtle morphing ([../motion-and-interaction/motion-principles.md](../motion-and-interaction/motion-principles.md)); keep interior content on readable regular areas.
**Mistakes:** blobs behind body text (irregular contrast paths); every section boundary a different blob family; organic shapes at tiny sizes (mushy edges).

## 5. The texture vocabulary

Background and surface treatments for specific atmospheres. Format: **Cue → Build → Watch for.** These compose with any structural style as the page's atmosphere layer; encode parameters as tokens ([../design-systems/design-tokens.md](../design-systems/design-tokens.md)).

| Texture | Cue | Build | Watch for |
| --- | --- | --- | --- |
| Fluted glass | Vertical ribbed translucency, the 2023–25 interior-design import | Repeating linear-gradient ribs over a blurred layer, or pre-rendered asset; pairs with §4.1 glass | Ribs under text destroy legibility — keep fluting decorative |
| Thermal gradients | Heat-map colour ramps (blue→red) as decorative fields | CSS conic/radial ramp with posterised steps; animate slowly or not at all | Reads as data — never use where real heat-maps appear nearby |
| Water ripples | Refraction rings, interference patterns | SVG turbulence displacement or WebGL; static caustic patterns via layered gradients | Motion ripples must pause off-screen; strong ripples over text |
| Speckled graphite | Charcoal/dark pencil grain, matte mineral | Dark ground + grain (§4.1) + soft white chalk accents; slightly rough borders | Contrast floor on dark grounds ([../accessibility/accessible-colour.md](../accessibility/accessible-colour.md)) |
| Single-hue landscapes | Monochrome photographic terrain, tinted to one hue | Duotone treatment (§4.4) over landscape photography; hue = palette anchor | Subject recognition; hue choice must survive CVD |
| Blueprint grids | Dimensional drafting lines on blue ground | Grid lines + dimension ticks + small annotations in mono type; white/cyan lines on blueprint blue | Decorative annotations must not read as real UI labels |
| Grass / foliage textures | Photographic organic ground | Tiled photographic texture or blurred large-format still; deep depth of field preferred | Busy under text; keep content on solid panels |
| Paper textures | Fibrous matte ground | Paper asset tile or grain (§4.1) in paper tones; deckled edges via masks | Warm paper shifts perceived text colour — verify contrast |
| Contour lines | Topographic map linework | Repeating SVG path set or generated concentric curves; low-contrast single hue | Keep off text areas; one curvature character |
| Cloud and sky backgrounds | Photographic or gradient skies, dawn/dusk drama | Large-format sky stills or layered gradient + blur "clouds"; pairs with glass panels | Skies shift all day — pick the time of day deliberately; text over bright sky needs scrim |
| Pixel mosaics | Colour-blocked tile fields, mosaic murals | CSS grid of colour cells or pre-rendered tile sheet; one mosaic grammar per page | Too many colours = noise; cells must not read as UI |
| Lens distortion | Optical imperfection as style — chromatic aberration, barrel warp | RGB-split text shadows, subtle radial distortion on imagery via filter/SVG | Strong distortion on text = illegible; one dealt moment |
| Stippled gradients | Gradients rendered as dot density | Dot pattern with varying density via SVG pattern or canvas; pairs with dithering (§4.3) | Dot scale too fine = grey mush at 1× DPR |
| Square-dot grids | Engineering-paper dot fields | `background-image: radial-gradient(circle, token 1px, transparent 1px)` on square repeat | Ensure dots stay below 4.5:1 interference with overlaid text |

## 6. Typographic style extensions

- **Rebus typography** — type that substitutes pictograms or images for syllables (the "rebus puzzle" mechanic); display-moments only, with an accessible text alternative carrying the full reading ([../accessibility/accessible-typography.md](../accessibility/accessible-typography.md)).
- **Kinetic typography** — type animated along its meaning: entrance choreography, variable-font weight/width animation, scroll-driven type reveals. Governed by [../motion-and-interaction/motion-principles.md](../motion-and-interaction/motion-principles.md); implemented with variable fonts ([../typography/web-typography.md](../typography/web-typography.md)) and GSAP/Motion ([../motion-and-interaction/animation-libraries.md](../motion-and-interaction/animation-libraries.md)). Legibility floor: the word must be readable in its final state, and under reduced motion the static version carries the same content.
- **Experimental typography** — grid-breaking type compositions: rotated baselines, mixed sizes, outlined and filled pairs, type as image. Works in editorial and portfolio contexts; requires the accessible-name discipline (real text nodes, aria labels for image-constituted type) and a conventional fallback in reading surfaces.
- **Modular typefaces** — construction-system fonts (letters built from visible modules, stencils, grids); strong technical identity for display; pair with a neutral workhorse for body ([../typography/font-pairing.md](../typography/font-pairing.md)).

## 7. How it works — combining

Atmosphere layers stack in this order: **ground** (paper, sky, graphite, dot field) → **atmosphere texture** (grain, halftone, contour) → **period/style layer** (Y2K gloss, riso inks, cyberpunk neon) → **content** (flat, clean, untextured). Each layer below content sits at lower contrast; content itself carries no texture. One period layer per identity; textures may combine (grain over paper is canonical; halftone + dithering in one composition is a fight). The combination is written into tokens: ground token, grain-opacity token, accent-ink tokens.

## 8. Decision framework

| Atmosphere wanted | Ground | Texture layer | Period/style layer |
| --- | --- | --- | --- |
| Print-culture, independent | Warm paper | Grain + halftone | Risograph (2 inks, misregistration) |
| Tech-optimist, playful | Bright white or aqua | Glossy translucency | Y2K (chrome type, blobs, flare) |
| Dark, technical, nocturnal | Near-black | Dot grid or contour, faint | Cyberpunk (neon accents, HUD frames) |
| Craft, hospitality | Paper | Grain, deckle edges | Tactile (stitching, tape accents) |
| Nature, wellness, soft | Tinted white | Organic blob masks, cloud stills | Organic shapes |
| Editorial, magazine | Paper white | Grain, duotone imagery | Collage accents in features |
| Optimist-tech campaign | Silver/white | Chrome gradients | Retro-futurism (era chosen deliberately) |

Reject the whole table if the product's working surfaces are dense and expert-facing — carry atmosphere to marketing surfaces only, keep the product sober.

## 9. Examples

**Example 1 — a festival identity carrying risograph to the web.** Two spot inks (fluorescent pink + blue) on warm paper ground; grain at 5% over everything except text blocks; hero typography offset-printed (two text layers in the two inks, misregistered 2 px, `mix-blend-mode: multiply`); photography duotoned to the two inks; section boundaries as torn-edge masks. Every texture parameter (grain opacity, misregistration distance, ink hex values) is a token. Result: the web page reads as printed matter — the identity travels across print and web because the artefacts, not just the colours, travelled.

**Example 2 — cyberpunk product page with hierarchy intact.** Near-black ground; one neon cyan accent reserved for interactive affordances; one magenta accent for warnings only; terminal mono for data chips; a single glitch moment on the hero headline entrance (500 ms, interruptible, static under reduced motion); HUD corner frames on screenshots. The failure it avoids: neon applied to everything, which flattens hierarchy and fails contrast — the accents' scarcity is what makes the style work.

## 10. Common mistakes

- **Texture through content** — grain, fluting or halftone under body text; the atmosphere tax became a legibility defect.
- **Period without technology logic** — Y2K as "pastel blobs", risograph without misregistration, cyberpunk without scarcity of neon: close-but-off pastiche.
- **Texture soup** — several competing texture systems on one page; grain + halftone + contour + dot grid reads as noise.
- **Unbounded texture parameters** — grain at 15%, misregistration at 8 px, flares everywhere; textures need budgets like motion does.
- **Atmosphere on working surfaces** — dense expert tools carrying full texture stacks; atmosphere belongs to marketing and moment surfaces.
- **Contrast assumptions** — warm paper and dark graphite both shift perceived text contrast; every texture/ink pair is measured ([../accessibility/accessible-colour.md](../accessibility/accessible-colour.md)).

## 11. Evaluation checklist

- [ ] One texture system with tokenised parameters (density, opacity, colours) governs the identity.
- [ ] No texture overlays body text; contrast measured on textured grounds, not assumed.
- [ ] Period styles carry their technology artefacts (misregistration, gloss, glitch budgets), not just palettes.
- [ ] Layer order respected: ground → atmosphere → period layer → clean content.
- [ ] Texture cost bounded: no animated grain/ripples without pause and reduced-motion handling.
- [ ] Decorative annotations (blueprint ticks, contour labels) cannot be mistaken for real UI text.
- [ ] The atmosphere is absent or minimal on dense working surfaces.

## 12. Related topics

- [Interface styles](interface-styles.md) — the structural styles these textures complete.
- [Visual styles (classic families)](../graphic-design/visual-styles.md) — theory, lifecycle and mixing rules.
- [Patterns and textures](../graphic-design/patterns-and-textures.md) — repeat-pattern construction craft.
- [Image treatment](../imagery/image-treatment.md) — duotone and family treatment for photography.
- [Assets: textures and materials](../assets/textures-and-materials.md) — where to source photographic textures.
- [Motion principles](../motion-and-interaction/motion-principles.md) — governing kinetic typography and glitch budgets.
- [Accessible colour](../accessibility/accessible-colour.md) — the contrast floor every texture/ink pair must meet.

## 13. References

- This file is a synthesis of documented style practice and the library's own theory files; period attributions are professional knowledge, not sourced claims.
- MDN, SVG filter effects (`feTurbulence`, `feColorMatrix`) — the grain/gooey mechanism. https://developer.mozilla.org/en-US/docs/Web/SVG/Element/feTurbulence [search-verified, accessed 2026-11-25]
- MDN, `mix-blend-mode` — the overprint/duotone mechanism. https://developer.mozilla.org/en-US/docs/Web/CSS/mix-blend-mode [search-verified, accessed 2026-11-25]
- Risograph printing artefacts (spot inks, misregistration, overprint) — described from print-culture practice; see riso studio documentation for working examples. [canonical]
- W3C, WCAG 2.2 — contrast criteria bounding every treatment here. [canonical]
