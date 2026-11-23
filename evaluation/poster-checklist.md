# Poster Checklist

## 1. What is it?

A checklist for evaluating posters — printed or digital display artefacts meant to be read from a distance, briefly, by someone passing by. It covers information completeness, hierarchy at distance, contrast, print production specifications, identity compliance and the characteristic poster defects. It applies the master method of [design-quality-framework.md](design-quality-framework.md) to the poster's defining constraint: one fixed canvas, one glance, no interaction.

The evaluation question for a poster is never "does it look good close up?" It is "does a person walking past at 2–10 metres receive the right message in the right order, and can this file be printed correctly at size?"

## 2. Why does it matter?

Posters fail differently from screen artefacts. A website defect can be patched after release; a poster defect is printed a hundred times. Wrong dates, missing bleed and unreadable-from-distance text are the three classic poster failures, and all three are invisible when the file is reviewed at desk distance on screen. The checklist forces evaluation at the artefact's real conditions: viewing distance, print scale and physical environment.

Posters are also the most common first application when extending a fixed event logo into a kit (the library's core use case): the poster exercises logo clear space, colour grounds, type hierarchy and print production in a single artefact.

## 3. Core principles

**Principle 1 — One message, one glance.** A poster communicating an event needs a strict attention order: primary hook (title or image) → event identity → key details (date, time, venue) → action (CTA, QR, URL). Everything else is secondary and must not compete. The squint test from [design-quality-framework.md](design-quality-framework.md) §4.1 (dimension 1) is the primary instrument here.

**Principle 2 — Size is a function of distance, not of taste.** Type size for posters is derived from viewing distance using letter-height conventions (§5.2). A headline that reads beautifully on screen at 100% may be illegible at 4 metres; conversely, body detail never read from distance does not need to be large — it needs to be findable up close.

**Principle 3 — The print file is part of the design.** Bleed, safe area, resolution and colour mode are not production footnotes; a poster without them is a failed poster. These are objective, binary checks (§5.4).

**Principle 4 — Information accuracy outranks everything.** A poster with the wrong date is worse than a poster with no date: it actively misleads. All facts are verified against the source of truth before aesthetic review (§5.1), per the severity model — information errors are blockers.

**Principle 5 — Identity compliance is contextual.** Where a brand kit exists, the poster must comply (logo rules, palette, type). Where the poster *is* the identity's first application, coherence with the fixed logo governs (E-section of [brand-identity-checklist.md](brand-identity-checklist.md)).

## 4. How it works

Evaluate in this order: facts first (they gate everything), then distance legibility, then contrast and hierarchy, then identity, then print production. Each item: what to check, how, pass criteria. Severity per the blocker/major/minor/polish model.

## 5. Practical application — the checklist

### 5.1 Information completeness and accuracy

| # | What to check | How | Pass criteria |
| --- | --- | --- | --- |
| I1 | Required facts present: event/subject name, date, time, venue/location, price (if any), CTA or contact | Read the poster once; list every fact against the brief | Every brief-required fact present; absence of a fact the brief did not require is fine |
| I2 | Facts verified against source of truth **[B]** | Cross-check each fact with the brief, calendar or database — never with memory or the poster's own consistency | Zero discrepancies; any unverifiable fact marked as assumption in the report |
| I3 | Date format unambiguous | Check the date string | Format resolves the year and the day/month order for the audience (e.g. "Sat 14 March 2026", not "14/03") |
| I4 | CTA is singular and actionable | Identify the action (visit URL, scan QR, buy ticket, "just come") | Exactly one primary action, stated as an imperative or clearly signalled |
| I5 | QR code / URL tested **[B]** | Scan the QR from the file and at printed scale if possible; type the URL | Destination correct; QR sized ≥ ~2 × 2 cm printed with quiet zone and tested contrast |
| I6 | No placeholder content | Search for "lorem", "TBC", "XXX", dummy URLs | None present |

### 5.2 Hierarchy at distance (with the sizing convention)

The established sign/letter-height convention: **about 1 inch (≈ 25 mm) of capital letter height per 10 feet (≈ 3 m) of viewing distance for comfortable reading; roughly 1 inch per 20–30 feet as a minimum legibility bound.** Sources give the comfortable figure at 1 inch/10 ft and a minimum at 1 inch/20–30 ft; treat this as a **convention, not a law** — it assumes sans-serif capitals in decent contrast, and it is for headline/destination text, not body detail. Converting: 1 inch ≈ 72 pt in print terms for capital height purposes (the point size approximates the cap height plus leading, so use cap-height ≈ 0.7 × point size as a sanity check).

Derived working table (conventional starting point — verify against the real venue):

| Viewing distance | Comfortable cap height | Approx. point size (cap ≈ 0.7 × pt) | Typical role |
| --- | --- | --- | --- |
| 1.5 m (corridor, shop window) | ≥ 4 mm | ≥ ~16 pt | smallest readable detail up close |
| 3 m (office, café wall) | ≥ 8 mm | ≥ ~24–32 pt | secondary details, date/venue |
| 5 m (street poster) | ≥ 13 mm | ≥ ~48–60 pt | title readable, details glanceable |
| 10 m (roadside, hall back) | ≥ 25 mm | ≥ ~90–120 pt | title only; everything else is texture |

| # | What to check | How | Pass criteria |
| --- | --- | --- | --- |
| H1 | Title size vs. realistic distance | Measure cap height; apply the convention above | Title cap height meets the comfortable figure for the intended distance |
| H2 | Squint test order | Blur/squint; list readable elements in order | Order matches: hook → identity → details → action; exactly one dominant element |
| H3 | Three-level hierarchy minimum | Identify title / details / support levels | Levels distinguishable by size and/or weight; body detail still findable at 1.5 m |
| H4 | No competing equal-weight elements | Count elements at or near maximum contrast/size | ≤ 1 dominant; competing pairs are a Major |
| H5 | Reading flow logical (language direction, Z/F pattern) | Trace the eye path | No dead centre unless deliberate; path lands on the CTA |

### 5.3 Contrast and legibility

| # | What to check | How | Pass criteria |
| --- | --- | --- | --- |
| C1 | Every text pair measured **[B]** | Compute WCAG-style ratio for each text/background pair (method: [../accessibility/wcag-fundamentals.md](../accessibility/wcag-fundamentals.md)) | Apply print-adjusted judgement: aim ≥ 4.5:1 for detail text, ≥ 3:1 for large title text; below 3:1 anywhere is a Blocker |
| C2 | Text over imagery | Check for scrim/overlay/panel treatment | Contrast guaranteed at the text, not the average image |
| C3 | Reversed-out text (light on dark) tested | Measure; view a print proof or simulate dot gain | Reversed text slightly heavier weight/looser tracking than positive (conventional print practice) |
| C4 | Colour-only meaning avoided | Check any colour-coded info | Meaning duplicated by label or symbol |
| C5 | Environmental contrast (real surface) | Consider glass glare, night lighting, wall texture if known | Design still legible under the likely worst condition; where unknown, note as assumption |

### 5.4 Print production specifications

| # | What to check | How | Pass criteria |
| --- | --- | --- | --- |
| P1 | Bleed **[B]** | Inspect document setup | Bleed present on all sides — commonly 3 mm for small-format, 5 mm for large format (conventional; confirm with the printer) |
| P2 | Safe area **[B]** | Measure distance from trim to nearest text/logo/QR | No critical content within ~3–5 mm of trim (conventional); QR further out |
| P3 | Resolution **[B]** | Check effective DPI at final printed size | ≥ 300 DPI at 100% for close viewing; large-format viewed from distance can drop to ~100–150 DPI (conventional; confirm with the printer) |
| P4 | Colour mode | Check document mode | CMYK (or printer-specified); spot/Pantone only where specified; RGB files rejected for offset/litho |
| P5 | Fonts embedded or outlined | Check export settings | No font-substitution risk at the printer |
| P6 | Rich black / registration | Inspect large black areas | Rich black build for large solids per printer spec (commonly C40 M30 Y30 K100 — conventional); fine black text 100 K only |
| P7 | Export integrity | Open final PDF; check page size includes bleed, no hidden layers, images not downsampled | File opens clean at correct dimensions |

### 5.5 Identity compliance

| # | What to check | How | Pass criteria |
| --- | --- | --- | --- |
| L1 | Logo from official assets, correct variant | Compare against the kit's files ([brand-identity-checklist.md](brand-identity-checklist.md) A1/B5) | Official file, unmodified |
| L2 | Clear space respected | Measure the exclusion zone | Nothing inside the stated zone |
| L3 | Minimum size respected | Measure logo height | ≥ the kit's stated minimum |
| L4 | Ground rules | Check logo contrast against its ground | Kit's light/dark/photo rules followed |
| L5 | Palette and type discipline | Sample used colours and type sizes against the kit | Zero stray colours; type from the kit's scale or documented exceptions |

## 6. Decision framework

Priorities for posters, in order: (1) I2/I5 information and destination accuracy — a wrong fact invalidates the print run; (2) P1–P3 production blockers — the file cannot go to print; (3) C1 contrast failures on detail text; (4) H1/H2 distance failures; (5) identity items; (6) polish (spacing refinement, decorative coherence). The distance convention is the decision tool for H1: if the title fails the convention for the stated distance, the correction is a scale change to the hierarchy, not a re-design of the concept. Re-evaluate after corrections with the loop in [design-quality-framework.md](design-quality-framework.md) §6 — a resized title changes the hierarchy, so H2 is always re-run after H1 corrections.

## 7. Examples

**Example 1 — street poster for a festival.** Title 120 pt (cap ≈ 22 mm — meets ~5 m comfortable), date "Sat 14 March 2026" at 28 pt (glanceable at 3 m, verified against the calendar), QR 25 × 25 mm with white quiet zone, bleed 3 mm, CMYK, logo clear space 10 mm respected. Findings: C2 — title overlaps a photo without a scrim, measured 2.4:1 at the title's worst region → Blocker; proposal: 40% dark scrim panel behind the title block; risk: dampens the image's brightness in that corner — re-check C2 and H2 after. Everything else passes.

**Example 2 — classroom poster that fails the convention.** A0 poster with a 40 pt title intended for a 10 m hall. Convention says ≥ 90–120 pt at 10 m. Correction: title to ~110 pt, drop the subtitle into the details level, re-run the squint test. Also caught: date as "14/03" (I3 fail — ambiguous for an international audience), corrected to "14 March 2026".

**Example 3 — digital-only "poster" (screen display).** Same checklist applies with substitutions: P1–P7 collapse to export pixel dimensions and safe margins for the screen; the distance table still governs type sizes (viewing distance ~2–3 m for a lobby screen). The reviewer states this adaptation explicitly in the report rather than silently skipping section 5.4.

## 8. Common mistakes

- **Reviewing at desk distance.** The most common poster review error. Simulate distance: zoom out to 10–15%, print a thumbnail, or apply the convention table (§5.2).
- **Beautiful-but-empty.** Strong concept, missing venue or an ambiguous date — hierarchy failures are majors, fact failures are blockers.
- **Multiple CTAs.** "Scan the QR, visit the site, follow us, buy tickets" is four messages; choose one primary action and let the rest be findable details.
- **Text over busy imagery without a scrim** — the single most common contrast failure on posters.
- **RGB file sent to a CMYK printer**, or bleed omitted because "the printer will handle it" — some will, some will not; the safe assumption is the file must be correct.
- **Decorative fonts for critical facts.** A display face acceptable for the title may be illegible for the venue line; facts get the most legible level available.
- **Treating the convention table as law.** It assumes sans-serif capitals and good contrast; serif faces, italic, low contrast and non-Latin scripts shift the numbers — say so in the report when relevant.

## 9. Evaluation checklist

- [ ] All brief-required facts present and verified against the source of truth (I1–I2).
- [ ] Date, time and venue formats unambiguous for the audience (I3).
- [ ] One primary CTA; QR/URL scanned/typed and correct (I4–I5).
- [ ] Title cap height meets the distance convention for the stated viewing distance (H1).
- [ ] Squint-test order matches message order; one dominant element (H2, H4).
- [ ] Every text pair measured; scrim present over imagery; no colour-only meaning (C1–C4).
- [ ] Print specs: bleed, safe area, DPI, colour mode, fonts embedded, export integrity (P1–P7).
- [ ] Logo variant, clear space, minimum size and ground rules per the kit (L1–L4).
- [ ] Findings classified and prioritised per §6; corrections carry risk notes.
- [ ] Re-evaluation re-ran H2 after any scale change.

## 10. Related topics

- [design-quality-framework.md](design-quality-framework.md) — master method, severity model and report template.
- [brand-identity-checklist.md](brand-identity-checklist.md) — logo rules and kit values referenced by section 5.5.
- [social-media-checklist.md](social-media-checklist.md) — sibling display format with the same hierarchy-at-a-glance logic.
- [../foundations/principles-of-design.md](../foundations/principles-of-design.md) — hierarchy, contrast and composition theory.
- [../foundations/design-critique.md](../foundations/design-critique.md) — critique stance for one-glance artefacts.
- [../accessibility/wcag-fundamentals.md](../accessibility/wcag-fundamentals.md) — contrast ratio definitions and measurement.

## 11. References

This checklist is a synthesis of the sources below and the library's theory files; the viewing-distance table is a convention, marked as such.

- "Typography & Viewing Distance Guide for Digital Signage", digitalsignage.com — 1 inch letter height per 10 feet comfortable, 1 inch per 20 feet minimum convention. https://digitalsignage.com/digital_signage/docs/guides/typography-viewing-distance [search-verified, accessed 2026-11-23]
- "Letter Height and Viewing Distance: How Big Should Sign Letters Be", Arrowhead Sign Company — 1 inch per 30 feet rule-of-thumb variant. https://arrowheadsigncompany.com/blog/letter-height-viewing-distance [search-verified, accessed 2026-11-23]
- Josef Müller-Brockmann, *Poster Designs* and *Grid Systems in Graphic Design*, Niggli — poster composition and grid conventions. [canonical]
- W3C, "Web Content Accessibility Guidelines (WCAG) 2.1" — contrast ratio definitions applied in §5.3. [canonical]
