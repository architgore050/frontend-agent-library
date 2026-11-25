# 3D Asset Sources

## 1. What is it?

Verified sources for 3D models, HDRI environments and rendered stills — the input layer for the [3D and isometric style](../visual-styles/interface-styles.md) §4.10, product renders, and WebGL scenes: what each source provides, licence positions, format/optimisation reality, and when a rendered still beats a live scene. The decision of whether 3D belongs at all is [Interface styles](../visual-styles/interface-styles.md) §4.10 and the performance filter in [../frontend-engineering/performance.md](../frontend-engineering/performance.md); generation of custom renders is [image-generation.md](image-generation.md) and the [AI image generation](../imagery/ai-image-generation.md) craft.

## 2. Why does it matter?

3D is where asset licensing mistakes and page-weight disasters concentrate together: a glamour-shot GLB can weigh more than the rest of the page, and a non-commercial-licensed model shipped in a product is a real legal exposure. The CC0 ecosystem documented below exists so agents never have to touch licence-unknown models, and the still-vs-live rule keeps the weight honest: for most product pages, a compressed rendered image *is* the right 3D deliverable, and the live scene is the exception that must justify itself.

## 3. The sources

### 3.1 Poly Haven — https://polyhaven.com/ [accessed 2026-11-25]

**Provides:** the flagship CC0 3D ecosystem: models (GLTF/GLB), HDRI environment maps, textures (see [textures-and-materials.md](textures-and-materials.md)) — all physically accurate, all public domain.
**Licence:** CC0 1.0 — no attribution owed, commercial use free.
**Craft:** HDRIs are the quiet star — a proper environment map lifts any three.js/R3F scene's lighting from "programmer default" to "studio quality" ([../motion-and-interaction/animation-libraries.md](../motion-and-interaction/animation-libraries.md) §4.5). Download resolution tiers to need; HDRI .exr/.hdr files are heavy — pick the smallest usable tier.
**Limits:** physical realism focus; no stylised/game-ready cartoon sets.

### 3.2 Poly Pizza — https://poly.pizza/ [accessed 2026-11-25; 403 to automated fetches — browser access]

**Provides:** a searchable catalogue of low-poly models (aggregating Google Poly-era CC-BY assets and KitBash collections), with a consistent friendly-geometric aesthetic.
**Licence:** per-model — mostly CC-BY (attribution required, recorded per model) and some CC0; **the attribution-per-model rule makes this the manifest-heaviest source — read each model's licence before shipping.**
**Craft:** perfect for the isometric/explainer style ([../visual-styles/interface-styles.md](../visual-styles/interface-styles.md) §4.10): low-poly renders fast, looks intentional, ships light. Build one scene grammar (camera, lighting, palette) per project and render all models through it.
**Limits:** quality varies per upload; verify geometry and licence per model.

### 3.3 Sketchfab (free filter) — https://sketchfab.com/ [accessed 2026-11-25]

**Provides:** the large 3D marketplace; a downloadable-models filter with per-model licence display (CC licences and Sketchfab Standard non-commercial terms are mixed — read per model).
**Craft:** use as a *discovery* surface; prefer CC0/CC-BY models; the non-commercial filter is a trap for product use — filter to CC licences explicitly.
**Limits:** mixed licensing makes it the source needing the most care; verify every download.

### 3.4 Game-ready CC0 kits — Quaternius and KayKit (leads, search-verified)

Quaternius (https://quaternius.com) and KayKit (search "KayKit 3D") publish large CC0 game-ready model packs (characters, props, environments) — the standard sources for stylised game-adjacent and playful-product 3D. **Status: not fetched directly from this sandbox; recorded as search-verified leads** — verify licences (historically CC0) on the site before use.

## 4. The comparison table

| Source | Licence | Attribution | Character | Best for |
| --- | --- | --- | --- | --- |
| Poly Haven | CC0 | None | Physical, studio-grade | Product renders, WebGL scenes, HDRI lighting |
| Poly Pizza | Per-model (mostly CC-BY) | Per model | Low-poly friendly | Isometric/explainer styles, playful scenes |
| Sketchfab (CC filter) | Per-model (CC options) | Per model | Vast, mixed | Discovery of specific objects |
| Quaternius/KayKit | CC0 (verify) | None | Stylised game-ready | Game-adjacent, playful products |

## 5. Practical workflow

1. **Decide still vs live first.** Default: render a still (or short loop) and ship it as an image; live WebGL only when interaction is the product ([../visual-styles/interface-styles.md](../visual-styles/interface-styles.md) §4.10). A rendered still also frees the palette: render in the project's lighting and colours.
2. **Search the CC0 sources first** (Poly Haven, Quaternius/KayKit); Poly Pizza/Sketchfab when the specific object is missing — attribution recorded per model.
3. **Build one scene grammar** per project (camera angle, lighting environment, background, palette) so every model renders into the same visual family — the 3D version of [Image treatment](../imagery/image-treatment.md).
4. **Optimise ruthlessly:** GLB → decimate/compress (Draco/meshopt) for live scenes; renders → modern image formats at rendered size ([../frontend-engineering/performance.md](../frontend-engineering/performance.md)).
5. **Accessibility:** live scenes are decorative-by-default (`aria-hidden`) with the same information available outside the scene ([../motion-and-interaction/animation-libraries.md](../motion-and-interaction/animation-libraries.md) §4.5).
6. **Manifest per asset** (source, creator, licence, date) ([licensing-and-provenance.md](licensing-and-provenance.md)).

## 6. Common mistakes

- **Live scene by default** — the weight/GPU cost shipped when a render would do; the still-vs-live rule is the fix.
- **CC-BY attribution forgotten** — Poly Pizza models shipped without the per-model credit; the manifest discipline exists for this.
- **Programmer lighting** — default three.js lighting with no HDRI; Poly Haven's environment maps are the one-download fix.
- **One model, one camera, no grammar** — five renders with five lighting directions read as five brands.
- **Heavy GLB shipped raw** — a 40 MB model is a page defect, not an asset.

## 7. Evaluation checklist

- [ ] Still-vs-live decision recorded; live WebGL justified against the performance filter.
- [ ] Licence per model verified (CC0 preferred; CC-BY attributions recorded in the manifest).
- [ ] One scene grammar applied to all renders (camera, lighting, palette).
- [ ] GLBs compressed (Draco/meshopt) or stills delivered as optimised images.
- [ ] HDRI tier sized to need.
- [ ] Live scenes: aria-hidden, paused off-screen, static fallback, reduced-motion story.

## 8. Related topics

- [Interface styles](../visual-styles/interface-styles.md) — the 3D/isometric style this feeds.
- [Animation libraries](../motion-and-interaction/animation-libraries.md) — three.js/R3F selection and budgets.
- [Textures and materials](textures-and-materials.md) — Poly Haven's texture library.
- [Image generation](image-generation.md) — generating renders and product imagery.
- [Licensing and provenance](licensing-and-provenance.md) — the manifest.

## 9. References

- Poly Haven (CC0, models/HDRI/textures) — https://polyhaven.com/ [accessed 2026-11-25]
- Poly Pizza — https://poly.pizza/ [accessed 2026-11-25 (403 to bots; browser access)]
- Sketchfab download/licence model — https://sketchfab.com/ [accessed 2026-11-25]
- Quaternius — https://quaternius.com/ [search-verified, accessed 2026-11-25]
- Licences are per-model where marked: read the live page per download.
