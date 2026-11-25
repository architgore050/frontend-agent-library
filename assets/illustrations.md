# Illustration Sources

## 1. What is it?

The verified catalogue of free and libre illustration systems for frontend projects: character-based libraries, flat vector systems, and generative illustration tools — with licence positions, style characteristics, and the coherence rules that stop a page looking like a sticker book. The decision of whether illustration (rather than photography or 3D) belongs in a slot at all is [Image selection](../imagery/image-selection.md) and [Illustration](../graphic-design/illustration.md).

## 2. Why does it matter?

Free illustration libraries are the fastest way to make a page look simultaneously finished and generic: unDraw's figures are on a thousand landing pages, and unrelated illustration systems pasted together (three character styles, two line weights) read instantly as assembled-from-parts. The catalogue below is therefore organised around *systems* — each source offers a coherent style — and the workflow is built around picking one system and bending it to the project's palette, not sampling several.

## 3. The sources

### 3.1 unDraw — https://undraw.co/ [accessed 2026-11-25]

**Provides:** a large library of flat, modern SVG illustrations (people, objects, scenes) with a live theme-colour recolouring tool — every illustration re-inks to the project's accent colour on download.
**Licence:** unDraw's open licence — free for commercial and personal use, no attribution required, modification allowed. (Verify the current licence page at integration — historically stable and permissive.)
**Style:** flat vector, friendly geometry, consistent figure proportions across the set.
**Craft:** recolour to a palette token before download; the set's uniformity makes coherent pages easy; its ubiquity means it reads "generic startup" fastest of all sources here — best for supporting slots, internal tools, and drafts, or restyled heavily ([Image treatment](../imagery/image-treatment.md)).

### 3.2 Open Peeps — https://www.openpeeps.com/ [accessed 2026-11-25]

**Provides:** a hand-drawn character illustration system ("people picker") by Pablo Stanley — busts, standing and sitting poses built from interchangeable parts; exported as SVG/PNG.
**Licence:** CC0 1.0 (public domain dedication) — zero attribution needed, modification free. The most permissive licence in this catalogue.
**Style:** hand-drawn line-and-fill characters, casual and expressive.
**Craft:** assemble consistent characters (one hair/face/clothes grammar per project); suits friendly product copy, empty states, persona panels.

### 3.3 ManyPixels Gallery — https://www.manypixels.co/gallery [accessed 2026-11-25]

**Provides:** a searchable gallery of flat and monochrome SVG illustrations, filterable by style and colour, free tier included.
**Licence:** free-tier illustrations are usable without attribution per ManyPixels' terms (verify per download; paid tiers add exclusive rights).
**Style:** flat/lineal business illustration; more corporate than unDraw.
**Craft:** the style filter is the feature — pick one style family and stay in it.

### 3.4 Blush — https://blush.design/ [accessed 2026-11-25]

**Provides:** a free tier of *multi-artist* illustration collections with in-browser customisation (poses, colours, combinations); an ecosystem of artist-made systems rather than one house style.
**Licence:** free tier with per-collection terms (attribution required on most free collections — check per collection; paid removes it).
**Style:** varies by artist — the value is curated diversity; the risk is mixing styles, so lock one collection per project.
**Craft:** the customiser buys palette fit; record licence per chosen collection in the manifest.

### 3.5 Humaaans — https://www.humaaans.com/ [accessed 2026-11-25]

**Provides:** Pablo Stanley's modular people illustrations (mix-and-match bodies, clothes, scenes) as SVG/Figma files.
**Licence:** CC0 (public domain) — free, no attribution, remix freely.
**Style:** flat modernist characters; predates and differs from Open Peeps' hand-drawn look.
**Craft:** Figma-native customisation; pairs well with geometric UI styles.

### 3.6 Storyset — https://storyset.com/ [accessed 2026-11-25]

**Provides:** Freepik's illustration builder — animated and static SVG illustrations across many styles, editable (colour, crop, animation on/off) in browser.
**Licence:** free with attribution for most uses (Freepik licence terms apply — verify per export); paid removes attribution.
**Style:** broad house catalogue in several named styles; animation toggle is the differentiator.
**Craft:** when using animated illustrations, respect reduced motion ([../motion-and-interaction/motion-principles.md](../motion-and-interaction/motion-principles.md)) — the SVG animations must be disabled under the media query.

## 4. The comparison table

| Source | Licence | Attribution | Style | Best for |
| --- | --- | --- | --- | --- |
| unDraw | open licence (verify page) | None | Flat, modern | Product/support slots; fast recolour |
| Open Peeps | CC0 | None | Hand-drawn characters | Friendly empty states, personas |
| ManyPixels | free tier, per terms | None (free tier) | Flat/lineal corporate | Business contexts |
| Blush | per collection (often attribution) | Usually yes (free) | Multi-artist | Distinctive character needs |
| Humaaans | CC0 | None | Flat modernist | Modular people compositions |
| Storyset | Freepik terms | Usually yes (free) | Broad, animated option | Animated support illustrations |

## 5. Practical workflow

1. **Decide illustration's job** in the design (support slots? hero? empty states?) — [Illustration](../graphic-design/illustration.md) owns the photography-vs-illustration decision.
2. **Pick ONE system** for the project; record it in the decision notes. Two systems maximum, and only with a shared visual bridge (same line weight or palette).
3. **Recolour to tokens** before download (every source here supports colour customisation except where noted); the illustrations should read as drawn *for* this brand.
4. **Check licence per download**; record the manifest entry ([licensing-and-provenance.md](licensing-and-provenance.md)).
5. **Optimise the SVGs** — most free exports carry editor metadata: strip it, compress (SVGO-class tooling), verify rendering ([../frontend-engineering/performance.md](../frontend-engineering/performance.md)).
6. **Constrain animation** — animated SVGs get reduced-motion handling or stay static.

## 6. Common mistakes

- **The sticker book** — three illustration systems on one page; the fastest way to look assembled.
- **Default colours shipped** — unDraw's signature purple everywhere because nobody recoloured it; it also feeds the generic-AI-look complaint ([../evaluation/ai-design-failures.md](../evaluation/ai-design-failures.md) §6).
- **Attribution obligations ignored** — Blush/Storyset free tiers usually require credit; the manifest is where this survives contact with shipping.
- **Editor metadata shipped** — multi-hundred-KB SVGs that should be 20 KB.
- **Animated illustrations without reduced-motion handling.**

## 7. Evaluation checklist

- [ ] One illustration system per project, recorded in the decision notes.
- [ ] Palette recoloured to project tokens before integration.
- [ ] Licence checked per download; attribution requirements met via the manifest.
- [ ] SVGs optimised (metadata stripped, compressed) and rendering verified.
- [ ] Animated illustrations respect `prefers-reduced-motion`.
- [ ] Character grammar consistent (one construction logic across figures).

## 8. Related topics

- [Illustration](../graphic-design/illustration.md) — the craft and the photography-vs-illustration decision.
- [Image treatment](../imagery/image-treatment.md) — colour/grade coherence.
- [Graphic language](../graphic-design/graphic-language.md) — where illustration sits in an identity system.
- [Licensing and provenance](licensing-and-provenance.md) — manifest and licence table.
- [icons.md](icons.md) — the icon layer (different job, same coherence rules).

## 9. References

- unDraw licence — https://undraw.co/license (verify current at integration). [search-verified, accessed 2026-11-25]
- Open Peeps licence (CC0) — https://www.openpeeps.com/ [accessed 2026-11-25]
- Humaaans licence (CC0) — https://www.humaaans.com/ [accessed 2026-11-25]
- ManyPixels terms — https://www.manypixels.co/gallery [accessed 2026-11-25]
- Blush terms — https://blush.design/ [accessed 2026-11-25]
- Storyset licence — https://storyset.com/ (Freepik terms). [search-verified, accessed 2026-11-25]
- Licence terms are volatile facts: every integration re-reads the live page.
