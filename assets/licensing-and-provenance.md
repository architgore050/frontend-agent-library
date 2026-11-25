# Licensing and Provenance

## 1. What is it?

The record-keeping layer of asset intelligence: the licence positions of every source in this subsystem summarised in one table, the asset manifest that projects maintain for every shipped asset, and the local-asset organisation rules (formats, folders, naming) that make projects auditable. The rights *theory* (what licences mean, how releases work, where AI-output rights stand) is [Image rights](../imagery/image-rights.md); this file is the operational discipline.

## 2. Why does it matter?

Licence mistakes are the project failures that surface months late — a takedown demand, an attribution dispute, a client audit — and they are almost always failures of *recording*, not of intent: the team used a CC-BY texture and nobody wrote down who to credit. Provenance is also a design capability: a project that can answer "what model and prompt produced this hero, what seed, can we make the spring variant?" is a project that can iterate its assets. The manifest is the cheap insurance that makes both possible.

## 3. Core principles

**Principle 1 — Every shipped asset has a manifest row.** Sourced: filename, source URL, creator, licence, attribution requirement, original URL, date. Generated: filename, generation model, prompt (or style-sheet reference), seed, date, post-processing. No row, no ship.

**Principle 2 — The licence page is read at integration time, per project.** The table below is a summary with access dates; it is a map, not the law. Licence terms are volatile facts — the live page wins, and the manifest records which version was read.

**Principle 3 — "Free" categories are not interchangeable.** Public domain (CC0) ≈ unrestricted; attribution licences (CC-BY) require recorded credit; platform licences (Unsplash/Pexels/Mixkit) carry their own redistribution restrictions; site-terms sources (Bencho, Texturelabs, GetLayers) need the per-project read. The table's "attribution" column is the decision line.

**Principle 4 — Projects own their assets; this library owns its knowledge.** No central asset dump lives here — the library curates sources and workflows; each project keeps its own `assets/` with its own manifest.

## 4. The licence table (summaries; live pages govern)

| Source | Licence | Attribution | Verify page |
| --- | --- | --- | --- |
| Unsplash | Unsplash Licence (commercial OK) | Optional | unsplash.com/license |
| Pexels (photo/video) | Pexels Licence (commercial OK) | Optional | pexels.com/license/ |
| Openverse results | Per-work CC (shown) | Per work | shown per result |
| Pixabay | Pixabay Content Licence | None | pixabay.com/service/license-summary/ |
| Shopify Burst | Free-commercial terms | None | shopify.com/stock-photos |
| unDraw | Open licence | None | undraw.co/license |
| Open Peeps / Humaaans | CC0 | None | site pages |
| ManyPixels (free tier) | Site terms | None (free tier) | manypixels.co |
| Blush | Per collection (often CC-BY-like) | Usually yes (free tier) | blush.design |
| Storyset | Freepik terms | Usually yes (free tier) | storyset.com |
| Poly Haven (models/HDRI/textures) | CC0 | None (appreciated) | polyhaven.com/faq |
| ambientCG | CC0 | None | ambientcg.com |
| Texturelabs | Free-commercial terms | Appreciated | texturelabs.org |
| Poly Pizza | Per model (mostly CC-BY) | Per model | per-model page |
| Sketchfab | Per model (CC options) | Per model | per-model page |
| Quaternius / KayKit | CC0 (verify) | None | site pages |
| Lucide | ISC-family | None | lucide.dev |
| Phosphor / Tabler / Heroicons | MIT | None | repo/site |
| Simple Icons | CC0 (code); trademarks separate | None (respect trademark policy) | simpleicons.org |
| Iconify | MIT (per-set licences apply) | Per set | iconify.design |
| Google Fonts | OFL/Apache per family | None | per-family licence file |
| Fontshare | ITF free licence | None | fontshare.com/licenses |
| Fontsource | MIT + OFL/Apache | None | fontsource.org |
| Mixkit (video/SFX) | Mixkit Licence | None | mixkit.co/license/ |
| Coverr | Site terms | Per terms | coverr.co |
| LottieFiles | Per animation | Often yes | per-animation page |
| UISFX | MIT | None | repo |
| Bencho sounds | Site terms (verify) | Per terms | bencho.dev/sounds |
| Freesound | Per clip (CC0/CC-BY/NC) | Per clip | freesound.org/help/licenses/ |
| Zapsplat | Site terms (account) | Per terms | zapsplat.com |
| Haikei | Free tool (verify terms) | None | haikei.app |
| tsParticles | MIT (runtime) | None | repo |
| GetLayers / ScrollTide / Casberry | Per plan (commercial tools) | Per plan | site terms |

CC0 1.0 legal text: https://creativecommons.org/publicdomain/zero/1.0/ [canonical]. All summaries checked 2026-11-25 ([../references/frontend-phase-sources.md](../references/frontend-phase-sources.md)); **non-CC entries are volatile facts — read the live page per integration** ([README §H provenance rules](../README.md)).

## 5. Practical application — the manifest

Per-project file, `assets/MANIFEST.md` (or CSV for large sets), one row per shipped asset:

```markdown
| File | Slot/Use | Source type | Source / Model | Creator / Prompt | Licence | Attribution needed | Original URL / Seed | Date acquired |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| hero-counter.webp | Home hero | Sourced | Unsplash | Ana D. | Unsplash Licence | No | unsplash.com/photos/… | 2026-11-25 |
| oven-interior.webp | Process section | Generated | Qwen Image (local) | style-sheet v1 + "brick oven interior…" | N/A (generated) | Label as AI-generated | seed 1423 | 2026-11-25 |
| icons.sprite.svg | Global UI | Built | Lucide family | — | ISC | No | lucide.dev | 2026-11-25 |
| grain-overlay.svg | Atmosphere layer | Procedural | feTurbulence (ours) | — | Project-owned | No | — | 2026-11-25 |
```

Attribution-bearing entries (CC-BY and site-terms sources) additionally render their credit where the licence requires it — in a credits footer line ([../skills/taste/SKILL.md](../skills/taste/SKILL.md) rule 1: credits in one footer line) or a credits page — and the manifest records *where* the credit renders.

**Generated-asset labelling:** generated imagery is labelled as such in the manifest; where it depicts scenes that could be mistaken for documentary photography of real people/events, a visible disclosure is the honest default. Generated imagery never presents fictional people as real customers, staff or testimonials ([image-generation.md](image-generation.md) §6).

## 6. Local asset organisation

- **Folder structure:** `assets/images/`, `assets/video/`, `assets/audio/`, `assets/icons/`, `assets/fonts/`, `assets/3d/` — one level, predictable; source files (uncompressed originals, .exr HDRI, editing files) live in `assets/_sources/` excluded from deploy.
- **Naming:** lowercase-hyphen semantic names (`hero-counter.webp`, `icon-arrow-right.svg`) — the filename is the manifest's join key; no `IMG_2043.jpg`.
- **Formats:** images AVIF/WebP (JPEG/PNG fallback), SVG optimised (metadata stripped), video MP4 (H.264) with WebM where smaller, audio Opus/MP3, fonts WOFF2 only.
- **Dimensions:** assets sized to their largest rendered size ×2 DPR maximum; no multi-megabyte originals in the deploy path ([../frontend-engineering/performance.md](../frontend-engineering/performance.md) §5.1).
- **Responsive delivery:** `srcset`/`sizes` per image slot; art-directed crops as separate files.

## 7. Common mistakes

- **No manifest** — the audit that cannot be answered; rows are written at acquisition time, not reconstructed later.
- **Desktop/web licence confusion** — the fonts case ([typography.md](typography.md) §6); only web-covered licences count.
- **NC-licensed assets in commercial projects** — the Freesound/Poly Pizza filter discipline.
- **Attribution "somewhere"** — unrendered credit; the manifest records where credit actually appears.
- **Source files in the deploy path** — 40 MB originals shipped to production.
- **Generated assets unlabelled** — the provenance and honesty failure.

## 8. Evaluation checklist

- [ ] Manifest exists; one row per shipped asset, written at acquisition.
- [ ] Licence pages read at integration (this project's dates recorded in rows).
- [ ] Attribution-bearing assets render their credit; the manifest records where.
- [ ] Generated assets labelled, with model/prompt/seed recorded.
- [ ] NC/restricted assets excluded from commercial contexts.
- [ ] Folder structure, naming, formats and dimension rules applied.
- [ ] Source files excluded from deploy.

## 9. Related topics

- [Image rights](../imagery/image-rights.md) — the rights theory behind the table.
- [Acquisition workflow](acquisition-workflow.md) — where manifest completion sits in the procedure.
- Every source file in this subsystem — the per-source craft.
- [Source accessibility](../references/source-accessibility.md) — the library's own provenance system (this file applies the same discipline to project assets).
- [Performance](../frontend-engineering/performance.md) — the format and dimension rules.

## 10. References

- Creative Commons, CC0 1.0 — https://creativecommons.org/publicdomain/zero/1.0/ [canonical]
- Creative Commons licence suite — https://creativecommons.org/licenses/ [canonical]
- Per-source licence pages as tabled in §4 (all checked 2026-11-25; live pages govern at integration). [accessed/search-verified per ../references/frontend-phase-sources.md]
- The manifest template and organisation rules are this library's conventions.
