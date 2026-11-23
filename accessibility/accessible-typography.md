# Accessible Typography

## 1. What is it?

Accessible typography is the practice of setting type so that it can be read, re-read and re-formatted by people with low vision, reading disabilities such as dyslexia, cognitive and attention limitations, and situational impairments (small screens, bright sunlight, shaky transport). It covers minimum sizes, user resizing, spacing overrides, line length, alignment, case, and the visual shaping of text blocks. It is distinct from, and sits on top of, colour-contrast rules: a perfectly sized paragraph at 2.5:1 contrast is still unreadable. The contrast rules themselves live in [Accessible colour](accessible-colour.md) and the palette side in [Colour accessibility](../colour/colour-accessibility.md).

The organising idea is *resilience*: accessible typography is less about picking one magic font and more about a type system that degrades gracefully when the user changes size, spacing, zoom or display settings. WCAG operationalises this through criteria on resize, reflow and text-spacing overrides, which this file explains and tests.

## 2. Why does it matter?

Reading is the primary activity of most web content, and text is the most economically accessible medium — provided the type can adapt. Low vision affects a large and growing share of audiences (age-related decline is universal); dyslexia and related processing differences affect perhaps one in ten people to a meaningful degree; many more users read on small screens, in motion, or at unusual distances. Every one of those groups depends on the text *system* rather than the type *choice*.

There is also a legal and conformance dimension: WCAG 2.2 success criteria 1.4.4 Resize Text, 1.4.10 Reflow and 1.4.12 Text Spacing are Level AA, meaning they belong to the level named by most public-sector regulation. Unlike some criteria, they are easy to verify mechanically and easy to break accidentally — a component library that hard-codes pixel heights or clips overflow can fail all three without anyone noticing until a user overrides their styles.

Finally, accessible type decisions are good typographic decisions: comfortable line lengths, generous line height and clear hierarchy improve the reading experience for everyone, including fully sighted readers on good hardware.

## 3. Core principles

1. **Legibility first, style second.** Letterforms must be distinguishable: adequate x-height, open apertures, distinctive characters. Decorative and condensed faces are reserved for display sizes and never used for body text. (Established typographic convention.)
2. **Real text, resizable.** Text must exist as selectable, zoomable text — not images of text (WCAG 1.4.5, AA) and not locked-pixel components. The author sets defaults; the user controls the final size.
3. **Spacing is a user right, not a design signature.** WCAG 1.4.12 requires that users can impose minimum spacing values without losing content — the author's defaults can differ, but the layout must tolerate the overrides.
4. **Linear reading flow.** Text blocks must reflow to a narrow column (320 CSS px, WCAG 1.4.10) without two-dimensional scrolling, meaning measures, indentation and multi-column tricks must be flexible.
5. **Hierarchy from more than size.** Users who cannot perceive subtle size differences still need hierarchy: weight, spacing, position and headings carry structure redundantly (this supports WCAG 1.3.1 and 1.4.1).
6. **Avoid gratuitous shape distortion.** Justified text with large gaps, all-caps body copy and stretched letterforms destroy the word-shape cues that aid fluent reading.

Principles 1, 2 and 4 are strongly grounded in standards and research; 5 and 6 are professional conventions with wide practitioner agreement; dyslexia-specific prescriptions (see 6.3) rest on mixed evidence and must be presented as options, not laws.

## 4. How it works

### 4.1 Minimum sizes: requirement versus convention

No WCAG success criterion specifies a minimum font size — the standard's philosophy is that usability matters more than exact author settings, which is why it instead guarantees *user* resizing and reflow. What the standard does define is **large-scale text** for contrast purposes: at least 18 point (≈ 24 px) or at least 14 point bold (≈ 18.66 px), with 1 pt = 1.333 px [accessed, Understanding SC 1.4.3].

Common professional conventions (not requirements — verify per project):

- Body text on the web: a default of **16 px (1 rem)** or larger; 12 px and below is effectively unreadable for sustained reading by a general audience.
- Secondary/annotation text: never below 12–14 px, and used sparingly.
- Display text: sized by hierarchy need; contrast still applies (3:1 once it reaches the large-text threshold).

Set sizes in `rem` or `%`, not `px`, so that user browser preferences scale everything proportionally.

### 4.2 Resizing and reflow

Two Level AA criteria work together:

- **1.4.4 Resize Text**: text can be resized up to 200% without loss of content or functionality. In practice this means no `maximum-scale=1` viewport locking, no fixed-height containers clipping enlarged text, and no functionality that disappears when text grows.
- **1.4.10 Reflow**: at a viewport **320 CSS px** wide (equivalent to 1280 px at 400% zoom), content reflows to one dimension without horizontal page scrolling and without loss of information [accessed, Understanding SC 1.4.10]. Data tables, maps, video, games and other content that genuinely requires two dimensions for use or meaning are exempt, but everything around them (headings, controls, pagination) still must reflow; the accepted pattern for tables is a scroll container around the table only.

The design consequence: measure (line length), font sizes, grid columns and container heights must all be expressed in flexible units, and overflow behaviour must be `visible` or wrapping, never `hidden` on text-bearing elements.

Reading distance and environment complete the picture. Mobile reading happens at shorter distances with higher ambient glare, which is why effective sizes below 16 px feel smaller on phones than the same CSS value on a desktop monitor; presentation screens and kiosks invert the problem, multiplying required sizes by viewing distance (a rule of thumb for event signage is to size text so it is legible from the furthest expected viewing point — a display-context judgement, not a WCAG number). Zoom interaction also matters: browser zoom scales CSS pixels, so layouts tested only at 100% hide clipping that appears the moment a low-vision user zooms — hence the 200%/400% checks in [Accessibility testing](accessibility-testing.md).

### 4.3 Text-spacing overrides

WCAG 1.4.12 (AA) requires that users can set the following and lose nothing [accessed, Understanding SC 1.4.12]:

| Property | User-set minimum |
|---|---|
| Line height (line spacing) | ≥ 1.5 × font size |
| Spacing following paragraphs | ≥ 2 × font size |
| Letter spacing (tracking) | ≥ 0.12 × font size |
| Word spacing | ≥ 0.16 × font size |

The author's own spacing may be tighter; the requirement is that imposing these values causes no clipping, overlap or loss of functionality. Typical failures: buttons and cards with fixed pixel heights where enlarged line spacing pushes text out of view; `overflow: hidden` on headings; tooltips and icon labels clipped; absolutely positioned elements stacked on the text. Test with a spacing bookmarklet or style override (see [Accessibility testing](accessibility-testing.md)).

### 4.4 Line length (measure)

- Established convention: 45–75 characters per line for continuous reading, with 66 as a classic target [canonical, Robert Bringhurst, *The Elements of Typographic Style*; widely taught].
- WCAG 1.4.8 Visual Presentation (AAA) specifies a maximum of 80 characters per line, line height ≥ 1.5, paragraph spacing ≥ 1.5 line-spaces and black-on-white or white-on-black among its options [canonical — verify against the normative standard before making conformance claims].
- Implement with `max-width` in `ch` units (e.g. `max-width: 70ch`) so the measure adapts to the user's chosen font size — a direct accessibility win over fixed pixel widths.

### 4.5 Line height and paragraph spacing

Tight leading hurts readers with low vision and dyslexia first, but everyone suffers below roughly 1.4. Working conventions: body text line height 1.4–1.6; paragraphs and headings optically tighter (1.1–1.2 for display sizes is acceptable because of larger absolute whitespace); paragraph spacing at least 0.75–1 em. Because 1.4.12 requires tolerance of 1.5 line height and 2× paragraph spacing, never build components whose layout collapses at those values. One nuance worth knowing: generous leading interacts with measure — long lines with tight leading cause double-reading (the eye loses its place on the return sweep), so when a layout forces a longer measure than ideal, raise line height rather than keeping both tight.

### 4.6 Justification, case and style hazards

- **Justified text**: on the web, without hyphenation control, justification produces rivers and uneven word spacing that specifically impede dyslexic and low-vision readers. Recommendation: left-align (ragged right) for body text; justification only with real hyphenation and variable word spacing, and never in narrow columns. (Professional convention; strongly held.)
- **All-caps**: word shapes become uniform rectangles, slowing reading for many people; ensure body text is never set in caps. Keep caps for short labels. Two corrections to common myths: screen readers do not "shout" all-caps text (they read it normally, mostly), and automatic conversion tools make this an accessibility *convenience* issue more than a screen-reader issue. Long strings of capitals should also be avoided in `alt` text.
- **Italics and light weights**: italic body text and very light font weights reduce stroke distinctness; use them for short emphasis only, not long passages. Avoid `font-weight` below 400 for body copy.
- **Underlines and links**: links should be distinguishable without colour (WCAG 1.4.1) — the convention is to underline in body text; in navigation where links are visually obvious, alternative affordances may pass, but verify.
- **Text on complex backgrounds**: images or gradients behind text must still meet contrast requirements measured against the actual overlapped colours.

### 4.7 Fonts and dyslexia-friendly considerations

Present this honestly: the evidence is mixed. Claims that specific typefaces (or widely marketed "dyslexia fonts") improve reading for dyslexic readers have limited and inconsistent research support; what is better supported is that *individual preferences vary* and that text *customisability* — letting users change size, spacing, colour and font — is what reliably helps. Therefore:

- Do not claim a specific font is "dyslexia-friendly" as fact; offer user controls instead.
- Apply the robustly supported basics first: ragged-right alignment, adequate spacing (1.4.12 values are a good floor), clear hierarchy, no all-caps body text, high contrast.
- Some organisations publish dyslexia style guidance (e.g. short lines, sans-serif preference, avoiding italics); treat these as reasonable defaults for certain audiences, not as validated universal requirements. (Context-dependent recommendation.)

### 4.8 Cognitive load

Typography also serves readers with cognitive and attention limitations: consistent, descriptive headings (WCAG 2.4.6) make scanning possible; a predictable visual hierarchy reduces working-memory demand; short paragraphs (3–5 sentences), informative link text (2.4.4) and clear labels (3.3.2) lower the cost of comprehension. These are Level A/AA criteria, not enhancements.

### 4.9 Language, scripts and international text

Spacing and readability rules are script-sensitive. The 1.4.12 exception acknowledges this: "Human languages and scripts that do not make use of one or more of these text style properties … can conform using only the properties that exist for that combination of language and script" [accessed]. Practical consequences for multilingual event or brand work:

- Set `lang` (and switch it inline for foreign-language passages, 3.1.1/3.1.2) — screen-reader pronunciation depends entirely on it.
- CJK text tolerates and often prefers tighter line height than Latin; 1.5 still works but inter-character density differs, and letter-spacing overrides behave differently. Verify spacing overrides with the actual languages of the audience.
- Long unbroken words (compound German, URLs) break narrow columns unless `overflow-wrap`/`hyphens` are handled — a reflow (1.4.10) failure waiting to happen.
- Fonts must cover the scripts of every audience locale; fallback stacks that silently substitute system fonts change metrics and can break contrast-tested pairings at display sizes.

## 5. Practical application

### 5.1 A resilient base type stylesheet

```css
:root {
  /* sizes in rem so user preferences scale everything */
  --fs-body: 1rem;        /* 16px default, respects browser setting */
  --fs-large: 1.125rem;
  --lh-body: 1.5;         /* passes 1.4.12 floor by default */
  --measure: 70ch;        /* line length adapts to user font size */
}

body {
  font: 400 var(--fs-body)/var(--lh-body) system-ui, sans-serif;
  text-align: left;        /* ragged right */
  overflow-wrap: break-word;
}

.prose {
  max-width: var(--measure);
}

/* modern niceties, progressive enhancement only */
h1, h2 { text-wrap: balance; }   /* avoids orphaned last words; ignored by older browsers */
.prose { text-wrap: pretty; }    /* similar for paragraphs where supported */

/* never lock user scaling */
/* <meta name="viewport" content="width=device-width, initial-scale=1"> */
```

Key rules encoded here: `rem` sizing (1.4.4), 1.5 line height (1.4.12 floor), `ch`-based measure (1.4.10), left alignment (4.6 above), and no viewport scaling lock.

### 5.2 Designing for the overrides

Check every text-bearing component against the 1.4.12 override table before build: does a 1.5 line height push the button label out of a fixed 32 px-high button? Does 2× paragraph spacing reveal a clipped third paragraph in a collapsed card? Convert fixed heights to `min-height`, replace `overflow: hidden` with wrapping or disclosure patterns, and give tooltips enough box to grow. A useful design-file drill: duplicate the screen, apply the four override values to the type styles, and look for the first thing that breaks — that component is your next ticket, found for the cost of ten minutes.

### 5.3 Hierarchy that survives

When the brand type system is subtle — close sizes, similar weights — add redundancy: pair size changes with weight or spacing changes, give sections real headings, and label regions. This helps everyone and provides the programmatic structure required by 1.3.1 and 2.4.6.

### 5.4 A workable type scale

A scale keeps hierarchy legible without relying on hairline size differences. The values below are a conventional starting point (common in practice, not a standard — verify against audience and brand):

| Role | Size (rem) | Weight | Notes |
|---|---|---|---|
| Display / hero | 2.5–3.5 | 600–700 | Contrast 3:1 applies (≥ 24 px = large text) |
| H2 section | 1.5–1.75 | 600 | Real `h2` element, not a styled `div` |
| H3 subsection | 1.25–1.375 | 600 | Keep ≥ 25% larger than body, or add weight difference |
| Body | 1.0 | 400 | 1.5 line height, ≤ 75ch measure |
| Secondary/annotation | 0.875–0.9 | 400 | Sparingly; never below 0.75rem (12 px) |

Two rules keep a scale accessible as it grows: steps must be *perceivable* (a 1.05rem "heading" reads as body text and breaks scannability) and headings must be marked up as real headings regardless of their visual size, because screen-reader navigation depends on the markup, not the font size. Fluid sizing with `clamp()` (e.g. `font-size: clamp(1.75rem, 4vw, 3rem)`) is a safe display-type technique — the floor still respects `rem`, so user font preferences keep working.

## 6. Decision framework

### 6.1 Choosing defaults

| Decision | Rule of thumb | Basis |
|---|---|---|
| Base size | 16 px / 1 rem, larger for older audiences | Convention |
| Measure | 45–75 ch (target ~66) | Canonical convention |
| Body line height | 1.4–1.6; 1.5 default | Convention + 1.4.12 floor |
| Alignment | Left for body; justify only with hyphenation | Convention (strong) |
| Case | Sentence case; caps only for short labels | Convention |
| Justify contrast needs | ≥ 24 px or bold ≥ 18.66 px counts as "large" (3:1) | WCAG 1.4.3 [accessed] |
| Font choice | High x-height, open apertures for body | Convention |
| Dyslexia options | Offer controls; don't claim magic fonts | Evidence mixed |
| Annotation floor | ≥ 12 px, used sparingly | Convention |
| Scale steps | Perceivable jumps (≥ ~25% between roles, or add weight) | Convention |

### 6.2 When conventions may bend

Marketing display type can violate measure and case rules because it is not continuous reading text — but it still must meet contrast (logotype exemption applies only to actual logos, per 1.4.3 [accessed]) and still must not become an image of text (1.4.5) unless it is a logo. Long-form content (articles, reports, policies) gets the strictest settings: full measure control, generous leading, no justification games.

## 7. Examples

**Event schedule page.** Session titles 1.25 rem semibold, descriptions 1 rem regular at 1.5 line height in a 66ch column; both reflow at 320 px; the "Add to calendar" button is 44 px tall with `min-height` so 1.5 line-height overrides stay inside it.

**Brand kit typography.** The client's display face is condensed and tight-tracked — acceptable for the logo and hero (display use), but the body system pairs it with a high-x-height sans at 1.5 leading, ragged right. The logo text is exempt from contrast (1.4.3 logotype exception [accessed]); hero text is not.

**Legal-notice modal.** Dense 13 px text in a fixed-height scroll box fails three ways at once: below comfortable conventions, clipped when spacing is overridden (1.4.12), and horizontally scrolling when zoomed (1.4.10). The fix: 1 rem body, min-height container, wrapping text, single-dimension scroll.

**Multi-column programme.** A printed-style three-column CSS `columns` layout for the conference programme reads column-by-column in the visual layout, but reading order for screen readers follows the DOM — with unbalanced column fill the announced order interleaves sessions (1.3.2 Sequence). The accessible pattern: a linear HTML order that also works visually (stacked sections or a real table), reserving columns for genuinely linear content.

**Large-print variant.** An event offers an accessibility page as a "large print" version. Done by baking 24 px fixed sizes into a separate template, it drifts out of sync and still blocks user scaling; done properly, it is the same page — the standard template already respects 200% resize and reflow, and a print stylesheet serves the printed handout. This is the general lesson: separate accessible variants are a last resort; resilient defaults usually make them unnecessary.

## 8. Common mistakes

- **Locking zoom** with `maximum-scale=1` or a fixed-width layout — directly violates 1.4.4 and breaks every low-vision user's browser setup.
- **Hiding text with zero-size fonts** (font-size: 0, clip hacks) for "screen-reader-only" content without also providing visible equivalents — hidden text is a supplement, never a substitute for visible labels.
- **Fixed pixel heights on text containers** — the single most common 1.4.12 failure; text disappears under `overflow: hidden` when spacing is overridden.
- **`ch` measure ignored**: a fixed `max-width: 600px` becomes 100+ characters long when the user doubles font size; `ch` units keep the measure honest.
- **Justified text without hyphenation** in narrow columns, producing rivers and uneven spacing.
- **Placeholder text as the only field label** — invisible after typing, often below contrast threshold.
- **Treating a dyslexia font purchase as accessibility work** while alignment, spacing and contrast remain broken.
- **All-caps body copy and letter-spacing squeezed below 0** — both distort word shapes for no benefit.
- **Images of text for stylistic reasons** (baked-in headlines) — violates 1.4.5, resizes badly, and is invisible to screen readers without `alt`.
- **Design-file-only testing**: typography verified at the default 100% zoom on a laptop display hides the failures that appear with browser zoom, OS text scaling and mobile font-size overrides.

## 9. Evaluation checklist

- [ ] Base body size ≥ 16 px equivalent, set in `rem`/`em`/`%` (convention) and never locked against scaling (1.4.4 requirement).
- [ ] At 320 CSS px viewport width there is no page-level horizontal scrolling (1.4.10); tables scroll in their own container only.
- [ ] Applying line height 1.5×, paragraph spacing 2×, letter spacing 0.12×, word spacing 0.16× causes no clipping, overlap or lost controls (1.4.12).
- [ ] Measure is 45–75 characters (convention) and expressed in `ch` or flexible units.
- [ ] Body text is left-aligned; justified text (if any) has hyphenation and is not in narrow columns.
- [ ] No all-caps body text; caps limited to short labels; no light body weights; italics not used for long passages.
- [ ] Headings are real `h1`–`h6` in order and describe their content (2.4.6); hierarchy is not size-only.
- [ ] Every form field has a visible persistent label; placeholder is supplementary only.
- [ ] Text contrast verified against actual backgrounds per [Accessible colour](accessible-colour.md) (large text = ≥ 24 px or ≥ 18.66 px bold).
- [ ] No text baked into images except logotypes; decorative images use empty `alt`.
- [ ] Typography choices for neurodivergent audiences are presented as options (user controls), not asserted as universal fixes.
- [ ] Line-height and measure work together: no measure/leading combination that causes double-reading at typical content widths.
- [ ] `lang` is set on the page and switched for foreign-language passages; fonts cover every locale the audience uses.
- [ ] Display-size text still meets contrast at its actual size (large-text thresholds verified in [Accessible colour](accessible-colour.md)).

## 10. Related topics

- [WCAG fundamentals](wcag-fundamentals.md) — the criteria framework behind 1.4.4, 1.4.10 and 1.4.12.
- [Accessible colour](accessible-colour.md) — contrast rules and testing that complement type decisions.
- [Accessibility testing](accessibility-testing.md) — how to run the spacing, zoom and reflow tests.
- [Colour accessibility](../colour/colour-accessibility.md) — building palettes that pass text contrast.
- [Typesetting](../typography/typesetting.md) — the craft foundations (measure, leading, grid) these constraints refine.
- [Web typography](../typography/web-typography.md) — implementation-side type systems, variables and fluid scales.
- [Website visual QA](../evaluation/website-visual-qa.md) — where the typography checks sit in review.
- [Data visualisation](../information-design/data-visualisation.md) — labelling and in-chart text legibility.

## 11. References

- W3C, *Understanding SC 1.4.12 Text Spacing* (WCAG 2.2) — <https://www.w3.org/WAI/WCAG22/Understanding/text-spacing.html> [accessed 2026-11-23]
- W3C, *Understanding SC 1.4.10 Reflow* (WCAG 2.2) — <https://www.w3.org/WAI/WCAG22/Understanding/reflow.html> [accessed 2026-11-23]
- W3C, *Understanding SC 1.4.3 Contrast (Minimum)* (WCAG 2.2) — large-text definition and pt/px conversion [accessed 2026-11-23]
- W3C, *Web Content Accessibility Guidelines (WCAG) 2.2* (normative spec, incl. 1.4.4, 1.4.5, 1.4.8) — <https://www.w3.org/TR/WCAG22> [canonical; verify 1.4.8 details against the normative text before conformance claims]
- Robert Bringhurst, *The Elements of Typographic Style* — measure conventions (45–75 characters) [canonical]
- Evidence on dyslexia-specific typefaces: mixed; synthesised from general professional knowledge — do not cite specific studies without verification [synthesis]
