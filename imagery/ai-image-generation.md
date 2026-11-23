# AI image generation

## 1. What is it?

AI image generation is the production of imagery from text prompts and reference images using diffusion-style models. For design work it is best understood as a new kind of production tool sitting alongside photography, stock and illustration — powerful for speed, iteration and photorealistic invention, unreliable by default, and legally distinctive. A model does not know your brand, your layout or your rights situation; it produces plausible images that a designer must direct, select, grade, composite and clear.

This file covers the craft: prompting for design contexts, keeping a generated series consistent, controlling composition, protecting brand elements, keeping typography out of generated pixels, checking quality, and navigating usage rights. Where generated images fit among sourcing options is decided by the framework in [Image selection](image-selection.md); the underlying legal map is in [Image rights](image-rights.md); how generated plates are finished (grading, cropping, export) is in [Image treatment](image-treatment.md).

## 2. Why does it matter?

Generation changes the economics of concepting. A mood board that once took a photographer or an illustrator days can be explored in an afternoon; a background plate, a texture or a stylistic experiment costs seconds, which allows design teams to test many directions before committing budget to real production. For events and small organisations without photography budgets, generation is often the only route to bespoke, on-style imagery that stock cannot match.

The same properties create the risks. Models drift: ten prompts intended as one series produce ten slightly different styles. Models invent: hands, text, geometry and faces carry characteristic artefacts. Models approximate: brand colours arrive near the hex, not at it. And the legal ground is genuinely unsettled: platform terms differ from each other, training data is contested in litigation and public debate, and — in the United States — purely AI-generated images are not copyrightable, per the U.S. Copyright Office's March 2023 registration guidance on works containing AI-generated material [search-verified, URL in References]. Generation is therefore a high-velocity, low-certainty tool: its output must pass through the same art direction, QA and rights checks as any other imagery, plus a few of its own.

For the library's reference use case — extending an already-fixed event logo into a complete brand kit — generation plays a specific role: the logo and its rules are settled (see [Fixed logo analysis](../branding/fixed-logo-analysis.md)), photography of the real venue and speakers may not exist yet or may not be budgetable, and much of the needed imagery is atmospheric (backgrounds, textures, social plates) rather than documentary. That is the environment where generation earns its place: fast, on-palette scaffolding around a fixed mark, with the mark itself never generated.

## 3. Core principles

**The model is an assistant, not an art director.** It executes descriptions; it does not hold a brief. Every discipline of traditional art direction ([Art direction](../graphic-design/art-direction.md), [Photography](photography.md)) applies with more force, because nothing defaults to your style unless you state it.

**Anchor the style before generating volume.** A fixed, reusable style description — palette, medium, lighting, lens, mood — written once and prepended to every prompt is the difference between a series and a pile. This is the same move as defining a photography style ([Photography](photography.md)), expressed as text.

**Verify before use.** Every generated image is a draft containing artefacts until inspection proves otherwise. QA (section 5.3) is a gate, not a formality.

**No factual claims from synthetic pixels.** Generated imagery must not be presented as documentation of real people, products, venues or events — the truthfulness ladder in [Image selection](image-selection.md) applies with the same force to generation as to stock.

**Imagery and typography are separate crafts.** Text is set in design tools over clean plates, not generated inside images (section 4.5). This is the single most violated rule and the most visible failure.

**Rights are part of the tool choice.** Platform terms differ materially — who owns output, whether companies above a revenue threshold need paid plans, what the platform itself may do with your images. Check terms per platform per project ([Image rights](image-rights.md)).

**Separate exploration from production.** Generation is excellent for throwaway material — concept boards, style tests, pre-visualisation — where artefacts and rights ambiguity cost little. Production imagery deserves the full loop: anchor, batch, curate, grade, QA, log. Teams that blur the two ship exploration quality into production slots, or pay production rigour for images nobody kept. Decide per asset which kind it is before generating, and label drafts as drafts in the working files so nothing ambiguous reaches an export.

## 4. How it works

### 4.1 Using references

Most current tools accept images alongside text: as style references ("generate in the mood of this board"), as content references ("this product, re-photographed in snow"), or as composition guides ("this layout, different subject"). Used well, references do most of the work that adjectives struggle to do.

- **Reference the style, not the artist.** A mood board of five images that share warm backlight, medium distance and a muted grade directs better than a name. Naming living artists' styles in prompts is contested ethically and, increasingly, by platform policy — describe the visual properties you actually want instead; the properties are what transfer anyway.
- **Reference real constraints.** For brand work, the most valuable reference set is the brand's own approved imagery ([Photography](photography.md)) plus the palette ([Palette development](../colour/palette-development.md)). Ask for images "consistent with" that set, then grade the output into the family.
- **Separate style from subject in the prompt.** A workable prompt structure keeps the style block constant and swaps only the subject — which is also what makes a series cohere (section 4.2).
- **Describe, do not hope.** If the reference must yield "generous empty space on the left for the headline", say that explicitly; the model will not infer layout intent from an image alone.
- **Build the reference board before prompting.** The working sequence for a new project: assemble five to ten approved images from the existing library (or, for a new kit, from sources that match the intended style); write down in prose what they share — light, distance, palette, mood; use that prose as the first style anchor; keep the two or three strongest board images as reference inputs for the first anchor round. The board converts taste into instructions, which is what the model actually consumes.
- **Keep references rights-clean.** Reference images should be the brand's own or licensed material — feeding another organisation's imagery in as a style source imports its problems into your output (see [Image rights](image-rights.md)).

### 4.2 Maintaining consistency across a series

Consistency across many generated images is the core production challenge. Four generic techniques, ordered by reliability:

1. **The style anchor (text).** Write a fixed style block — medium, palette (with hex names), lighting, lens/angle, mood, negative constraints — and reuse it verbatim in every prompt, changing only a subject slot:

```text
STYLE: warm documentary photograph, natural window light, medium distance,
eye-level angle, muted warm palette (terracotta #B4562F, sand #E4D5B8),
shallow depth of field, soft grain, no studio look, no neon, no text.
SUBJECT: two volunteers arranging folding chairs in a bright hall.
```

2. **Seed reuse (generically described).** Where a tool exposes a seed — the random starting point of generation — reusing the seed with small prompt changes keeps structure and palette closer together than fresh randomness. Tools differ in whether seeds are exposed and how strongly they bind; test the behaviour of your tool rather than assuming.
3. **Reference-image conditioning (generically described).** Feeding one approved image back as a style reference for the rest of the series is the strongest visual lock most tools offer. Generate one candidate you like, curate it hard, then propagate it. Tools implement this as image prompts, style references or fine-tuning of a personal model; the workflow is generic, the mechanics are tool-specific.
4. **Post-generation unification.** Everything passes through the same grading preset as the rest of the library ([Image treatment](image-treatment.md)) — often the cheapest way to hide residual drift.

Expect to combine all four. The anchor prevents gross drift, seed/reference work holds the series together, and the grade equalises the residue.

### 4.3 Generating visual variations

Variation is where generation outperforms every other source: producing ten honest alternatives to one concept costs seconds.

- **Vary one variable at a time.** To explore, change subject, or angle, or palette — not all three in one prompt. A/B comparisons need isolation to teach you anything.
- **Batch, then curate.** Generate wide (five to ten candidates per concept), select with the scorecard from [Image selection](image-selection.md), and only then refine. First outputs are rarely the keepers; planning around that expectation is the professional habit.
- **Upsample the direction, not the image.** When one candidate is right in mood but wrong in detail, re-prompt towards its description rather than trying to edit the specific pixels — editing one image repeatedly usually accumulates artefacts.
- **Harvest the accepted image's settings.** Record the prompt, seed and reference set of every accepted image in the same log used for rights documentation (section 6) — it is the only reliable way to regenerate a family later, or to hand the recipe to another designer or tool.
- **Distinguish exploration from production variations.** Wide random batches explore the concept space; tightly constrained regenerations (one variable changed) build the final series. Teams that blur the two end up with a series that drifts as much as the exploration batch did.

### 4.4 Controlling composition

Composition control works through four levers, in decreasing reliability:

- **Aspect ratio.** The most reliable control: request the delivery ratio (16:9 hero, 1:1 tile, 9:16 story) or generate larger and crop to it from the master. Generate with headroom for the crops the system needs ([Photography](photography.md), section 4.6).
- **Camera and lens vocabulary.** "Wide shot", "close-up detail", "aerial view", "shallow depth of field", "35 mm documentary" — photographic terms map well to model behaviour because training data is captioned photographically. This is why the photography style translates almost verbatim into prompts.
- **Positional language.** Statements like "large empty sky in the upper left", "subject on the right third" work partially and vary by tool and model version. Treat positional control as approximate: plan to re-crop or composite rather than relying on the prompt to place things exactly.
- **Explicit layout intent.** For backgrounds and plates, prompt for the function: "abstract gradient texture, darker on the left, no focal point, suitable as a headline backdrop". Describing the slot's job outperforms describing an imaginary picture.

Composition intended for text overlay deserves emphasis: generate the negative space deliberately (section 4.5), and verify it survives cropping into each delivery ratio.

### 4.5 Preserving brand elements

- **Never ask the model to render the logo.** Current models cannot reliably reproduce an exact mark: letterforms distort, geometry drifts, and even near-hits are unusable. Generate or select the space for the logo — clean plate, planned empty zone — and composite the real logo file in a design tool. The logo's own geometry and clear-space rules are governed by [Fixed logo analysis](../branding/fixed-logo-analysis.md) and [Logo systems](../branding/logo-systems.md).
- **Hold brand colour by grading, not by prompt.** Prompts produce approximate colour; hexes in the prompt help, but the reliable route is grading the output to the palette afterwards ([Image treatment](image-treatment.md), [Colour in code](../colour/colour-in-code.md) for the token source). Check for brand-colour drift explicitly in QA (section 5.3).
- **Protect wordmarks and typography.** For the same reason as logos: any text in generated pixels is unreliable. Type is set in design tools.
- **Composite brand patterns and textures separately.** If the kit's graphic language includes patterns ([Patterns and textures](../graphic-design/patterns-and-textures.md)), overlay them as design layers rather than hoping the model reproduces them.

### 4.6 Separating imagery from typography

The rule is absolute in professional practice: **type is added in design tools, not generated inside images.** The reasons are practical, not stylistic:

- **Distortion.** Models render letterforms as textures, not as glyph geometry — inside longer words, lines wobble, letters fuse, and spacing drifts. Small amounts of text sometimes survive; headlines almost never do. Even when a short word renders cleanly, it is non-editable, non-accessible and unsearchable.
- **Avoiding distorted text means never requesting it.** Add "no text" to the style block's negative constraints so stray signage and captions do not appear in the plate; if in-world text is unavoidable (a café scene), expect to fix or crop it out in QA.
- **The workflow that follows:** generate a clean plate with planned negative space → composite in the design tool → set the headline in the brand typeface ([Typeface selection](../typography/typeface-selection.md), [Typographic hierarchy](../typography/typographic-hierarchy.md)) → export. This yields editable, translatable, accessible text with correct kerning.
- **Accessibility consequence.** Text baked into an image is invisible to screen readers and fails WCAG's images-of-text criterion (1.4.5, Level AA) unless the alt text repeats it verbatim — the WAI Images Tutorial is explicit that images of text should be avoided except for logos. [accessed] Real text over real plates is also simply easier to maintain.

### 4.7 Copyright and usage rights of AI output

This is an evolving area; verify current terms before each project. The stable points as of writing:

- **Platform terms differ and matter.** OpenAI's Terms of Use state that users "own the Output" and that OpenAI "hereby assign[s] to you all our right, title, and interest, if any, in and to Output", while warning that "output may not be unique and other users may receive similar output from our Services" [accessed, URL in References]. Midjourney's Terms of Service state "You own all Assets You create with the Services to the fullest extent possible under applicable law", require companies above USD 1,000,000 in annual revenue to subscribe to Pro or Mega plans to own their assets, and note that "If you upscale the images of others, these images remain owned by the original creators" [accessed, URL in References]. Users also grant the platforms broad licences to use their outputs. Read the current terms of whichever tool you use; they change.
- **Ownership is not copyright.** Even where a platform assigns output to you, purely AI-generated images are not copyrightable in the United States: the Copyright Office's 2023 guidance requires human authorship and disclaims AI-generated material on registrations (the *Zarya of the Dawn* graphic-novel review is the reference example) [search-verified, URL in References]. Human-authored contributions — your selection, arrangement, editing and compositing — may be protectable; the raw output is not. Practical consequence: if exclusivity matters (a key visual no competitor may use), generation alone may not provide it.
- **The training-data controversy is unresolved.** Generators are trained on large image collections whose licensing is contested in active litigation and public debate; a generated image can resemble existing work. For brand use, mitigate: prompt from your own references rather than named artists, check distinctive outputs against reverse image search, and avoid generating trademarks, character designs and recognisable logos.
- **Disclosure norms are forming.** Where imagery could be mistaken for documentation, disclose that it is synthetic — consistent with the truthfulness ladder in [Image selection](image-selection.md). Some platforms and jurisdictions are introducing labelling expectations; treat disclosure as the default for photorealistic content.
- **Company terms sit on top.** Your client or employer may restrict AI tools, require human review, or own workflows differently. The rights log (section 6) should record which tool, which terms version, and who approved use.

The full legal map — including how these terms interact with stock licences and releases — lives in [Image rights](image-rights.md).

### 4.8 Tool selection and generic parameter vocabulary

Choosing a generation tool is partly a rights decision and partly a control decision. Criteria worth scoring per project:

- **Terms fit.** Who owns output, whether the organisation crosses any revenue-threshold plan requirements (Midjourney's Pro/Mega rule is the verified example [accessed]), whether the platform may publicly display or relicense your outputs, and whether prompts remain private.
- **Control features.** Does the tool expose seeds, reference images or style presets, negative prompts, aspect-ratio control, and region-based editing? The more control surfaces, the easier series consistency and composition become (sections 4.2–4.4).
- **Integration.** Whether outputs can be graded, composited and exported inside the team's existing pipeline ([Image treatment](image-treatment.md)).
- **Data sensitivity.** If the brief involves confidential products or unreleased venues, check whether prompts and uploads are retained or used for training, and whether an opt-out exists (OpenAI's terms, for example, describe an opt-out from content being used to train models [accessed]).

Beyond plain text prompts, most tools share a small family of controls (described generically; exact names and behaviour differ per tool):

| Control | What it does | Design use |
| --- | --- | --- |
| Negative prompt | Lists what to avoid | "no text, no watermark, no studio look" as standing constraints |
| Seed | Fixes the random starting point | Series consistency when combined with a style anchor |
| Reference image / image prompt | Conditions style or content on an image | Anchoring a series on one approved frame |
| Guidance / strength settings | How literally the model follows the prompt | Lower for natural results, higher for strict style adherence |
| Region editing / masking | Regenerates part of an image while keeping the rest | Fixing an artefact without re-generating the frame |
| Upscaling | Increases resolution from a chosen candidate | Final production pass after curation, not before |

Treat parameter tuning like photography settings: learn the tool's behaviour on throwaway batches, then apply the working recipe to the real brief.

## 5. Practical application

### 5.1 Prompting craft for design contexts

A design-context prompt has five slots. Build them in this order:

1. **Subject** — the concrete scene, translated from the brief the same way stock briefs are ([Image selection](image-selection.md), section 4.1): "volunteers arranging chairs" not "teamwork".
2. **Style** — the fixed anchor block from section 4.2: medium, palette, grade, mood. Kept constant across the series.
3. **Light** — source, direction, quality, temperature, drawn from the photography style: "natural window light, soft, slightly warm".
4. **Composition** — ratio, distance, angle, and the negative-space plan: "medium shot, eye level, generous empty space on the left for headline".
5. **Constraints** — the negatives and finish requirements: "no text, no watermark, no logos, no studio look, photorealistic, no people looking at camera".

Worked example — a hero plate for an event kit:

```text
STYLE: warm documentary photograph, natural golden-hour light, medium distance,
eye-level, muted warm palette (terracotta #B4562F dominant), soft grain,
photorealistic, no studio look.
SUBJECT: a festival courtyard at dusk, string lights, small groups in
conversation, seen from the entrance.
COMPOSITION: wide 16:9 frame, upper-left third kept as clear dusk sky
with no detail, for headline overlay.
CONSTRAINTS: no text, no signage, no readable logos, no watermark.
```

And a background plate for speaker cards, where the subject is deliberately non-specific:

```text
STYLE: soft abstract photograph, shallow depth of field, warm-neutral palette
(sand #E4D5B8 dominant with terracotta #B4562F accents), natural light.
SUBJECT: out-of-focus texture of a sunlit brick wall with climbing plants.
COMPOSITION: 1:1 frame, uniform tonality, no focal point, darker lower third
to support a name overlay.
CONSTRAINTS: no faces, no text, no watermark.
```

Note what the second prompt does: it designs for its slot (a name overlay needs a quiet, darker lower third) instead of picturing a scene first — the same slot-first thinking that governs negative space in [Photography](photography.md).

Two prompt-craft habits carry most of the quality: specificity beats adjectives (the stock-search lesson transfers directly), and fewer ideas per prompt (a prompt trying to say five things produces mush).

### 5.2 The iteration workflow

A repeatable loop keeps generation inside the design process:

1. **Brief** — write the slot's job and the style anchor; confirm the subject passes the truthfulness ladder.
2. **Anchor round** — generate five to ten candidates for one concept; do not polish yet.
3. **Curate** — scorecard against the brief and the family; keep at most two directions.
4. **Fix** — iterate the kept directions with one-variable changes; use seed/reference techniques for series membership.
5. **Finish** — grade into the library preset; crop to ratios; composite brand elements and set type in the design tool.
6. **QA gate** — run the checklist in 5.3; reject and re-generate rather than shipping artefacts.
7. **Log** — record prompt, seed, tool, terms version, and clearance decision ([Image rights](image-rights.md)).

Keep exploration batches in a separate working directory from curated production assets, and promote an image to production only after it has passed the finish and QA steps — the discipline costs nothing and prevents the classic accident of a half-finished draft appearing in a delivered kit.

A note on repair techniques, described generically since implementations differ: when a strong candidate carries one local flaw — a malformed hand, garbled background signage — region-based editing (masking the flaw and regenerating only that area) usually beats re-rolling the whole frame, because it preserves the composition you curated. Extending a frame outward (outpainting) is useful for generating extra negative space when a plate lacks room for its headline; the result must still pass QA, and compositing the extra space in a design tool remains the simpler fallback. Repair passes count as generation for rights purposes: log them like any other step.

### 5.3 QA of generated imagery

Inspect at full resolution, at 100% zoom, before any image enters the library. Two passes work better than one: a first pass at reading size to judge mood and message, a second zoomed pass hunting artefacts. Then review the whole set as a grid against the anchor images — generation-specific drift, like photography drift, hides in single-image view and appears in grids ([Photography](photography.md), section 5.2).

- **Artefacts.** Fused fingers and wrong digit counts; garbled or semi-legible text (including background signage); melted geometry (glasses, cutlery, jewellery, architecture); impossible reflections and shadows that disagree with the light source; texture noise on skin and fabric.
- **Semantic plausibility.** Does the scene make sense — objects doing impossible things, wrong uniforms or tools, cloned faces in a crowd, signage that spells nothing? Models satisfy aesthetics before physics.
- **Brand-colour drift.** Check the dominant colours against the palette tokens; grade back to tolerance ([Colour in code](../colour/colour-in-code.md)).
- **Style drift.** Compare against the anchor set in a grid; re-anchor or grade if the series is separating.
- **Rights checks.** Reverse-image-search distinctive outputs; confirm no trademark or recognisable mark entered the frame; confirm the tool's terms cover this use ([Image rights](image-rights.md)).
- **Truthfulness.** Confirm nothing in the image will be read as documentation of a real person, place, product or event.

### 5.4 Limits of current tools

Design teams should assume, as of writing, the following limitations — and re-test them each project, because they move:

- **Text rendering.** Short words sometimes render; headlines, sentences and wordmarks almost never survive distortion-free. Text belongs in design tools (section 4.6).
- **Exact reproduction.** No reliable rendering of specific logos, brand marks, real products or precise geometric arrangements. Composite real assets instead of prompting for them.
- **Colour precision.** Prompt colour is approximate; hexes in the prompt narrow the gap but grading to tokens ([Colour in code](../colour/colour-in-code.md)) is what actually lands brand colour.
- **Identity persistence.** Keeping "the same person", "the same room" or "the same product" across many generations is fragile; reference-image conditioning improves it without guaranteeing it.
- **Positional control.** Prompt-based placement ("subject on the left third") is approximate and tool-dependent; plan to crop or composite.
- **Physics and semantics.** Shadows disagreeing with light sources, objects fused to hands, crowds of cloned faces — artefact rates rise with hands, crowds, text-bearing scenes and reflective surfaces.
- **Resolution and finish.** Raw output often needs an upscaling pass and the standard treatment pipeline before it matches commissioned photography's finish.

The practical consequence: generation is fastest and safest at the abstract and atmospheric end of the work, and most expensive at the photorealistic, text-bearing, brand-exact end — which is also where the rights risks concentrate ([Image rights](image-rights.md)).

## 6. Decision framework

Generation is the right option when most of these hold: no factual claim is made; the subject is abstract, atmospheric, experimental or impossible to photograph; speed and cheap iteration outweigh exclusivity; the brand can absorb post-grading and compositing work; the platform's terms and the organisation's policies permit the use. Reach for photography when reality must be documented or exclusivity matters; for stock when generic supporting imagery suffices; for illustration when long-term system voice and clean rights dominate (full ladder in [Image selection](image-selection.md)).

Two tie-breakers help when the ladder is ambiguous. First, the *scaffolding test*: if the asset will be replaced by real capture later (a pre-venue hero, a pre-product shot), generation is ideal precisely because nothing permanent is claimed. Second, the *durability test*: if the asset must live for years and be reproduced at scale, the rights uncertainty and drift risk of generated imagery argue for illustration or photography instead.

A rights-sensitivity ladder worth fixing as a team rule: generate freely for textures, gradients, abstract scenes and stylised illustration-like content; use caution (QA plus disclosure) for photorealistic scenes with no identifiable real entities; avoid entirely for fake "customers", fake "staff", fake products and anything presented as news documentation.

Expressed as content tiers:

| Content type | Generation risk | Handling |
| --- | --- | --- |
| Textures, gradients, abstract plates | Minimal | Generate freely; grade to palette |
| Stylised / illustration-like scenes | Low | Generate freely; rights check on distinctive outputs |
| Photorealistic scenes, no identifiable entities | Medium | QA gate; disclose synthetic origin |
| Photorealistic people, venues, products | High | Real capture instead; generation only as pre-visualisation scaffolding |
| Anything presented as documentation or news | Highest | Do not generate; real capture and disclosure only |

## 7. Examples

- **Event hero without a venue.** An event brand needs a hero before the venue exists: generate the dusk-courtyard plate above, grade to the kit palette, composite the fixed logo bottom-right per its clear-space rules, set the headline over the planned sky ([Fixed logo analysis](../branding/fixed-logo-analysis.md)). When the real venue photography arrives, the plate is replaced — the generated asset was scaffolding, not a claim.
- **A consistent social series.** Ten quote-card backgrounds generated from one style anchor with only the subject slot varying; all ten pass through the same duotone recipe ([Image treatment](image-treatment.md)); the series survives a grid review without visible drift.
- **The variation board.** Before commissioning an illustration system, six style directions are generated as throwaway concept art to test palette and mood cheaply — the chosen direction then goes to a human illustrator for the durable asset ([Illustration](../graphic-design/illustration.md)).
- **Textures for the kit.** A brand kit needs paper-grain and fabric textures matching the palette but absent from any stock library: three generations per texture against the style anchor, graded to the palette tokens, exported as tileable-friendly square plates ([Patterns and textures](../graphic-design/patterns-and-textures.md)). Because textures make no factual claim, they sit at the safe end of the rights ladder — and uniqueness here is cheap, which stock cannot offer.
- **The failure worth studying.** A team prompts "conference banner, 2026 International Design Summit" directly: the model renders distorted pseudo-words, invented logos and drifted colours. Every failure class at once — text in-image, brand elements in-image, no grade — and the fix is procedural: clean plate, real type, real logo, grading, QA gate.

## 8. Common mistakes

- **Asking for the logo in-image.** Unusable output and possible mark infringement; composite the real asset instead (section 4.5).
- **Asking for headlines in-image.** Distorted, inaccessible, uneditable text (section 4.6).
- **Using the first acceptable image.** Skipping the batch-and-curate loop wastes the tool's main advantage.
- **No style anchor.** Ten prompts, ten styles; the series reads as a mood board, not a brand.
- **Changing everything between iterations.** Re-rolling with a rewritten prompt each time destroys the ability to learn what worked; vary one variable per iteration (section 4.3).
- **Generating at the wrong ratio.** Producing square output for a 16:9 slot and cropping away the composition; request the delivery ratio or generate with crop headroom (section 4.4).
- **Repair-pass sprawl.** Endless local edits accumulating artefacts until the frame is worse than the original re-roll; cap repair attempts, then re-generate.
- **Trusting hexes in prompts.** Prompt colour is approximate; grade to tokens instead.
- **Fake-documentation imagery.** Generated "attendees" or "customers" presented as real — a misinformation failure, not a style failure ([Image selection](image-selection.md)).
- **Skipping rights reading.** Terms differ by platform and change; the OpenAI and Midjourney terms summarised here were read on 2026-11-23 and will not stay current ([Image rights](image-rights.md)).
- **No provenance log.** Six weeks later, nobody knows which tool, prompt or terms produced a shipped image.
- **Treating QA as optional.** Artefacts ship when nobody inspects at 100% zoom.

## 9. Evaluation checklist

- Every prompt uses the five-slot structure with a fixed style anchor.
- A reference board was built from rights-clean material before prompting.
- Series were built with seed or reference techniques and pass a side-by-side grid review.
- No generated image contains the logo, wordmark or rendered headline text.
- Any in-world text in generated scenes was flagged in QA and fixed or cropped.
- Brand elements and type were composited in design tools from real assets.
- Output colours were graded to palette tokens and verified against drift.
- Style drift was checked per series, not only per image.
- QA covered artefacts (hands, text, geometry), semantic plausibility and 100%-zoom inspection.
- No image makes a factual claim; photorealistic content is disclosed as synthetic where it could be misread.
- The tool's current terms were checked for this use case and this organisation (including any revenue-threshold plan requirement).
- Distinctive outputs were reverse-image-searched before shipping.
- Prompt, seed, tool, terms version and approval are logged for every shipped image.
- Iterations changed one variable at a time, and the accepted recipe was recorded.
- Repairs were capped (region edits tried before full re-rolls; sprawl avoided).
- Delivery ratios were requested up front, with crop headroom planned.
- Confidential subjects were checked against the tool's data-retention and training-opt-out terms.
- Exploration assets are clearly marked and never mixed into the production library.
- The distinction between exploration and production assets was decided before generating, per asset.
- Where generated imagery could be mistaken for photography, the synthetic-origin labelling was applied before shipping.

## 10. Related topics

- [Image selection](image-selection.md) — the sourcing ladder that decides when generation is appropriate.
- [Photography](photography.md) — the style definitions that become the prompt anchor.
- [Image treatment](image-treatment.md) — grading, cropping and compositing that finish generated plates.
- [Image rights](image-rights.md) — the legal map for platform terms, copyrightability and disclosure.
- [Art direction](../graphic-design/art-direction.md) — the steering discipline this tool still requires.
- [Illustration](../graphic-design/illustration.md) — the alternative for durable, rights-clean system imagery.
- [Fixed logo analysis](../branding/fixed-logo-analysis.md) — the logo geometry that must be composited, never generated.
- [Visual identity](../branding/visual-identity.md) — the system generated imagery must join.
- [Patterns and textures](../graphic-design/patterns-and-textures.md) — graphic-language layers better applied than generated.
- [Palette development](../colour/palette-development.md) — the tokens generated colour must be graded to.

## 11. References

- OpenAI, "Terms of Use" (output ownership: "you (a) retain your ownership rights in Input and (b) own the Output"; "We hereby assign to you all our right, title, and interest, if any, in and to Output."; "output may not be unique and other users may receive similar output from our Services"; restriction on using "Output to develop models that compete with OpenAI"), https://openai.com/policies/row-terms-of-use. [accessed 2026-11-23]
- Midjourney, "Terms of Service" ("You own all Assets You create with the Services to the fullest extent possible under applicable law"; companies over USD 1,000,000 annual revenue must be on Pro or Mega plans to own their assets; "If you upscale the images of others, these images remain owned by the original creators"; broad licence granted to Midjourney over user content), https://docs.midjourney.com/hc/en-us/articles/32083055291277-Terms-of-Service. [accessed 2026-11-23]
- U.S. Federal Register, "Copyright Registration Guidance: Works Containing Material Generated by Artificial Intelligence" (March 2023; human authorship requirement, disclosure and disclaiming of AI-generated material, *Zarya of the Dawn* example), https://www.federalregister.gov/documents/2023/03/16/2023-05321/copyright-registration-guidance-works-containing-material-generated-by-artificial-intelligence. [search-verified — page itself was bot-blocked at access time]
- U.S. Copyright Office, "Copyright and Artificial Intelligence" initiative page, https://www.copyright.gov/ai. [search-verified]
- W3C WAI, "Images Tutorial" (images-of-text guidance underlying section 4.6), https://www.w3.org/WAI/tutorials/images/. [accessed 2026-11-23]
- Prompt structures, workflows and QA lists are this file's own synthesis of the sources above and of current generative-tool practice; tool capabilities and platform terms change quickly — re-verify per project.
