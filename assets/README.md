# Asset Intelligence (subsystem index)

## 1. What is this subsystem?

The asset layer of the library: where visual assets come from, how to choose among candidates, how to generate original assets when existing ones are not enough, and how to keep licences and provenance honest. Two acquisition routes, deliberately of equal standing:

- **Route A — discover existing assets.** Search curated sources (the catalogues below), evaluate candidates, integrate. Fast, legal-clear when licences are checked, and usually sufficient.
- **Route B — generate original assets.** Use available image-generation capability when custom artwork, imagery or visual elements would produce a better result than anything findable.

Assets serve the design, not the reverse: a source catalogue cannot be a slot-filling service. The needs come from the design direction ([skills/frontend-design](../skills/frontend-design/SKILL.md) phase 4), and the selection discipline comes from [Image selection](../imagery/image-selection.md) and [Image treatment](../imagery/image-treatment.md).

## 2. The catalogues

| File | Contents | Key sources |
| --- | --- | --- |
| [photography.md](photography.md) | Free/libre photography | Unsplash, Pexels, Openverse, Pixabay, Shopify Burst |
| [illustrations.md](illustrations.md) | Illustration systems and figures | unDraw, Open Peeps, ManyPixels, Blush, Humaaans, Storyset |
| [textures-and-materials.md](textures-and-materials.md) | Surface textures and materials | ambientCG, Texturelabs, Poly Haven textures, transparent textures |
| [3d-assets.md](3d-assets.md) | 3D models, HDRI, renders | Poly Haven, Poly Pizza, Sketchfab, Quaternius/KayKit (CC0 game assets) |
| [icons.md](icons.md) | Icon systems and integration | Lucide, Phosphor, Tabler, Heroicons, Simple Icons, Iconify, Noun Project |
| [typography.md](typography.md) | Font sourcing and discovery | Google Fonts, Fontshare, Fontsource, Fontesk, Fonts In Use, Typewolf |
| [video-and-motion.md](video-and-motion.md) | Stock video and motion assets | Mixkit, Coverr, Pexels Video, LottieFiles |
| [sound.md](sound.md) | UI sound effects | UISFX, Bencho, Mixkit SFX, Freesound, Zapsplat |
| [backgrounds-and-effects.md](backgrounds-and-effects.md) | Backgrounds, gradients, particles, effects | Haikei, CSS Gradient, Mesh Gradient, Cool Backgrounds, particles.js/tsParticles, Casberry particles, GetLayers, Kinetics, ScrollTide |
| [image-generation.md](image-generation.md) | Route B: generating original assets | Local models (WAN Image, Qwen Image), prompt craft, art direction |
| [acquisition-workflow.md](acquisition-workflow.md) | The decision and evaluation procedure | the nine-step workflow, evaluation criteria |
| [licensing-and-provenance.md](licensing-and-provenance.md) | Licences and record-keeping | per-source licence table, manifest template |

## 3. Ground rules

1. **Licence before download.** Every source's licence is recorded; "free" never means "unrestricted". The full licence table and the manifest template: [licensing-and-provenance.md](licensing-and-provenance.md); the rights theory: [Image rights](../imagery/image-rights.md).
2. **No central asset dump in this library.** This subsystem curates sources and teaches workflows; individual projects maintain their own assets, organised per the local-asset guidance in [licensing-and-provenance.md](licensing-and-provenance.md).
3. **Record provenance for everything that ships.** Source URL, creator, licence, date — or generation model and prompt for generated assets. The manifest template makes this mechanical.
4. **Evaluate visually before committing.** The evaluation criteria in [acquisition-workflow.md](acquisition-workflow.md) (composition, subject placement, lighting, colour compatibility, crop, ratio, resolution, consistency, relevance) are applied per candidate, not per source.
5. **Optimise at integration.** Formats, compression, responsive sizing and lazy loading are part of acquisition, not a QA afterthought ([../frontend-engineering/performance.md](../frontend-engineering/performance.md)).

## 4. Browser-based discovery

Agents with browser automation capability (Playwright MCP or equivalent — the library deliberately does not assume a specific server; see [../evaluation/website-visual-qa.md](../evaluation/website-visual-qa.md) §8) can search these sources interactively, compare candidates side by side, download permitted assets and verify final rendering in context. The workflow: search → open candidates in tabs → compare against the evaluation criteria → download to the project's asset folder with manifest entry → integrate → verify rendered. Sites that block automated access (several in the photography category do) are recorded in each file; fall back to their official APIs or to a different source rather than circumventing blocks.

## 5. Related topics

- [Image selection](../imagery/image-selection.md) — which visual belongs in a slot at all.
- [Image treatment](../imagery/image-treatment.md) — making sourced assets one consistent family.
- [AI image generation](../imagery/ai-image-generation.md) — the craft and limits of generated imagery (this subsystem's route-B file builds on it).
- [Performance](../frontend-engineering/performance.md) — the optimisation half of acquisition.
- [github-resources catalogue](../github-resources/catalogue.md) — the open-source tooling (Fontsource, Iconify, tsParticles) behind several of these sources.
