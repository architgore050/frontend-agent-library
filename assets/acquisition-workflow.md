# Asset Acquisition Workflow

## 1. What is it?

The procedure that turns "this page needs imagery" into sourced-or-generated, evaluated, optimised, licensed and recorded assets: the nine-step workflow, the evaluation criteria applied to every candidate, and the route decision (discover vs generate) that precedes them. It is the operational spine of this subsystem — every catalogue file ([photography.md](photography.md) through [image-generation.md](image-generation.md)) implements a step of it.

## 2. Why does it matter?

Asset work fails in two characteristic ways: the *slot-filling* failure (search once, take the first result, ship it) and the *afterthought* failure (assets sourced at the end, fighting the layout that already exists). Both produce the generic look this library exists to prevent, and both skip the licence discipline that keeps projects legally clean. The workflow exists so asset acquisition is a designed activity inside the build — needs identified from the design direction, candidates compared, quality verified in context — rather than a treasure hunt between components.

## 3. Core principles

**Principle 1 — Needs come from the design, not from the sources.** The design direction states what the page must show (subjects, moods, ratios, palette behaviour); the sources are consulted *for those needs*. Browsing galleries first and designing second is how every page acquires the same look.

**Principle 2 — Every candidate is evaluated against the same criteria.** Composition, subject placement, lighting, colour compatibility, crop suitability, aspect ratio, resolution, visual consistency and relevance to the product — the same list for sourced and generated candidates (§5), so route choice never lowers the quality bar.

**Principle 3 — The route decision is explicit.** Discover (Route A) and generate (Route B, [image-generation.md](image-generation.md)) are both legitimate; the choice per asset is recorded with its reason — including the reason for not generating (identifiable people, factual imagery) and for not sourcing (palette/subject mismatch).

**Principle 4 — Quality is verified in context.** An asset is accepted when it works *in the layout* — rendered, at the real size, under the real text — not when it looks good in a gallery or a generation grid.

**Principle 5 — Licence and provenance complete the acquisition.** An unlicensed or unrecorded asset is not acquired; it is a liability. The manifest ([licensing-and-provenance.md](licensing-and-provenance.md)) is part of the workflow's definition of done.

## 4. How it works — the nine steps

1. **Identify the visual needs.** From the design direction: list the slots (hero, section imagery, product shots, backgrounds, icons, textures, video, sound) with each slot's subject, mood, ratio, size and colour constraints. Written down before any source is opened.
2. **Determine what is necessary.** Cut slots that do not serve the design (the "we need images" reflex); decide which slots genuinely need custom assets versus conventional treatment ([Image selection](../imagery/image-selection.md)).
3. **Search the catalogues.** Use this subsystem's source files with the search craft each documents (scene-specific searches, photographer browsing, licence filters).
4. **Collect multiple candidates.** 3–5 per slot, across sources where needed; for generation, a seeded candidate set ([image-generation.md](image-generation.md) §5.3).
5. **Evaluate visually.** The criteria in §5, per candidate, against the slot's written needs.
6. **Generate if sourcing is insufficient.** The route decision with reason; the generation workflow runs its own candidate/iterate loop ([image-generation.md](image-generation.md)).
7. **Optimise.** Resize to rendered dimensions, modern formats, compression, SVG stripping — per asset class ([../frontend-engineering/performance.md](../frontend-engineering/performance.md)).
8. **Integrate.** Place into the layout with the treatment family applied ([Image treatment](../imagery/image-treatment.md)); responsive delivery (`srcset`, lazy loading) configured.
9. **Verify and record.** Check the rendered result at real widths (browser inspection — [../evaluation/website-visual-qa.md](../evaluation/website-visual-qa.md)); confirm performance budget; complete the manifest entry (licence, source/creator or model/prompt, date).

## 5. Practical application — the evaluation criteria

Applied to every candidate, sourced or generated, scored against the slot's written needs:

| Criterion | What to check | Common failure caught |
| --- | --- | --- |
| Composition | Focal point, balance, depth, framing | Cluttered stock shots; off-centre subjects |
| Subject placement | Where the eye lands; room for text overlay | Headline over the subject's face |
| Lighting | Direction, softness, consistency with the family | Mixed light directions across the set |
| Colour compatibility | Palette behaviour against project tokens | Clashing colour casts; saturation wars |
| Crop suitability | Survives the slot's crop (cover, focus point) | Subjects decapitated by hero crops |
| Aspect ratio | Available in the needed ratio (or croppable) | Portrait-only shots in landscape slots |
| Resolution | Sharp at rendered size ×2 DPR | Upsampled mush; visible artefacts |
| Visual consistency | Belongs to the project's family | One glossy corporate shot among matte editorial ones |
| Relevance | Shows *this product's* actual subject | Generic "team collaboration" for a bakery |
| Licence/attribution (sourced) | Terms verified, manifest-ready | NC-licensed clip in a product |
| AI-tell quality (generated) | Hands, text, edges, light logic ([image-generation.md](image-generation.md) §5.6) | Six fingers; garbled signage |

The five "avoid" categories from the brief map onto these criteria: generic stock imagery (relevance + composition), repetitive AI imagery (consistency + AI-tell), irrelevant illustrations (relevance), random decorative elements (every criterion — decoration without purpose fails by definition), and assets that dictate the design accidentally (needs-first ordering).

## 6. Decision framework — the route decision

For each slot, in order:

1. **Can conventional sources hit the need?** Try the catalogues first — faster and usually sufficient.
2. **Is the gap a subject gap or a style gap?** Subject gaps (niche objects) → deeper sourcing ([photography.md](photography.md) niche searches, [3d-assets.md](3d-assets.md)). Style gaps (right subject, wrong palette/style) → generation often wins.
3. **Does the need involve identifiable people or factual claims?** → sourcing (or commissioned photography); generation is out ([image-generation.md](image-generation.md) §6).
4. **Is generation available in this environment?** If not, Route A covers the project (the fallback rule) — record the constraint rather than shipping unlicensed "found" assets.

## 7. Examples

**Example 1 — a bakery site run through the workflow.** Needs list (from the direction): hero (bread counter, warm morning light, 3:2, headline space left), four section images (hands at work, oven, interior, product close-ups), icon set, paper texture ground. Sourcing: Unsplash scene-specific searches ("artisan bakery counter morning light") yield a strong hero and two sections; the oven interior needs the *project's* palette — Route B generates it against the style sheet. Optimisation, integration, browser verification at 390 and 1440, manifest completed for six assets (five sourced, one generated). Total asset phase: one focused session, zero licence surprises.

**Example 2 — the slot-filling failure caught.** A SaaS landing page draft ships with three Unsplash first-results: a handshake (generic stock), a team photo whose lighting contradicts the hero (consistency failure), and a dashboard screenshot for a product that does not look like that (relevance failure). The workflow's needs list had never been written — the fix is not re-searching but running steps 1–2 first, which cuts two slots entirely and re-briefs the third as a real product UI capture ([../skills/taste/SKILL.md](../skills/taste/SKILL.md) §2: the client's own subject leads).

## 8. Common mistakes

- **No needs list** — sources browsed before the design states its needs; the root of the generic look.
- **First-result acceptance** — one candidate per slot; the evaluation criteria never ran.
- **Assets sourced after layout** — the layout bends around whatever was found; needs-first prevents it.
- **Licence as a launch-week cleanup** — the manifest is part of acquisition, not a pre-launch audit.
- **Generation as the default route** — sourcing skipped; the route decision §6 exists.
- **No rendered verification** — assets accepted from galleries; the 390 px crop decapitates the subject nobody checked.

## 9. Evaluation checklist

- [ ] Visual needs list written from the design direction before any source opened.
- [ ] Slots cut that do not serve the design; necessity decided per slot.
- [ ] 3–5 candidates per slot; evaluation criteria §5 applied per candidate.
- [ ] Route decision (discover/generate) recorded per asset with reason.
- [ ] Generated assets ran the full generation workflow (style sheet, seeds, QA).
- [ ] Optimisation applied per asset class; responsive delivery configured.
- [ ] Rendered verification at real widths and sizes.
- [ ] Manifest complete for every shipped asset (licence/provenance fields).

## 10. Related topics

- Every catalogue file in this subsystem — the sources each step uses.
- [Image selection](../imagery/image-selection.md) and [Image treatment](../imagery/image-treatment.md) — the slot and family craft.
- [Image generation](image-generation.md) — Route B in full.
- [Performance](../frontend-engineering/performance.md) — the optimisation step.
- [Website visual QA](../evaluation/website-visual-qa.md) — the rendered-verification step.
- [Licensing and provenance](licensing-and-provenance.md) — the record-keeping step.

## 11. References

- This file is the library's synthesis of professional asset-direction practice; the criteria table operationalises the needs-first principle stated across the imagery domain files.
- The nine-step structure mirrors the library's evaluation loop (propose → verify → apply → evaluate) applied to assets; see [Iteration](../methodology/iteration.md) for the general loop.
