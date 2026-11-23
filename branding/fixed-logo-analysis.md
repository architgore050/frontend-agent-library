# Fixed-logo analysis

## 1. What is it?

Fixed-logo analysis is a structured methodology for building a complete visual identity **around a logo that already exists and cannot be changed** — the initial project use case for this repository: an event whose logo is finished, but which needs the full brand kit (colour system, typography, graphic language, templates, applications) developed to support it. Instead of designing a logo and deriving a system from it, the designer reverses the flow: the logo becomes the fixed constraint, the analysis extracts everything it implies, and the identity is designed to agree with it.

The methodology has twelve steps, each answering a specific question about the logo and converting the answer into design decisions. It ends with two verification steps — testing whether the identity works without the logo, and checking that nothing in it conflicts with the logo — and with a documented list of prohibited modifications that protects the mark afterwards.

The core move the methodology enables is **derivation**: extracting motifs, proportions and stylistic signals from the logo's geometry to build supporting elements that visibly belong to it, while the logo itself remains untouched. Logo handling fundamentals (variants, clear space, formats) are in [Logo systems](logo-systems.md); the complete component inventory the analysis feeds is in [Visual identity](visual-identity.md).

## 2. Why does it matter?

A fixed logo is not a minor constraint; it is the strongest prior in the whole project. Every colour, typeface, texture and layout decision either corroborates or contradicts it, and audiences experience contradictions immediately — a playful hand-drawn badge next to a stark corporate grotesque feels like two organisations sharing a document. Since the logo usually cannot be renegotiated (it may be approved by committee, registered, merchandised or already printed), the only workable strategy is to analyse it deeply enough that the rest of the system can be designed *from* it rather than *despite* it.

The methodology also protects against the two opposite failure modes that recur in fixed-logo projects. The first is **ignoring the logo**: producing a plausible generic identity that happens to carry the mark but matches none of its characteristics. The second is **over-reading the logo**: copying it so literally that posters repeat its shapes verbatim, devaluing the mark and cluttering layouts. Deep analysis finds the middle path — a system that is clearly related, clearly derived, and clearly quieter than the mark it supports.

Finally, an explicit procedure matters because agents and non-designers must be able to defend each decision ("this pattern uses the badge's 12-segment star because the logo is built on one") using evidence from the artwork itself, which is exactly the reasoning standard this repository requires.

## 3. Core principles

### 3.1 The three-way distinction (fundamental)

Every element in a fixed-logo project falls into exactly one of three categories. Confusing them is the root of most failures, so this distinction is stated before anything else:

| Category | Definition | Examples | Governing rule |
|---|---|---|---|
| (1) Modifiable elements | Parts of the brand that may be adjusted or extended without permission beyond normal use | Secondary palette, neutral greys, body-copy styling, template layouts, photography direction, most graphic elements | Design freely, within consistency rules |
| (2) Immutable elements | The logo and its designed renderings that must remain unchanged | The mark itself: geometry, letterforms, proportions, approved colourways, approved lockups | Never redraw, recolour, distort, rotate or re-set; use supplied files only |
| (3) Derivable elements | New supporting graphics abstracted from the logo's geometry without altering the logo | Patterns built from the badge's segments; a corner radius shared by logo and UI; an angled divider echoing a logo slash; derived icon style | Derivation may *echo* the geometry but must never contain, enclose, crop or modify the mark; derived elements stay subordinate |

Two boundary rules make category 3 safe in practice. First, **derivation, not incorporation**: a derived motif must be able to stand without the mark — if a pattern only works when the logo is visible inside it, it is incorporating the logo, not deriving from it (University at Buffalo's rule that its mark "may not stand alone or be combined with other words/graphics to form a new mark" illustrates how institutions guard exactly this boundary [accessed]). Second, **subordination**: derived elements support the mark; they never compete in weight, size or salience on the same surface.

### 3.2 The logo anchors the system

Every stylistic decision inherits from the analysis: the logo's construction logic becomes the grid; its colour becomes the palette's core; its letterforms define the companion type's target proportions; its era defines the stylistic register. When the analysis and a fashionable preference conflict, the analysis wins.

### 3.3 Analysis precedes synthesis

The methodology forbids jumping to aesthetics before the evidence is gathered. Steps 1–6 are pure analysis with no design output; steps 7–10 are synthesis that must cite the analysis; steps 11–12 are verification and protection. The worksheet in section 6 enforces this order.

### 3.4 The system must work without the logo

An identity that only reads correctly when the logo is visible is not a system. The test in step 11 — can materials be recognised from the system alone? — is the methodology's quality gate, mirroring the reinforcement principle in [Visual identity](visual-identity.md).

## 4. How it works — the twelve-step procedure

### Step 1: Inspect the original artwork

Establish what you actually have before interpreting anything.

- **Source files.** Ask for the master artwork: AI, EPS, PDF or SVG. The existence of a vector master determines everything downstream (see the decision table in section 7).
- **Vector or raster?** Zoom to 400–800%: vector stays crisp; raster shows pixels. A raster-only logo constrains reproduction (no clean rescaling, no recolouring, risk of halos) and changes the export strategy — you may need to redraw *supporting derivatives* while leaving the supplied raster as the sole official logo source, or escalate for a vector rebuild through governance (see [Brand governance](brand-governance.md)).
- **Resolution and dimensions.** For raster, record pixel dimensions and estimate print viability: a conventional working rule is that logos should reproduce at ≥ 300 ppi at final print size; a 500 px logo cannot fill an A3 poster cleanly. Label this a verification target, not a law.
- **Structure.** Layers, groups, transparency, effects (drop shadows, gradients, blends) baked into pixels? Note what is editable and what is flattened.
- **Colour space and specification.** Extract exact colours: HEX/RGB at minimum; check whether CMYK or Pantone specifications exist. If the logo arrives with no colour specification at all, sampling the artwork becomes the palette's primary definition (record sampled values as the official specification, flagging print matching as unverified).
- **Integrity check.** Note any existing distortions in the supplied artwork (stretched lettering, inconsistent strokes) — you must reproduce the mark as supplied, but the analysis should record such flaws so derived elements do not amplify them.

### Step 2: Identify the geometry

Search for the underlying construction. Lay construction overlays (circles, squares, diagonal guides) over the artwork at large scale and look for: consistent circle diameters or radii; repeated angles (check against 15°/30°/45° increments); symmetry or deliberate asymmetry; alignment of letterforms to common baselines or stems; a visible modular grid. Logo construction with geometric grids and ratio-based circles is established professional practice in mark design [search-verified: Figma golden-ratio resource; Medium design-bootcamp logo-grid article], but not every logo is geometrically constructed — hand-drawn and emblem-style marks may not yield a grid. Record honestly which case applies: "no detectable grid" is a valid and useful finding that steers the system away from rigid geometric motifs (decision table, row 4).

### Step 3: Analyse the proportions

Measure, numerically, the relationships inside the mark: mark height to width; symbol height to wordmark cap height (if a lockup); letter-spacing to stroke weight; internal spacing between elements. Record each as a ratio (for example "symbol : cap height = 1 : 0.42"). These ratios have three downstream uses: they set the companion type's optical size relationships; they define spacing rhythm for the layout system (a logo with airy internal spacing suggests generous, not cramped, layouts); and they provide the unit for clear-space definition per [Logo systems](logo-systems.md) 4.3.

### Step 4: Identify visual characteristics

Characterise the mark's style in controlled vocabulary that later steps must match:

| Dimension | Spectrum | Why it matters |
|---|---|---|
| Weight | Hairline ↔ bold/heavy | Sets the tonal register for type weights, icon strokes, dividers |
| Stroke contrast | Monoline ↔ high-contrast (thick/thin) | A high-contrast logo clashes with monoline icons and vice versa |
| Construction | Geometric ↔ organic/hand-drawn | Dictates graphic language: ruler-precision or warmth and irregularity |
| Style period/association | Modernist, retro, playful, institutional, luxe | Anchors the whole identity's register; see note below |
| Texture | Flat ↔ textured/gradient/3D | Flat marks pair with flat graphic elements; textured marks need restraint elsewhere |
| Density | Enclosed/detailed ↔ open/simple | Detailed marks need quiet layouts and larger clear space |

Style-period attribution requires care: describe what you see ("geometric monoline badge with mid-century lettering") rather than naming a movement you cannot verify, and treat period labels as informed description, not fact.

### Step 5: Examine the logo typography

If the mark contains lettering, determine its status, because three different cases demand different responses:

- **Identifiable typeface.** The lettering matches a real, licensed typeface (verify by comparing distinctive glyphs — a, g, R, terminals — at large scale, not just overall impression). Then that typeface is the natural display type for the identity, and one companion is selected for body text (see [Font pairing](../typography/font-pairing.md)).
- **Custom lettering.** The lettering is a drawing (modified or bespoke letterforms). No typeface will match it exactly; select a companion whose proportions (x-height, cap height, width, weight) sit close to the lettering's, and never attempt to fake the logo lettering by re-typesetting — that violates the immutability rule and never matches.
- **Mixed or uncertain.** Record the evidence and choose the closest match, documenting the residual mismatch as an accepted compromise. Font-identification tools can assist but their output must be verified by glyph comparison; state confidence honestly.

Record for all cases: weight, width, contrast, serif/sans, case, and any distinctive details (spurs, angles, ink traps) that the graphic language may echo.

### Step 6: Determine colour constraints

Extract and classify every colour present: count the palette, convert to HEX/RGB (and estimate CMYK), and identify relationships (complementary, analogous, monochrome — see [Colour theory](../colour/colour-theory.md)). Then set the constraint statements the palette must obey: which colours are locked (the logo's own colours, if colourways are fixed), which are inherited (the logo's colours become the identity's primary roles), and which are open (supporting and neutral colours, to be designed in steps 8 and beyond). If the logo is single-colour or monochrome only, the constraint is different but equally strong: the accent colours of the identity are unconstrained by the mark, and the mark's neutrality must be preserved on all surfaces (see decision table, row 6).

### Step 7: Identify potential supporting motifs (derivation)

Derive, without altering, from the evidence of steps 2–4:

- **Geometric extraction.** Take actual radii, angles, segment counts, spacing intervals from the construction (step 2) and proportion analysis (step 3). A badge built on a 12-segment star yields a 12-division divider and a radial pattern at 30° intervals; a slash at 24° yields an angled cut motif for image frames and section edges.
- **Contour extraction.** Trace the mark's outer silhouette, offset it outward, and use the resulting contour as a frame, a halftone mask or a pattern tile — the silhouette is recognisable without reproducing the mark.
- **Detail echo.** Carry one or two letterform details (a terminal cut, an aperture shape) into icon corners and bullet forms.
- **Weight and rhythm echo.** Set the graphic vocabulary's line weights from the logo's stroke weights (see step 10).

Guardrails: each motif must pass the three-way-distinction test (3.1) — no incorporation, no enclosure, no cropping of the mark itself, subordinate salience — and the motif set stays small (three to five elements). A motif inventory that faithfully restates the logo beats a large library of loose associations.

### Step 8: Develop a complementary colour system

Build the palette on top of the constraints from step 6, following the role structure of [Palette development](../colour/palette-development.md): logo colours (inherited) take primary roles; secondaries are chosen to harmonise with the primary's hue and temperature relationships observed in step 6; neutrals are tuned to the logo's own tonal behaviour (a warm-cream logo on a cool-grey system feels wrong); one accent is allowed for calls-to-action and highlights. Validate every text/background pairing against the contrast requirements in [Colour accessibility](../colour/colour-accessibility.md), including the logo's own pairings where the mark sits on system colours. Specify the palette in HEX, RGB and CMYK, with Pantone equivalents flagged as to-be-verified where no print standard exists.

### Step 9: Select compatible typefaces

Choose display and body type whose anatomy agrees with the logo evidence from steps 4–5: weight register (a heavy geometric badge wants confident, medium-to-bold display type; a hairline mark wants lighter settings), construction (geometric with geometric, organic with humanist or expressive display faces), and era-appropriateness. Then apply the functional criteria from [Typeface selection](../typography/typeface-selection.md): licensing, language coverage, screen rendering, and availability of needed weights. Document the pairing with specimen comparisons against the logo lettering, and record the reasoning — "selected for matching x-height and terminal angle, verified at 48 px and 12 px" — not taste language.

### Step 10: Establish the graphic vocabulary

Consolidate steps 7–9 into the element layer of the identity: line weights (taken from logo strokes), corner radii (from logo geometry), the derived motif set with usage rules, divider and frame conventions, pattern applications, and icon-family style (grid, stroke weight and corner treatment echoing the mark). Define placement zones that respect the logo's clear space on every core template. The result is the graphic language section of the guidelines (see [Brand guidelines](brand-guidelines.md)) and the element library referenced by [Graphic language](../graphic-design/graphic-language.md).

### Step 11: Test the identity without the logo

The recognition test. Produce three or four sample materials — a poster, a social card, a document cover, a web header — with the logo removed and replaced by a neutral placeholder. Then check: (a) **self-consistency** — do the samples look like one family? (b) **anchor recognition** — would someone who knows the organisation recognise the family as theirs, from palette, type and motifs alone? (c) **false-positive check** — do they accidentally resemble another well-known identity? For (b), a quick practical method: show a set of mixed sample materials (some from this identity, some not) to people familiar with the organisation or event and ask which belong to it; above-chance correct attribution indicates the system carries recognition. Informal tests do not replace research, but they catch obvious failures cheaply. If the system fails, the fix is usually stronger reinforcement between components (section 4.11 of [Visual identity](visual-identity.md)), not more decoration.

A minimal repeatable protocol: prepare six to eight sample cards, half from the new identity (logo replaced by a neutral grey placeholder) and half from unrelated organisations; show each card for a few seconds; ask viewers familiar with the organisation to sort "ours" from "not ours", and for every "ours" answer, to name what makes it feel theirs. The named reasons are the diagnostic: "the green" or "that angular cut" identifies which components carry recognition, and a card sorted correctly for no articulable reason is luck, not signal. Weak attribution across the board means the identity leans on the mark and needs stronger reinforcement — a different treatment colour, bolder motif use, tighter type consistency — before release. Keep the cards and results with the project record so the test can be re-run after changes.

### Step 12: Verify no conflict and document prohibited modifications

Two closing actions. First, a **conflict audit**: place the logo back onto every sample and compare against the analysis evidence — does any derived element compete with the mark's weight? does any colour clash with the logo's colours? does any typeface fight the lettering's proportions? does any pattern approach the mark's salience? Fix by subordinating the derived element, never by adjusting the logo. Second, write the **prohibited-modifications list** for the mark — the immutable category (3.1) converted into explicit rules: no redraw, recolour, stretch, rotate, effects, enclosure, cropping, re-typesetting of lettering, unauthorised lockups — using the misuse catalogue and rule-writing style referenced in [Logo systems](logo-systems.md) and [Brand guidelines](brand-guidelines.md). This list becomes the logo section's "never" rules and is enforced through [Brand governance](brand-governance.md).

The list works best as a published, numbered block in the guidelines, addressed to everyone who might touch the files:

```markdown
## Prohibited logo modifications — [Organisation]

This mark is fixed. Without written approval from [owner role]:
1. Do not redraw, trace or recreate the mark. Supplied files only: [paths].
2. Do not recolour outside the approved colourways: [list colourways].
3. Do not stretch, squeeze or re-proportion.
4. Do not rotate or tilt.
5. Do not apply effects: shadows, gradients, outlines, bevels, filters.
6. Do not crop, mask or use the mark partially.
7. Do not enclose the mark in containers, or combine it with words or
   graphics to form new marks.
8. Do not re-typeset the lettering in any font.
9. Do not create unauthorised partner or sponsor lockups (route via [process]).
10. [Project-specific prohibitions from the analysis, with reasons.]

Approved variants and files: [list].  Contact for new needs: [custodian].
```

Each prohibition carries its reason in the guidelines' full rule entries; the block above is the at-a-glance version that travels with every asset handoff.

## 5. Practical application — worked sketch

Consider a fixed event logo: a circular badge, deep indigo on white, containing a geometric 8-point star and the event name in heavy custom slab lettering. The analysis would run: vector source supplied in AI (step 1); geometry reveals an 8-segment star at exact 45° intervals and a circle grid (step 2); symbol height is 0.62 of badge diameter, cap height of lettering 0.35 (step 3); characteristics: heavy weight, monoline slabs, geometric, flat (step 4); lettering is custom — companion type chosen for matching slab weight and cap-height ratio (step 5); palette constraint: indigo is locked as primary; supporting colours to be designed (step 6); motifs: 45° radial divider, star-fragment pattern, badge-contour frame (step 7); palette: indigo primary, warm amber secondary (contrast to indigo but same weight), off-white neutrals, accessibility-checked (step 8); type: geometric slab display + neutral sans body (step 9); vocabulary: 45° cuts on image frames, 8-division pattern at 8% opacity, icons at 2 px stroke matching slab weight (step 10). Then the no-logo test and conflict audit close the loop (steps 11–12). Every decision cites a measured feature of the mark — that is the methodology's signature.

A second sketch shows the constrained case: the fixed logo is a monochrome script wordmark, no symbol. Analysis: no detectable grid — organic lettering (step 2); proportions: tall ascenders, tight letter-spacing (step 3); characteristics: high stroke contrast, elegant, pre-digital register (step 4); typography: custom lettering, so the companion face is a humanist serif matched by x-height and contrast, never an imitation of the script (step 5); colour: the mark is single-colour, so the palette is fully open but restrained by the mark's neutrality (steps 6, 8); motifs: the swash underline becomes the divider motif and its entry angle the image-frame cut (step 7); vocabulary: serif display, hairline rules, generous margins (step 10). The no-logo test matters more than usual here, because a characterful mark can mask a thin system until applications appear without it.

## 6. Analysis worksheet template

Fill this worksheet before any design output. It is the deliverable of steps 1–6 and the citation source for steps 7–10.

```markdown
# Fixed-logo analysis worksheet

## Project
Organisation / event: ______________          Date: ______________
Analyst: ______________                        Logo status (fixed/frozen): ______________

## 1. Artwork inventory
Master file(s) provided: [ ] AI [ ] EPS [ ] PDF [ ] SVG [ ] PNG [ ] JPG   Path/owner: ______
Vector or raster: ______   Raster dimensions/quality: ______   Layers/editable: ______
Colour specs supplied: [ ] HEX [ ] RGB [ ] CMYK [ ] Pantone   Values: ______
Existing distortions or flaws noted: ______

## 2. Geometry
Detected construction: [ ] circles (r = ______) [ ] squares [ ] angles (____°) [ ] grid (____)
Symmetry: [ ] axis ______  /  [ ] none detectable
Construction verdict: geometric / partially geometric / organic (evidence: ______)

## 3. Proportions (measured)
Mark h : w = ______      symbol : cap height = ______
Internal spacing : stroke weight = ______   Other key ratios: ______

## 4. Visual characteristics
Weight: ______  Contrast: ______  Construction: ______
Style description (own words): ______
Texture: ______  Density: ______

## 5. Typography
Lettering status: [ ] identified typeface (name/licence: ______)
                  [ ] custom lettering  [ ] uncertain
Distinctive features to echo: ______  Confidence: ______

## 6. Colour constraints
Locked colours (logo's own): ______
Inherited roles: ______
Open decisions remaining: ______
Relationship observed: [ ] complementary [ ] analogous [ ] monochrome [ ] other: ______

## 7–10. Synthesis (each must cite worksheet evidence)
Motifs derived (≤5) + source feature: 1.______ 2.______ 3.______ 4.______ 5.______
Palette directions + citation: ______
Typeface candidates + match evidence: ______
Graphic vocabulary values (weights/radii/cuts): ______

## 11. No-logo test
Samples produced: ______   Self-consistent: [ ]   Recognisable without logo: [ ]
False positives noted: ______   Actions: ______

## 12. Conflict audit + prohibited modifications
Conflicts found and fixed: ______
Prohibited modifications list written: [ ]  (stored in guidelines section: ______)
```

## 7. Decision table

Given X about the logo, do Y. Each row applies the procedure above to the most common situations.

| Given (observation about the logo) | Do |
|---|---|
| Vector master provided | Build export set and palette from it directly; treat it as the immutable source of truth |
| Only raster artwork exists | Use supplied raster as the only official logo source; design derivatives (patterns, icons) as new vector art that never redraws the mark; escalate request for a vector rebuild through governance; restrict print sizes to raster-safe dimensions |
| Clear geometric construction found | Derive grid, angles and radii for layout, patterns and frames from the construction; document the grid values |
| No detectable grid (organic/hand-drawn mark) | Derive motifs from silhouette contours and details instead; avoid rigid geometric decoration that would clash; favour warmer, irregular supporting elements |
| Heavy/bold mark | Set display type at confident weights; give icons heavier strokes; keep layouts airy to balance density |
| Hairline/light mark | Increase clear space and minimum sizes; choose lighter type registers; protect against thin-stroke drop-out in print |
| High stroke contrast in lettering | Avoid monoline icons and hairline rules; echo contrast in display type and dividers |
| Monoline mark | Keep the whole graphic language monoline; avoid high-contrast display faces |
| Custom lettering in the logo | Never re-typeset; select companion type by measured proportion match; record residual mismatch |
| Identifiable licensed typeface in the logo | Adopt it as display face (verify licence scope); pair with a quiet body face |
| Logo colour(s) fixed and distinctive | Lock them as palette primaries; design secondaries to harmonise; restrict brand-critical surfaces to the locked colours |
| Logo monochrome only | Treat colour as an open system decision; keep the mark neutral on all surfaces; ensure accent colours never recolour the mark |
| Multi-colour logo | Define which colours carry which system roles; limit new palette additions to keep total palette small |
| Enclosed/emblem-style badge | Prefer symbol-with-clear-space usage; avoid enclosing containers in layouts (double-framing); extract interior geometry for motifs |
| Very detailed/ornate mark | Quiet the system: restrained palette, generous whitespace, simple patterns; reserve the mark's detail by never competing with it |
| Logo includes a year/date (typical for events) | Establish the rule for edition changes before launch (which elements change, which persist); see [Brand architecture](brand-architecture.md) |
| Logo contains a photographic or textured element | Treat the texture as immutable; derive motifs only from the non-photographic parts; restrict reproduction contexts where the texture degrades |
| Supplied artwork has baked-in effects (shadows, bevels) | Record them as part of the immutable supplied mark; compensate with a quieter system; consider requesting a flat master via governance |
| Retro or period-styled mark | Decide deliberately: either echo the period in supporting choices (type, texture) or modernise *around* the mark — both are defensible, half-measures are not |

## 8. Common mistakes

- **Designing a parallel identity.** Producing a nice system whose colours and type ignore the mark's evidence, then bolting the logo on. Fix: require every synthesis decision to cite a worksheet field.
- **Incorporating the mark into motifs.** Patterns that contain the badge, frames that crop it — violating the immutability rule. Fix: apply the three-way-distinction test to every derived element.
- **Over-derivation.** Echoing so many features that layouts become logos-in-disguise. Fix: cap the motif set at five and keep salience subordinate.
- **Re-typesetting the lettering.** Recreating the wordmark in a similar font for "flexibility". This alters the mark and never matches. Fix: immutable category, supplied files only.
- **Sampling colours from compressed files.** JPEG artefacts shift hues; palette built from a screenshot drifts from the true brand colour. Fix: sample from the master vector, or the highest-quality source, and flag uncertainty.
- **Skipping the no-logo test.** The system ships, and every application depends on the mark to be recognisable. Fix: run step 11 before releasing templates.
- **Silent conflicts.** A second accent colour close to the logo's hue but not equal to it — reads as a mistake rather than a choice. Fix: the conflict audit in step 12, plus the palette pairing rules.
- **No prohibited-modifications list.** The first vendor or volunteer "improves" the logo. Fix: publish the list in the guidelines and enforce via [Brand governance](brand-governance.md).

## 9. Evaluation checklist

- [ ] Artwork inventory recorded: source format, vector/raster, colour specs, flaws.
- [ ] Geometry and proportions measured and documented as numeric values, with honest "not detectable" verdicts where applicable.
- [ ] Visual characteristics described in controlled vocabulary (weight, contrast, construction, period, texture, density).
- [ ] Logo typography status determined (identified / custom / uncertain) with evidence and confidence.
- [ ] Colour constraints classified as locked / inherited / open.
- [ ] Motif set (≤ 5 elements) derived from documented features; each passes the three-way-distinction test.
- [ ] Palette, typefaces and graphic vocabulary each cite worksheet evidence.
- [ ] No-logo recognition test run and passed (or failing aspects fixed).
- [ ] Conflict audit completed; all conflicts resolved by subordinating derived elements.
- [ ] Prohibited-modifications list written, published in guidelines, and ownership assigned.
- [ ] Immutable/derivable boundary is explicit in the guidelines and templates (no template invites editing the mark).

## 10. Related topics

- [Visual identity](visual-identity.md) — the component inventory this analysis feeds.
- [Logo systems](logo-systems.md) — anatomy, clear space, variants and formats for the fixed mark.
- [Brand guidelines](brand-guidelines.md) — where the analysis results are documented, including prohibited modifications.
- [Brand governance](brand-governance.md) — enforcing the immutable category; requesting vector rebuilds or exceptions.
- [Brand architecture](brand-architecture.md) — edition/year variants of event marks; co-branding with a fixed mark.
- [Palette development](../colour/palette-development.md) — building the complementary colour system (step 8).
- [Colour theory](../colour/colour-theory.md) and [Colour accessibility](../colour/colour-accessibility.md) — relationships and contrast checks behind steps 6 and 8.
- [Typeface selection](../typography/typeface-selection.md) and [Font pairing](../typography/font-pairing.md) — the companion-type method (step 9).
- [Graphic language](../graphic-design/graphic-language.md) — principles for the derived element layer (steps 7 and 10).
- [Composition](../foundations/composition.md) — grid and placement decisions that follow logo proportions.
- [Brand identity checklist](../evaluation/brand-identity-checklist.md) — evaluation companion.

## 11. References

- [accessed] University at Buffalo, "Clear Space — Identity and Brand", https://www.buffalo.edu/brand/identity/usage/Clear-space.html, accessed 2026-11-23 (evidence for the no-new-mark boundary: the interlocking UB may not be combined with other words or graphics to form a new mark).
- [accessed] MIT, "Do/Don't | MIT Brand Guide", https://brand.mit.edu/applying-brand/do-dont, accessed 2026-11-23 (prohibition practice: no redrawing, modifying, deconstructing or repurposing of logo components; lockups used as provided).
- [accessed] Uber Eats, "Marketing Tools & Brand Guidelines for Merchants", https://merchants.ubereats.com/us/en/resources/learning-center/co-marketing-tools, accessed 2026-11-23 (misuse practice: no scaling, wrapping, altering, tilting, recolouring or filters).
- [search-verified] Figma, "What is the golden ratio + how can it elevate your designs?", https://www.figma.com/resource-library/golden-ratio (ratio/circle construction in logos; appeared in search results, not fetched).
- [search-verified] "Logo Grid System, How Professional Designers Build Logos That Last Decades", Medium Design Bootcamp, https://medium.com/design-bootcamp/logo-grid-system-how-professional-designers-build-logos-that-last-decades-9f2d42378364 (grid-based logo construction; appeared in search results, not fetched).
- [canonical] Josef Müller-Brockmann, *Grid Systems in Graphic Design*, Niggli, 1981 — construction and proportion discipline underlying geometric analysis.
- [canonical] Alina Wheeler, *Designing Brand Identity*, Wiley — identity programmes built around an existing mark.
- The ≥ 300 ppi print figure (step 1) and the informal recognition-test method (step 11) are conventional professional starting points, labelled as such; verify against the actual press and research context of the project.
- The twelve-step procedure is this repository's expansion of the fixed-logo extension procedure in the source mission document, synthesised with the sources above.
