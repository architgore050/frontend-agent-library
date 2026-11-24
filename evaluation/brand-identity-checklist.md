# Brand Identity Checklist

## 1. What is it?

A structured checklist for evaluating a brand identity or brand kit — the package of logo assets, colour system, type system, graphic language, application examples and guideline documentation that extends a fixed mark (for example an event logo) into a complete, usable identity. The checklist asks, for every item: what to check, how to check it, and the pass criteria. It is the artefact-specific application of the master method in [design-quality-framework.md](design-quality-framework.md), with brand compliance as the leading dimension.

The typical scenario for this checklist: a logo already exists and is fixed. The evaluation question is not "is the logo good?" but "does the kit built around the logo make the logo usable everywhere, consistently, by people who were not in the room?"

## 2. Why does it matter?

A brand kit fails in specific, recurring ways: a logo provided only as a flat PNG stretched onto a dark banner; a palette with no contrast evidence producing unreadable text pairs; a "complete" guideline document that never says which colour may sit behind white text. Each failure multiplies — every downstream designer and every future agent inherits it. Checking the kit before release is cheaper than discovering the gaps in the first campaign that uses it.

There is also a reusability contract: this library explicitly targets extending a fixed event logo into a brand kit that works for future projects, events and organisations. A kit that passes this checklist is transferable; one that relies on undocumented assumptions is not.

## 3. Core principles

**Principle 1 — Completeness is judged against use, not against a universal template.** A kit is complete when a designer who has never seen the brand can produce a business card, a slide and a social post without asking questions. List the expected use cases first, then verify the kit covers them.

**Principle 2 — Every rule must be testable.** "Use the colours thoughtfully" is not a rule. "Body text uses ink on paper only; the accent colour is reserved for interactive and highlight elements" is. The checklist rewards kits whose documentation states pass/fail-able conditions, consistent with the objective/subjective split in [design-quality-framework.md](design-quality-framework.md).

**Principle 3 — Contrast evidence is mandatory, not optional.** A colour system without measured text/background pairs is unverified. This checklist requires actual ratios for the approved pairings.

**Principle 4 — The documentation is a deliverable, not an afterthought.** A kit with perfect assets and no guidelines is half a kit. Section 5.7 scores documentation as rigorously as the logo.

**Principle 5 — Distinguish what is fixed from what is flexible.** The logo (or its elements) is given; the kit's flexible layers (supporting graphics, layout conventions, voice) are evaluated for coherence and coverage, not conformance to a pre-existing rulebook. Where this checklist says "consistent", the reference is internal coherence of the kit itself.

## 4. How it works

The checklist has eight sections (A–H). Work through them in order; each item has *what to check*, *how*, and *pass criteria*. Score each item Pass / Partial / Fail and record evidence. Items marked **[B]** are blockers per the severity model in [design-quality-framework.md](design-quality-framework.md) — a kit with any [B] failed is not releasable.

### 4.1 How to run it

1. Collect the kit's contents: logo files, colour values, type files/licences, graphics, templates, guideline document, exports.
2. Verify each section; where measurement is required (contrast, sizes, clear space), measure and record the number in the evidence column.
3. Score and classify defects using the severity model; propose corrections; re-check after fixes (the loop in §6 of [design-quality-framework.md](design-quality-framework.md)).

## 5. Practical application — the checklist

### A. Completeness of components

| # | What to check | How | Pass criteria |
| --- | --- | --- | --- |
| A1 | Logo variants cover the real use cases: primary, horizontal, stacked/square, icon-only/app badge, monochrome (all-black and all-white) | List variants; map each to a realistic application | Every plausible placement (light ground, dark ground, photo ground, tiny favicon, square avatar) has a designated variant |
| A2 | File formats: vector (SVG/AI/PDF/EPS) and raster (PNG with transparency at ≥ 2× typical display size) | Open every file; check vector files scale without artefacts; check PNG transparency actually transparent | Vector sources exist for every variant; raster exports are sharp at target sizes |
| A3 | Colour values supplied in needed models: HEX + RGB (screen), CMYK + Pantone or equivalent (print) | Compare values across documents | One authoritative value set; no silently divergent duplicates |
| A4 | Typography: licensed font files or documented web-safe/free substitutes | Attempt to install/use as a new designer would | Fonts usable without extra purchases or licensing ambiguity |
| A5 | Supporting assets: graphic language elements (patterns, shapes, icon set), imagery style guidance, sample applications | Inventory against the expected use cases from §3 Principle 1 | Every planned application type has the assets it needs |

### B. Logo rules

| # | What to check | How | Pass criteria |
| --- | --- | --- | --- |
| B1 | Clear space defined **[B]** | Find the stated exclusion zone (an x-height margin, a fixed unit, or a margin box) | A measurable rule exists; verify on 3 sample layouts that nothing enters the zone |
| B2 | Minimum sizes defined | Find the stated minimum per variant (print mm, screen px) | Rule exists and is realistic (icon remains legible at stated minimum — test at that size) |
| B3 | Misuse rules stated **[B]** | Look for an explicit prohibition list | Covers at least: stretch/skew, rotation, recolour, drop shadows/effects, re-composition, low-contrast grounds |
| B4 | Dark/light/photo-ground rules | Check guidance for each ground type | For each ground: which variant, and (for photo) what treatment if contrast is insufficient |
| B5 | Logo reproduced from official files in all templates | Compare template logo pixels to the official asset (overlay or diff) | Byte-level or visually identical; no re-traced or scaled-up raster versions |

### C. Colour system with roles and contrast evidence

| # | What to check | How | Pass criteria |
| --- | --- | --- | --- |
| C1 | Palette defined with roles: primary, secondary, accent, neutrals, semantic (success/warning/error if digital) | Read the role table; check each colour has exactly one primary role | Every colour role-named; no orphan colours |
| C2 | Contrast evidence for text pairs **[B]** | Measure ratio for every sanctioned text/background pairing (WCAG relative luminance; method in [../accessibility/wcag-fundamentals.md](../accessibility/wcag-fundamentals.md)) | Body text pairs ≥ 4.5:1; large text and UI ≥ 3:1; failing pairs are explicitly forbidden in the documentation |
| C3 | Dark-ground palette behaviour verified | Render white logo + key text pairs on the darkest neutral and the primary | Same thresholds as C2 |
| C4 | Proportion guidance (e.g. 60/30/10 or equivalent) | Check the documented usage balance guidance | A stated, sane distribution exists; consistent with the palette's roles |
| C5 | Colour values match across all kit files | Sample the values used in templates/exports against the master list | Zero divergent values (token discipline, see [../design-systems/design-tokens.md](../design-systems/design-tokens.md)) |

### D. Type system with hierarchy

| # | What to check | How | Pass criteria |
| --- | --- | --- | --- |
| D1 | Typeface roles assigned (display, headings, body, data) and families limited (≤ 2–3) | Read the type section; count families | Each role has a designated face and weight set |
| D2 | Type scale defined **[B]** | Look for the size ladder (e.g. a modular scale or explicit px/pt list) | A scale exists; all templates draw from it (no off-scale sizes in templates) |
| D3 | Hierarchy demonstrable: minimum 3 distinguishable levels with size and/or weight contrast | Render a sample text block from the kit's own rules | Levels distinguishable at the artefact's realistic viewing size; heading/body ratio ≥ 1.5 (conventional starting point) |
| D4 | Line-height and measure guidance for running text | Check documented values | Line height ≈ 1.4–1.6 × size (conventional); measure guidance exists for text-heavy applications |
| D5 | Fallbacks for environments without the brand fonts (email, slides made by others, constrained platforms) | Read fallback rules | Named fallback stack or substitute face documented |

### E. Graphic language coherence

| # | What to check | How | Pass criteria |
| --- | --- | --- | --- |
| E1 | Graphic elements derive from or harmonise with the logo's visual logic (shared geometry, motif, stroke weight, corner treatment) | Compare supporting graphics to the logo's construction | A describable relationship exists; state it in evidence (e.g. "pattern built from the logo's 12° chamfer") |
| E2 | Icon style consistent (single family, single stroke weight, single corner radius) | Compare all icons in the kit | One system; no mixed metaphors for the same concept |
| E3 | Imagery treatment defined (colour grading, composition rules, or explicit "no photography" decision) | Read and test against supplied sample images | Samples comply with the stated treatment |
| E4 | Layout system for applications (margins, grid or safe margins per format) | Check templates | Same margins/grid logic across formats; content respects the safe area |

### F. Application prototypes tested

| # | What to check | How | Pass criteria |
| --- | --- | --- | --- |
| F1 | Mockups exist for the priority applications (at minimum: one print item, one social item, one screen/slide item) | Inventory mockups against expected use cases | Each priority application rendered from the kit's own assets |
| F2 | Each mockup checked with the artefact checklists | Run [poster-checklist.md](poster-checklist.md), [social-media-checklist.md](social-media-checklist.md), [presentation-checklist.md](presentation-checklist.md) as applicable on the mockups | Each mockup passes the relevant checklist's blocker items |
| F3 | Edge cases exercised: logo on the busiest background, longest name/word, smallest sanctioned size | Render these three stress cases | All legible and rule-compliant |
| F4 | Responsive behaviour for digital applications (logo lockups at narrow widths, grid collapse) | Resize the digital mockups | Defined behaviour (which lockup swaps in when) exists and works |

### G. Accessibility tested

| # | What to check | How | Pass criteria |
| --- | --- | --- | --- |
| G1 | All sanctioned text pairs measured (links to C2) — including text over imagery rules | Re-measure independently; include the "text on photo" recipe (e.g. scrim/overlay specification) | No sanctioned pair below threshold; the photo-text recipe guarantees contrast |
| G2 | Colour never the sole carrier of meaning in kit templates | Inspect templates (status colour + label? links underlined/bold?) | Meaning duplicated by text, weight or icon |
| G3 | Minimum sizes respected in the kit's own templates | Check smallest text in each template | Template minimums meet the medium's floor (web body ≥ 16 px conventional; slides ≥ 24 pt per published guidelines) |
| G4 | Logo variant usable by low-vision viewers (monochrome, high contrast against the ground) | Render monochrome variants on all grounds | Distinct silhouette at small size and in monochrome |

### H. Guideline documentation quality

| # | What to check | How | Pass criteria |
| --- | --- | --- | --- |
| H1 | Structure covers: logo rules, colour (with values and roles), type, graphic language, applications, misuse, asset index | Read the document's table of contents | All sections present with real content (no empty sections — see [design-quality-framework.md](design-quality-framework.md) §4.1 dimension 9) |
| H2 | Every rule testable (pass/fail form) | Sample 10 rules at random; attempt to falsify each | ≥ 9 of 10 decidable without asking a person |
| H3 | Do's and don'ts illustrated | Look for visual examples | Misuse rules have "don't" images; key rules have "do" images |
| H4 | Versioning and source-of-truth stated | Check document header/footer | Version, date and the location of master assets stated |
| H5 | Asset export quality **[B]** | Open every export; check naming, transparency, resolution, formats; check no placeholder or stale assets | Every file opens correctly, is named sensibly, and matches the documented values |

## 6. Decision framework

Scoring: each item Pass / Partial / Fail. Compute per-section pass rate; a kit is release-ready when **every [B] item passes and ≥ 80% of all items pass with no failed item in sections C, D, G or H** (those sections define the system itself). Typical correction priorities:

1. Missing contrast evidence (C2) — cheapest high-value fix: measure the existing pairs and forbid the failures.
2. Missing misuse rules (B3) and clear space (B1) — one paragraph + one diagram each.
3. Off-scale type in templates (D2) — mechanical fix once the scale exists.
4. Missing fallbacks (D5) and dark-ground behaviour (C3) — prevents the most common downstream breakage.
5. Documentation gaps (H1–H3) — write rules as you fix assets, so they stay in sync.

Corrections follow the proposal-and-re-evaluation loop in [design-quality-framework.md](design-quality-framework.md) §6.

## 7. Examples

**Example 1 — event kit, mostly complete.** A festival logo kit has: primary + white variants, 5 colours with HEX/RGB but no CMYK, one display face and one text face, a pattern derived from the logo's wave, and a 6-page PDF. Findings: C1 partial (no role table); C2 fail (no contrast evidence — measuring revealed the accent yellow on white at 1.9:1, now forbidden for text); D2 pass (scale in PDF); F1 partial (no slide mockup); H1 partial (no misuse section). Verdict: not release-ready; five corrections, all cheap; re-check after fixes.

**Example 2 — kit with a blocker.** A conference kit provides the logo only as a 1200 px JPG on white. B1–B3 all undocumented; the JPG is being scaled onto dark banners and visibly fringes. This is a [B] chain: vector sources missing (A2 fail), no dark-ground rule (B4 fail). Correction: obtain/regenerate vector assets first — every other logo fix depends on it. Prioritisation follows §6: the dependency rule beats the severity ordering here because the vector asset unblocks the rest.

**Example 3 — a "partial" done right.** A kit permits "accent colour on section dividers, never behind text". This is testable (divider = decorative, not text-bearing), illustrated, and consistent with C2's forbidden list. A Partial rating would be wrong here — it is a Pass; evidence: the rule's falsifiability and the contrast table excluding text pairs for the accent.

## 8. Common mistakes

- **Evaluating the logo instead of the kit.** The logo is fixed; the checklist judges whether the system around it works.
- **Accepting a palette without measured pairs.** "The colours look fine" is not contrast evidence; measure or fail.
- **Treating the guideline PDF as proof of compliance.** Templates and exports drift from documents; verify values in the artefacts, not the brochure (H5, C5).
- **Checking only the happy ground.** White logo on white background, long names, and tiny sizes are where kits actually break — use the stress cases (F3).
- **Mockups that never get checked.** A mockup is an evaluation input; run the relevant artefact checklist on it (F2), otherwise it is decoration.
- **Scoring documentation leniently.** Beautiful prose with untestable rules fails H2; rewrite rules in pass/fail form.
- **Ignoring licensing.** Unlicensed or ambiguous font rights (A4) is a real-world blocker that visual review misses entirely.

## 9. Evaluation checklist

- [ ] All sections A–H completed with evidence recorded, not ticked from memory.
- [ ] Every [B] item (A2, B1, B3, C2, D2, H5) explicitly passed.
- [ ] Contrast ratios recorded as numbers for every sanctioned pair, including text-on-photo recipe.
- [ ] Colour values cross-checked between master list, templates and exports (zero divergence).
- [ ] Type scale verified against every template (no off-scale sizes).
- [ ] Stress cases rendered (busiest background, longest word, smallest size).
- [ ] Each application mockup run through its artefact checklist.
- [ ] Documentation sampled for testability (H2 sample of 10 rules).
- [ ] Findings classified and prioritised per the severity model; corrections proposed with risk.
- [ ] Re-evaluation completed after fixes.

## 10. Related topics

- [design-quality-framework.md](design-quality-framework.md) — the master method, severity model and report template.
- [poster-checklist.md](poster-checklist.md) · [social-media-checklist.md](social-media-checklist.md) · [presentation-checklist.md](presentation-checklist.md) · [website-visual-qa.md](website-visual-qa.md) — checklists for the application mockups (section F).
- [../design-systems/design-tokens.md](../design-systems/design-tokens.md) — token model for value discipline (C5).
- [../accessibility/wcag-fundamentals.md](../accessibility/wcag-fundamentals.md) — contrast definitions and measurement method.
- [../foundations/principles-of-design.md](../foundations/principles-of-design.md) — hierarchy and coherence principles behind sections D and E.

## 11. References

This checklist is a synthesis of the library's own theory files and established identity-guideline practice; no single external source defines it.

- W3C, "Web Content Accessibility Guidelines (WCAG) 2.1" — contrast thresholds applied in section C/G. [canonical]
- American Institute of Graphic Arts (AIGA), brand and identity design resources — professional convention for logo variant sets, clear space and misuse rules. [canonical]
- British Standards Institute / ISO-style corporate identity manual tradition (e.g. the identity manual genre exemplified by historical corporate standards such as the 1970s–80s corporate identity manuals) — basis for documentation structure in section H. [canonical]
- W3C Web Accessibility Initiative, "Understanding Success Criterion 1.4.10: Reflow", https://www.w3.org/WAI/WCAG21/Understanding/reflow.html — referenced for digital application testing (F4). [search-verified, accessed 2026-11-23]
