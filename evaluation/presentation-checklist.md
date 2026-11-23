# Presentation Checklist

## 1. What is it?

A checklist for evaluating slide decks and presentations as visual artefacts: slide hierarchy, projection legibility (type sizes), data slide quality, template consistency, image quality, and the narrative flow of the deck's visual devices. It applies the master method of [design-quality-framework.md](design-quality-framework.md) to the presentation's defining conditions: one large screen, a seated audience, a fixed sequence, and a presenter competing for attention.

The deck is judged as a *sequence*, not as a stack of independent posters. The unit of evaluation includes the transitions between slides — whether the visual system carries the argument from beginning to end.

## 2. Why does it matter?

Presentation defects differ from web and print defects in one crucial way: the audience cannot re-read, zoom or scroll back. A slide that is legible only in the source file — dense charts, 12 pt footnotes, low-contrast projectors wash-outs — simply fails in the room, in real time. Published accessibility guidance for presentations converges on a minimum body text of 24 pt for exactly this reason.

Presentations are also where data visualisation quality is most exposed: the axis label nobody can read from row 12 is a data slide failing its only job. This checklist defines the presentation-level criteria and defers chart-specific judgement to [../information-design/data-visualisation.md](../information-design/data-visualisation.md).

## 3. Core principles

**Principle 1 — Projection is the medium.** Evaluate in presentation conditions: dark or bright room, projector or TV wash-out, last-row viewing distance. A deck reviewed only on a laptop screen at 100% has not been reviewed. Projectors commonly lose contrast versus LCD screens — dark text on light grounds survives better than light-on-dark in bright rooms (context-dependent recommendation; know the room).

**Principle 2 — Type size floors are real standards, not taste.** Published presenter-accessibility guidance (e.g. the Association of Research Libraries' PowerPoint guidelines) sets a minimum of 24 pt for body text; a widely cited ACS slide-accessibility guideline recommends ~28–38 pt titles with ≥ 24 pt body. Treat these floors as conventions with sources, not universal laws — dense reference decks for on-screen reading differ from projected talks.

**Principle 3 — One slide, one point.** A slide is a unit of argument. If a slide carries two points, the audience reads ahead of the speaker or misses one. Titles state the point, body supports it, and everything else leaves.

**Principle 4 — The deck is a system with a narrative.** Template consistency makes individual slides free; recurring visual devices (section dividers, progress markers, consistent chart styles) carry the story. Evaluate both the per-slide quality and the sequence-level rhythm (§5.5).

**Principle 5 — Data slides obey visualisation rules first.** Chart type, label legibility, colour encoding and honesty of scales are chart criteria — checked here at deck level (legible from the back row, consistent styling) and in depth by the data-visualisation domain file.

## 4. How it works

Review the deck twice. **Pass 1 — sequence:** flip through at speed; check narrative flow, template consistency, section rhythm and slide-per-point discipline. **Pass 2 — per-slide detail:** check title/body hierarchy, type floors, contrast, data slides, and image quality slide by slide. Then verify the technical envelope (aspect ratio, fonts embedded, media tested). Classify defects with the standard severity model; a legibility blocker on the keynote's core slide outranks a dozen cosmetic majors.

## 5. Practical application — the checklist

### 5.1 Slide hierarchy

| # | What to check | How | Pass criteria |
| --- | --- | --- | --- |
| H1 | Title states the point, not the topic | Read titles alone, in order — they should form the deck's skeleton | Title sequence reads as a summary of the argument (assertion-evidence style is a common convention, not a law) |
| H2 | One point per slide | Inspect each slide's content | One primary message; two co-equal messages is a Major — split the slide |
| H3 | Per-slide hierarchy | Squint test per slide ([design-quality-framework.md](design-quality-framework.md) §4.1) | Title dominant, then supporting element, then detail; ≤ 3 levels |
| H4 | Body density | Count lines/bullets per slide | Conventional ceiling ~5–6 bullets × ~6–8 words for spoken decks; dense handout decks are a different genre — say which this is |
| H5 | Emphasis devices consistent | Check how highlights are marked across slides | One emphasis vocabulary (bold, colour chip, or box) used consistently |

### 5.2 Projection legibility

| # | What to check | How | Pass criteria |
| --- | --- | --- | --- |
| L1 | Body text ≥ 24 pt **[B]** | Sample smallest body text on content slides | ≥ 24 pt per published presenter guidance (ARL; ACS recommends 28–38 pt titles, ≥ 24 pt body); smaller only for labelled handout decks, noted as exception |
| L2 | Titles ≥ ~28–38 pt (conventional) | Sample title sizes | Title clearly dominant over body at the back of the room |
| L3 | Back-row test | Render one slide at reduced zoom (~25–30% on a laptop ≈ hall distance) or project | All content the audience needs (not speaker notes) readable |
| L4 | Contrast survives the projector **[B]** | Measure text pairs ([../accessibility/wcag-fundamentals.md](../accessibility/wcag-fundamentals.md)); test on the actual projector if possible | ≥ 4.5:1 body, ≥ 3:1 large text in the file; verified wash-out behaviour in the room |
| L5 | Colour scheme matches room lighting | Consider dark-room decks (light-on-dark) vs. bright rooms (dark-on-light) | Deliberate, stated choice; not a default left unexamined |
| L6 | Speaker notes not on slides | Check slide surface vs. notes pane | Notes in notes pane; no paragraphs of prose on slides |

### 5.3 Data slide quality (deck-level criteria)

| # | What to check | How | Pass criteria |
| --- | --- | --- | --- |
| D1 | Chart legible from the back row | Back-row test on data slides; smallest text in charts (axis, legend, labels) | Axis/legend text ≥ ~18–20 pt on a 16:9 slide (conventional floor derived from L1's proportion); data labels readable |
| D2 | One message per chart | Check each chart's title and take-away | Chart makes one point; a stated take-away (title or callout) exists — not a raw data dump |
| D3 | Consistent chart styling across the deck | Diff colours, fonts and gridlines across all charts | One visual grammar for charts; same series = same colour everywhere |
| D4 | Encoding honesty | Check axis baselines, truncated scales, dual axes, 3D effects | No misleading scale tricks ([../information-design/data-visualisation.md](../information-design/data-visualisation.md) is the authority) |
| D5 | Tables | Check table slides | Tables on slides limited to ≤ ~5 rows × 5 cols (conventional); bigger data becomes a chart or a handout |
| D6 | Data-ink discipline | Inspect decoration on data slides | Gridlines light, no 3D pie, no drop-shadow charts (conventional professional practice) |

### 5.4 Template consistency

| # | What to check | How | Pass criteria |
| --- | --- | --- | --- |
| T1 | Master slides used, not hand-built layouts | Inspect slide layout inheritance | Content slides derive from masters; off-master one-offs are deliberate and few |
| T2 | Logo, footer, page numbers uniform | Diff repeated elements across all slides | Identical position/size everywhere (or correctly omitted on section dividers per the template's rule) |
| T3 | Margins and safe edges constant | Inspect content bounds per layout | Content respects the template's margins; nothing crowds the projector's overscan edge (conventional ~3–5% edge margin) |
| T4 | Colour and font discipline | Sample used values against the deck's template/kit | Zero stray colours; kit faces only ([brand-identity-checklist.md](brand-identity-checklist.md) D-section governs if a kit exists) |
| T5 | Section dividers used rhythmically | Check divider placement in sequence | Dividers at consistent narrative intervals, same design each time |

### 5.5 Image quality and narrative flow

| # | What to check | How | Pass criteria |
| --- | --- | --- | --- |
| I1 | Image resolution adequate for projection **[B]** | Check effective DPI at rendered size | No visible pixelation on a 1920-wide (or larger) canvas; ≥ ~150 DPI effective is a conventional print-like floor for projected photos |
| I2 | Aspect ratios preserved | Inspect all photos/diagrams | No stretched images; crops deliberate |
| I3 | Text over images | Check scrims/panels | Contrast guaranteed behind text ([poster-checklist.md](poster-checklist.md) C2 logic) |
| I4 | Devices carry the narrative | Review sequence: recurring visual motifs (progress bar, motif graphic, colour shifts per section) | Devices recur deliberately and map to the argument's structure; a device that appears once is either removed or made systemic |
| I5 | Transition and animation discipline | Check animations/motion | Motion only where it explains (build-ups of a diagram); no decorative transitions (conventional professional practice) |
| I6 | Deck opens everywhere **[B]** | Open on a second machine/viewer; check embedded media plays; fonts render | Fonts embedded or installed fallback documented; videos/audio tested at the venue if possible |

## 6. Decision framework

Priorities for decks: (1) L1/L4 and I6 — unreadable body text, wash-out contrast and a deck that will not open are blockers; (2) D1/D4 — data slides failing legibility or honesty; (3) H2/H4 — density and multi-point slides (Major: they cost comprehension in real time); (4) T1–T4 template discipline; (5) I1–I3 image quality; (6) narrative devices and polish. The correction loop differs from web QA in one respect: most fixes happen in the master/template, so fix the master first, then sweep the deck, then re-run Pass 1 (sequence) — per [design-quality-framework.md](design-quality-framework.md) §6.

## 7. Examples

**Example 1 — 30-slide conference deck.** Pass 1 finds the template drifting after slide 12 (logo 20 px higher, footer missing — T2 Major). Pass 2 finds body text at 18 pt throughout (L1 Blocker), one slide carrying three co-equal take-aways (H2 Major), and a line chart with 10 pt axis labels (D1 Major; correction: re-export chart with ≥ 18 pt axis text, or split the chart). Sequence reads well (H1 titles form an argument). Corrections ordered: master fix → type floor sweep → split the multi-point slide → chart re-export → re-run Pass 1.

**Example 2 — pitch deck for a bright room.** Dark-on-light palette chosen deliberately (L5 documented choice); wash-out test on the actual projector showed the accent orange at 2.8:1 on white for body-size text — corrected to the kit's deeper accent shade, re-measured 4.6:1. The re-evaluation loop confirmed the darker accent still distinct from the semantic error red (D3 consistency re-check).

**Example 3 — handout deck exception handled honestly.** A reference deck with 14 pt body is *not* auto-blocked: the reviewer records that its genre is on-screen reading, not projection — and flags that if any slide is ever projected, L1 applies and the deck fails. This is the convention-versus-law distinction in practice ([design-quality-framework.md](design-quality-framework.md) Principle 6).

## 8. Common mistakes

- **Reviewing on a laptop at 100% zoom.** The room is the medium; use the back-row test (L3) and, where possible, the actual projector.
- **Deck as document.** Paragraphs and 10 pt footnotes on slides serve the reader, not the audience; put prose in notes or a handout.
- **Titles that label instead of argue.** "Q3 Results" tells the audience nothing; "Q3 revenue grew 14% on retention, not pricing" carries the slide.
- **Raw data dumps as charts.** A chart without a stated take-away outsources the thinking to a distracted audience (D2).
- **Template drift in hand-copied decks.** Fixing slides one by one instead of fixing the master (§6 loop).
- **Decorative animation.** Motion that explains beats motion that entertains; build-ups belong to diagrams, not bullet lists.
- **Ignoring the second machine.** Fonts missing, media unlinked and aspect-ratio surprises appear on the venue's machine, not yours (I6).

## 9. Evaluation checklist

- [ ] Two passes completed: sequence, then per-slide detail.
- [ ] Title sequence alone reads as the argument (H1); one point per slide (H2).
- [ ] Body text ≥ 24 pt or genre exception documented (L1); back-row test passed (L3).
- [ ] Contrast measured in file and tested in room conditions (L4–L5).
- [ ] Charts: back-row legible, one message each, consistent styling, honest scales (D1–D4, with [../information-design/data-visualisation.md](../information-design/data-visualisation.md)).
- [ ] Masters used; repeated elements identical; margins constant (T1–T3).
- [ ] Colours and fonts match template/kit (T4); dividers rhythmic (T5).
- [ ] Images at projection resolution, undistorted, text scrims in place (I1–I3).
- [ ] Narrative devices deliberate and systemic (I4); animation only explanatory (I5).
- [ ] Deck verified on a second machine with media tested (I6).
- [ ] Master-first corrections; sequence re-checked after fixes.

## 10. Related topics

- [design-quality-framework.md](design-quality-framework.md) — master method, severity model and report template.
- [../information-design/data-visualisation.md](../information-design/data-visualisation.md) — authoritative chart criteria behind section 5.3.
- [brand-identity-checklist.md](brand-identity-checklist.md) — kit rules for decks produced under a brand.
- [poster-checklist.md](poster-checklist.md) — shared distance-legibility logic.
- [../foundations/principles-of-design.md](../foundations/principles-of-design.md) — hierarchy and emphasis theory.
- [../foundations/design-critique.md](../foundations/design-critique.md) — critique stance for sequential artefacts.

## 11. References

This checklist is a synthesis of the sources below and the library's theory files; type floors are sourced, other numeric conventions are marked as such.

- Association of Research Libraries, "PowerPoint Guidelines for Presenters" — minimum 24 pt body text for slides. https://www.arl.org/accessibility-guidelines-for-powerpoint-presentations [search-verified, accessed 2026-11-23]
- "Best Font Size for Presentations: Titles, Body, Charts", presentations.ai — cites American Chemical Society slide-accessibility guidance: ≥ 24 pt body, ~28–38 pt titles. https://www.presentations.ai/blog/what-font-size-is-best-for-presentations [search-verified, accessed 2026-11-23]
- Edward Tufte, *The Visual Display of Quantitative Information* — data-ink discipline and chart honesty conventions. [canonical]
- Garr Reynolds, *Presentation Zen* — one-point-per-slide and narrative-device conventions. [canonical]
- W3C, "Web Content Accessibility Guidelines (WCAG) 2.1" — contrast ratio definitions applied in L4. [canonical]
