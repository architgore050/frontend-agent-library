# Typographic Hierarchy

## 1. What is it?

Typographic hierarchy is the system that tells a reader, before they read a single sentence, what a page contains and in what order to attend to it. It works by assigning distinct visual treatments to *roles* — headline, subheading, body, caption, label, metadata, button text, numerals, technical information — and applying those treatments consistently everywhere the roles appear. Hierarchy is typography's answer to the general design principle of visual order ([Principles of design](../foundations/principles-of-design.md)).

This file covers: the standard role inventory and what each role's text is actually doing; the four levers that create hierarchy (size, weight, colour/tone, spacing — plus case and style); how to build a type scale with named steps; how hierarchy differs between editorial and interface contexts; and how to evaluate whether a hierarchy works. The mechanics of setting each role well (measure, leading, justification) live in [Typesetting](typesetting.md); the choice of faces lives in [Typeface selection](typeface-selection.md) and [Font pairing](font-pairing.md).

## 2. Why does it matter?

Readers do not read pages; they scan them and then commit. Eye-tracking research popularised as the "F-pattern" and scan-first behaviour shows users orient by the most visually salient structures first — headlines, then openings, then body — so the hierarchy *is* the interface between the content and the reader's attention. A document or screen with clear hierarchy can be understood in skim mode and read in depth mode; the same content without hierarchy forces the reader to parse raw text to find anything.

For an agent or a design system, hierarchy is also the mechanism that makes typography *reproducible*. "Make this stand out" is not a system; "headlines are step 4 of the scale at weight 700" is. Because type covers most of the visual surface ([Typography fundamentals](typography-fundamentals.md)), inconsistent hierarchy is the most visible symptom of an immature design system — and the cheapest one to fix, since the fix is a defined set of roles and steps applied mechanically.

The reproducibility argument has a machine-readable form worth stating: a defined hierarchy is exactly what lets an agent generate a new screen, a new document or a new event kit without re-deciding typography from scratch. The role inventory (3.2) tells it *what* kinds of text exist; the scale (3.4) tells it *what values* each role takes; the levers (3.1) tell it *how* to express a relationship that the roles do not cover. Every undefined role or unnamed size is a decision pushed back onto the generator — and every such decision is an opportunity for inconsistency. Hierarchy is therefore not decoration for the design system; it is the interface the system exposes to its own automation.

## 3. Core principles

### 3.1 The levers: how hierarchy is actually created

Four primary levers, plus two secondary ones. Effective hierarchies combine two or more levers per contrast; a single-lever hierarchy is fragile.

1. **Size** — the strongest lever and the loudest. Doubling perceived size (mind x-height differences, [Typography fundamentals](typography-fundamentals.md) 4.1) reads instantly as "more important". Because it is so strong, size should change in deliberate steps, not ad hoc pixels — hence type scales (4).
2. **Weight** — the workhorse of interface hierarchy. On a scale where size is fixed (tables, dense UI), weight carries the structure: 600/700 for headings and emphasised rows, 400 for body, 400–500 for supporting text. Weight steps of 100–200 create clear contrast without shouting; intermediate steps (500 vs 400) are useful for *low-amplitude* hierarchy where 700 would over-signal.
3. **Colour/tone** — de-emphasis is as important as emphasis: metadata in a muted tone, body in near-black, headings in full-strength ink. Colour as a hierarchy lever interacts with the brand palette ([Colour theory](../colour/colour-theory.md)) and must respect contrast accessibility ([Accessible typography](../accessibility/accessible-typography.md)) — muted does not mean uncontrastful.
4. **Spacing** — white space above a headline groups it with what follows (proximity, [Principles of design](../foundations/principles-of-design.md)). Margin rhythm is often more visible in scanning than any glyph property: generous space *before* a section heading and little *after* it binds the heading to its section.
5. **Case and style (secondary)** — all-caps labels, italics for citations, letter-spacing on eyebrows. Case is a strong signal in small doses: an all-caps tracked label reads as UI chrome, not content (see [Typography fundamentals](typography-fundamentals.md) 3.6 for the spacing treatment caps need).
6. **Typeface voice (secondary)** — the display/text split ([Font pairing](font-pairing.md)) adds a structural difference; used sparingly it adds event, used everywhere it adds noise.

A note on ordering: size is the lever readers notice first, weight the one they trust most in dense UI, colour the one that scales best to de-emphasis, spacing the one that organises groups. A hierarchy that uses all four deliberately beats one that maxes out size alone.

Each lever also has a cost profile worth knowing before you reach for it:

| Lever | Strength | Cost / limit | Best for |
|---|---|---|---|
| Size | Loudest, first-noticed | Consumes space; loud steps hard to use in dense UI | Editorial structure, heroes |
| Weight | Reliable in tight spaces | Weights must exist in the family; 700 everywhere flattens | Dense UI, tables, forms |
| Colour/tone | Scales to de-emphasis beautifully | Contrast floor limits how far it can go ([Accessible typography](../accessibility/accessible-typography.md)) | Metadata, captions, secondary UI |
| Spacing | Organises without styling | Invisible when wrong; needs a spacing scale | Section grouping, forms |
| Case/style | Strong signal, cheap | Reads as chrome; unreadable in runs | Labels, eyebrows, citations |
| Typeface voice | Structural event | Quirk budget is one face deep ([Font pairing](font-pairing.md)) | Display moments |

### 3.2 The role inventory

The roles below recur across almost every product and document. For each: its job, and its conventional treatment.

| Role | Job | Conventional treatment |
|---|---|---|
| Headline / page title | Orient; state the largest unit of content | Largest step; bold; tight leading; display voice if one exists |
| Subheading (H2/H3...) | Structure the body into scannable units | Steps below headline; medium-to-bold weight; spacing above > below |
| Body text | Carry the actual content | Body step (web convention ~16 px); regular weight; comfortable measure and leading ([Typesetting](typesetting.md)) |
| Lead / intro | Bridge from headline into body | One step above body, lighter tone or larger size, shorter measure |
| Caption | Describe images, tables, figures | Below body size; muted tone; often italic or medium; tight measure |
| Label / eyebrow | Name UI regions and data fields | Small; all-caps with positive tracking; medium weight; muted or accent tone |
| Metadata | Timestamps, authors, counts, tags | Below body size; muted tone; secondary weight; often tabular figures |
| Button text | Name actions | Body-ish size; medium-to-semibold weight; no muted tones (actions stay legible) |
| Numerals / data | Quantities users compare | Body size or larger; tabular figures in columns; monospace where alignment is critical |
| Technical info | Code, identifiers, paths, versions | Monospace voice; body size or slightly smaller; distinct tone or background |

Two clarifications. First, the roles are *semantic*, not just visual: a "caption" is a caption because of what it does, so the same visual class can map to different HTML elements in different contexts (a `figcaption`, a table footnote). Second, roles nest: a card in a dashboard contains its own miniature headline/body/metadata hierarchy within the page's larger one — the scale must work at both amplitudes (5.4).

### 3.3 Established conventions and what they are worth

A few conventions are near-universal and useful precisely because readers have seen them everywhere: headings larger and bolder than body; body text near-black on light backgrounds; muted tones for metadata; all-caps reserved for short labels, never sentences. These are professional conventions — strong starting points, all routinely broken by deliberate design (all-caps editorial headlines, inverted colour schemes) and none of them encodes a reader-legal requirement except where accessibility standards say otherwise ([Accessible typography](../accessibility/accessible-typography.md)).

The web-specific baseline also worth naming: a body size convention of 16 px as the practical floor for comfortable reading on the web (a convention, not a standard; minimum sizes are genuinely context-dependent — see [Accessible typography](../accessibility/accessible-typography.md) for the WCAG treatment). And the structural convention of heading *levels* (h1–h6 in HTML) mapping to document outline — a semantic hierarchy that the visual hierarchy should express but not replace.

That semantic layer deserves its own note, because it is where implementation drifts. The outline rules that assistive technology and readers rely on: exactly one h1 per page (the page's own title, not the site's — the site name lives in header chrome); levels nest without skipping (an h3 follows an h2, not an h4); a heading introduces content that follows it, so a heading followed by another heading is a smell; and heading levels are structural, not stylistic — "make this text bigger" is never a reason to change its level. The visual scale (3.4) is applied *on top of* these semantics, and the two can even diverge deliberately (an h4 styled smaller than an h3, to de-emphasise a minor branch) — the semantics stay intact for outline navigation while the optics serve scanning.

### 3.4 Building a type scale

A **type scale** is the fixed set of font sizes a product uses, with named steps. Its value is consistency: implementers pick a step, not a pixel value; review checks against steps, not taste.

**Modular scales.** The classic construction picks a base size (web convention: 16 px) and a ratio, then generates steps by repeated multiplication: base × rⁿ. Common ratios, named for musical intervals — the names are conventions inherited from early modular-scale tools:

| Ratio | Interval name | Character |
|---|---|---|
| 1.125 | Major second | Very quiet; suited to dense UI with many steps |
| 1.2 | Minor third | Quiet; the classic "screen scale" |
| 1.25 | Major third | Balanced; versatile default |
| 1.333 | Perfect fourth | Clear contrast; editorial feel |
| 1.414 | Augmented fourth (√2) | Strong; poster-like |
| 1.5 | Perfect fifth | Dramatic; large display steps |
| 1.618 | Golden ratio | Maximum contrast; few steps needed |

A 1.25 scale on a 16 px base generates: 16, 20, 25, 31.3, 39.1, 48.8, 61 — rounded and named (body, delta, gamma, beta, alpha...). A 1.2 scale generates many closely spaced steps, which is why it suits interface typography where hierarchy must be quiet; a 1.5+ scale suits editorial display where headlines must shout. The ratio choice is a *contrast amplitude* decision: how loud should the loudest step be relative to body?

**Named steps.** Real systems do not ship raw numbers; they ship names. Two naming conventions dominate:

- **Semantic role names**: `body`, `body-strong`, `caption`, `heading-sm`, `heading-md`, `heading-lg`, `display`. Maps directly to the role inventory (3.2); the most common in design systems.
- **T-shirt / scale-degree names**: `t-1, t-2...` or `delta, gamma, beta, alpha`. Decouples names from roles so one size can serve two roles; used in editorial-flavoured systems.

Both work; the failure mode is *unnamed* sizes — CSS files where 15 px, 16 px and 17 px body sizes coexist because each feature improvised. The scale exists to make that impossible.

**Rounding and composition.** Generated values are rounded to whole pixels (or 0.5 px) for rendering stability; steps above body usually also get explicit leading values (tighter as size grows — 1.1–1.3 for display, 1.4–1.5 for body, per [Typography fundamentals](typography-fundamentals.md) 3.6) and, in complete systems, paired weights and letter-spacing per step. The scale is therefore not just sizes: it is a table of size + leading + weight (+ face) per step. That table *is* the typographic layer of a design system.

### 3.5 Hierarchy in interface vs editorial contexts

The same levers build both, but the amplitude and the roles differ:

- **Interface hierarchy is quieter and denser.** Steps are closer (1.125–1.25 ratios), weight and tone do more of the work than size (labels vs values in a form are often the same size, differing by weight and tone), and roles are smaller and more numerous (buttons, badges, input labels, helper text, error text). Restraint is the discipline: when everything is bold, nothing is.
- **Editorial hierarchy is louder and sparser.** Steps are farther apart (1.333–1.618), size and voice do the heavy lifting, and the hierarchy expresses the *document outline* (chapters, sections, subsections) over long reading distances. Editorial hierarchies also lean on structural devices interfaces rarely use: drop caps, running heads, folios, cross-references ([Editorial design](editorial-design.md)).
- **The bridge case** — content products (news sites, documentation, dashboards with prose surfaces) — needs both amplitudes: quiet steps for UI chrome, loud steps for article headlines. The scale must therefore define the amplitude boundary explicitly (which steps are "editorial" vs "interface"), the same handover discipline as display/text faces in [Font pairing](font-pairing.md) 3.6.

A note on hierarchy in *empty and loading* states, where hierarchy is tested hardest: with little content, the loudest step can read as shouting at nothing, and with placeholder content, skeleton screens distort the scale's intent. The conventions worth adopting: empty states drop to the quiet middle of the scale (a caption-lead message, not a display headline); loading skeletons reproduce the *roles and spacing* of the real content, not just grey boxes; and promotional overlays get their own bounded amplitude so they neither inherit nor distort the page's hierarchy. These are context-dependent recommendations rather than laws — but every product that skips them rediscovers the same complaint, that its empty screens feel either shouted-at or abandoned.

## 4. How it works: building the hierarchy

### 4.1 The construction sequence

1. **Inventory the roles** actually present in the product (3.2) — walk real screens and pages and list every kind of text.
2. **Choose the amplitude** — quiet (UI-led) or loud (editorial-led) — and pick the ratio (3.4).
3. **Fix body first.** Body size is the pivot everything is measured from; set it from reading conditions (medium, audience, density) rather than from the headline.
4. **Generate steps** above and below body by the ratio; round; prune steps nobody uses.
5. **Assign roles to steps**, with paired leading, weight and tone per role (the table of 3.4).
6. **Encode it** as design tokens or CSS custom properties (5.1) so the scale is enforceable.
7. **Pressure-test** on the three hardest real pages: the densest table screen, the emptiest marketing hero, the longest article.

### 4.2 A worked scale

A quiet-to-moderate product scale (1.25 ratio, 16 px base), with roles, as a table — leading values are conventional starting points:

| Step | Size | Leading | Weight | Typical roles |
|---|---|---|---|---|
| display | 61 px | 1.05 | 700 | Hero headlines |
| h1 | 49 px | 1.1 | 700 | Page titles |
| h2 | 39 px | 1.15 | 700 | Section heads |
| h3 | 31 px | 1.2 | 600 | Sub-sections |
| h4 | 25 px | 1.25 | 600 | Minor headings, lead paragraphs |
| body-strong | 16 px | 1.5 | 600 | Emphasis within body |
| body | 16 px | 1.5 | 400 | Body text, button text |
| caption | 13 px | 1.4 | 400 | Captions, helper text |
| label | 12 px | 1.3 | 600, caps | Eyebrows, field labels |
| micro | 11 px | 1.3 | 500 | Metadata, footnotes (use sparingly) |

Note the pattern to copy: leading tightens as size grows; weight concentrates contrast at the top and middle; the bottom of the scale is carried by tone and case rather than weight. A louder editorial scale would widen the gaps (1.333 or 1.5 ratio) and reserve the display step for the display face.

## 5. Practical application

### 5.1 Encoding the scale in CSS custom properties

```css
:root {
  /* size steps — 1.25 modular scale on 16 px */
  --fs-display: 3.8125rem;  /* 61 px */
  --fs-h1:      3.0625rem;  /* 49 px */
  --fs-h2:      2.4375rem;  /* 39 px */
  --fs-h3:      1.9375rem;  /* 31 px */
  --fs-h4:      1.5625rem;  /* 25 px */
  --fs-body:    1rem;       /* 16 px */
  --fs-caption: 0.8125rem;  /* 13 px */
  --fs-label:   0.75rem;    /* 12 px */
  --fs-micro:   0.6875rem;  /* 11 px */

  /* paired leading */
  --lh-tight: 1.1;
  --lh-heading: 1.25;
  --lh-body: 1.5;
  --lh-caps: 1.3;
}

body { font-size: var(--fs-body); line-height: var(--lh-body); }
h1   { font-size: var(--fs-h1);   line-height: var(--lh-tight); font-weight: 700; }
h2   { font-size: var(--fs-h2);   line-height: var(--lh-heading); font-weight: 700; }

.eyebrow {
  font-size: var(--fs-label);
  font-weight: 600;
  line-height: var(--lh-caps);
  letter-spacing: 0.08em;
  text-transform: uppercase;
}

.metadata { font-size: var(--fs-caption); color: var(--ink-muted); }
```

The point of the custom properties is not aesthetics but *enforcement*: any new component pulls from the scale, and a review can diff sizes against the token list. Spacing values that position roles (margins around headings) belong in the same token layer — hierarchy lives in spacing as much as in glyphs (3.1, lever 4).

Enforcement has a machine-checkable form worth adopting in code review and agent workflows: a lint rule (or simple script) that scans stylesheets for font-size, font-weight and line-height values *not* present in the token list, and flags each as either a new token candidate or a bug. The same scan over margins and padding against the spacing tokens closes the spacing half. What remains uncovered — whether the *right* step was chosen for a role — is a design judgement, but it is a judgement applied to five candidate steps instead of a thousand pixel values, which is exactly the difference a system exists to make.

```css
:root {
  /* spacing rhythm for the role system — one scale, reused everywhere */
  --space-1: 0.5rem;   /* intra-role: label to value */
  --space-2: 1rem;     /* within a block: paragraph gap */
  --space-3: 1.5rem;   /* body-to-body block separation */
  --space-4: 2.5rem;   /* section gap */
  --space-5: 4rem;     /* major section boundary */
}
h2 { margin-top: var(--space-4); margin-bottom: var(--space-2); }
.field { gap: var(--space-1); }        /* label above value: tight grouping */
.section { padding-top: var(--space-5); }
```

Two rules keep the rhythm meaningful: spacing *above* a heading should exceed spacing below it (proximity binds the heading to its own content, not the previous section's), and the spacing scale should be independent of the size scale — ten sizes and five spaces cover nearly every layout, while thirty ad-hoc margins cover none.

### 5.2 Buttons, numerals and technical text

Three roles deserve explicit treatment because they break the body-first assumptions:

- **Button text**: sized at body or a hair above, weight 500–600, never muted — actions are content users search for. Keep letter-spacing neutral (tracked caps on buttons is a dated pattern) and leading single-line.
- **Numerals**: comparison is the job, so tabular figures (`font-variant-numeric: tabular-nums`) for anything in columns or updating in place; larger sizes for KPI values; monospace for values that must align across mixed content ([Typography fundamentals](typography-fundamentals.md) 5.2). Never let a proportional-figure headline font own a data table.
- **Technical info**: code, IDs, paths in the mono voice ([Font pairing](font-pairing.md) 3.7), sized at body or one step down, distinguished by voice *and* tone so scanning eyes can filter for it.

The **metadata** role deserves one more paragraph because it is the most abused. Metadata (timestamps, authors, counts, versions) is text the reader mostly ignores — until they need it, and then they need it *precisely*. So its treatment is a narrow target: small but above the legibility floor, muted but above the contrast floor, consistent in position across the product (a fixed slot where metadata always lives), and never the place where critical information hides (error details, deadlines are not metadata). A useful test: imagine the one moment a user hunts for a timestamp — does the hierarchy make it findable *and* ignorable everywhere else?

### 5.3 Responsive hierarchy

Hierarchy must survive the small screen, where the loudest steps shrink first. Two mechanisms: reduce the top steps' sizes at narrow widths (media queries), or scale continuously with fluid typography — `clamp()`-based sizes that grow with the viewport between fixed floors and ceilings, covered with a worked example in [Web typography](web-typography.md) 3. Either way, the *relationships* between steps must survive: if display shrinks to h1's size while h1 stays put, the hierarchy collapses into two equal headings. Scale the ratio, not just the top step.

## 6. Decision framework

When building or reviewing a hierarchy, ask in order:

1. **Is the role inventory complete?** Walk real content; any text that has no role will improvise one.
2. **What amplitude does the context need?** UI-led → quiet ratio (1.125–1.25); editorial-led → loud ratio (1.333+); bridge case → define both and the boundary.
3. **Which levers lead?** Dense UI → weight + tone + spacing lead, size quiet; editorial → size + voice lead.
4. **Is every contrast multi-lever?** A heading distinguished only by size is fragile; add weight, spacing or tone.
5. **Does de-emphasis exist?** Metadata and captions must be *visibly* quieter than body; a hierarchy without a quiet end reads as all-shout.
6. **Are the steps named and encoded?** Tokens or custom properties; no raw pixel values in components.
7. **Does it survive the three pressure pages?** Densest, emptiest, longest.

Explicitly: the role inventory and lever set are established professional structure; the ratios and their musical names are conventions from modular-scale practice; the specific values in the worked table are conventional starting points to be tuned to the product's content and audience.

## 7. Examples

**Example 1 — the dashboard card.** A card contains: an all-caps tracked label ("REVENUE"), a 31 px tabular-figure KPI value, a 13 px muted delta line, and a 12 px metadata footnote. Hierarchy inside the card uses tone + weight + case, not size alone; the KPI value is the only large element, so the card scans in one fixation. The card nests inside the page's h2/h3 structure without competing — two amplitudes, one scale.

**Example 2 — the article page.** A content page uses the loud end: 49 px h1, 31 px h2 with generous space above, 16 px body at 65-character measure, 13 px captions under figures. The h2 spacing pattern (large top margin, small bottom margin) binds headings to their sections (3.1, lever 4) and gives the page its scannable outline.

**Example 3 — the form.** A dense settings form uses almost no size hierarchy: 16 px values at weight 500, 13 px all-caps tracked labels at muted tone, 13 px helper text, 13 px error text in the semantic error colour. The hierarchy is legible because weight and tone are consistent; a size-based version would crowd the layout and break alignment.

**Example 4 — the collapsed scale.** A marketing page's h1 (49 px) and display step (61 px) both shrink to 39 px on mobile, while h2 (39 px) stays — three competing 39 px headings. The fix: shrink the *interval* (ratio 1.15 on mobile) so relative order survives ([Web typography](web-typography.md) 3 shows the fluid version).

**Example 5 — a hierarchy evaluation walkthrough.** The pressure test (4.1, step 7) on a real SaaS product: the *densest* page (a settings table) reveals that field labels (13 px, 400) and helper text (13 px, 400) are indistinguishable — a role collision fixed by giving labels 500 weight and tracked caps. The *emptiest* page (a welcome screen) shows the display step is defined but nobody dares use it; the fix is an editorial decision recorded in the scale, not a new size. The *longest* page (a knowledge-base article) shows h3 spacing equal above and below, so sections blur; the fix is the spacing rule above (space-above > space-below). Three pages, three different levers — which is the point: the walkthrough finds the lever the scale under-uses, not just the sizes that are wrong.

## 8. Common mistakes

- **Size-only hierarchy.** One lever; fails in dense layouts and for readers with low size sensitivity. Combine levers.
- **Too many weights.** Six weights in one screen flatten contrast into noise; two or three carry a page ([Typeface selection](typeface-selection.md) 3.4).
- **Muted text that is also small.** De-emphasis stacking (small + light + low contrast) makes metadata illegible; keep at least one accessibility floor ([Accessible typography](../accessibility/accessible-typography.md)).
- **Missing de-emphasis.** Every role at full contrast — captions, metadata and body all shouting; the quiet end of the scale is hierarchy too.
- **Steps nobody can name.** Raw pixel values scattered across components; encode the scale as tokens.
- **All-caps sentences.** Caps are a label signal; applied to headings or body they slow word recognition and read as UI chrome.
- **Hierarchy that ignores spacing.** Headings floating with equal margins above and below; proximity groups the heading into the wrong block.
- **Responsive scaling that collapses intervals.** Shrinking the top steps without shrinking the intervals; preserve relative order.
- **Skipping the quiet end.** No caption/metadata treatment defined, so features improvise 14 px grey text at three different tones.
- **Heading levels used as styles.** Choosing h3 because it *looks* right, then nesting the outline wrong; semantics and optics are separate layers and must each stay coherent (3.3).
- **Spacing scale missing.** Sizes tokenised but margins improvised; the proximity lever (3.1, lever 4) then varies per developer, and grouping reads inconsistently.
- **Metadata treated as an afterthought.** No defined slot, tone or floor, so timestamps and authors scatter; metadata is a role like any other (5.2) and earns a definition.

## 9. Evaluation checklist

- [ ] Role inventory covers every text element on real screens and pages
- [ ] Scale defined with named steps; encoded as tokens/custom properties
- [ ] Ratio matches the intended amplitude (quiet for UI, loud for editorial)
- [ ] Every heading contrast uses at least two levers (size + weight, or size + spacing)
- [ ] De-emphasis exists and stays accessible (caption/metadata contrast meets requirements)
- [ ] Leading paired per step; tightens as size grows; unitless in CSS
- [ ] Spacing rhythm groups headings with their sections (more space above than below)
- [ ] Buttons at body-ish size, medium weight, never muted
- [ ] Numerals tabular where comparison matters; mono voice bounded to technical roles
- [ ] Responsive behaviour preserves relative order between steps
- [ ] Metadata role defined: slot, tone, floors, and nothing critical hidden in it (5.2)
- [ ] Heading levels follow the outline semantics: one h1, no skipped levels (3.3)
- [ ] Empty, loading and overlay states follow the hierarchy rather than improvising (3.5)
- [ ] Pressure-tested on the densest, emptiest and longest real pages

## 10. Related topics

- [Typography fundamentals](typography-fundamentals.md) — the anatomy and spacing mechanics behind every lever
- [Typesetting](typesetting.md) — measure, leading and alignment for the body roles
- [Font pairing](font-pairing.md) — the voice lever and the display/text handover
- [Web typography](web-typography.md) — fluid scales and token implementation in CSS
- [Editorial design](editorial-design.md) — document-scale hierarchy: running heads, folios, front matter
- [Accessible typography](../accessibility/accessible-typography.md) — contrast and resize obligations constraining every lever
- [Principles of design](../foundations/principles-of-design.md) — hierarchy as an instance of the general principles
- [Colour theory](../colour/colour-theory.md) — tone as a lever interacts with palette design

## 11. References

- Robert Bringhurst, *The Elements of Typographic Style* (Hartley & Marks, 4th ed. 2012) — canonical statements of typographic hierarchy, scale discipline and spacing conventions. [canonical]
- Ellen Lupton, *Thinking with Type* (Princeton Architectural Press, 2nd ed. 2010) — hierarchy, scale and the visual grammar of type. [canonical]
- Jakob Nielsen / Nielsen Norman Group, "F-Shaped Pattern For Reading Web Content" — the scan-first reading behaviour underlying interface hierarchy conventions. [canonical]
- WCAG 2.x, Success Criterion 1.4.8 (Visual Presentation) — line-spacing and paragraph-spacing thresholds cited by Baymard's readability research. https://baymard.com/research-articles/line-length-readability [accessed 2026-11-23]
- MDN Web Docs, "clamp()" — including the WCAG 1.4.4 sizing note (max ≥ 2 × min) used in responsive hierarchy. https://developer.mozilla.org/en-US/docs/Web/CSS/clamp [accessed 2026-11-23]
- Sections 3.1 (lever model), 3.4 (modular scale construction and musical-interval naming) and 5 (token encoding) are synthesis of the sources above and of established design-system practice; ratios and worked values are conventional starting points.
