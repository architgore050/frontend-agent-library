# Grid systems

A grid is the invisible scaffolding underneath a layout: the pre-decided set of horizontal and vertical divisions to which every element is positioned. This file explains what grids are, how to construct one from scratch for any medium, how the choice differs between posters, editorial work, websites, dashboards, presentations, social media and documents, and how to implement grids correctly in CSS Grid. It is the parent file for layout mechanics; spacing values and proportion systems are treated in [Spacing and proportion](spacing-and-proportion.md), and behaviour across viewport sizes in [Responsive layouts](responsive-layouts.md).

## 1. What is it?

A grid system is a deliberate framework of intersecting vertical and horizontal guidelines that divides a canvas into columns, rows and cells, and against which all content is aligned. It is not the visible furniture of a design — you rarely see it — but it determines where every margin, column, image, headline and caption sits. The professional vocabulary still in use today was codified by Swiss designer Josef Müller-Brockmann in *Grid Systems in Graphic Design* (Niggli, 1981, German–English edition), which treated the grid as the objective basis for rational, legible layout [canonical].

Grids exist on a spectrum of strictness. At one end sits the manuscript grid (a single text block, as in a novel); at the other, the modular grid (a dense matrix of cells, as in a data sheet or a Swiss poster). Between them lie column grids for general editorial and web work, baseline grids for vertical typographic rhythm, and hierarchical or asymmetric grids that deliberately weight parts of the canvas differently. A grid system is therefore a decision, not a default: you choose its type, density and proportions to fit the content and the medium.

## 2. Why does it matter?

A grid converts hundreds of individual placement decisions into a few systematic ones. Without one, an agent (or a designer under deadline) positions each element independently and the page accumulates small inconsistencies — left edges that almost line up, headings that sit at slightly different heights — which the eye reads as disorder even when it cannot name the cause. With one, related elements share edges and spacing values, and the viewer unconsciously perceives structure, craft and reliability.

The practical benefits, all of which are observable in the output rather than matters of taste:

- **Consistency at scale.** In a brand kit or a multi-page document, a grid guarantees that page 1 and page 40, or the poster and the website, share the same spatial logic. This is exactly what Vignelli meant when he described grids as a tool for "syntactical consistency" across a designer's whole output [search-verified: The Vignelli Canon, RIT Vignelli Center PDF].
- **Speed and delegation.** A defined grid lets any person or agent place new content correctly without re-deciding the layout. It is, in effect, documentation of the layout decisions.
- **Flexibility with cohesion.** A 12-column grid can host a full-width hero, a three-card row and a text-plus-image band on the same canvas, and they will still align. The variety comes from how much of the grid each zone occupies.
- **Responsive behaviour.** On the web, a well-built grid compresses predictably; [Responsive layouts](responsive-layouts.md) depends on the column structure defined here.

The limits are equally real. A grid disciplines placement, not quality: it cannot make weak imagery good or a poor hierarchy legible. Over-rigid grids also flatten expressive work — posters, fashion editorial and expressive brand moments often need the grid broken (see §6.3). The professional position, argued throughout Timothy Samara's *Making and Breaking the Grid* (Rockport), is that breaking the grid is only meaningful once you can build and use one well [search-verified].

## 3. Core principles

### 3.1 Anatomy of a grid: the standard vocabulary

Use this vocabulary consistently when specifying grids; it comes from Müller-Brockmann's systematisation [canonical] and is shared by print and digital practice.

| Term | Definition | Typical dimension |
| --- | --- | --- |
| Format (canvas) | The total working area: paper size, viewport, slide or artboard | Defined by medium |
| Margin | The outer zone between format edge and grid; frames the content and keeps it safe from trimming, binding or screen edges | Print 15–25 mm; web 24–64 px (conventional starting points) |
| Column | A vertical division of the content area into which elements are placed | Web 6–12 columns; print 2–8 |
| Gutter | The space between columns, and between rows in a modular grid | Print 3–5 mm; web 16–24 px (conventional) |
| Flowline | A horizontal guideline aligning elements across columns; rows in a modular grid are thick flowlines | Set from the baseline grid |
| Field / module | The rectangular unit where a column and a row intersect | Width = column, height = flowline interval |
| Spatial zone | A group of fields or columns assigned to one content element (e.g. a 4-column image zone) | Any rectangular grouping |
| Baseline grid | Evenly spaced horizontal lines to which body text sits, giving vertical rhythm across columns and pages | 8 px (web) or 12–13 pt leading (print), conventional |

Two distinctions trip people up. First, the **gutter** separates columns; it is *not* the margin (which frames everything) and *not* padding (which is space *inside* an element — see [Spacing and proportion](spacing-and-proportion.md), §3.2). Second, a **spatial zone** is an assignment of grid units to content, not a structural part of the grid; two layouts on the same 12-column grid can look completely different because their zones differ.

Margins deserve one more note because they are not always symmetric. In bound print the inner (spine-side) margin is conventionally narrower than the outer — a rule of thumb associated with Robert Bringhurst's *The Elements of Typographic Style* sets the inner at roughly half the outer — because the fold of an open spread swallows part of the inner margin and the two facing pages must still read balanced [canonical]. Unbound posters and documents use symmetric margins; digital surfaces default to symmetric side margins. The transferable principle is that margin width encodes physical constraints (binding, trimming, device edges), not decoration.

### 3.2 The main grid types

| Type | Structure | Best for | Watch out for |
| --- | --- | --- | --- |
| Manuscript (1 column) | Single continuous text block | Books, long-form documents, articles | Monotonous; hard to host side elements |
| Column grid | N vertical columns, one flowline axis | Websites, magazines, reports | Too many columns create noise |
| Modular grid | Columns × rows → modules (cells) | Posters, timetables, catalogues, dashboards, image-heavy editorial | Can feel mechanical; needs varied zone sizes |
| Baseline grid | Horizontal lines only | Any multi-column text layout; whole brand kits | Pointless if type sizes ignore it |
| Hierarchical | Rows/columns of unequal, content-driven sizes | Web dashboards, posters, expressive layouts | Can drift into "no grid at all" |
| Asymmetric | Unequal column widths and/or off-centre margins | Swiss-style posters, editorial, modern web | Needs strong hierarchy to stay balanced |

- **Manuscript grid** — the oldest form: one block of text with generous margins, as in a novel or an essay. Its variants add marginal notes or hanging figures. It is the right grid whenever reading flow is the only job.
- **Column grid** — the workhorse for mixed content. Each element occupies one or more columns; gutters keep them apart. Web pages, reports and magazine spreads all use column grids, differing mainly in column count and whether a baseline grid is layered underneath.
- **Modular grid** — adds horizontal divisions, producing a matrix of modules. Müller-Brockmann demonstrated its flexibility for both graphic design and even architectural planning [search-verified: baselinehq.com; ixdf.org]. Use it when content comes in repeatable units: event programmes, product listings, dashboards, photography grids.
- **Baseline grid** — not a placement grid but a rhythm grid: every line of text in every column sits on the same horizontal lines, so text columns that sit side by side align optically across their whole height. It is essential in editorial design and the quiet backbone of disciplined web typography (implemented conventions in [Spacing and proportion](spacing-and-proportion.md) §7 and [Web typography](../typography/web-typography.md)).
- **Hierarchical grid** — a loose grid of rows and columns with deliberately unequal sizes, ordered by content importance. Dashboards and poster layouts often work this way: the hero statistic gets a large zone, secondary metrics smaller ones.
- **Asymmetric grid** — unequal column widths and/or deliberately off-centre margins create tension and direct the eye. The Swiss modernists (Müller-Brockmann in particular) championed asymmetric layouts as more dynamic than centred classical symmetry [canonical]. Asymmetry is a compositional choice, not a technical one; see [Composition](../foundations/composition.md) for the perceptual reasoning.
- **Compound grid** — two grids overlaid on the same canvas, for example a 3-column and a 4-column grid superimposed, so that usable widths relate in systematic but less obvious ways (the combined divisions create the compound's module set). Samara treats the compound grid alongside column and modular grids among the basics [search-verified]. Reach for it when one layout must host two different rhythmic systems at once — running text in regular columns plus a filmstrip of thumbnails — while refusing arbitrary widths.

### 3.3 What a grid does and does not decide

A grid fixes *positions and widths*, not *visual weight, colour, hierarchy or meaning*. A perfectly gridded layout can still fail if the largest element is unimportant or if the type hierarchy is weak — those are governed by [Principles of design](../foundations/principles-of-design.md) and [Typographic hierarchy](../typography/typographic-hierarchy.md). Conversely, an expressive layout can sit on a grid: knowing where the grid is precisely what lets you break it deliberately rather than accidentally.

## 4. How it works — building a grid from scratch

### 4.1 The decision sequence

Build every grid in the same order: **canvas → margins → columns → gutter → flowline → spatial zones**. Working in this order means each decision constrains the next sensibly.

1. **Canvas.** Fix the format and orientation: A3 portrait poster, 1440 px desktop viewport, 16:9 slide, 1080×1350 px social post. Everything else is relative to this. On the web the canvas is fluid, so define it as a maximum content width (e.g. 1200–1440 px) inside any viewport.
2. **Margins.** Set the outer frame. Decisions that drive it: print finishing (bleed, trimming, binding eats margin — allow more on the bound edge), handheld viewing distance (posters viewed from metres need smaller relative margins than documents held in the hand), and on screens, the need for breathing room at narrow widths. A common poster convention is margins between 8% and 15% of the shorter side; web pages commonly use 24–64 px side margins (conventional starting points — verify against the project's own design system).
3. **Columns.** Choose the count from content density and needed flexibility. More columns = more possible zone sizes but more visual complexity. Divisible counts multiply your options: 12 columns divides into halves (6), thirds (4), quarters (3) and sixths (2), which is the historical reason 12 became the web default. Posters need few columns (2–6); body-text layouts need enough for the measure to stay readable (see the 45–75 character guidance in [Web typography](../typography/web-typography.md)).
4. **Gutter.** Choose the space between columns. The gutter must be visibly smaller than the column (commonly 1:4 to 1:8 of column width, conventional) or the eye reads the gutters as extra columns. Too-small gutters make adjacent zones touch and lose separation.
5. **Flowline.** If the content repeats vertically (cards, timetable rows, magazine articles), add horizontal divisions — usually multiples of the baseline grid — creating a modular grid. Otherwise a single flowline axis (the baseline grid alone) is enough.
6. **Spatial zones.** Assign content to zones *before* designing details: e.g. title spans columns 1–12, intro spans 1–6, image spans 7–12, timetable spans 1–12 in three modules per row. This step is where a grid stops being theory and becomes the layout.

Always record the result as a spec (canvas, margins, columns, gutter, flowline, zone map) — this is what makes the grid reusable across a brand kit.

### 4.2 Worked example A: A3 portrait poster for an event

- Canvas: 297 × 420 mm, portrait, bleed 3 mm (conventional print finishing value — confirm with the printer).
- Margins: 20 mm all round (≈ 7% of the short side). Content area: 257 × 380 mm.
- Columns: 6, for a composition with a dominant image zone and layered text.
- Gutter: 5 mm (1:7.7 of column width). Column width = (257 − 5×5) ÷ 6 ≈ 38.7 mm.
- Flowline: none — a poster is one composition, not repeating rows. A baseline grid at 14 pt leading sits underneath all type.
- Spatial zones: title spans columns 1–5; date/venue block spans column 6 (vertical); image spans columns 1–4 in the lower half; credits span 1–6 at the foot.

Check the arithmetic with code, never in your head: `width = (content − gutters) ÷ columns` gives (257 − 25) ÷ 6 ≈ 38.7 mm here. If the division produces awkward fractions, adjust gutter or margin until it resolves — this is the ordinary iteration of grid building.

### 4.3 Worked example B: 1440 px desktop web page

- Canvas: fluid viewport, content capped at 1440 px and centred.
- Margins: 64 px each side at full width (shrink to 24 px below ~768 px — see [Responsive layouts](responsive-layouts.md)). Content area: 1312 px.
- Columns: 12. Gutter: 24 px. Column width = (1440 − 2×64 − 11×24) ÷ 12 = (1312 − 264) ÷ 12 ≈ 87.3 px.
- Flowline: baseline grid at 8 px; card rows snap to multiples of 8.
- Spatial zones (landing page): navigation 12; hero headline 7, hero image 5; feature cards 3×4 (three cards of four columns); full-width footer 12.

Notice the arithmetic that makes 12 columns attractive: 4-col cards, 3-col cards, 6-col splits and 2-col splits all resolve to exact column counts with no fractional leftovers.

### 4.4 Worked example C: 16:9 presentation slide

- Canvas: 33.87 × 19.05 cm (the standard widescreen slide size), landscape.
- Margins: 8% of the width ≈ 2.7 cm left and right; slightly less top and bottom (2 cm). Content area: ≈ 28.5 cm wide.
- Columns: 12. Gutter: 0.4 cm. Column width = (28.5 − 11×0.4) ÷ 12 = 24.1 ÷ 12 ≈ 2.0 cm.
- Flowlines: two — a title baseline fixed at the same height on every slide, and a footer line near the bottom edge. Everything between them is the variable zone.
- Spatial zones: title columns 1–10; logo/wordmark columns 11–12 at top right; statement layouts span 1–12; text+image layouts split 1–6 / 7–12.

The slide grid earns its keep through repetition: because the title zone and footer are identical on every slide, the deck reads as one object. The percentages (margins as a fraction of width) transfer to social-media canvases and story formats far better than absolute centimetres do.

### 4.5 From grid to CSS

Print grids live in the file or on the artboard; web grids must be *implemented*. CSS Grid is the correct tool — it natively expresses columns, gutters, named zones and spans (syntax verified against MDN [accessed]: grid container, tracks, lines, areas, `gap`). Section 7.2 gives complete implementations. Flexbox remains appropriate for one-dimensional runs of items, but anything with both rows and columns — or anything that must stay aligned to a page-wide grid — belongs to CSS Grid.

### 4.6 Inspecting the grid in built work

A grid you cannot see is a grid you cannot evaluate. In print files, keep the grid on a locked non-printing layer and toggle it during review; in code, every modern browser's developer tools can overlay the computed CSS Grid tracks, lines and gaps on a live page (the grid inspector in Firefox and Chrome-based browsers highlights tracks and shows line numbers), which turns alignment checking from eyeballing into verification. Three inspection habits catch most defects: toggle the overlay and look for elements whose edges miss a track line; compare two pages of the same product side by side to confirm margins and zone positions match; and read the layout's source of truth — the written grid spec from §4.1 — against what the inspector shows. Where the built page and the spec disagree, one of them is wrong and must be fixed; the disagreement itself is the finding.

## 5. Practical application by medium

The same anatomy serves every medium, but the *type* of grid and its proportions differ. This is the core answer to "which grid does each application need, and why".

| Medium | Grid type | Columns / structure | Why |
| --- | --- | --- | --- |
| Poster | Column or modular, often asymmetric | 2–6 columns; few or no rows | One composition, strong hierarchy, large scale elements |
| Editorial (magazine, report) | Column + modular + baseline | 8–12 columns, rows for articles; strict baseline | Mixed article lengths and image sizes must align across spreads |
| Website | Fluid 12-column grid | 12 columns, content max-width, responsive collapse | Maximum zone flexibility; collapses predictably at breakpoints |
| Dashboard | 12-column + modular rows | 12 columns; widget rows on 8 px rhythm | Mixed widget sizes must tile without misalignment |
| Presentation | 12-column slide grid, generous margins | 12 columns on a 16:9 canvas, margins ≈ 6–10% of width | Few elements per slide need clear, repeatable zones |
| Social media | Platform-imposed canvases | Design to the platform's export sizes and safe areas | You do not control the canvas; specs change, so verify current sizes |
| Document (A4) | Manuscript or simple 2–6 column | 1 column for reports; 2–3 for brochures; 25 mm margins | Reading comfort and print margins dominate |

### 5.1 Posters

A poster is a single composition seen from distance, so the grid serves hierarchy rather than density. Keep the column count low (2–6); assign a dominant spatial zone to the primary message and let secondary blocks (date, venue, credits) occupy narrow zones — a vertical date block in the last column is a classic Swiss device. Margins can be tighter than in documents because the poster is framed by the wall, but the grid must still protect the type from the trim edge. Modular grids suit event posters whose content is inherently tabular (a programme with times and acts). Asymmetric grids earn their keep here: an off-centre dominant zone creates the tension that makes a poster memorable, while the grid keeps every secondary element disciplined.

### 5.2 Editorial layouts

Editorial design is the most demanding grid context because articles of different lengths, images of different shapes and captions must align across facing pages. The standard solution stacks three layers: an 8–12 column grid for placement, modular rows for article units, and a strict baseline grid so adjacent text columns align line-for-line (see [Editorial design](../typography/editorial-design.md) for the typographic side). Vignelli's work is a canonical reference for the discipline this requires — his diagrammatic grids for magazines specified every line and station of the layout [search-verified: The Vignelli Canon]. When you extend an event brand into a printed programme, this is the model to copy: one grid, defined once, applied to every page.

### 5.3 Websites

Web grids are fluid: the columns scale with the viewport and collapse at breakpoints. Use a 12-column grid with a maximum content width, implement it with CSS Grid (`minmax()` and `fr`, see [Responsive layouts](responsive-layouts.md)), and define margins and gutters as spacing tokens rather than magic numbers (see [Spacing and proportion](spacing-and-proportion.md)). Two web-specific duties: components must align to the page grid *and* manage their own internal spacing — solved with subgrid or container-based component grids — and the grid must degrade gracefully: the same 12 columns become 1 column on a phone via media queries or `auto-fit`. Product-level responsive strategy (mobile-first thinking, content prioritisation, touch targets) is covered in [Responsive design](../ui-ux/responsive-design.md); this file covers the layout mechanics.

### 5.4 Dashboards

Dashboards tile widgets of mixed importance — a large KPI, several charts, a table — so they need both a 12-column placement grid and a modular row rhythm (widget heights on an 8 px baseline) to avoid ragged vertical edges. Treat widget sizes as a closed vocabulary (e.g. 4-col tall, 8-col wide, 12-col full) rather than letting each widget pick arbitrary dimensions; this is a hierarchical/modular hybrid. Density matters more than in marketing pages: compact spacing scales (4 px-based) are common here — see [Spacing and proportion](spacing-and-proportion.md) §6.2. The grid must also reserve zones for states (empty data, loading) so widgets do not resize when content arrives.

### 5.5 Presentations

Slides share the poster's problem (few elements, distant viewing) and the document's problem (many slides must match). The conventional solution is a 12-column grid on the 16:9 canvas with margins around 6–10% of the slide width and one consistent title zone (e.g. columns 1–9, fixed vertical position) used identically on every slide. Aligning every slide's title and footer to the same grid positions is what makes a deck feel professionally made. Content zones then repeat per slide type: a full-width statement layout, a two-column text+image layout, a three-card layout — all drawn from the same grid.

### 5.6 Social media

Here the grid is imposed from outside: each platform defines export canvas sizes, aspect ratios and safe areas (regions covered by interface chrome or cropping), and these specifications change over time — always verify current sizes against the platform's own documentation rather than memorising values. The professional workflow treats each export size as its own canvas and maps the brand grid onto it: define the brand's margin proportion (say 8% of width) and a 3- or 4-column mini-grid, so a post and a story both read as the same family even though the canvases differ. Compositions should also survive the platform's profile-grid preview, which crops to a square or rectangle depending on the platform and changes without notice — keep the primary message within the centre zone.

### 5.7 Documents

A report or proposal on A4 needs, above all, a comfortable manuscript grid: one text column with margins around 20–25 mm (conventional for print documents), a baseline grid for vertical rhythm, and — when figures, sidebars or multi-column sections appear — an upgrade to a 2–6 column grid. Because documents flow continuously, the grid must accommodate page breaks: never leave a heading stranded at the foot of a column, and let figures span defined column groups rather than arbitrary widths. When a document is part of a brand kit, reuse the margins and baseline interval from the master grid so the document, the slides and the website share one rhythm.

## 6. Decision framework

### 6.1 Choosing the grid type

Ask, in order:

1. **Is the content continuous prose?** → Manuscript grid (plus baseline grid).
2. **Does content come in repeatable units?** → Modular grid (posters/programmes, dashboards, catalogues).
3. **Is the content mixed in shape and importance?** → Column grid (12 for web; 8–12 for editorial; 2–6 for posters).
4. **Is one part of the content clearly dominant and expressive?** → Hierarchical or asymmetric grid on top of a simple column base.
5. **Is the canvas dictated by someone else?** → Map your brand grid onto the imposed canvas (social media, platforms).

Annotated walkthrough — an event brand kit with these deliverables: a landing page (mixed content, unknown devices), a printed programme (articles plus schedules), an A3 street poster (one dominant message), a results dashboard (repeatable stat tiles) and Instagram posts (imposed canvas). Working down the list: the landing page gets the 12-column fluid grid of §4.3; the programme gets the editorial stack — 12-column placement grid plus baseline grid plus modular rows for schedule entries (§5.2); the poster gets a 6-column asymmetric grid with a dominant image zone (§5.1), not a web-style 12 because its content is one composition; the dashboard gets the hierarchical/modular hybrid (§5.4); the posts get the brand grid's proportions mapped onto the platform's canvas (§5.6). Five deliverables, one recorded system: every grid above derives from the same margin proportion, gutter ratio and baseline interval, which is what makes the outputs recognisably a family.

### 6.2 Choosing the numbers (conventional starting points)

The values below are professional conventions, not laws — verify against the project's design system, print vendor or platform before committing.

| Parameter | Poster | Editorial print | Web (desktop) | Dashboard | Presentation |
| --- | --- | --- | --- | --- | --- |
| Columns | 2–6 | 8–12 | 12 | 12 | 12 |
| Margins | 8–15% of short side | 15–25 mm | 24–64 px | 16–32 px | 6–10% of width |
| Gutter | 3–8 mm | 3–5 mm | 16–24 px | 8–16 px | 16–24 px equiv. |
| Baseline interval | 12–14 pt leading | 12–13 pt leading | 8 px | 8 px | 8–12 px |

Gutter-to-column ratio of roughly 1:4 to 1:8 keeps columns reading as columns. Margin-to-content-width ratio around 1:10 to 1:15 gives most screens and documents adequate framing.

### 6.3 When to break the grid

Breaking the grid is a deliberate compositional act, legitimate when it earns attention for a genuinely important element: a headline rotated across column boundaries, an image bleeding off the margin, a pull quote occupying white space. The discipline is that a *broken* grid is still visible underneath — the viewer should sense tension against a structure, not randomness. Samara's *Making and Breaking the Grid* organises the whole genre around this idea: understand the rules first, then violate specific ones for specific effects [search-verified]. Break one thing at a time; if everything is off-grid, there is no grid and therefore no break. In brand-kit work, restrict deliberate breaks to hero moments (poster, cover slide) and keep functional surfaces (documents, dashboards) strictly on-grid.

## 7. Examples

### 7.1 Exercise: extend an event logo into a grid-based brand kit

Take a fixed event logo (the common starting point for this library's use case) and build the spatial system around it:

1. **Grid derivation.** Measure the logo's bounding box. Choose the canvas for each deliverable: A3 poster, A4 programme, 1440 px web page, 16:9 slides, 1080×1350 px social post.
2. **Poster grid (do it by hand).** Draw a 297×420 mm frame with 20 mm margins; divide into 6 columns with 5 mm gutters; compute and verify the column width ≈ 38.7 mm; sketch three zone maps (dominant-image, dominant-type, split) using only the grid.
3. **Web grid (do it in code).** Implement the 1440 px grid from §4.3 in CSS (§7.2 below) and lay out the event landing page with named zones.
4. **Consistency test.** Place the logo, the title treatment and the date/venue block on every canvas at the same *proportional* position (e.g. title baseline at 12% of canvas height). If a canvas cannot honour the proportion, record the exception rather than silently improvising.
5. **Baseline pass.** For the printed programme, choose a leading interval (e.g. 12 pt), snap every text style to it, then print a spread at full size and hold two facing columns up to the light: their baselines should align line-for-line. On the web equivalent, inspect with the browser's grid overlay (§4.6) and check that adjacent card text blocks share the same vertical rhythm.
6. **Evaluation.** Swap two pieces of content between canvases (poster headline into the hero zone) and confirm they drop onto the other grid without redesign. A grid passes when content is portable.

### 7.2 Correct CSS Grid implementation examples

A 12-column page grid with tokens and centred max width (syntax per MDN [accessed]):

```css
:root {
  --grid-max-width: 90rem;      /* 1440 px */
  --grid-columns: 12;
  --grid-gutter: 1.5rem;        /* 24 px */
  --grid-margin: 4rem;          /* 64 px */
}

.page-grid {
  max-width: var(--grid-max-width);
  margin-inline: auto;
  display: grid;
  grid-template-columns: repeat(var(--grid-columns), 1fr);
  gap: var(--grid-gutter);
  padding-inline: var(--grid-margin);
}

/* Spatial zones: line numbers count track lines, 1..13 across 12 tracks */
.hero-headline { grid-column: 1 / 8; }
.hero-media    { grid-column: 8 / 13; }
.feature-card  { grid-column: span 4; }
.page-footer   { grid-column: 1 / -1; }  /* -1 = last line, writing-mode aware */
```

Named template areas for a layout that must reflow by re-mapping zones only:

```css
.event-layout {
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  gap: var(--grid-gutter);
  grid-template-areas:
    "head head head head head head head head head head head head"
    "intro intro intro intro intro intro . media media media media media"
    "card card card card card card card card card card card card";
}
.zone-head  { grid-area: head; }
.zone-intro { grid-area: intro; }
.zone-media { grid-area: media; }
.zone-cards { grid-area: card; }
```

An asymmetric grid with unequal tracks and named lines (poster logic from §5.1):

```css
.poster {
  display: grid;
  grid-template-columns:
    [full-start] 3rem [content-start] 2fr 1fr 1fr 1fr 2fr [content-end] 3rem [full-end];
  gap: 0.5rem;
}
.poster .headline { grid-column: content-start / content-end; }  /* spans all five content tracks */
.poster .image    { grid-column: content-start / span 3; }       /* dominant zone: wide track + two narrow */
.poster .date     { grid-column: -2 / -1; }  /* date set into the margin band — the one deliberate break */
```

Note the last rule: placing content into a margin track contradicts the grid, so it is only legitimate as a *commented, deliberate* break — exactly the discipline §6.3 requires. Everything else stays on named lines, which keeps the asymmetric system auditable.

A modular grid board (programme timetable) with row rhythm on the 8 px baseline:

```css
.programme {
  display: grid;
  grid-template-columns: repeat(6, 1fr);
  grid-auto-rows: minmax(4rem, auto);   /* rows grow, never squash */
  gap: 1.5rem;
}
.session { grid-column: span 2; }        /* 3 sessions per row */
```

Nested alignment with `subgrid` — a card whose internal content lines up with the parent grid:

```css
.card-grid { display: grid; grid-template-columns: repeat(12, 1fr); gap: var(--grid-gutter); }
.card {
  grid-column: span 4;
  display: grid;
  grid-template-columns: subgrid;   /* inherits the parent's 4 tracks */
  gap: inherit;
}
```

Baseline-grid discipline in CSS: type sizes and line-heights chosen so every line lands on a shared 8 px rhythm (the scale from [Spacing and proportion](spacing-and-proportion.md) §3.1):

```css
:root { font-size: 1rem; }               /* 16 px base */
body     { font-size: 1rem;   line-height: 1.5rem; }  /* 24 px */
h3       { font-size: 1.5rem; line-height: 2rem;   }  /* 32 px */
h2       { font-size: 2rem;   line-height: 2.5rem; }  /* 40 px */
h1       { font-size: 3rem;   line-height: 3.5rem; }  /* 56 px */
```

Two honest caveats. First, setting `line-height` in rem (rather than unitless multipliers) is what makes multi-column text align line-for-line across columns, but it sacrifices some scaling flexibility for users who change their base font size — treat this as a documented trade-off rather than a universal law, and see [Web typography](../typography/web-typography.md) for the accessibility side. Second, pixel-perfect baseline alignment is stronger discipline than most product surfaces need; editorial print and multi-column editorial web layouts benefit most, while single-column marketing pages can settle for consistent spacing between blocks.

## 8. Common mistakes

- **Choosing the column count first.** Columns before margins produce cramped frames; always fix canvas and margins first (§4.1 order exists because each step constrains the next).
- **Gutters as wide as columns.** The eye then reads each column as split in two. Keep gutters a fraction (1:4–1:8) of column width.
- **Twelve columns for a poster.** Web defaults leak into print. Posters need 2–6 columns; density is not a virtue at large scale.
- **Decorative alignment failure.** Elements "roughly" on the grid — a few pixels off every edge. This reads as error, not freedom. Snap or move away decisively.
- **Ignoring the baseline grid in multi-column text.** Columns of body text at different line intervals drift apart vertically and the spread looks unmade.
- **Breaking the grid accidentally.** One element sits off-grid because it was never considered; the layout reads as sloppy rather than expressive. Breaks must be deliberate and singular (§6.3).
- **One canvas, no system.** Designing the poster, then the web page, then the slides from scratch each time instead of deriving all from one recorded grid spec. The brand kit then drifts apart.
- **Hard-coded pixel grids in CSS.** Fixed column widths that overflow small viewports; use `fr`, `minmax()` and tokens (see [Responsive layouts](responsive-layouts.md)).
- **Treating the margin as wasted space.** Cramming content to the edges. The margin frames the composition and protects it from trimming, binding and interface chrome.

## 9. Evaluation checklist

- [ ] The grid type is stated and suits the medium (§6.1).
- [ ] Canvas, margins, columns, gutter and flowline are recorded as a written spec with real numbers.
- [ ] Arithmetic checks out: columns × width + gutters = content width (computed with code, not by eye).
- [ ] Every visible element edge aligns to a column, flowline or margin — no "almost aligned" edges.
- [ ] Gutter is visibly narrower than column; gutters are consistent across the layout.
- [ ] Body text sits on the baseline grid where a baseline grid is defined; adjacent text columns align.
- [ ] Spatial zones map cleanly onto columns; no zone forces content into arbitrary widths.
- [ ] Any off-grid element is a deliberate break (one per composition), not an oversight.
- [ ] The same grid (or its documented proportional equivalent) is applied across the kit's canvases.
- [ ] In code: implemented with CSS Grid, tokens for margins/gutters, no fixed pixel columns (§7.2).

## 10. Related topics

- [Spacing and proportion](spacing-and-proportion.md) — the spacing values, scales and ratios that fill the grid's gaps.
- [Responsive layouts](responsive-layouts.md) — how the grid behaves across viewports; `minmax()`, `auto-fit`, container queries.
- [Composition](../foundations/composition.md) — perceptual reasons behind asymmetry, tension and focal points.
- [Principles of design](../foundations/principles-of-design.md) — balance, rhythm and unity, which the grid operationalises.
- [Editorial design](../typography/editorial-design.md) — the typographic layer (measure, leading, hanging elements) on editorial grids.
- [Web typography](../typography/web-typography.md) — measure and line-height conventions that a web baseline grid must serve.
- [Responsive design](../ui-ux/responsive-design.md) — product-level responsive strategy: mobile-first, content priority, touch targets.
- [Frontend implementation](../ui-ux/frontend-implementation.md) — engineering conventions for shipping design systems in code.

## 11. References

- Josef Müller-Brockmann, *Grid Systems in Graphic Design*, Niggli, 1981 (bilingual German–English edition). The codification of the column/modular/baseline grid vocabulary and the advocacy of asymmetric layout. [canonical]
- Timothy Samara, *Making and Breaking the Grid*, Rockport Publishers (3rd edition, 2023) — listing seen at https://www.amazon.com/Making-Breaking-Grid-Third-Workshop/dp/0760381933 . Structure of grid types and the "understand before breaking" framework. [search-verified]
- Massimo Vignelli, *The Vignelli Canon*, PDF hosted by the RIT Vignelli Center: https://www.rit.edu/vignellicenter/sites/rit.edu.vignellicenter/files/documents/The%20Vignelli%20Canon.pdf — grids as the tool of "syntactical consistency". [search-verified]
- MDN Web Docs, *Basic concepts of grid layout* (tracks, lines, cells, areas, gap semantics): https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_grid_layout/Basic_concepts_of_grid_layout [accessed 2026-11-23]
- MDN Web Docs, *repeat()* (auto-fill/auto-fit semantics and fixed-size requirement): https://developer.mozilla.org/en-US/docs/Web/CSS/repeat [accessed 2026-11-23]
- MDN Web Docs, *minmax()* (min/max argument rules, fr restrictions): https://developer.mozilla.org/en-US/docs/Web/CSS/minmax [accessed 2026-11-23]
- IxDF, *What are Grid Systems?*: https://ixdf.org/literature/topics/grid-systems — history of Swiss modular grids (Gerstner, Ruder, Müller-Brockmann). [search-verified]
- Baseline HQ, *4 Grid Systems*: https://baselinehq.com/4-grid-systems.html — summary of Müller-Brockmann's grid typology. [search-verified]
- web.dev, *Responsive web design basics*: https://web.dev/articles/responsive-web-design-basics — content-first breakpoint method (also used in [Responsive layouts](responsive-layouts.md)). [accessed 2026-11-23]

Note on numeric values: margin, gutter, column-count and baseline figures given as ranges (mm, px, percentages) are conventional starting points synthesised from the sources above and standard practice; where a figure is a verified property of CSS or a hard external requirement, the text says so explicitly.
