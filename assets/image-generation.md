# Image Generation (Route B)

## 1. What is it?

The library's second acquisition route: producing original assets with image-generation models — when to generate instead of sourcing, how to art-direct a generation session, how to write prompts that produce usable web assets (correct ratios, negative space, no embedded text), how to build cohesive sets, and how to optimise and record the output. The general craft and limits of diffusion-model imagery are [AI image generation](../imagery/ai-image-generation.md) — that file teaches the model-agnostic skill; this file is the workflow agents run inside frontend projects, including the local-model provision (WAN Image, Qwen Image, and environment equivalents).

## 2. Why does it matter?

Generation is the only route that produces *exactly* what the design needs — the right subject in the right crop with the project's palette and light — and the only route that can also produce exactly the wrong thing (plastic AI textures, mangled text, six-fingered hands, photorealistic people who do not exist being used as "customers"). The library's position: generation is a professional tool with real strength (illustration, atmosphere, product-adjacent scenes, brand artwork) and real limits (identifiable people, factual imagery, embedded typography); the workflow here makes the strength reliable and the limits explicit.

## 3. Core principles

**Principle 1 — Generation is chosen, not defaulted.** The route decision is step 6 of the acquisition workflow ([acquisition-workflow.md](acquisition-workflow.md)): generate when sourcing cannot produce the subject/crop/palette the design needs — not because generating is fun.

**Principle 2 — Art direction before prompts.** The project's direction (style, palette, lighting, mood — [Art direction](../graphic-design/art-direction.md)) is written as a generation *style sheet* first: a paragraph of consistent descriptors applied to every prompt in the session. Cohesion comes from the sheet, not from luck.

**Principle 3 — No text in generated imagery.** Diffusion models render typography unreliably; every generated image is produced *without* text and receives type in the layout layer (HTML/CSS). Where a generated graphic must include lettering, it is added in post (SVG/HTML overlay) — this is also the accessibility route.

**Principle 4 — Plan for the layout's negative space.** Hero images are generated with the composition the layout needs — subject placement, breathing room for the headline, aspect ratio specified before generation, not cropped after.

**Principle 5 — Provenance is mandatory.** Every generated asset records model, prompt (or prompt reference), date and any post-processing in the manifest ([licensing-and-provenance.md](licensing-and-provenance.md)) — this is both honest practice and the reproducibility record for future variants.

## 4. How it works — the local-model provision

The library assumes frontend agents may have access to local image-generation capability — typically **WAN Image** and **Qwen Image** models or equivalent tools in the execution environment — without specifying the deployment (the models are managed outside this library's scope). The workflow below is tool-agnostic; agents adapt it to whatever generation surface exists:

1. **Discover capability at project start:** check what generation tooling is available (CLI, API, local pipeline). If none exists, Route A sources cover the project ([acquisition-workflow.md](acquisition-workflow.md) fallback rule).
2. **Use the model's strengths:** check the model's documentation for what it does well (photorealism vs illustration vs graphic styles) and its parameter surface (aspect ratio, guidance/strength, seeds, negative prompts).
3. **Seed discipline:** fix seeds for reproducibility; vary seeds for candidate sets; record the seed with the chosen output — a variant later in the project reproduces exactly.

## 5. Practical application

**5.1 The art-direction style sheet.** One paragraph applied to all prompts in the session, derived from the project direction: medium and style ("soft 3D clay render, matte materials"), lighting ("warm key light from upper left, soft shadows"), palette ("muted sage and cream, warm neutrals"), mood ("calm, domestic"), lens/render character ("50mm, shallow depth of field" or "claymorphism soft bevel"). Every prompt = style sheet + subject + composition notes + negative space note.

**5.2 Prompt construction for web assets.** Subject in concrete visual language (not brand claims): "a ceramic pour-over coffee set on a linen cloth, morning window light" not "premium artisanal coffee experience". Composition explicit: "centred, generous negative space above for headline, 3:2 ratio". Include the ratio in the generation parameters, not the prompt alone. Negative prompts: "no text, no watermark, no logo, no distorted hands" plus the session's specific exclusions.

**5.3 The candidate-and-iterate loop.** Generate 3–4 candidates per slot (vary seed/composition), evaluate against the same criteria as sourced assets ([acquisition-workflow.md](acquisition-workflow.md) §5), iterate on the strongest candidate (targeted edits: "same scene, slightly lower camera"), then produce the final at the needed ratio and resolution. Two iterations is normal; ten means the prompt (or the route decision) is wrong.

**5.4 Cohesive sets.** For series (hero + 3 section images): identical style sheet, consistent seed families, consistent palette tokens mentioned in every prompt, and a final *family check* — the set viewed together must read as one photographer/renderer ([Image treatment](../imagery/image-treatment.md) finishes the job with shared grading).

**5.5 Optimise and integrate.** Generated output is oversized by default: resize to rendered dimensions, compress to modern formats, apply `srcset` discipline ([../frontend-engineering/performance.md](../frontend-engineering/performance.md) §5.1). Upscaling beyond ~2× degrades diffusion detail — generate at the needed size instead.

**5.6 QA against the AI tells.** Before integration, inspect candidates for the diffusion failure set: garbled text, impossible hands/objects, melted edges, inconsistent light direction, plastic skin — and for the aesthetic failure (the generic-AI look: [../evaluation/ai-design-failures.md](../evaluation/ai-design-failures.md) §6 "repetitive AI imagery"). Failing candidates are regenerated, never shipped with "it's mostly fine".

## 6. Decision framework

| Situation | Route |
| --- | --- |
| Standard subjects (people at work, products, nature) with palette flexibility | Route A (sourced) |
| Specific subject + specific crop + brand palette that sourcing cannot hit | Route B (generate) |
| Illustration/atmosphere in the project's exact style | Route B (generate) — strength area |
| Identifiable real people, journalism, factual evidence | **Neither** — sourced editorial imagery or commissioned photography; generated fake people are not "customers" |
| Typography-bearing graphics | Generate background layer only; type in HTML/SVG |
| Long-tail subjects (niche tools, unusual scenes) | Route B, or Route A niche searches ([photography.md](photography.md)) — try A first |

## 7. Examples

**Example 1 — a hero that sourcing could not hit.** A ceramics studio site needs a hero: workbench, mid-century potter's wheel, exactly the brand's sage-and-cream palette, subject left-of-centre with headline space right. Sourcing returns close-but-wrong palettes. Route B: style sheet written; four candidates at 3:2; the third nails palette and composition; one iteration lowers the camera; final generated at 2400×1600, compressed to WebP (~340 KB), manifest records model, style sheet, prompt, seed, date. The type lands in HTML on the reserved negative space.

**Example 2 — the cohesive illustration set.** A developer tool wants four section illustrations in one style (isometric, brand blue, soft shadows). One style sheet, four prompts (one per section concept), shared seed family; the four outputs pass the family check (same weight, same palette behaviour) after two iterations; each ships as optimised SVG-compatible PNG at rendered size. The set reads as bespoke artwork — the generation strength area.

## 8. Common mistakes

- **Generating because it is available** — sourced imagery would have been faster, cheaper and more honest; the route decision comes first.
- **Text inside generated images** — garbled lettering shipped because nobody planned the type layer.
- **Prompt-as-brief** — brand claims ("premium world-class platform") instead of visual language; the model renders words, not strategies.
- **One candidate accepted** — no comparison, no iteration; the slot gets whatever came first.
- **Set incoherence** — four illustrations, four styles; the style sheet exists to prevent this.
- **Fake people as real customers** — the ethical line: generated humans presented as identifiable people (testimonials, "our team") misrepresent; record and label generated imagery.
- **No provenance** — an unlabelled generated asset nobody can reproduce or licence-audit.

## 9. Evaluation checklist

- [ ] Route decision (A vs B) recorded per asset with the reason.
- [ ] Art-direction style sheet written before the session; applied to every prompt.
- [ ] Aspect ratios and negative space specified in generation parameters.
- [ ] No text/watermark/logos in generated output; type added in the layout layer.
- [ ] Candidate sets (3–4) evaluated per slot; iteration targeted, bounded.
- [ ] Sets pass the family check; shared treatment applied.
- [ ] AI-tell QA passed (hands, text, edges, light, plastic surfaces); failures regenerated.
- [ ] Manifest records model, prompt/style-sheet reference, seed, date, post-processing.
- [ ] Output resized and compressed to rendered dimensions; `srcset` discipline applied.
- [ ] No generated imagery presented as factual/identifiable people or evidence.

## 10. Related topics

- [AI image generation](../imagery/ai-image-generation.md) — the model-agnostic craft and limits.
- [Acquisition workflow](acquisition-workflow.md) — where Route B sits in the decision sequence.
- [Image treatment](../imagery/image-treatment.md) — the shared grading that finishes a generated set.
- [Art direction](../graphic-design/art-direction.md) — the direction the style sheet derives from.
- [Licensing and provenance](licensing-and-provenance.md) — the manifest fields for generated assets.
- [Performance](../frontend-engineering/performance.md) — the optimisation half.

## 11. References

- This file is the library's synthesis of diffusion-model production practice; the craft file's sources apply ([AI image generation](../imagery/ai-image-generation.md) §11).
- WAN Image and Qwen Image are named as the anticipated local-model provision per the library's frontend brief; capability details are deliberately tool-agnostic and discovered per environment. [canonical — provision assumption, not a sourced claim]
- The style-sheet, seed and manifest disciplines are this library's workflow conventions.
