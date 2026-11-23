# Presentations

## 1. What is it?

A presentation is a timed sequence of projected visuals (slides) delivered alongside a speaker, designed for a room — or a video call — where the audience watches from metres away and cannot re-read. Slide design therefore optimises for **glance legibility and speech support**, not documentation: the slide carries the structure and the evidence, the speaker carries the sentences. This page covers the visual design of decks — hierarchy, the standard slide archetypes (cover, content, data, divider, image, closing), projection typography and master systems. Delivery technique and narrative-writing methods are adjacent crafts (see [Art direction](../graphic-design/art-direction.md) for the visual narrative layer).

## 2. Why does it matter?

Slides are the highest-frequency artefact most organisations produce, and the failure modes are the most public: walls of text read aloud, charts nobody can parse from row ten, and decks where every slide has different margins because no master system existed. For an agent producing event collateral, the deck is also a brand surface — often the single longest continuous exposure an audience has to the identity. A disciplined deck extends the fixed logo into a slide master with the same care a poster gets, and it reuses the same hierarchy, palette and grid thinking as every other application.

The deck also has an unusual evaluation asymmetry: the audience never sees the file, only the projection, so a deck that looks flawless on a laptop can fail completely in a lit room on a washed-out projector (§4.6). Conversely, small improvements to slide discipline compound visibly — consistent margins, statement titles, one chart per slide — because the audience absorbs hundreds of slides in sequence. The craft therefore splits cleanly: per-slide decisions (what goes on this slide) and deck-level decisions (master, theme, sequence), and the deck-level decisions are the ones that save the most time and prevent the most drift.

## 3. Core principles

- **One idea per slide.** If a slide needs "and", it is two slides. The title states the idea; the body (visual, chart, or ≤ 30 words) supports it.
- **Slides support the speaker, not replace them.** Design for the back row first: if text must be read, it fails as a slide and belongs in the handout (see 5.4).
- **Consistency is structural, not stylistic.** Margins, title position and type scale come from a slide master so that every slide inherits them; manual per-slide styling is the root cause of visual drift.
- **Contrast for projection.** Projectors wash out in lit rooms and screens vary; body text must exceed the contrast a desktop reader needs (see [Colour accessibility](../colour/colour-accessibility.md)).
- **Motion and transition with restraint.** Transitions carry meaning (a section change, a build) or they do not exist; decorative animation consumes attention.
- **The deck is a sequence, not a stack.** Section dividers, progress cues and a deliberate closing give the audience orientation — the same narrative logic as carousel sequencing in [Social media graphics](social-media.md).

## 4. How it works

### 4.1 Canvas and dimensions

The default modern format is 16:9 widescreen at 13.333 × 7.5 inches (33.87 × 19.05 cm), the setting Microsoft PowerPoint applies to new presentations; the legacy 4:3 format is 10 × 7.5 inches ([search-verified] Microsoft Support). For pixel-based design work, treat the canvas as 1920 × 1080 px. Design once at this ratio; do not mix 4:3 and 16:9 assets. Vertical 9:16 decks for phone-first viewing exist but are a separate deliverable, not a crop of the 16:9 deck.

### 4.2 Slide hierarchy and the title system

Every content slide answers the same question instantly: *what is this slide's point?* The mechanism:

- **Title = the takeaway, not the topic.** "Attendance grew 40% in two years" beats "Attendance statistics". The audience reads titles in sequence and gets the argument for free.
- **One visual hierarchy per slide:** title (largest) → primary element (chart/image/statement) → supporting labels → footer meta (deck name, page number, section). The scale relationships come from [Typographic hierarchy](../typography/typographic-hierarchy.md).
- **Fixed title position.** The title sits in the same rectangle on every slide — this is a master-level rule, not a per-slide choice. Eye travel between slides then costs nothing.

### 4.3 The slide archetypes

**Cover slide.** Event or deck title, subtitle, presenter and affiliation, date, one organising visual (full-bleed image with a dark scrim, or a bold colour field). The logo appears here at its governed size and clear space (see [Logo systems](../branding/logo-systems.md)). Nothing else.

**Agenda / contents slide.** Optional for short decks; for long ones it orients. Use a list the speaker can return to as a progress marker between sections.

**Content slides.** The workhorses. One idea per slide discipline: a statement title plus the minimal evidence — a diagram, three bullets of ≤ 8 words, a pair of images, or a short quote. If content exceeds one line of thought, split the slide or split the deck.

**Diagram and table slides.** A relationship (process, hierarchy, flow) is drawn, never listed: boxes and connectors from the master's shapes, labelled directly, with the "you are here" or "before → after" element accented. A genuine comparison table (≤ 4 columns, ≤ 5 rows, ≤ 6 words per cell) may stay a table; anything denser is a handout table, not a slide. Both follow the grid and palette of the master — diagrams built from ad-hoc shapes in random colours are the fastest way to make a deck look homemade. Icon use inside diagrams follows one family and weight, per [Iconography](../graphic-design/iconography.md).

**Data slides.** One chart per slide, titled with the finding ("Cost fell fastest in Q3"), source cited on-slide, axes labelled directly rather than via legend where possible. Chart selection, de-junking and annotation practice live in [Data visualisation](../information-design/data-visualisation.md) — this page holds only the slide-level rules: never paste a spreadsheet, never show two unrelated charts side by side, and size the chart to occupy the dominant area (roughly 60–70% of the slide).

**Section dividers.** A full-bleed colour or image slide carrying only the section number and name. They reset attention, mark progress, and are the natural place for a transition animation.

**Image slides.** A full-bleed photograph with either nothing or a single caption. Full-bleed demands image resolution: at 1920 px wide, source images should be ≥ 1920 px across, ideally 2560+ for large rooms; a 600 px web image will visibly fail. Ensure text over images sits on a scrim or clean region and passes contrast checks.

**Quote slides.** Attribution, one short quote (≤ 2 sentences — keep within fair-use norms), generous whitespace, the speaker's photo if relevant. No bullet decoration.

**Closing slide.** The action and the contact: the single call to action (register, adopt, approve), handle/URL, thanks, and the logo. The closing must not be "Thank You" over clip art; it restates the ask. This mirrors the CTA discipline in [Marketing assets](marketing-assets.md).

### 4.4 Projection typography

Room legibility is the constraint. Conventional starting points, widely used in professional practice (not laws — a 5 m huddle room can go smaller than a 20 m auditorium):

| Element | Minimum size on a 1920 × 1080 canvas |
|---|---|
| Slide titles | 28–44 pt equivalent (≥ 40 px) |
| Body / bullet text | 18–24 pt equivalent (≥ 30 px); never below 18 pt |
| Chart axis and data labels | ≥ 18 pt equivalent |
| Footnotes / source lines | ≥ 12–14 pt equivalent |
| Any text on video-call decks | one size larger — compression softens edges |

Supporting rules:

- The **zoom-out test**: view the deck at 25–30% zoom. Every title and every chart's message should still be findable. This cheap simulation of the back row catches most type failures.
- **Worked sizing example.** For a 3 m screen viewed to 12 m: the back row sits at 4× the slide height, so a 30 px body line on a 1920-px canvas projects to roughly 17 mm of physical height at the screen — readable at 12 m only for normal vision in a dim room. Doubling the type (or splitting the slide) is cheaper than squinting; when in doubt, run the distance logic from [Posters](posters.md) §4.3 on the projected size rather than the file size.
- **Sans serif, medium weight, high x-height** faces perform best on projectors; thin weights and small serifs disappear (see [Typeface selection](../typography/typeface-selection.md)).
- **Line discipline:** bullets ≤ 2 lines each, ≤ 6 per slide; paragraphs do not belong on slides — they belong in the handout.
- **Colour strategy for rooms:** dark text on light slides survives lit rooms; light-on-dark decks flatter dark auditoriums and video calls. Either way, verify body-text contrast well above the desktop minimum (see [Colour accessibility](../colour/colour-accessibility.md)).

### 4.5 Slide master systems

The master is the deck's design system: named layouts (title, section divider, content A, content B, two-column, full-bleed image, quote, closing), each with locked margins, title rectangle, footer zone and colour roles. Authoring discipline:

1. Build the **grid** first — outer margins ≈ 5–7% of width (about 100 px on a 1920 canvas), a baseline rhythm from [Spacing and proportion](../layout/spacing-and-proportion.md), and column structure from [Grid systems](../layout/grid-systems.md).
2. Define **placeholder types** (title, body, image, chart) so authors drop content into governed zones rather than free-drawing text boxes.
3. Map **palette roles** (background, ink, accent, data series colours) from [Palette development](../colour/palette-development.md) into the theme, so colour never gets eyedropped per slide.
4. Version the master once per event/brand, and forbid ad-hoc layouts: if a needed layout is missing, add it to the master, not to the slide.

### 4.6 Room and AV factors

The physical room edits your design before the audience sees it:

- **Aspect mismatch:** a 16:9 deck on a 4:3 projector letterboxes or crops; ask the venue, and if 4:3 is unavoidable, produce a real 4:3 variant (re-flowed, not squeezed) with the master's 10 × 7.5 in canvas.
- **Luminance loss:** projectors in lit rooms can halve perceived contrast; dark greys and low-contrast accents disappear. Pre-empt with the projection-worst-case contrast pass, and request a dimmed room for data-heavy sections where possible.
- **Colour shift:** projector colour gamut is narrower than a monitor's; saturated brand colours shift, and thin coloured text on coloured backgrounds fails first. Keep text near-black or near-white on the projector, and let colour live in blocks and charts.
- **Cables and hydration of the file:** embed media rather than linking it; test the actual laptop/projector before the session, not the design machine.
- **Speaker notes and presenter view** are part of the deliverable — the notes field carries what the slide does not, which is what keeps slides minimal in the first place.

### 4.7 Handouts and leave-behinds

Handouts are a different artefact with different rules, decided deliberately:

- **Notes-style handout** (slide thumbnail + speaker notes) supports reviewers who need the talk's reasoning; produce it from the deck automatically, and write the notes field knowing it will be read.
- **Full-page leave-behind** for data and detail: a separate document that carries the tables, references and methods the slides omitted — designed per [Certificates and documents](certificates-and-documents.md), not as shrunken slides.
- **What never works:** a 6-up slide grid as the only record — text too small to read, charts stripped of their narration. If the deck was designed by the one-idea rule, the slides alone cannot document the argument; the handout exists precisely because of that.
- Decide the format before the event and name it in the deck master (notes fields written to handout standard), so the leave-behind is not a post-hoc scramble.

## 5. Practical application

### 5.1 Build order

1. Write the **outline** as titles only — one line per slide. If the titles alone tell the story, the deck is sound before any visual work begins.
2. Edit ruthlessly against the one-idea rule; merge or cut.
3. Apply the master; set the cover, dividers and closing.
4. Produce data slides with the chart discipline of [Data visualisation](../information-design/data-visualisation.md).
5. Run the zoom-out test and the contrast pass; export.

### 5.2 Pacing and deck length

A conventional planning figure is 1–2 minutes of speaking per content slide, so a 15-minute talk lands at roughly 10–15 slides plus dividers. Guy Kawasaki's widely cited **10/20/30 rule** — 10 slides, 20 minutes, no text below 30 points — remains a useful aggressive baseline for pitch contexts ([canonical] Guy Kawasaki). These are planning aids, not laws; a dense technical walkthrough legitimately needs more slides, each carrying less.

### 5.3 Images and assets

- Source imagery at ≥ 1920 px width for full-bleed use; keep a consistent treatment (crop ratio, colour grade) across the deck so slides feel like one film.
- Prefer diagrams made from the master's shapes and palette over pasted screenshots; a screenshot of UI is acceptable when the point *is* the UI — crop to the relevant region.
- Icons from one family, one weight; mixing icon metaphors mid-deck reads as carelessness (see [Iconography](../graphic-design/iconography.md)).

### 5.4 Export and handouts

- **Screen deck:** keep the native 16:9 file for presenting; export a PDF for distribution only if fonts embed correctly and no animation is load-bearing.
- **Handout:** produced per §4.7 — notes-style from the deck, or a separate document for detail; never a 6-up grid as the sole record.
- **Video calls:** supply the deck in the call platform's shared aspect (usually 16:9), raise text one size, and avoid pure black backgrounds that halo against compression.

### 5.5 Final check and rehearsal pass

Before the session, run the deck through one rehearsal pass with the checks applied live:

1. Present it aloud once — every slide you find yourself *reading* is a slide to cut or rebuild.
2. Verify the zoom-out test (§4.4) and the room factors (§4.6) against the actual venue or call.
3. Check the sequence economics: title-only read-through tells the story; dividers land every 5–8 minutes; the closing states the ask.
4. Fix issues in the master where they are structural (a wandering title is a master fix, not 40 slide fixes).
5. Export the deliverables decided in §4.7 and archive the master for the next event.

## 6. Decision framework

- **Bullet slide, diagram or chart?** A sequence or list → bullets (short). A relationship or process → diagram. Evidence or magnitude → chart. If you cannot name which, the slide has no single idea yet.
- **How many dividers?** Roughly one per 5–8 minutes of talk; each divider earns its cost by resetting attention.
- **How long is the deck?** Plan with the 1–2 minute-per-content-slide convention:

| Talk length | Content slides (approx.) | Plus cover/dividers/closing |
|---|---|---|
| 5 min (lightning) | 3–5 | 2–3 |
| 15 min (conference slot) | 8–12 | 3–4 |
| 30 min (session) | 15–22 | 4–6 |
| 60 min (workshop/lecture) | 25–40 | 6–8 |

  These are pacing aids; a dense technical walkthrough legitimately needs more slides, each carrying less (see also the 10/20/30 baseline in 5.2).
- **Light or dark theme?** Lit room / projected luminance loss → light theme. Dark auditorium or streamed call → dark theme. The brand's palette must accommodate both roles (see [Palette development](../colour/palette-development.md)).
- **One deck or presenter variants?** Shared event decks use one master with per-speaker title slides; each speaker never restyles body slides.
- **PDF or live deck for distribution?** PDF only when no animation is load-bearing; otherwise a notes-style handout (§4.7) carries the record while the live deck keeps its transitions.

## 7. Examples

### 7.1 Event opening deck master spec

```text
Canvas:      1920 × 1080 px (13.333 × 7.5 in, 16:9)
Margins:     96 px outer; title zone x=96, y=72, height 120 px
Type:        Titles 44 px semibold; body 30 px regular; captions 24 px
Palette:     Background ink/white per section; accent for dividers and data highlight
Layouts:     cover, divider, statement, bullets, chart, 2-up images, quote, closing
Footer:      event name 20 px, slide number bottom-right, off-palette grey
Dividers:    full-bleed accent, section number 160 px, name 60 px
```

### 7.2 Data slide built to spec

Title: "Registrations doubled after the social push". Single line chart, three series max, direct end-labels instead of a legend, source line "Source: registration system, exported 2026-11-20" at 18 px, one accent colour isolating the post-launch period. No gridline jungle, no 3D, no drop shadows — the de-junking rules are [Data visualisation](../information-design/data-visualisation.md)'s.

### 7.3 Agenda and divider pair

Agenda slide: four sections listed in the body zone, each with a number, a two-word label and a one-line promise ("03 Results — what the pilot actually changed"). Divider slides reuse the agenda's numbering at 160 px against the full-bleed accent — the audience always knows which numbered block they are inside. The pairing costs two layouts in the master and pays back in orientation for the whole deck.

### 7.4 Full-bleed image slide spec

Image sourced at 2560 × 1440 px minimum, cropped to the deck's 16:9 with the focal subject on the right third; a left-edge gradient scrim (ink at ~60% opacity fading out) hosts a single caption line at 30 px; no title bar, no footer except the page number. The slide exists to give the room a shared emotional beat between data sections — one per talk is usually enough, two if the story has a genuine turning point. Image treatment consistency (grade, crop logic) follows [Art direction](../graphic-design/art-direction.md).

## 8. Common mistakes

- **Walls of text.** Full paragraphs projected and then read aloud. Correction: statement title + minimal evidence; the prose moves to speaker notes or the handout.
- **No master, so inconsistent margins.** Every slide nudged by hand; titles wander. Correction: build layouts in the master; never free-draw on slides.
- **Chart junk.** 3D bars, dual legends, spreadsheet screenshots, one chart showing four unrelated metrics. Correction: one chart, one message, direct labels, source cited.
- **Type too small for the room.** 14 pt body read by nobody past row three. Correction: the minimums in 4.4 plus the zoom-out test.
- **Decorative transitions everywhere.** Motion that signals nothing. Correction: transitions only where structure changes.
- **Cover slides that violate logo clear space** or cram sponsor marks against the title. Correction: governed lockup placement (see [Brand architecture](../branding/brand-architecture.md)).
- **Low-contrast themes for lit rooms.** Grey-on-grey text vanishing on a washed projector. Correction: contrast check at projection-worst-case, not on the design monitor.
- **"Thank you" endings with no action.** The ask never gets stated. Correction: closing slide with one CTA and contact.
- **Multi-author decks without a shared master.** Six authors, six margin systems. Correction: distribute the master with layouts and a one-page usage note; merge in the master, not on slides.
- **Screenshots as data.** A pasted dashboard screenshot with 9 pt text "presented" as evidence. Correction: rebuild the one chart that matters in the master's chart style; link the dashboard for exploration.
- **Deck inflation on the eve.** The 12-slide plan becomes 40 the night before, none of them edited. Correction: enforce the outline-first workflow (§5.1); new content must delete something.
- **Decorative stock imagery carrying no meaning.** Generic handshake/lightbulb photos that fill space. Correction: image slides need a reason — atmosphere, evidence or a named subject (§7.4); otherwise no image.
- **Charts sized like thumbnails.** A 600-px chart floating in whitespace on a 1920 canvas, unreadable from the room. Correction: data occupies 60–70% of the slide per §4.3.

## 9. Evaluation checklist

- [ ] Titles alone, read in sequence, tell the story.
- [ ] Every content slide carries exactly one idea, stated in its title.
- [ ] No body text below the projection minimums (≈18 pt / 30 px on a 1920 canvas).
- [ ] Zoom-out test (25–30%) passes: structure findable, chart messages visible.
- [ ] Data slides: one chart, one message, direct labels, source on-slide.
- [ ] All margins, titles and footers inherited from the master; no free-drawn text boxes.
- [ ] Full-bleed images ≥ 1920 px wide with contrast-safe text regions.
- [ ] Transitions used only where structure changes.
- [ ] Cover and closing present the governed lockup; closing states one CTA.
- [ ] Contrast passes projection-worst-case checks per [Colour accessibility](../colour/colour-accessibility.md).

## 10. Related topics

- [Data visualisation](../information-design/data-visualisation.md) — chart selection and de-junking rules for data slides.
- [Typographic hierarchy](../typography/typographic-hierarchy.md) — the scale system behind slide titles and body.
- [Typeface selection](../typography/typeface-selection.md) — choosing projection-safe faces.
- [Grid systems](../layout/grid-systems.md) and [Spacing and proportion](../layout/spacing-and-proportion.md) — the master's structural grid.
- [Palette development](../colour/palette-development.md) — theme roles and data-series colours.
- [Colour accessibility](../colour/colour-accessibility.md) — projection-worst-case contrast checks.
- [Logo systems](../branding/logo-systems.md) and [Brand architecture](../branding/brand-architecture.md) — lockups on cover, dividers and sponsor slides.
- [Posters](posters.md) and [Social media graphics](social-media.md) — sibling applications sharing the identity.
- [Art direction](../graphic-design/art-direction.md) — image treatment and visual narrative.

## 11. References

- Microsoft Support, "Change the size of your PowerPoint slides" — widescreen 16:9 default at 13.333 × 7.5 in; 4:3 at 10 × 7.5 in. https://support.microsoft.com/en-us/powerpoint/change-the-size-of-your-powerpoint-slides [search-verified 2026-11-23]
- Nancy Duarte, *slide:ology: The Art and Science of Creating Great Presentations* (O'Reilly) — slide archetypes, master systems, presentation visual discipline. [canonical]
- Garr Reynolds, *Presentation Zen* (New Riders) — restraint, one-message slides, delivery-first design. [canonical]
- Guy Kawasaki, "The 10/20/30 Rule of PowerPoint" — 10 slides, 20 minutes, 30-point minimum. [canonical]
- Josef Müller-Brockmann, *Grid Systems in Graphic Design* (Niggli) — grid foundations applied in 4.5. [canonical]
- Section 4.4 numeric minimums and section 6 pacing figures are conventional professional starting points, labelled as such in the text; they are synthesis of the canonical works above and current platform defaults.
