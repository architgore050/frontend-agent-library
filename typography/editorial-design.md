# Editorial Design

## 1. What is it?

Editorial design is the craft of organising typography and content across *multipage* artefacts — books, reports, magazines, programmes, journals, annual reviews. It takes the single-page disciplines of typesetting ([Typesetting](typesetting.md)) and hierarchy ([Typographic hierarchy](typographic-hierarchy.md)) and extends them over pages and spreads: column structures, baseline grids, page composition, running systems (folios, running heads, cross-references) and the conventions of front and back matter.

This file focuses on the *editorial application* of those systems. The general mechanics of grids — what modular grids are, their construction mathematics, and their use in layouts of all kinds — live in [Grid systems](../layout/grid-systems.md); here we cover how editorial work actually deploys them: why columns and baselines exist, how a document's typography scale binds to its grid, and how consistency is maintained across hundreds of pages.

## 2. Why does it matter?

Multipage documents have a problem no single page has: *memory and rhythm*. A reader who turns from page 40 to page 41 carries expectations — where columns start, where text sits, how sections announce themselves — and every broken expectation is a small stumble that accumulates into a sense of amateurism or, worse, confusion. Editorial systems are how one designer's decisions survive hundreds of pages, multiple contributors and late content changes; they are the difference between a document and a pile of pages.

Editorial design also matters to the repository's core use case: extending an event identity into a complete kit means producing programmes, brochures and reports that feel like the same organisation on every page and across every future event. The multi-page consistency practices here are what make that reusable ([Visual identity](../branding/visual-identity.md)).

The discipline divides cleanly across the repository's structure: the *single-page* craft (measure, leading, alignment, breaks) is [Typesetting](typesetting.md)'s subject; the *structure* (columns, modules, margins as geometry) is [Grid systems](../layout/grid-systems.md)' subject; and what remains here is the editorial synthesis — how those systems are chosen, coupled, scheduled and kept consistent when the artefact is a hundred pages produced by several hands. A reader who wants only single-page polish can skip this file; a reader producing any bound, paginated or multi-artefact work needs it.

## 3. Core principles

### 3.1 Column structures

Columns are the editorial grid's first decision, and the driver is the measure: the 45–75-character convention ([Typesetting](typesetting.md) 3.3) sets a maximum comfortable line length, so a page width that exceeds it must be divided — a narrow A5 page holds one column; a full A4 needs two; a broadsheet needs more. Conventional counts and uses:

| Structure | Conventional use | Behaviour |
|---|---|---|
| Single column | Books, essays, narrow formats | Longest measures; strongest reading flow; least flexibility |
| Two columns | Reports, magazines, catalogues | Balanced measure and flexibility; the workhorse editorial grid |
| Three columns | Newspapers, dense journals | Short measures (~35–45 characters), tight leading, high density |
| Asymmetric/unequal columns | Magazines with editorial character | A wide text column beside a narrow margin column for captions, notes, images |
| Mixed widths per spread | Feature layouts | Deliberate variation within one grid: spans of 1, 2 or full width |

The professional pattern is not "pick one structure everywhere" but **one grid, many legitimate arrangements**: a 12-column grid (see [Grid systems](../layout/grid-systems.md) for the arithmetic) lets body text span 6, images span 8, captions sit in 2, and full-bleed features span 12 — every variation still landing on the same lines. That is what Müller-Brockmann's grid tradition is for: freedom within structure rather than freedom against it. [canonical]

Gutters — the space between columns — belong to the same decision. Conventional practice sets gutters wide enough that adjacent columns never read as one (in print, roughly one em of the body size or a touch more; on screens, a spacing-scale value such as 16–24 px) and narrow enough that the columns still feel related. Two failure modes bracket the sensible range: gutters so tight that the reader's eye crosses columns mid-line (the classic 3-newspaper-column readability complaint), and gutters so wide that the columns stop cohering into a page. Gutter width is also a rhythm variable — larger gutters slow the page down editorially, which is a deliberate choice in lifestyle magazines and a defect in dense journals.

### 3.2 The baseline grid

The baseline grid is a fixed rhythm of horizontal lines (say, one every 4 or 5 mm in print) to which the *baselines* of body text align across columns and pages. Its promise: text in column one and text in column two sit on the same horizontal lines, so the page acquires a visible, felt order even where nothing else lines up.

How it is actually made to work:

1. **Pick a grid increment** that divides the leading: with body leading of 14 pt, a 14 pt grid (or 7 pt, half the leading) makes alignment trivial. The increment and the leading must be chosen *together* — this is the single most common integration error.
2. **Align body text to it** and let larger elements *skip* whole numbers of lines: an h2 whose leading does not land on the grid occupies the nearest larger multiple, and the following body text resumes on the next grid line.
3. **Let images and boxes snap to multiples** of the increment so depth below the text baseline is preserved.
4. **Accept the trade-offs**: baseline grids constrain leading choices (a 1.618-em headline on a rigid grid gets rounded), cost implementation effort (CSS: `line-height` in the grid unit, spacing tokens in the same unit), and matter less in web contexts where fluid sizes shift continuously. On the web, the practical equivalent is a *spacing rhythm* — all vertical spacing drawn from a 4 px/8 px scale so blocks align even when baselines do not ([Web typography](web-typography.md) 5).

The decision is medium-dependent: rigid baseline grids are standard in print editorial work (their tools support it) and progressively looser on screens; claiming a baseline grid while shipping unaligned leading is worse than choosing a spacing rhythm deliberately.

### 3.3 Modular and hierarchical grids, editorially

- A **modular grid** adds horizontal rows to the column structure, creating cells; editorially it excels where content is item-based — catalogues, timetables, event programmes — with each module holding one entry. Modules force consistent image/text ratios, which is why product catalogues and event listings look disciplined.
- A **hierarchical grid** abandons equal cells for zones of different importance sized by content: a lead story zone, secondary zones, a running footer zone. Newspapers and dashboards are hierarchical grids. The discipline that keeps them from becoming chaos is *zones with fixed roles*: the same zone always does the same job across issues/pages.
- The **manuscript grid** (one large text block) is the book's grid, sometimes with a marginal notes column.

Construction arithmetic, ratios and gutter theory are [Grid systems](../layout/grid-systems.md)' subject; the editorial points are the *assignments* above — which content gets which cells and why — and the consistency rules of 3.6.

The assignment logic, stated as a question: *what does one unit of this content mean?* In a catalogue, one unit is one product, so the module is the unit and the grid is modular. In a newspaper, one unit is "a story of this importance", so zones of importance are the structure and the grid is hierarchical. In a novel, one unit is the whole text, so the manuscript grid suffices. Editorial grid failures usually trace to a mismatch between that unit definition and the chosen grid — sessions listed in zones (importance has no meaning for parallel sessions), or stories in equal modules (importance flattened into sameness). Getting the unit right makes the grid feel inevitable rather than imposed.

### 3.4 The editorial type system: scale meets grid

An editorial document binds its typographic scale ([Typographic hierarchy](typographic-hierarchy.md) 3.4) to its grid in four documents-of-record:

1. **The body specification**: face, size, leading, measure — all three chosen together (leading on the grid increment, measure as whole columns or fractions).
2. **The heading schedule**: each heading level's size, leading, weight and *grid behaviour* — space above in whole grid lines, keep-with-next, whether it spans columns.
3. **The auxiliary schedule**: captions, folios, running heads, notes, pull quotes — each with size (usually two steps below body), tone and column assignment.
4. **The exceptions list**: pull quotes, sidebars, full-width features — legitimate departures, each defined so they read as decisions.

In print practice these live in a "style sheet" the production team follows; in design-tool practice, as paragraph styles; in code, as the token layer ([Web typography](web-typography.md) 5). The editorial scale is usually quieter than a marketing site's — a 1.2–1.333 ratio — because the *document structure* (parts, chapters, sections) adds a second hierarchy dimension that size must not exhaust.

### 3.5 Page composition: margins, spread, and the type area

- **Margins are structured, not padded.** Editorial margins have roles: the *outside* and *head* margins frame; the *spine-side (inner) margin* accounts for binding and is conventionally equal or slightly larger than the outer; a widened *bottom (foot) margin* anchors the page. Tschichold's classical proportions and Van de Graaf's canon are the historical formulations of the book's type area; the working principle is that the margin ratio encodes the document's character — generous margins signal leisure and prestige; tight margins signal density and economy. [canonical]

| Margin | Role | Conventional behaviour |
|---|---|---|
| Inner (spine) | Binding allowance | Equal to or larger than outer; never shaved below binding needs |
| Outer | Framing; folio position | Often hosts the page number in book work |
| Head | Top framing; running head position | Visually slightly lighter than the foot |
| Foot | Visual anchor | Conventionally the largest margin; grounds the page |

- **Facing pages are one composition.** In a bound, two-sided document the spread, not the page, is the unit: images crossing the spine, mirrored margins (inner margins meeting at the spine), and headings positioned to be seen together. Design tools and print PDFs think in spreads; single-page thinking produces binding-cramped work.
- **The type area is a contract.** Once the grid and margins fix where text may sit, *everything* sits there: exceptions (full-bleed images, marginalia) are defined in the exceptions list, not improvised per page.

### 3.6 Multi-page consistency

Consistency across a document is enforced by a short list of systems, each decided once:

- **Running heads and folios** (page numbers): same position, size and tone on every page; conventions — folios usually at the outer edge or foot centre; running heads often suppressed on chapter openers; front matter commonly numbered separately (see 5.2).
- **Chapter/section openers**: a fixed composition — same margins for the title block, same grid behaviour, same space before body starts — that repeats with only the words changing. Openers are where documents earn their rhythm.
- **Repeated furniture**: figure numbering, caption position, footnote position, table rules, source lines — one rule each, applied everywhere.
- **The content pressure plan**: late changes (a longer chapter, a pulled image) get absorbed by the grid's flexibility (3.1), not by ad-hoc re-layout. If every exception is defined, production fixes are mechanical.

The running furniture, with its conventions:

| Element | Conventions |
|---|---|
| Folio (page number) | Outer margin, head or foot; suppressed on chapter openers; front matter numbered separately (5.2) |
| Running head | Document or chapter title at head margin; mirrored across the spread; often absent on openers |
| Running foot | Alternative folio position; sometimes carries the chapter or event name |
| Chapter opener | Fixed composition: extra head space, no running head, title block on defined grid lines |
| Figure numbering | Sequential per chapter (Fig. 3.2) or per document; captions always in the same position relative to the figure |
| Footnotes / endnotes | Footnotes at foot of column or page with a rule; endnotes as a defined back-matter section |

## 4. How it works: building an editorial system

The sequence that produces a coherent document rather than a pile of pages:

1. **Analyse the content**: volume, structure depth (parts/chapters/sections), image ratio, table density, expected life of the document.
2. **Choose format and margins**: page size and the type area proportion that matches the document's character (3.5).
3. **Choose the grid**: columns from the measure convention; modules or zones from content type (3.1/3.3).
4. **Set the leading and baseline increment together** (3.2) — body size, leading and grid increment as one decision.
5. **Build the type schedules** (3.4): body, headings, auxiliaries, exceptions — each mapped to grid behaviour.
6. **Define the running systems**: folios, running heads, openers (3.6).
7. **Prototype on real content**: lay out the three hardest spreads — densest, emptiest, most mixed — before committing to the whole document.
8. **Document the system**: the style sheet/paragraph styles/tokens that let other people reproduce it.

## 5. Practical application

### 5.1 A worked system: A4 event report

A concrete configuration showing the decisions interacting (values are conventional starting points):

- Format: A4 portrait, 12-column grid, gutters 16 px, margins 96 px outer / 80 px head / 96 px foot; body text typically spans 6 columns, wide figures 10, full-bleed features 12.
- Body: 10.5 pt/14 pt (leading on a 7 pt baseline grid; 2 lines = 28 px spacing rhythm), measure 2 columns ≈ 60 characters.
- Headings: h1 opener 28 pt/31 pt skipping 5 grid lines above body; h2 18 pt/21 pt, 2 grid lines above, 1 below; h3 14 pt/14 pt (on-grid), 1 line above. Weights from the paired family's 600/700.
- Captions and folios: 8.5 pt/11 pt, muted tone, folio at outer foot margin with running head at outer head margin.
- Exceptions: pull quotes span both columns at 16 pt/21 pt; full-width images bleed to margins, captions sit in the outer column.

The numbers matter less than the *coupling*: leading ↔ grid increment, measure ↔ columns, headings ↔ grid-line multiples, openers ↔ fixed composition. Change one and the system tells you what else must move.

### 5.3 Worked brief: the event programme

The repository's stated use case — extending a fixed event logo into a complete brand kit — lands directly in editorial design, because the kit's printed core is a programme. A reusable brief shape:

1. **The logo stays scarce.** The fixed logo is not a texture; it appears on the cover, the opener and the sponsors' page — nowhere else. Everything else is carried by the type system and colour, so the identity survives the page count ([Visual identity](../branding/visual-identity.md)).
2. **One grid for every artefact in the kit.** Programmes, badges, signage cards and web schedules share the 12-column grid and spacing rhythm, so a session's content can move between formats without re-layout — the grid is the brand's structural signature.
3. **Item-based modular grid for the schedule** (3.3): each session a module; room codes in the mono voice; times in tabular figures; speakers in the text face's medium weight. The module is the unit volunteers can extend without design review.
4. **The opener composition is the kit's most repeated page** — cover inside, day openers, venue map page — so it earns the design attention the cover gets.
5. **Next year's reuse is a content swap.** The documented system (grid, schedules, furniture) plus new copy and dates reproduces the kit; the logo is the only fixed asset the next event inherits.

The brief pattern generalises: identify the *fixed* asset (logo), the *systems* (grid, type, colour, furniture), and the *content modules* (sessions, talks, sponsors) — then design the systems, not the pages.

### 5.2 Front matter, back matter, and document furniture

Long documents carry conventions inherited from book tradition — worth knowing even for reports, because readers recognise them:

- **Front matter**: title page, colophon/credits, contents, and (in books) a half-title before the title page. Front matter is conventionally numbered with roman numerals (i, ii, iii...) or unnumbered, with body text starting at page 1 *after* it — a convention readers never notice until it is wrong (contents pointing at page "12" that is actually the twelfth *sheet* is the classic self-published error).
- **Back matter**: appendices, glossary, index, colophon. Appendices continue arabic numbering; a colophon recording typefaces, sizes and papers is a long-standing editorial courtesy and, in brand work, a quiet signature ([Visual identity](../branding/visual-identity.md)).
- **Opening-page conventions**: chapters often open with a drop zone (extra head margin, no running head, sometimes a drop cap — see [Typesetting](typesetting.md) 3.1 on alignment discipline for display settings).

## 6. Decision framework

| Decision | Choose rigid (grid-bound) when | Choose loose (rhythm-bound) when |
|---|---|---|
| Baseline grid | Print, fixed format, many contributors, long life | Web, fluid type, short-lived artefacts |
| Column count | Content is prose-led | Content is module-led (catalogues, programmes) |
| Grid type | Item-based content (modular) or role-based zones (hierarchical) per 3.3 | Pure prose (manuscript grid) |
| Margins | Bound/printed (spine allowance, mirrored) | Screen-only (uniform, generous) |
| Numbering | Long front matter (roman numerals, body starts at 1) | Short documents (straight numbering) |

Explicitly: margin proportions, roman-numeral front matter and opener suppressions are professional conventions with book tradition behind them; the coupling rules (3.2, 3.4, 5.1) are engineering necessities; the classical canons (Tschichold, Van de Graaf) are historical references rather than requirements.

A worked grid-choice comparison, since the decision is easier to see in contrast:

| Document | Content profile | Grid choice | Reasoning |
|---|---|---|---|
| Novel / essay collection | Pure prose, long | Manuscript grid, single column | Reading flow outranks flexibility |
| Annual report | Prose + data + images | 12-column, prose spans 6, tables span 10–12 | Two rhythms on one structure |
| Conference programme | Items with times/rooms | Modular grid | Each session one module; extension is mechanical |
| Newspaper front page | Hierarchical news mix | Hierarchical zones | Importance, not items, drives size |
| Catalogue | Comparable entries | Modular with strict cells | Comparison across entries is the point |
| Magazine feature well | Editorial character | Asymmetric columns + margin column | Captions and notes live beside, not under |

## 7. Examples

**Example 1 — the conference programme.** A programme's content is item-based (sessions, rooms, times), so a modular grid carries it: each session occupies one module, room codes sit in a fixed sub-cell in the mono voice ([Font pairing](font-pairing.md) 3.7), times use tabular figures ([Typographic hierarchy](typographic-hierarchy.md) 5.2). The opener spread carries the event identity; interior pages repeat one composition — extendable next year by swapping content, not redesigning ([Visual identity](../branding/visual-identity.md)).

**Example 2 — the annual report.** Prose-led chapters (2 columns, 60-character measure) alternate with data sections (full-width tables on the same 12-column grid). The two rhythms coexist because they share the grid lines; captions in the outer column track figures throughout. Folios and running heads appear on every page except openers.

**Example 3 — the broken baseline.** A team designs a magazine with a 4 mm baseline grid but sets headings at leadings that ignore it, so body text after every heading starts off-grid and the columns' baselines never meet across the spread. The fix is the coupling rule: re-derive heading spacing as whole multiples of the 4 mm increment, and let headings *skip lines* rather than land fractional.

**Example 4 — the front-matter trap.** A 60-page report's contents list cites "page 12" for a section that a PDF reader calls page 19: the cover and four unnumbered pages were never accounted for. Fix: number the front matter separately (i–v), start arabic numbering where body starts, and make the contents' numbers match the folios — not the sheet count.

**Example 5 — the programme that reused itself.** The second edition of an annual conference inherited the documented grid and type schedules from the first; production swapped sessions, dates and the sponsor page, and the only new design work was the cover. The first edition's investment in the exceptions list (3.4) paid out as hours, not aesthetics.

## 8. Common mistakes

- **Grid chosen after the typography.** Leading and grid increment must be decided together (3.2); retrofitting one to the other produces either off-grid text or ugly leadings.
- **Claiming a baseline grid without aligning to it.** Worse than a declared spacing rhythm; reviewers and printers will find it.
- **Measure forgotten in column sizing.** Three columns of 30 characters on A4 because the grid was chosen for rhythm, not reading ([Typesetting](typesetting.md) 3.3).
- **Single-page thinking in bound documents.** No spine allowance, no mirrored margins, images positioned without the spread in mind.
- **Improvised exceptions.** Every pull quote a different size, every opener a different composition — the document's rhythm dies by exceptions. Define the exceptions list once (3.4).
- **Contents vs folio mismatch.** Front matter numbered inconsistently with the contents (5.2).
- **Heading stranded at column foot.** No keep-with-next; the heading opens a section that begins overleaf.
- **Grid rigidity carried onto the web.** Pixel-exact baseline claims break under fluid type; use spacing rhythm there ([Web typography](web-typography.md) 5).
- **The logo used as texture.** Stamping the fixed logo into headers and footers of every page dilutes the identity it was meant to carry (5.3); scarcity is the logo's protection.
- **Furniture redesigned mid-document.** Folios moving, caption positions changing between chapters — each is a small inconsistency a reader feels as carelessness; furniture is decided once (3.6).
- **Content pressure absorbed by re-layout.** A late chapter arrives and the grid is abandoned for that section; the pressure plan (3.6) exists precisely so changes land inside the system's flexibility.

## 9. Evaluation checklist

- [ ] Column structure derived from the measure convention, not from taste alone
- [ ] Grid increment and body leading chosen together and consistent
- [ ] Baseline alignment (or a declared spacing rhythm) actually holds across columns and pages
- [ ] Heading schedule specifies grid behaviour: lines above/below, spans, keep-with-next
- [ ] Auxiliary schedule (captions, folios, running heads, notes) defined and repeated
- [ ] Exceptions list defines every departure (pull quotes, bleeds, sidebars)
- [ ] Margins structured: spine allowance and mirrored margins in bound work
- [ ] Openers share one fixed composition
- [ ] Front matter numbering consistent with contents; body starts at 1 after it
- [ ] System prototyped on the densest, emptiest and most mixed spreads
- [ ] Gutter width deliberate: columns distinct but related (3.1)
- [ ] Grid choice justified against the content profile (6 table)
- [ ] Running furniture decided once and repeated (3.6 table)
- [ ] Style sheet / paragraph styles / tokens documented so others can reproduce the system

## 10. Related topics

- [Grid systems](../layout/grid-systems.md) — grid construction arithmetic, gutters and ratios (the mechanics this file applies editorially)
- [Typesetting](typesetting.md) — the page-level disciplines (measure, leading, breaks) the grid carries
- [Typographic hierarchy](typographic-hierarchy.md) — the scale and role system scheduled onto the grid
- [Font pairing](font-pairing.md) — the voices assigned to editorial roles
- [Web typography](web-typography.md) — the token layer and spacing rhythm that translate grids to code
- [Visual identity](../branding/visual-identity.md) — extending an identity across documents
- [Principles of design](../foundations/principles-of-design.md) — rhythm, alignment and proximity at document scale

## 11. References

- Josef Müller-Brockmann, *Grid Systems in Graphic Design* (Niggli, 1981) — the canonical articulation of grid discipline and the "freedom within structure" tradition. [canonical]
- Jan Tschichold, *The Form of the Book* (Hartley & Marks, English ed. 1991) — classical page proportions, margin canons and book typographic conventions. [canonical]
- Jan Tschichold, *The New Typography* (1928; English ed. University of California Press, 1998) — the modernist case for systematic, function-driven typography. [canonical]
- Robert Bringhurst, *The Elements of Typographic Style* (Hartley & Marks, 4th ed. 2012) — page shape, measure and multipage discipline conventions. [canonical]
- Ellen Lupton, *Thinking with Type* (Princeton Architectural Press, 2nd ed. 2010) — grids and editorial systems in contemporary teaching. [canonical]
- Section 3.2's web-equivalent spacing-rhythm guidance is synthesis of the sources above with current web practice as covered in [Web typography](web-typography.md).
