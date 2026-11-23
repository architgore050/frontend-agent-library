# Typesetting

## 1. What is it?

Typesetting is the craft of arranging continuous text so that reading is effortless: choosing the measure (line length), the leading (line height), the alignment, the paragraph handling and the spacing system that turn a stream of characters into a comfortable page. Where hierarchy decides *what matters* ([Typographic hierarchy](typographic-hierarchy.md)) and pairing decides *who speaks* ([Font pairing](font-pairing.md)), typesetting decides *how the text flows* — the discipline most responsible for readability in the precise sense defined in [Typeface selection](typeface-selection.md) 3.2.

This file covers: alignment options and when each is legitimate; justification and its machinery (hyphenation, rivers, rag control); the measure convention and its reasoning; line height by context; letter-spacing adjustments for caps and small text; paragraph spacing; widows and orphans; and modern CSS text wrapping, including `text-wrap: balance` and `pretty`. The anatomy concepts behind these controls (x-height, extenders, tracking) are defined in [Typography fundamentals](typography-fundamentals.md).

## 2. Why does it matter?

Typesetting is invisible when right and exhausting when wrong. Readers cannot name a 90-character measure or a 1.2 line height, but they feel the difference: lines that are too long make the eye lose its way on the return sweep; lines too short fragment every phrase; leading too tight makes ascenders and descenders collide and the page claustrophobic; leading too loose disconnects the lines so the eye re-anchors at every line start. Because these effects accumulate over paragraphs, typesetting quality determines whether long-form content gets read at all.

For interface work, typesetting also carries a scanning cost: dense screens (tables, settings, empty states, notifications) are read in bursts, and every burst benefits from short measures, clear alignment and unambiguous grouping. The good news is that typesetting is the most rule-friendly part of typography: its conventions are stable, numeric, and translate directly into CSS.

## 3. Core principles

### 3.1 Alignment

Four options, with legitimate uses and failure modes:

- **Left-aligned (ragged right)** is the default for screens and most contemporary text. It is legitimate nearly everywhere: the rag absorbs word-length variation without hyphenation games, and every line starts at a predictable anchor. Its failure mode is a *bad rag* — a right edge so erratic that the text block looks torn (see 3.3).
- **Right-aligned (ragged left)** suits short, disconnected elements: numbers in a table column, dates, page numbers, pull-quote attributions. For running text it is hostile: the left edge — where the eye re-anchors each line — is ragged, which measurably slows reading. Use for short runs only.
- **Centred** suits ceremonial and display contexts: titles, invitation lines, epitaphs, short poems. Like right alignment it destroys the reading anchor, so paragraphs of centred body text are a classic amateur marker; but a centred three-line dedication is perfectly judged.
- **Justified** fills each line to the full measure by expanding word spaces. It produces the clean block shape of print tradition and is the norm in high-end book and newspaper setting *where hyphenation and optical margin control are available*. On screens without hyphenation, justification produces wide, uneven word gaps ("rivers") that damage texture badly. Web guidance in one line: do not justify web body text unless you also enable hyphenation — and even then prefer ragged right for UI and screen reading (a professional convention, not a law; justified text with good hyphenation remains standard in print).

A fifth, hybrid technique worth knowing from print: *optical margin alignment* (hanging punctuation), which pushes punctuation at line edges into the margin so the visual edge of the text block aligns even when commas and quotes protrude. CSS expresses it as `hanging-punctuation` (limited support; progressive enhancement where available).

The alignment decision, as a reference table:

| Content | Alignment | Why |
|---|---|---|
| Running text (web, UI) | Left, ragged right | Preserves the reading anchor; no hyphenation dependency |
| Long-form print (books, reports) | Justified with hyphenation | Print tradition and tools support it; block shape aids long reading |
| Table numbers and currencies | Right | Digits align by place value; comparison becomes vertical |
| Dates, IDs in lists | Right or left per column meaning | Consistency of the column's axis |
| Pull-quote attributions | Right | Short runs; conventional attribution position |
| Titles, dedications, epigraphs | Centred | Ceremonial register for very short runs |
| Running body in centred layouts | Almost never | Destroys the anchor for no gain |

The column of "why" is the part to internalise: alignment choices follow from what the eye does with the edge — reading anchors on the left (in Latin scripts), compares on the right in numeric columns, and tolerates centring only when lines are few and self-contained.

### 3.2 Justification machinery: hyphenation, rivers, rag

Justification works by distributing surplus space into word gaps. The variables:

- **Hyphenation** gives the engine more, smaller fragments to distribute, which tightens word gaps. In CSS: `hyphens: auto` (requires a `lang` attribute so the browser picks the right hyphenation dictionary — a real gotcha: set `lang` on `<html>`). For print and professional layouts, hyphenation is usually paired with limits: no hyphenating consecutive lines (cap around 2–3 in a row), no hyphenation of the last line of a paragraph, and none in headings or narrow display settings.
- **Rivers** are diagonal channels of white space that appear when consecutive lines have word gaps aligned vertically. They are the visual signature of poorly justified text (or of justified text at short measures). Corrections: enable hyphenation, adjust the measure, or in professional tools apply letter-spacing fines per paragraph.
- **The rag** is the shape of the right edge in ragged setting. A good rag varies line endings naturally while keeping the edge roughly even; a bad rag has extremes — very short lines ("ambush lines") next to very long ones. Print practice reviews the rag line by line and rewords or adjusts where needed; on the web, `text-wrap: pretty` (5.5) automates the worst offenders.

Reading rag quality takes a minute and follows the shape, not the rules: scan down the right edge and look for (a) lines dramatically shorter than their neighbours, (b) repeated one-word lines, (c) hyphens clustering in the same column position, (d) an edge that jogs in and out like a saw blade rather than undulating gently. Patterns (a) and (b) are copy problems — a reword or a slightly wider column fixes them; (c) is a hyphenation-settings problem; (d) is often a measure problem, since very narrow measures make even words look long. A rag that fails all four checks is usually a symptom of a measure outside the 45–75 convention (3.3), and the measure fix dissolves the others.

Professional justification settings worth naming (conventional print values): minimum line length for justified setting around 55–65 characters (below it, gaps become visible; justified narrow columns are the classic newspaper failure), and hyphenation "zones" that allow slight width flexibility so the engine is not forced into bad breaks on every line.

The CSS hyphenation controls, as a reference (support varies; check before relying on any beyond `hyphens: auto`):

| Property / setting | What it controls | Practical note |
|---|---|---|
| `hyphens: auto` | Enables dictionary hyphenation | Requires `lang` on `<html>` or an ancestor; the one property that works everywhere current |
| `hyphens: manual` | Only `&shy;` (soft hyphen) markers apply | The default; explicit author control |
| `hyphenate-character` | Which character marks the break | Rarely changed; defaults to the hyphen |
| `hyphenate-limit-zone` | How much trailing space justifies a break | Part of CSS Text Level 4; partial support |
| `hyphenate-limit-chars` | Minimum letters before / after / total | The print-style control (e.g. 6 3 3); partial support, worth declaring with fallback |

The reading of that table for web work: declare `hyphens: auto` plus `lang`, and treat the finer limits as progressive enhancement — professional hyphenation discipline (no consecutive-line hyphens, no hyphenating the last word) is not yet fully reachable in CSS, so bad breaks are corrected by adjusting measure or wording, exactly as print editors do.

### 3.3 Measure: line length and its reasoning

The measure is the number of characters per line, counted as an average of the lowercase alphabet (professionals count characters, not words or centimetres). The canonical convention, stated by Robert Bringhurst: anything from **45 to 75 characters** is widely regarded as a satisfactory length of line for a single-column page set in a serif text face, with around **66 characters** often cited as the sweet spot. [canonical; the 45–75 formulation also appears verbatim in typographic references surfaced in this session's search] Emil Ruder, working in the Swiss tradition, put the optimum at **50–60 characters**, observing that reader attention is strongest at the start of each line and fades across its length. [canonical; cited by Baymard]

Why the range exists — the reasoning, not just the numbers:

- **Too long (>~80)**: the eye's return sweep from line end to line start loses its place; readers either skip lines or (worse) re-read. Attention also fades across a long line, so the line end is skimmed. Long lines increase the cost of every fixations-to-fixation jump.
- **Too short (<~40)**: the eye jumps too often, every line breaks words out of their phrase context, hyphenation and rag become dominant, and the block fragments rhythm. Short measures also inflate the impact of every awkward break.
- **The sweet spot (45–75, ideally ~60–70)**: enough characters per fixation sweep to be efficient, short enough to keep the return sweep accurate.

Practical numbers for web contexts, verified from Baymard's readability research: **50–75 characters** optimal for body text; WCAG 1.4.8 allows up to **80 characters** per line (40 or fewer for CJK); implementation via `max-width` of roughly **70ch** or **34em** (both font-relative so the measure scales with type size); user fatigue observed at 100+ characters; mobile portrait rarely has a measure problem while mobile landscape can. [accessed]

Adjacency rule worth stating: measure and leading interact (see 3.4) — longer measures need more leading to keep the return sweep tracked; shorter measures tolerate tighter leading. And the "ch" unit note: `70ch` measures the *zero* glyph width, so the actual character count varies per face — set the measure optically and count on real content (an agent can count programmatically: render, then count).

### 3.4 Line height (leading) by context

Leading is a ratio, set unitless in CSS ([Typography fundamentals](typography-fundamentals.md) 3.6). Conventional starting points by context — tune optically for the face's extenders, the measure and the audience:

| Context | Conventional line-height | Reasoning |
|---|---|---|
| Display headlines (≥40 px) | 1.0–1.15 | Large glyphs carry their own air; tight leading binds multi-line headlines |
| Subheadings | 1.15–1.3 | Slightly airier than display |
| Interface body (16 px-ish) | 1.4–1.5 | Comfort plus density; matches WCAG 1.4.8's 1.5 suggestion for accessible text |
| Long-form editorial body | 1.5–1.7 | Fatigue accumulates; air helps sustained reading |
| All-caps settings | 1.1–1.3 (× cap height) | Caps have no descenders; visually they need less room than lowercase |
| Small labels / UI chrome | 1.2–1.4 | Single lines mostly; enough room for zoom/resize |
| Data tables | 1.3–1.4 | Density with distinctness; tabular figures need vertical room too |

The two governing rules: **longer measure ⇒ more leading** (the eye needs help tracking back), and **bigger size ⇒ tighter leading** (glyphs carry their own air). Both push in opposite directions across contexts, which is why the table has a spread rather than a single number. WCAG 1.4.8 (level AAA) asks for line spacing ≥1.5 within paragraphs and paragraph spacing ≥2 × line spacing for long-form text — an accessibility floor, not a design optimum. [accessed via Baymard]

### 3.5 Letter-spacing for caps and small text

The conventions (professional convention, not law): **open up all-caps and small tracked labels** — caps lack descenders and lowercase rhythm, so untracked caps look cramped; a common starting point is +0.05em to +0.1em, scaled in `em` so it tracks size ([Typography fundamentals](typography-fundamentals.md) 3.6). **Tighten large display** slightly (−0.01em to −0.03em) where the face's text-size sidebearings look loose at hero sizes. **Never tighten body text**: negative tracking on running text fuses word shapes and is the fastest way to make competent text look broken. Also: tracked caps need tracking-aware alignment — a tracked label's trailing letter-space shifts centring by half a space; CSS `text-box-trim`/padding nudges or simply left alignment avoid the artifact.

### 3.6 Paragraph handling: spacing, indents, breaks

Two legitimate systems, never mixed: **block paragraphs** (space between, no indent — the web and UI default; conventional spacing 0.75–1 × line height, with WCAG 1.4.8's ≥2 × line spacing as the accessibility floor) and **indented paragraphs** (no space between, first-line indent of 1–2 em — the book tradition, which keeps the text block's colour continuous). Mixing both is a known amateur marker in print.

Paragraph spacing also interacts with the scanning mode of the surface — the same 1.5em gap that is generous in a book is cramped in a settings screen:

| Context | Conventional paragraph gap | Reasoning |
|---|---|---|
| Book-style long-form (indented system) | None (first-line indent 1–2em) | The block's colour stays continuous |
| Web article / documentation | 1–1.5em | Air between ideas without breaking the column |
| Interface prose (descriptions, empty states) | 1.5–2em | Screens scan in bursts; clearer separation |
| WCAG 1.4.8 AAA long-form | ≥ 2 × line spacing | The accessibility floor [accessed via Baymard] |
| Data-adjacent prose (notes under tables) | 0.5–1em | Notes bind tightly to their table |

Related break rules that keep paragraphs professional: no *widows* (a paragraph's last line alone at the top of a page/column) and no *orphans* (a paragraph's first line alone at the bottom) in long documents — handled by editors and CSS (5.5); a minimum of two or three words on a wrapped last line (a one-word last line, especially a short one, is a rag failure); and no heading stranded at the bottom of a column with its body overleaf ("headless section" — print tools have keep-with-next; CSS `break-after: avoid` on headings).

### 3.7 Text wrapping in CSS

Modern CSS has grown real typesetting controls; the pair that matters most:

- **`text-wrap: balance`** wraps a block so that line lengths are balanced rather than greedily filled — the fix for ugly multi-line headings whose second line is one short word. MDN recommends it for short blocks (headings, captions, blockquotes) and notes the browser line caps: balancing applies to at most **six lines in Chromium and ten in Firefox**, beyond which it has no effect. Baseline across browsers since March 2024. [accessed]
- **`text-wrap: pretty`** keeps the default greedy filling but uses a slower algorithm that favours better layout — its stated purpose is avoiding bad last lines and orphans in body copy. No line cap, but a performance cost, so it belongs on long-form paragraphs, not on everything. [accessed]
- Historic and structural controls: `hyphens: auto` with `lang` set (3.2); `overflow-wrap: anywhere`/`break-word` for unbreakable strings (URLs, IDs); `word-break` for script-specific breaking; `white-space` for preformatted text; `line-break` for CJK punctuation rules.

The overflow and break controls, for the strings typesetting cannot change (identifiers, URLs, serial numbers):

| Control | Purpose | Typical use |
|---|---|---|
| `overflow-wrap: break-word` | Break an unbreakable word rather than overflow | Long URLs in prose |
| `overflow-wrap: anywhere` | As above, plus allow breaks for min-content sizing | Narrow columns with long tokens |
| `word-break: break-all` | Break anywhere, even mid-word in normal scripts | Last resort; distorts reading |
| `word-break: keep-all` | No breaks within CJK words | CJK text with meaningful compounds |
| `line-break: strict` | Enforce punctuation rules on breaks | CJK body text |
| `white-space: pre` / `pre-wrap` | Preserve spaces and newlines | Code blocks, transcripts |

The pattern for a data-dense product: let prose wrap normally, give code and identifiers `pre`-style preservation inside containers that scroll (`overflow-x: auto`), and reserve `break-all` for genuinely meaningless character runs (hashes, licence keys) where breaking anywhere is honest about the content.

## 4. How it works: the interaction model

Typesetting variables are coupled; changing one moves the others. The four working relationships:

1. **Measure × leading.** Longer measure, more leading; shorter measure, tighter. (3.3/3.4)
2. **Measure × justification.** Justification needs a minimum measure (~55–65 characters) to hide its word-gap expansion; ragged right tolerates any measure. (3.1/3.2)
3. **Size × leading.** Bigger size, tighter ratio — but the *face's* extender length sets the floor. (3.4; [Typography fundamentals](typography-fundamentals.md) 4.4)
4. **Measure × font size.** The measure is characters, not pixels: when type size grows, the same pixel width silently becomes a *shorter* measure. This is why measure must be set in font-relative units (`ch`, `em`) — a `max-width` in pixels breaks when type scales up ([Web typography](web-typography.md) ties this to fluid sizing).

An agent or reviewer can apply the model as a check sequence: fix body size → set measure in `ch`/`em` → set leading by context → choose alignment → only then decorate (tracking on labels, balance on headings).

A worked pass of the sequence on one surface — a documentation article: body fixed at 1 rem; measure set to `max-width: 68ch` on the article container; leading 1.6 on prose and 1.2 on the h2/h3 (their size wants less); alignment left-ragged with `text-wrap: pretty` on prose and `balance` on headings; and only then decoration — tracked caps on the section eyebrows (+0.08em), tabular figures on the version table, `break-after: avoid` on headings. Every later file in the domain ([Typographic hierarchy](typographic-hierarchy.md) 5.1, [Web typography](web-typography.md) 5) assumes this sequence has run; the tables above are its reference data.

The sequence matters because it runs from the least reversible decision to the most decorative. Measure is structural — it constrains the grid and the layout ([Grid systems](../layout/grid-systems.md)); leading follows measure; alignment follows the content's reading mode; and decoration adapts to whatever survived. Teams that start from decoration (a tracking treatment, a justified look) and work backwards constantly re-litigate earlier decisions; teams that follow the sequence ship typesetting that survives redesigns of everything above it.

## 5. Practical application

### 5.1 A web body-text recipe

```css
/* hyphenation requires the language attribute in markup: <html lang="en"> */

.prose {
  font-size: 1rem;                 /* 16 px body; scale in the hierarchy layer */
  line-height: 1.6;                /* unitless; long-form range 1.5–1.7 */
  max-width: 68ch;                 /* font-relative measure ≈ 50–75 characters */
  letter-spacing: normal;          /* never tighten body text */
  text-wrap: pretty;               /* better last lines and fewer orphans */
  hyphens: auto;                   /* only if justified or narrow columns demand it */
}

.prose + .prose {                  /* block paragraphs */
  margin-top: 1.5em;               /* ≥ 1 × line height; 2 × for WCAG 1.4.8 AAA */
}

h2 {
  text-wrap: balance;              /* balanced multi-line headings (≤6 lines: Chromium) */
  break-after: avoid;              /* never strand a heading at a column/page end */
  margin-top: 2.5em;
  margin-bottom: 0.75em;           /* binds the heading to what follows */
}

.data-table td { text-align: right; font-variant-numeric: tabular-nums; }
.pull-quote figcaption { text-align: right; }  /* short runs only */
```

For multipage web output (print stylesheets, paginated reports), the break rules translate directly:

```css
@media print {
  h2, h3 { break-after: avoid; }        /* no stranded headings */
  figure, table { break-inside: avoid; } /* keep captions with content */
  .prose { orphans: 3; widows: 3; }      /* minimum lines per fragment */
  .prose { text-align: justify; hyphens: auto; } /* print register: block shape */
}
```

The `orphans` and `widows` properties take the minimum number of lines a paragraph may leave at the bottom or top of a page — three is a common professional floor, two the minimum worth declaring. Browsers honour them in paged media (print, PDF export); on continuous screens they are harmless inert declarations. The justified setting here is the print-register choice from 3.1 — enabled *with* hyphenation and `lang`, which is why the print block is the one place web justification becomes legitimate.

### 5.2 Print and export recipes

For multipage documents (books, reports, programmes) the same variables carry over with print discipline: justified setting *with* hyphenation enabled and widow/orphan control on; measures per column rather than per page (a two-column A4 spread runs 35–45 characters per column — below the single-column floor, which is exactly why columns pair well with tighter leading); baseline-grid alignment so leading steps land on grid lines ([Editorial design](editorial-design.md) 3.2); and hanging punctuation where the tool supports it.

## 6. Decision framework

1. **What is the reading mode?** Sustained reading (articles, documentation) → ragged right or justified-with-hyphenation, measure 50–75, leading 1.5–1.7. Scanning (UI, tables) → ragged right, shorter measures, tighter leading per role.
2. **Is justification justified?** Only with hyphenation available and measure ≥ ~55 characters — otherwise ragged right. (Convention, not law; print tradition differs from web defaults.)
3. **Where does the measure break?** Set `max-width` in `ch`/`em`, verify with a character count on real content, not by eye on one string.
4. **Does every all-caps run have tracking?** +0.05–0.1em default; check centring artifacts.
5. **Are break rules enforced?** Widow/orphan control, heading keep-with-next, `text-wrap: balance` on headings, `pretty` on long prose.
6. **Is the accessibility floor met?** Line height ≥1.5 and paragraph spacing ≥2 × line height where WCAG 1.4.8 AAA applies; CJK measures ≤40 characters. [accessed via Baymard]
7. **Do unbreakable strings have a plan?** URLs, identifiers and hashes get overflow handling (3.7), not a broken layout.

A combined reference table for the most common surface — a responsive article or documentation page — gathering the decisions this file recommends into one place (all values are conventional starting points tuned per face and audience):

| Variable | Recommended starting point | Source of authority |
|---|---|---|
| Measure | `max-width: 68ch` (≈50–75 characters) | Bringhurst 45–75 [canonical]; Baymard 50–75 [accessed] |
| Body leading | 1.5–1.6, unitless | Context table 3.4; WCAG 1.4.8 floor [accessed] |
| Paragraph gap | 1.5em (2em for AAA long-form) | 3.6 table; WCAG 1.4.8 [accessed] |
| Alignment | Left, ragged right | 3.1; justified only with hyphenation |
| Headings | `text-wrap: balance`; space above > below | MDN [accessed]; proximity rule |
| Prose wrapping | `text-wrap: pretty` | MDN [accessed] |
| Hyphenation | `hyphens: auto` + `lang`; only if justified or narrow | 3.2 table |
| Numerals | Tabular in any column context | [Typography fundamentals](typography-fundamentals.md) 5.2 |

Explicitly: the 45–75 measure is the canonical convention (Bringhurst; Ruder's 50–60); 50–75 and the 80-character ceiling are the web-verified guidance (Baymard; WCAG); leading ranges and tracking values are conventional starting points; the alignment defaults for screens are professional convention, routinely and legitimately overridden in editorial contexts.

## 7. Examples

**Example 1 — the measure fix.** A documentation site's article column runs 100+ characters on desktop. Readers report "losing their place". Fix: `max-width: 68ch` on the prose container plus leading 1.6 — the same content, same font, same size, transformed reading comfort. The failure was never legibility; it was measure.

**Example 2 — the justified web page.** A team sets a marketing site's paragraphs justified "for the print look" without hyphenation. Wide word gaps and rivers appear; the rag of left alignment had been healthier. Fix: `text-align: left` (or justified + `hyphens: auto` + `lang` if the block shape is truly required).

**Example 3 — the balanced headline.** A hero heading wraps as three lines ending in a single word. `text-wrap: balance` redistributes the break so the three lines sit even — no copy changes, no manual `<br>`, one CSS line. On the same page, `text-wrap: pretty` on paragraphs removes the frequent one-word last lines.

**Example 4 — the cramped caps.** An all-caps nav set at 12 px with default tracking looks welded shut. `letter-spacing: 0.08em` opens it; the same treatment on the eyebrow labels unifies the chrome voice ([Typography fundamentals](typography-fundamentals.md) 3.6).

**Example 5 — the print report.** An A4 report sets justified 10.5 pt text with hyphenation at 66-character measure on a 6-column baseline grid; widows and orphans are checked on export. The same content on the web keeps left alignment, `68ch` and block paragraphs — one system of principles, two correct settings per medium.

**Example 6 — the settings screen.** A settings form's helper text was centred "for symmetry", leaving every line starting at a different x. Fix: left alignment at 1.5em paragraph gap, labels tracked caps, and the rag accepts a slightly uneven right edge — symmetry restored by the *left* edge, which is the one the eye uses.

**Example 7 — the CJK measure check.** A bilingual site inherits the 68ch measure for Chinese paragraphs. CJK glyphs are full-width, so `ch` (based on the "0" glyph) mis-measures badly; the fix is a separate measure for `[lang|="zh"]` content around 35–40 characters, matching the WCAG 1.4.8 CJK guidance Baymard cites. [accessed via Baymard]

## 8. Common mistakes

- **Pixel measure.** `max-width: 640px` silently becomes a short measure when type scales; use `ch`/`em`.
- **Justified text without hyphenation on the web** — rivers and gappy texture; the most visible typesetting failure on screens.
- **Missing `lang`.** `hyphens: auto` does nothing without a language attribute to pick a dictionary.
- **Centred or right-aligned paragraphs** of running text — destroyed reading anchor.
- **Negative tracking on body.** Fuses word shapes; tightening belongs to display sizes.
- **All-caps without tracking.** The opposite error; caps need the air.
- **Fixed line-height in px** inherited into larger text; unitless always.
- **Ignoring widows/orphans in long documents.** They survive every design review and surface in the PDF.
- **Leading tuned for the wrong face.** Long-extender faces need more room; short-extender faces look gappy at the same ratio (face-dependent, not a universal number).
- **`text-wrap: balance` on long paragraphs.** It caps out (6 lines Chromium / 10 Firefox) and belongs on headings; `pretty` is the body tool. [accessed]
- **One measure for every script.** `ch`-based measures mis-measure CJK and other wide scripts; set per-language measures (3.3, Example 7).
- **Mixed paragraph systems.** Indents *and* spacing together, or neither; pick one system per document.
- **Stranded headings.** No `break-after: avoid` (or keep-with-next equivalent) in long documents; headings open sections that begin overleaf.

## 9. Evaluation checklist

- [ ] Measure counted on real content, set in `ch`/`em`, inside 50–75 (web) / 45–75 (canonical) characters
- [ ] Long-form line height ≥1.5 and paragraph spacing ≥2 × line height where AAA applies
- [ ] Leading tuned to face extenders and measure; unitless in CSS
- [ ] Alignment matched to content: rag for running text, right/centred only for short runs
- [ ] Justified text (if any) has hyphenation, `lang`, and a ≥55-character measure
- [ ] All-caps runs tracked (+0.05–0.1em), centring artifacts checked
- [ ] Body text not tracked negative
- [ ] `text-wrap: balance` on multi-line headings; `pretty` on long prose
- [ ] Widow/orphan control and heading keep-with-next in long documents
- [ ] Unbreakable strings (URLs, IDs) handled (`overflow-wrap`)
- [ ] CJK content measured at ≤40 characters where applicable
- [ ] Overflow plan exists for unbreakable strings (3.7 table)
- [ ] Rag reviewed on real content: no ambush lines, no clustered hyphens, no saw-blade edge (3.2)
- [ ] Print/register variants (if any) keep their own justified-with-hyphenation discipline (5.1)
- [ ] Alignment table's "why" column satisfied for every non-default alignment (3.1)

## 10. Related topics

- [Typography fundamentals](typography-fundamentals.md) — anatomy behind leading and tracking decisions
- [Typographic hierarchy](typographic-hierarchy.md) — the roles whose body treatments this file sets
- [Editorial design](editorial-design.md) — grids, baseline alignment and multipage flow
- [Web typography](web-typography.md) — fluid sizing and the CSS delivery of these settings
- [Accessible typography](../accessibility/accessible-typography.md) — the WCAG thresholds cited throughout
- [Grid systems](../layout/grid-systems.md) — how measures derive from column structures
- [Principles of design](../foundations/principles-of-design.md) — the general principles (proximity, rhythm) that typesetting enacts

## 11. References

- Robert Bringhurst, *The Elements of Typographic Style* (Hartley & Marks, 4th ed. 2012) — the canonical measure convention (45–75 characters, ~66 ideal), leading and break rules. The 45–75 formulation also surfaced verbatim in typographic references found in this session's search. [canonical]
- Emil Ruder, *Typographie* (1967) — the 50–60-character optimum and attention-decay-across-the-line observation, as cited by Baymard. [canonical]
- Baymard Institute, "Readability: The Optimal Line Length" — web guidance (50–75 optimal; ≤80 WCAG; ~70ch/34em implementation; fatigue at 100+), WCAG 1.4.8 spacing thresholds, Ruder citation. https://baymard.com/research-articles/line-length-readability [accessed 2026-11-23]
- MDN Web Docs, "text-wrap" — `balance` (purpose, heading recommendation, 6-line Chromium / 10-line Firefox caps, March 2024 baseline) and `pretty` (body-copy intent, orphan avoidance). https://developer.mozilla.org/en-US/docs/Web/CSS/text-wrap [accessed 2026-11-23]
- Matthew Butterick, *Typography for the web* (webtypography.net) — line-length and justification guidance for web practice, as cited by Baymard. [search-verified 2026-11-23]
- Ellen Lupton, *Thinking with Type* (Princeton Architectural Press, 2nd ed. 2010) — alignment, justification and paragraph-system teaching. [canonical]
- Section 4 (interaction model) is synthesis of the sources above and of professional practice.
