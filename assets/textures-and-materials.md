# Textures and Materials Sources

## 1. What is it?

Where to source physical surface textures — paper, grain, fabric, wood, stone, plaster, metal — for the tactile and period styles documented in [../visual-styles/texture-and-period-styles.md](../visual-styles/texture-and-period-styles.md): verified sources, licence positions, seamless-tiling craft, and the performance discipline textures need. Repeat-pattern *construction* (designing your own) is [Patterns and textures](../graphic-design/patterns-and-textures.md); generated procedural backgrounds are [backgrounds-and-effects.md](backgrounds-and-effects.md).

## 2. Why does it matter?

Textures are the cheapest atmosphere available — a good paper texture is a few tens of kilobytes and transforms a page's perceived materiality ([Texture and period styles](../visual-styles/texture-and-period-styles.md) §5). But they are also the asset class most often shipped badly: visible seams, 8 MB photographic scans, textures under text, and licence assumptions from "I found it on Google Images" — which is not a source. This file exists so texture acquisition is legal, technical and design-literate.

## 3. The sources

### 3.1 Poly Haven textures — https://polyhaven.com/ [accessed 2026-11-25]

**Provides:** the public-asset project's texture library (with its 3D models and HDRIs — see [3d-assets.md](3d-assets.md)): physically accurate, seamless, multi-map (albedo/normal/roughness/AO) PBR textures.
**Licence:** CC0 1.0 (public domain) — the cleanest licence in asset sourcing; no attribution required, commercial use free. (The project survives on donations; crediting is appreciated but not owed.)
**Craft:** download the map set appropriate to the surface; the albedo map is usually what web surfaces need (the full PBR set is for WebGL materials — pair with [../motion-and-interaction/animation-libraries.md](../motion-and-interaction/animation-libraries.md) for three.js usage).
**Limits:** physically-real surfaces (real wood, real brick) — not stylised/print textures.

### 3.2 ambientCG — https://ambientcg.com/ [accessed 2026-11-25; connect failed from this sandbox at fetch time — status recorded as search-verified]

**Provides:** a very large CC0 PBR texture library (materials, surfaces, scenery) with multiple resolutions and map bundles.
**Licence:** CC0 1.0.
**Craft:** resolution tiers are the feature — take the tier matching rendered size, not the max; the LDR JPEG bundle is enough for most web surfaces.
**Limits:** same physical-realism skew as Poly Haven; enormous catalogue rewards specific searches ("painted plaster wall", "kraft paper").

### 3.3 Texturelabs — https://texturelabs.org/ [accessed 2026-11-25]

**Provides:** studio-grade photographic textures by Greg Vassilakos aimed at *design* use — paper, cardboard, ink, grain, grunge, fabric — pre-toned and immediately usable as design surfaces.
**Licence:** free for commercial use under Texturelabs' licence terms (verify the current page; attribution appreciated, not required).
**Craft:** this is the design-flavoured source — riso, paper, photocopy and ink textures that the print-culture styles need directly ([../visual-styles/texture-and-period-styles.md](../visual-styles/texture-and-period-styles.md) §4.5–4.7).
**Limits:** single-image textures (tile-ability varies — check before use as a repeating ground).

### 3.4 Procedural first (a reminder, not a source)

Grain, noise, halftone, dot grids, contour lines, blueprint grids and most *subtle* textures should be generated in CSS/SVG ([../visual-styles/texture-and-period-styles.md](../visual-styles/texture-and-period-styles.md) §3 principle 4 — `feTurbulence`, gradients, repeating patterns). Photographic sources are for surfaces that must feel *physically photographed*; procedural for everything else. Generated = resolution-independent, palette-exact and weight-free.

## 4. The comparison table

| Source | Licence | Attribution | Character | Best for |
| --- | --- | --- | --- | --- |
| Poly Haven textures | CC0 | None (appreciated) | Physical, PBR-accurate | Real-material surfaces; WebGL material maps |
| ambientCG | CC0 | None | Physical, huge catalogue | Specific material searches |
| Texturelabs | free-commercial (verify page) | Appreciated | Design-toned (paper/ink/grain) | Print-culture, tactile, riso styles |
| Procedural (CSS/SVG) | n/a (yours) | n/a | Abstract, palette-exact | Grain, dots, lines, grids, halftone |

## 5. Practical workflow

1. **Decide procedural vs photographic** per texture need (rule: if it can be one gradient/filter away from flat colour, generate it).
2. **Search specifically** ("translucent tracing paper", "rough concrete block", "carbon fibre") — texture searches reward specificity like photography searches do.
3. **Check tile-ability** for repeating grounds: load, tile 2×2, look for seams; non-tileable textures become large single surfaces (hero backgrounds) instead of repeats.
4. **Size to rendered use** — a texture tiled at 300 px needs no 8K source; resize and compress (WebP/AVIF; textures compress beautifully) per [../frontend-engineering/performance.md](../frontend-engineering/performance.md) §5.1.
5. **Contrast-check under text** — every texture that hosts text is measured ([../accessibility/accessible-colour.md](../accessibility/accessible-colour.md)); textures under text stay low-contrast ([../visual-styles/texture-and-period-styles.md](../visual-styles/texture-and-period-styles.md) §3 principle 1).
6. **Record the manifest entry** (source URL, licence, date) ([licensing-and-provenance.md](licensing-and-provenance.md)).

## 6. Common mistakes

- **Google Images as a source** — licence-unknown, resolution-unknown; the two CC0 libraries exist precisely so nobody does this.
- **Visible seams** — tile-ability unchecked; the tell of amateur texture work.
- **8K texture shipped for a 300 px tile** — the page-weight leak that is pure waste.
- **Texture under text at legibility cost** — grain at >10% opacity, busy paper under body text.
- **Photographic where procedural suffices** — weight and palette drift for what one CSS filter would do.

## 7. Evaluation checklist

- [ ] Procedural option considered first for subtle textures.
- [ ] Source licence verified (CC0 pages or Texturelabs terms) at integration; manifest recorded.
- [ ] Tile-ability checked (2×2 seam test) for repeating grounds.
- [ ] Asset sized/compressed to rendered use; format modern.
- [ ] Contrast measured under text-bearing areas.
- [ ] The texture's character matches the style system (one texture grammar per project — [../visual-styles/texture-and-period-styles.md](../visual-styles/texture-and-period-styles.md) §3).

## 8. Related topics

- [Textures and period styles](../visual-styles/texture-and-period-styles.md) — the style layer these sources serve.
- [Patterns and textures](../graphic-design/patterns-and-textures.md) — constructing repeats yourself.
- [3D assets](3d-assets.md) — Poly Haven's models and HDRI siblings.
- [Licensing and provenance](licensing-and-provenance.md) — the manifest.
- [Performance](../frontend-engineering/performance.md) — the optimisation half.

## 9. References

- Poly Haven licence (CC0) — https://polyhaven.com/faq [accessed 2026-11-25]
- ambientCG licence (CC0) — https://ambientcg.com/learn/legal [search-verified, accessed 2026-11-25; direct fetch failed from this sandbox — recorded honestly]
- Texturelabs terms — https://texturelabs.org/ [accessed 2026-11-25]
- CC0 1.0 legal text — Creative Commons. https://creativecommons.org/publicdomain/zero/1.0/ [canonical]
