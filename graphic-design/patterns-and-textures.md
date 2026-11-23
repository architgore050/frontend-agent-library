# Patterns and Textures

## 1. What is it?

A pattern is a graphic element repeated according to a rule until it fills a surface: a dot grid behind a hero image, a tiled monogram wallpaper, a diagonal stripe band. A texture is a surface quality — grain, noise, paper, halftone — that changes how a surface feels without adding figurative content. Both are vocabulary elements of the graphic language (see [Graphic language](graphic-language.md), element catalogue), and both do the same job: they fill large areas with brand identity at zero content cost, so that even an empty panel, a book cover, a phone wallpaper or a stage backdrop reads as the brand.

This file owns the construction of patterns from brand geometry, the tiling and scale rules that make them work, the hierarchy between hero and support patterns, dark/light variants, accessibility considerations, and the technical implementation in SVG and CSS. The choice of *which* patterns exist is a graphic-language decision; this file is the craft of making those patterns work.

## 2. Why does it matter?

**Patterns are identity density.** A logo appears once per artefact; a pattern covers square metres. On wallpapers, packaging interiors, tote bags, badge ribbons, website backgrounds and presentation masters, the pattern is often the largest single brand surface present — which makes it either the biggest recognition win or the biggest incoherence risk in the whole system. A well-built pattern keeps working at every size from favicon-scale to billboard; a badly tiled one shows seams, moiré, banding or arbitrary drift the moment it is scaled.

**Textures set tone without words.** The same layout with a paper grain reads handmade; with a halftone screen reads retro-print; with glass blur reads digital. Because texture is felt before it is analysed, it is the fastest tonal lever in the vocabulary — and the easiest to over-apply, which is why intensity rules (section 4.4) are non-negotiable.

## 3. Core principles

### 3.1 Derivation from brand geometry

A brand pattern should be *built from* the brand's own elements, not selected from a library of pretty repeats. The construction chain: take a vocabulary element (motif, shape, line — derived per [Graphic language](graphic-language.md) and, where the source is a fixed logo, [Fixed logo analysis](../branding/fixed-logo-analysis.md)); simplify it to its silhouette; decide the repeat rule; test at target scales. A pattern derived this way passes the ownership test of the graphic language automatically, and the family of patterns (often three to five tiles) stays visibly related because they share the same parent geometry.

### 3.2 One motif, many patterns

Professional systems prefer one parent motif rendered at several densities and scales over several unrelated motifs. The set might be: a statement large-scale version, a support medium version, and a whisper-fine version — all visibly the same family. This gives layouts a full value range (bold to nearly invisible) while keeping one idea, which is both cheaper to maintain and stronger in recognition. Multiple unrelated patterns compete with content and with each other, and each new motif dilutes the brand's claim on its geometry.

### 3.3 Patterns obey hierarchy

Patterns are tiered like every other element (hero/support/accent in [Graphic language](graphic-language.md)): a *hero* pattern may dominate a cover or backdrop; *support* patterns sit behind content at low contrast and never compete with text; *accent* uses are small defined patches (divider strips, badge fills, endpapers). The hierarchy answers the practical question every layout asks — "how loud may this surface be?" — with a rule instead of a mood.

### 3.4 Patterns serve layout, never fight it

A pattern's first obligation is to the content it hosts: it must never reduce legibility, compete with focal points, or push the eye harder than the composition intends (the perceptual principles are covered in [Gestalt and perception](../foundations/gestalt-and-perception.md) and [Composition](../foundations/composition.md)). Practically, that means the pattern's visual frequency and contrast are chosen *after* the layout's density is known — the same tile that is support-tier behind a sparse hero is whisper-tier behind a dense table. Direction assigns the tier per surface (see [Art direction](art-direction.md), register assignment); construction makes the assignment technically possible by building the intensity ladder (4.4) into every tile.

## 4. How it works

### 4.1 Constructing the tile

A repeatable tile is engineered, not drawn loosely. The working sequence:

1. **Choose the unit.** Extract the simplest state of the motif: a dot, a slash, a ring, a quarter-arc.
2. **Choose the repeat type** (section 4.2) and place unit copies on the tile so that edges match.
3. **Make edges seamless.** Elements crossing a tile edge must cross every edge it meets with identical continuation — draw half at each edge, or design the unit to avoid edge crossings entirely.
4. **Simplify to silhouette** for small scales: a pattern that needs interior detail will muddy when scaled down; keep a simplified variant for fine sizes.
5. **Test the three scales** (section 4.3) before approving the tile.

### 4.2 Tiling rules

| Repeat | Behaviour | Use |
| --- | --- | --- |
| Grid (straight) | Rows and columns aligned | Orderly, technical brands; easy to build |
| Half-drop | Alternate columns shifted by half the tile height | Hides visible rows; organic-feeling rhythm |
| Brick | Alternate rows shifted by half the tile width | The horizontal twin of half-drop |
| Mirror | Tiles alternate flipped | Zero edge mismatch by construction; can create kaleidoscope artefacts |
| Rotation (e.g. quarter-turn) | Tiles rotate per cell | Dynamic; watch for motion-like moiré at scale |
| Scatter (irregular) | Hand-placed variation, larger tile footprint | Natural, playful; needs a big tile (e.g. 4×4 units) to avoid visible repetition |

Conventional guidance, not laws: scatter and half-drop hide repetition best; grid repeats show their grid at large scales (which may be exactly the point for a technical brand). Mirrored repeats are the cheapest seamless construction and the first to read as "wallpaper kaleidoscope" — check a full-screen mock before committing.

### 4.3 Scale rules

Patterns must be designed against their deployment sizes:

- **Statement scale.** Motif large relative to the surface (one to a few repeats visible). For covers, backdrops, packaging faces. Detail must survive enlargement; edges must be crisp.
- **Support scale.** Repeats small but individually legible (10–30 per screen-width, conventional). The workhorse for section backgrounds and panels.
- **Whisper scale.** Repeats so small the pattern reads as texture; individual motifs nearly merge. Must be built from the simplified silhouette or it renders as noise.

Rules of thumb (conventional starting points — verify per medium): a pattern behind body text must sit well below text contrast and lose all internal detail; a pattern's tile at 50% scale should still look intentional, not broken; printing tiny repeats demands vector or very high raster resolution to avoid moiré.

### 4.4 Subtle versus statement; intensity rules

Define both modes in the ruleset, with numbers:

- **Statement patterns** run at full contrast and are rationed by surface (covers, backdrops, dedicated bands) — never behind body text.
- **Subtle patterns** run at reduced contrast: conventional opacities are 8–24% of the foreground colour on its background, chosen so the pattern never crosses the readability threshold of the text it hosts (see [Colour accessibility](../colour/colour-accessibility.md) for measuring).
- **Textures** (grain, halftone, noise) are specified by opacity band too: subtle 3–8%, deliberate 15–25% (conventional). Never on body-text surfaces.

The intensity ladder lets one tile serve many surfaces legally: full-strength statement, 50% band, 24% support, 8% whisper.

### 4.5 Pattern hierarchies

A complete pattern system defines, per tile: its tier (hero/support), its sanctioned scales, its colourways (palette tokens only — see [Palette development](../colour/palette-development.md)), its dark/light variants (section 4.6), and its keep-clear rules (never under body text, under the logo exclusion zone, or across faces in photography). One page can hold the whole policy; the format mirrors the graphic-language ruleset (see [Graphic language](graphic-language.md), section 4.2).

### 4.6 Dark and light variants

Invert deliberately, not mechanically. A dark-mode pattern usually needs: line/fill colours swapped to dark-palette tokens, opacity rebalanced (glow-like patterns read brighter on dark), and sometimes a simplified silhouette (fine detail becomes shimmer on dark screens). Two acceptable policies: (a) token-driven — the tile references palette variables, so dark mode resolves automatically (see [Colour in code](../colour/colour-in-code.md)); (b) explicit variant files — `pattern-rings-light.svg` and `pattern-rings-dark.svg`, paired and versioned together. Policy (a) is preferable where possible because new colourways cost nothing.

### 4.7 Accessibility considerations

- **Contrast.** A pattern that carries meaning (a legend fill, a zone code in wayfinding) is a graphical object and must meet 3:1 against adjacent colours; purely decorative patterns are exempt but must not interfere with content contrast (W3C guidance [accessed] — see [WCAG fundamentals](../accessibility/wcag-fundamentals.md)).
- **Reading interference.** Patterns behind text must stay far below the text/background contrast and avoid frequencies that shimmer (fine regular repeats near screen pixel pitches). Test body text over every support pattern at real sizes.
- **Motion sensitivity.** Animated patterns (scrolling, pulsing) must honour reduced-motion preferences with a static fallback (see [WCAG fundamentals](../accessibility/wcag-fundamentals.md)).
- **Redundancy.** Never encode meaning in pattern alone; pair with labels or shape changes, per the redundant-cue principle.

## 5. Practical application

### 5.1 Building a pattern family from brand geometry

The standard build for an event or organisation kit (the fixed-logo case):

1. Extract the motif per the graphic-language derivation method (e.g. the 45° cut, the ring, the dot from logo construction).
2. Build three tiles: statement (large motif, grid or scatter repeat), support (half-drop, medium), whisper (simplified silhouette, dense grid).
3. Assign colourways from palette tokens: one primary, one secondary, one single-colour-for-textures.
4. Write the policy page (tier, scales, colourways, dark variants, keep-clear rules).
5. Implement as SVG tiles with CSS consumption (section 5.2), and test on the five hardest surfaces: poster background, body-text page, dark-mode panel, small print (badge), large print (backdrop).

### 5.2 Implementation: SVG and CSS

SVG tiles scale losslessly and restyle via tokens; CSS consumes them without further tooling. A minimal production pattern:

```html
<!-- tile: pattern-rings.svg — support tier; half-drop; single colour -->
<svg xmlns="http://www.w3.org/2000/svg" width="48" height="48" viewBox="0 0 48 48">
  <!-- unit ring, duplicated at edges for seamless wrap -->
  <g fill="none" stroke="currentColor" stroke-width="2">
    <circle cx="0"  cy="0"  r="10"/>
    <circle cx="48" cy="0"  r="10"/>
    <circle cx="0"  cy="48" r="10"/>
    <circle cx="48" cy="48" r="10"/>
    <circle cx="24" cy="24" r="10"/>
  </g>
</svg>
```

```css
/* Consuming the tile; colour via currentColor keeps it token-driven */
.panel--rings {
  background-image: url("pattern-rings.svg");
  background-repeat: repeat;
  background-size: 48px 48px;   /* scale control lives here */
  color: var(--pattern-ink);    /* palette token; dark mode re-resolves */
}
.panel--rings--support { color: color-mix(in srgb, var(--pattern-ink) 24%, transparent); }
```

Notes: `currentColor` lets one SVG serve all colourways; `background-size` is the scale dial; for edge-crossing geometry, duplicate units at all four corners as above so the wrap is seamless; for raster textures, export PNG at 2× the largest deployment size. CSS gradient-based patterns (repeating-linear-gradient, radial dot fields) are a legitimate zero-asset alternative for whisper scales — see [Colour in code](../colour/colour-in-code.md).

### 5.3 Print and merchandise

Patterns for print: prefer vector (PDF/EPS/SVG-derived) for any repeat that scales; check the printer's minimum line weight; watch moiré from fine regular repeats interacting with halftone screens (rotate the pattern or coarsen it); for fabric and merchandise, request a physical test print — screen colours do not promise textile results.

### 5.4 Naming and versioning

Patterns are assets like any other and need the same library discipline as icons and illustrations: name by tier and motif (`pattern-rings-statement.svg`, `pattern-rings-support-dark.svg`), keep one source of truth with exports as build artefacts, record colourway and density changes in a change log, and pair every light/dark variant so they version together (section 4.6). When a tile is retired, deprecate rather than delete, so live artefacts are visibly flagged instead of silently breaking.

## 6. Decision framework

**Pattern or plain surface?** Default to plain unless the surface needs identity without content: empty areas, packaging interiors, covers, dividers. A pattern adds value when it *does a job* — filling dead space with recognition, signalling a surface's role (e.g. every aside panel wears the whisper pattern), or marking a special state (celebration endpapers). If the surface carries dense content, a pattern's job is to be nearly invisible or to not exist.

**Which tier on which surface?**

| Surface | Tier | Intensity |
| --- | --- | --- |
| Covers, key visuals, stage backdrops, packaging faces | Hero | Statement |
| Section backgrounds, aside panels, dividers, badge fills | Support | Subtle (conventional 8–24%) |
| Body-text surfaces, forms, tables | None or whisper | Texture ≤8%; never competes with text |
| Dark-mode surfaces | Variant of the same tile | Rebalanced per 4.6 |

**How many patterns?** One parent motif, three to five tiles (statement, support, whisper, plus optional texture) covers nearly every need. Add a second motif only for multi-brand families (e.g. per-event sub-identities), where each event owns one motif inside a shared structural system.

## 7. Examples

**Token-driven family (illustrative composite).** An event brand derives a ring motif from its logo's circular counter. Three tiles — statement rings at grid repeat, support rings at half-drop, whisper dots — all implemented with `currentColor` and palette tokens. Dark mode and the campaign recolour resolve automatically; the whole family is four small files and one policy page, and every future surface consumes it without new decisions.

**Texture as tone (illustrative composite).** A heritage-themed event applies an 8% paper grain to all print grounds and a 20% halftone treatment to photography edges — two textures, specified by opacity band, never under body text. The textures pass the language audit because they are enumerated in the ruleset rather than improvised per artefact (method per [Graphic language](graphic-language.md)).

**The pattern-policy pattern [accessed context].** Atlassian's design system includes "ambient pattern" as a named role for background texture that carries brand personality in areas needing no specific imagery [accessed] — the role-based thinking this file applies at construction level.

## 8. Common mistakes

- **Seams and misalignment.** Tiles whose edge geometry does not continue; visible tiling seams at any scale. Correction: duplicate edge-crossing units at corners (5.2) or use mirror repeats; test at full-screen scale.
- **Imported patterns.** Stock wallpapers unrelated to brand geometry; identity leaks to whoever else bought them. Correction: derive from brand geometry (3.1) or re-build the stock idea from own elements.
- **Too many motifs.** Five unrelated patterns in one kit; no family resemblance. Correction: one parent motif, many renderings.
- **Pattern behind text.** Support patterns too strong; body text shimmers and fatigues. Correction: intensity rules (4.4); test reading over every pattern.
- **Raster at any scale.** Raster tiles scaled past their resolution; blur and moiré. Correction: vector for scalable surfaces; explicit export sizes for raster.
- **Dark mode by inversion. `filter: invert()` on a textured pattern looks broken.** Correction: token-driven colour or explicit dark variants (4.6).
- **Meaning-carrying patterns failing contrast.** Legend fills or zone codes below 3:1. Correction: treat as graphical objects per W3C [accessed]; fix palette.

## 9. Evaluation checklist

- [ ] Every tile traces to brand geometry and is listed in the pattern policy with tier, scales and colourways.
- [ ] Tiles wrap seamlessly at statement, support and whisper scales (verified on-screen and in print).
- [ ] Subtle intensities stay within the sanctioned opacity bands and never cross text readability.
- [ ] Dark/light behaviour is token-driven or explicitly paired, and tested in both modes.
- [ ] Meaning-carrying pattern elements meet 3:1 contrast; decorative ones carry no meaning alone.
- [ ] Animated patterns have reduced-motion static fallbacks.
- [ ] Implementation uses SVG/tokens per the spec; file naming follows the system.
- [ ] The five hard surfaces (poster, text page, dark panel, small print, large print) all render correctly.

## 10. Related topics

- [Graphic language](graphic-language.md) — the ruleset patterns belong to; motif derivation.
- [Art direction](art-direction.md) — deciding where patterns are loud or silent.
- [Fixed logo analysis](../branding/fixed-logo-analysis.md) — extracting geometry from a fixed logo.
- [Palette development](../colour/palette-development.md) and [Colour in code](../colour/colour-in-code.md) — colourways and token-driven implementation.
- [Colour accessibility](../colour/colour-accessibility.md) and [WCAG fundamentals](../accessibility/wcag-fundamentals.md) — contrast and reduced-motion obligations.
- [Illustration](illustration.md) — ambient illustration as a pattern-adjacent role.

## 11. References

- W3C WAI, "Understanding Success Criterion 1.4.11: Non-text Contrast" — 3:1 for meaningful graphical objects; decorative and redundant graphics exempt. https://www.w3.org/WAI/WCAG21/Understanding/non-text-contrast.html [accessed 2026-11-23]
- Atlassian Design System, "Illustrations" — ambient pattern as a named background/brand-personality role. https://atlassian.design/foundations/illustrations [accessed 2026-11-23]
- Material Design 1 specification (mirror), "Icons" — source of the seam-safe edge-duplication habit in tile construction practice. https://www.mdui.org/en/design/1/style/icons.html [accessed 2026-11-23] (used here only as construction precedent)
- Synthesis note: tiling types, scale bands and opacity conventions in sections 4–5 are conventional professional starting points, presented as this project's synthesis of pattern-design practice; verify specific production numbers against the target medium.
