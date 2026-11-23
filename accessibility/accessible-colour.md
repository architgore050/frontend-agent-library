# Accessible Colour

## 1. What is it?

Accessible colour is the discipline of ensuring colour never becomes a barrier: text must have enough luminance contrast to be readable, interface components and meaningful graphics must be distinguishable, and colour alone must never be the only way information is conveyed. This file is the **rules-and-testing side** of that discipline — the exact WCAG thresholds, how to measure them, and how to interpret results — including dark-mode specifics. Building a palette that passes these rules from the start is the subject of [Colour accessibility](../colour/colour-accessibility.md); the underlying colour theory is in [Colour theory](../colour/colour-theory.md).

The key conceptual shift for newcomers: WCAG colour rules are about *luminance contrast*, not hue. Vibrant, colourful palettes are perfectly compatible with accessibility as long as light/dark relationships between text and background, and between component and adjacent colour, are strong enough.

## 2. Why does it matter?

Roughly speaking, colour vision affects how information is perceived by a very large audience: colour-blindness (about 8% of men and 0.5% of women with congenital red-green deficiencies [canonical, widely reported figure]), plus low vision, age-related contrast sensitivity loss, screen glare, and one-eyed or situational conditions. When a red asterisk is the only "required" marker or green is the only "success" signal, part of the audience literally cannot perform the task.

Contrast failures are also the most common automated-test finding in practice — they are cheap to make (every new pairing is a chance to fail) and cheap to fix if checked at design time. That cost profile makes contrast discipline the highest-leverage accessibility habit in this knowledge base: one palette decision prevents hundreds of downstream violations across a whole brand kit.

Finally, colour rules are overwhelmingly Level AA — the level named by public-sector regulation and most procurement standards — so they are not optional polish. Contrast-related criteria also have an unusual property that makes them attractive targets for early work: they are fully computable, so they can be verified in the design file before any code exists, and they can be encoded into tokens and linting so they stay verified. No other WCAG family offers that design-to-production chain of custody, which is why this file insists on recorded, re-checkable pairs rather than one-off approvals.

Finally, colour rules are overwhelmingly Level AA — the level named by public-sector regulation and most procurement standards — so they are not optional polish.

## 3. Core principles

1. **Text contrast** (WCAG 1.4.3, AA): text and images of text must reach **4.5:1**; large text (≥ 18 pt / 24 px, or ≥ 14 pt bold / ≈ 18.66 px) needs **3:1** [accessed, Understanding SC 1.4.3]. Enhanced Level AAA (1.4.6) requires 7:1 and 4.5:1 for large text respectively [canonical].
2. **Non-text contrast** (WCAG 1.4.11, AA): visual information required to identify user interface components and states, and parts of graphics required to understand content, must reach **3:1 against adjacent colours** [accessed, Understanding SC 1.4.11].
3. **Colour independence** (WCAG 1.4.1, A): colour must never be the *only* visual means of conveying information, indicating an action, prompting a response, or distinguishing an element — add icons, labels, patterns, underlines or text [canonical].
4. **Focus indicator contrast** (via 1.4.11 + 2.4.7): author-supplied focus indicators are non-text content and must meet 3:1; removing focus visibility entirely is a failure (F78) [accessed].
5. **Hard thresholds, no rounding**: "4.499:1 would not meet the 4.5:1 threshold" — ratios are exact, so always verify numerically, never by eye [accessed].
6. **Exceptions exist and matter**: inactive/disabled controls, pure decoration, logotypes (where brand-mandated), and presentation essential to the information are exempt — but exemptions are narrow and author-chosen low contrast is never exempt [accessed].
7. **Consistency of meaning** (WCAG 3.2.4): the same colour should keep the same meaning across the product — a hue that means "error" in one flow must not mean "live" in another, or greyscale-robust labels alone will not save predictability [canonical].

## 4. How it works

### 4.1 How contrast is computed

Contrast is computed from **relative luminance** of the two colours — a weighted sum of the sRGB channels: `L = 0.2126·R + 0.7152·G + 0.0722·B`, with each channel gamma-corrected (values ≤ 0.04045 divided by 12.92; otherwise `((c+0.055)/1.055)^2.4`) [accessed, Understanding SC 1.4.3]. The ratio is `(L1 + 0.05) / (L2 + 0.05)` with L1 the lighter colour, ranging from 1:1 (identical) to 21:1 (black on white). Two important measurement rules from the Understanding page: if only one of text/background colour is specified, white is assumed (so half-specified styles fail automatically), and evaluation uses the declared CSS values, not anti-aliased pixels.

Hue contributes only through these luminance weights: pure blue (#0000FF) on black is effectively invisible (contrast ≈ 2.4:1) despite being a vivid colour, because blue carries little luminance. This is why "colourful but accessible" is about pairing hues by lightness, not avoiding colour.

A worked example makes the mechanism concrete. Take #767676 on #FFFFFF: each channel is 118/255 ≈ 0.4627, which is above the 0.04045 cutoff, so the linearised value is ((0.4627+0.055)/1.055)^2.4 ≈ 0.1812; because all three channels are equal, the luminance is also ≈ 0.1812. White's luminance is 1.0, so the ratio is (1.0+0.05)/(0.1812+0.05) ≈ 4.54 — just above the AA threshold, which is why #767676 is the classic "darkest grey that passes" on white. One shade lighter (#7A7A7A) drops below it. Doing this arithmetic by hand is unnecessary in practice — tools and the script pattern in [Colour in code](../colour/colour-in-code.md) do it — but understanding *why* the boundary sits where it does prevents the common intuition errors (see 5.4).

One forward-looking note: the WCAG 2.x formula has known weaknesses at very light and very dark extremes, and the W3C community is developing successor approaches (notably APCA, the Advanced Perceptual Contrast Algorithm, designed around perceptual research on dark-mode and thin-type reading) [canonical — treat as emerging, not a replacement; WCAG 2.x conformance always uses the formula above]. The practical stance: use the WCAG 2.x numbers for conformance, and treat perceptual methods as supplementary judgement tools where their verdicts and the 2.x numbers disagree badly.

### 4.2 What the 4.5:1 and 3:1 numbers apply to

- **4.5:1 (text, AA)**: all body-size text, including placeholder text, hover and focus-visible text states, and text inside buttons or banners [accessed].
- **3:1 (large text, AA)**: only text at ≥ 24 px, or ≥ 18.66 px bold [accessed]. "Large" is a technical definition, not a design judgement.
- **3:1 (non-text, AA, 1.4.11)**: component boundaries (input borders, checkbox borders), state indicators (focus outline, selected/checked tick, slider thumb), and meaningful graphic parts (chart lines, pie slices, icon strokes). Measured against *adjacent* colours — e.g. an input's border is judged against the page background outside it [accessed].
- **7:1 (text, AAA, 1.4.6)** and **4.5:1 (large text, AAA)** [canonical].

Adjacent-colour judgement has practical consequences: a light-grey drop shadow is ignored; a border may be "subsumed" into whichever neighbouring colour has closer luminance; a control whose identity is conveyed by its text or a contrasting icon needs no additional boundary [accessed]. When measuring, the questions to ask per component are: what colour(s) sit immediately inside and outside the identifying stroke or fill; is any neighbouring layer semi-transparent (flatten first); did the author leave one of the two colours unspecified (white is then assumed and the pair must still be checked); and are very thin strokes rendering fainter than their declared colour — 1 px hairlines often fail in practice even when the token pair passes, which is a layout fix (thicker stroke), not a colour fix [accessed].

### 4.3 Exceptions in practice

The exception lists are short and narrow [accessed]:

- **Inactive components**: a disabled button has no contrast requirement (though users benefit from a clear disabled affordance).
- **Logotypes**: text that is part of a logo or brand name has no contrast requirement *under 1.4.3* — but only where the presentation is brand-mandated; an author choosing low-contrast presentation is not exempt, and a low-contrast logo used as a link needs an equivalent alternative.
- **Incidental/decorative**: invisible, decorative or inactive text has no requirement.
- **Essential graphics**: photos, flags, sensory artwork, screenshots, medically accurate diagrams, heatmaps — where the colours are the information.
- **User-agent defaults**: default browser focus rings or scrollbars you did not modify are exempt.

### 4.4 Colour independence (1.4.1)

Beyond ratios, information must survive greyscale. Standard safe patterns: pair status colour with an icon or label (error = red *and* "Error" text with an icon), mark required fields with text or an asterisk plus explanation, distinguish links with underlines (in body text) or clear affordances, differentiate chart series with both colour *and* pattern/marker/shape, and let focus indicators differ in shape or thickness as well as colour. Note that 1.4.1 has no contrast-ratio component — a red and a green of identical lightness can both pass 3:1 against the background and still fail 1.4.1 if colour is the only differentiator [canonical].

The cues you can stack on top of colour are worth listing explicitly, because design review needs an inventory to choose from: a visible text label; an icon with a distinct shape; position and grouping (error messages placed at the field); a border or background change with sufficient thickness; a weight or style change; a pattern or texture (for charts and maps); and motion (used sparingly, never as the only cue, and disabled under reduced-motion preferences). Two or three redundant cues cover nearly every real situation; the failure pattern is always the same — one cue, and that cue is hue.

## 5. Practical application

### 5.1 Testing workflow

1. **List the pairs** you must verify: body text, secondary text, large text, text on brand-coloured banners, placeholder text, button label vs button fill, button fill vs page background (component boundary), input border vs background, focus indicator vs both sides, icon stroke vs background, chart series vs background and each other, link text vs background.
2. **Check with a tool**, not your eye. Use a contrast checker that takes hex pairs and reports the ratio plus AA/AAA pass/fail for normal and large text; browser DevTools (Chrome, Firefox, Edge) include a colour picker that reports contrast against the page background, and WAVE flags contrast errors in place (see [Accessibility testing](accessibility-testing.md)).
3. **Interpret correctly**: the reported ratio is compared to the threshold exactly (4.49:1 fails); large-text exemption applies only at the technical sizes above; ratios against gradients and images must be checked at the *worst* point, not the average; overlapping semi-transparent layers (toasts over images) need the composited result, not the design-layer value.
4. **Record the pass list** in the design system: tokens that are pre-verified in allowed pairs remove this whole class of review work (see [Colour in code](../colour/colour-in-code.md)).
5. **Re-test on every trigger**: any new pairing, theme change, token rename, overlay introduction or background-image usage re-opens the pair list. Contrast verdicts attach to pairs, not to colours — a token can be "verified" only in specific combinations.

### 5.2 Dark-mode accessibility notes

Dark themes have their own failure patterns, all testable with the same rules:

- **Halation**: pure white (#FFFFFF) text on pure black (#000000) can bloom for readers with astigmatism and low vision; a common conventional starting point is an off-white (around #E0–#F2 range) on a near-black (around #0D–#1A range) — verify the resulting pair still passes 4.5:1 numerically [conventional starting point, not a standard].
- **Do not simply invert the brand palette**: a brand dark-on-light pair inverted becomes light-on-dark, but *contrast ratios are symmetric* — the same ratio passes; what breaks is hue-based thinking (dark blues and purples collapse on dark backgrounds because their luminance is already low).
- **Re-verify non-text contrast**: component borders and focus rings chosen for light mode often sit near 2:1 against dark surfaces; states (hover, selected) need re-checking against their new adjacent colours.
- **Elevation and overlays**: layered dark surfaces (cards on backgrounds, modal scrim over content) change the adjacent colour of everything behind them; re-check text sitting on overlays.
- **Respect user preference**: honour `prefers-color-scheme`, and make theme switching explicit and persistent; sudden forced themes are a predictability problem (WCAG 3.2 territory) as well as a preference one [synthesis of the sources below].
- **Focus rings in dark mode** are the most common re-verification miss: a ring chosen at 3:1 against a light background frequently drops below threshold against dark surfaces. Design a *separate* dark-mode focus token (e.g. a lighter outline or a two-colour indicator — an outer ring that contrasts with the page plus an inner gap that contrasts with the component, the pattern W3C technique C40 describes [canonical]), and include it in the dark-mode pair list during testing.

### 5.3 Overlays, scrims and gradients

Composite colours defeat naive checking, so treat anything translucent as a special case. A white toast over a photo does not inherit the photo's average colour — the composited result under the *text* is what must reach 4.5:1, and for a moving background that is a range, not a value. Working method: flatten the overlap at its worst point (highest-luminance background region under light text, darkest under dark text), sample the flattened colour, and check that. Gradients behind text or on button fills are checked at both ends and near edge text; a gradient that passes at the centre and fails at the edges fails. Semi-transparent scrims over content have a second job — separating overlay content from the page behind it — and the same worst-point rule applies to their boundaries. When the worst case cannot pass, the design fix is a solid backing panel or a stronger scrim, not an exception claim [synthesis of the sources below].

### 5.4 Worked ratios (computed, not estimated)

The ratios below were computed from the published formula (Section 4.1) as reference points for calibrating intuition. They describe these specific pairs only — recompute for any real pair.

| Foreground | Background | Ratio | Verdict |
|---|---|---|---|
| #000000 (black) | #FFFFFF (white) | 21.00:1 | AA and AAA text |
| #111111 (near-black) | #FFFFFF | 18.88:1 | AA and AAA text |
| #767676 (grey) | #FFFFFF | 4.54:1 | AA text (the classic minimal grey that passes) |
| #7A7A7A | #FFFFFF | 4.29:1 | fails 4.5:1; passes 3:1 large text only |
| #959595 | #FFFFFF | 3.00:1 | fails AA text; exactly the non-text boundary value |
| #64748B (slate-500) | #FFFFFF | 4.76:1 | AA text |
| #0000FF (pure blue) | #000000 (black) | 2.44:1 | fails everything — vivid hue, near-zero usable contrast |
| #FFFFFF | #3B82F6 (bright blue) | 3.68:1 | large-text AA only; body text on this fill fails |
| #005A9C (deep blue) | #FFFFFF | 7.14:1 | AA text and AAA |
| #B30000 (deep red) on white / white on it | | 7.20:1 | AA and AAA — same either way, ratios are symmetric |
| #EDEDED (off-white) | #121212 (near-black) | 16.00:1 | AA and AAA — comfortable dark-mode-style body pair |
| #94A3B8 (muted grey-blue) | #0F172A (dark navy) | 6.96:1 | passes AA, fails AAA by 0.04 — verify, never eyeball |

Three calibration lessons fall out of the table. First, greys are treacherous: #7A7A7A on white *looks* fine and fails. Second, luminance dominates hue: pure blue on black at 2.44:1 is a vivid colour with no readable contrast, while a dull deep red on white reaches AAA. Third, thresholds bite: 6.96:1 versus 7.14:1 is a visual difference nobody can see and the exact difference between AAA pass and fail.

The W3C Understanding pages confirm the same pattern with their own examples: a #767676 input border on white passes; a grey checkbox border at 2.7:1 and a grey focus outline at 2.3:1 fail; a dropdown arrow at 4.7:1 passes; a red underline as the sole link indicator fails 1.4.1 regardless of its ratio [accessed].

### 5.5 Component-state matrix (1.4.11)

For every interactive component, list its states and what must hold in each [accessed, Understanding SC 1.4.11]:

| State | What needs 3:1 | Against what |
|---|---|---|
| Default | The visual information identifying the component (border, fill difference, icon stroke) | Adjacent colour(s) — usually the page background |
| Hover | The component's own identifying information must not drop below 3:1; the hover change itself is not measured (pointer position already signals it) | Adjacent colour(s) |
| Focus | The author-supplied focus indicator | Outside indicator → page background; inside → component interior; on the border → both sides |
| Selected/checked | The tick, dot or thumb (or the flat fill change) | Adjacent colours |
| Disabled | No requirement (exception) | — |

Building this matrix during design review is the single most effective defence against the most-missed failure class, because states are designed once and shipped everywhere.

### 5.6 Greyscale and colour-independence testing

Cheap and highly revealing: render the design or page in greyscale (design tools have a desaturate view; a quick CSS `filter: grayscale(100%)` works for pages) and walk the key flows. Anything that becomes ambiguous — success vs error states, selected vs unselected tabs, chart series, required vs optional markers — fails 1.4.1 in spirit and usually in letter. This test also previews how the interface reads to users with colour-vision deficiencies, though greyscale is a stronger condition than most deficiencies, which retain some hue perception [synthesis of the sources below].

### 5.7 Preventing regressions with verified tokens

Testing finds contrast errors once; tokens prevent them forever. The pattern: define each colour as a design token, verify the *allowed pairs* (not just the colours), and name the verification level in the token documentation — for example `text-primary on surface-default: 12.02:1 (AA, AAA)` from the table in 5.4. Components then compose only pre-approved pairs; a linter or style-dictionary rule can reject any new combination that has no recorded verdict. This converts contrast from a per-release QA task into a property of the design system, and it is the mechanism behind the brand-kit annex in 6.4. The token file formats and naming live in [Colour in code](../colour/colour-in-code.md).

## 6. Decision framework

### 6.1 Deciding whether a pair passes

| Pair type | Rule | Threshold |
|---|---|---|
| Body text / any background | 1.4.3 AA | ≥ 4.5:1 |
| Text ≥ 24 px or ≥ 18.66 px bold | 1.4.3 AA | ≥ 3:1 |
| AAA text target | 1.4.6 AAA | ≥ 7:1 (4.5:1 large) |
| Input/checkbox border, icon stroke | 1.4.11 AA | ≥ 3:1 vs adjacent |
| Focus indicator | 1.4.11 + 2.4.7 | ≥ 3:1 vs adjacent + visible |
| Chart/graphic parts needed for meaning | 1.4.11 AA | ≥ 3:1 vs adjacent |
| Disabled control, logo, decoration | exceptions | no requirement |
| Colour-only distinction of any kind | 1.4.1 A | fails — add a second cue |
| Text over an image or gradient | 1.4.3 AA at the worst point | ≥ 4.5:1 composited |
| Chart/graphic series distinguished by hue alone | 1.4.1 + 1.4.11 | fails — add pattern/label/marker |
| Colour-only distinction of any kind | 1.4.1 A | fails — add a second cue |

### 6.2 When ratios do not settle it

Three judgement calls exceed the maths: (1) contrast is necessary but not sufficient — 4.6:1 text in an illegibly small size is still unreadable (see [Accessible typography](accessible-typography.md)); (2) maximum contrast is not optimal — eye-strain and halation make extreme pairs a poor default for long reading; (3) cognitive load — colour use must also stay *consistent* (3.2.4 predictability), so the same hue should keep the same meaning throughout the product. A fourth call is contextual: dense data displays (maps, heatmaps) may legitimately concentrate low-contrast detail that the "essential presentation" exception covers, provided the information also exists in an accessible form (labels, table, description) — the exception protects the visualisation, not the dataset's only copy [synthesis of the sources below].

### 6.3 Escalation when a brand colour fails

If the brand primary fails against white: use it as a background with white text at ≥ 4.5:1 if the fill passes 3:1 as a component against its surroundings; otherwise keep the brand colour for decorative uses and reserve an accessible darker/lighter variant for text-bearing components. Document both variants as separate tokens so future teams do not "fix" them. Full method: [Colour accessibility](../colour/colour-accessibility.md).

### 6.4 Recording the decisions in a brand kit

A brand kit that will be extended into pages (event sites, generated one-pagers, templates) should carry an accessibility annex: the verified pair list (which foreground/background token combinations pass AA text, large text and non-text), the component-state matrix from 5.5, the dark-mode token set, and the known exceptions (logo, decorative uses). Recording this once converts every downstream template from "hope it passes" into "assembled from pre-verified pairs", and it gives reviewers a contract to check against instead of re-deriving ratios from scratch. The token mechanics live in [Colour in code](../colour/colour-in-code.md); the palette-building method in [Colour accessibility](../colour/colour-accessibility.md).

## 7. Examples

**Event logo extension.** The event logo's low-contrast lettering is exempt (1.4.3 logotype, brand-mandated), but the nav built with it is not: nav links need 4.5:1, the nav background needs a 3:1 boundary or a text-level affordance, and the focus ring needs 3:1 against both header and page.

**Status badges.** "Sold out" in pale grey-pink on white at 3.2:1 fails as text (needs 4.5:1 unless ≥ 24 px). The same hue at a darker lightness passes and keeps the brand feel; adding a ticket icon preserves meaning in greyscale (1.4.1).

**Chart.** Four series in four hues of identical lightness: text labels carry the data, so 1.4.11 does not demand 3:1 between slices *if* values are visible as text [accessed]; but series lines without labels need 3:1 against the plot area, and relying on hue alone fails 1.4.1 — add markers or patterns. See [Data visualisation](../information-design/data-visualisation.md).

**Dark mode.** Brand yellow on near-black passes easily (high luminance difference), brand deep blue does not: the blue's luminance is too close to the background. Swap to the tinted variant reserved in the palette, not the same hex.

**Two-state indicator that passes everything.** A "selected" ticket row: background shifts to the brand tint *and* a check icon appears *and* the row label turns bold. The tint shift alone would fail 1.4.1; the icon carries the meaning in greyscale; the icon stroke and the bold label both clear their thresholds. Every state change should be auditable this way — one meaning, at least two cues, all measured.

**The cascade of a single hue decision.** Marketing picks a mid-tone teal for the hero band. White body text on it measures 3.4:1 — fails for body, passes only if the text reaches 24 px. The kit therefore ships three artifacts instead of one hex: a darker `--teal-text-bg` variant for text-bearing fills, a rule that body copy on any teal fill uses the variant, and a recorded pair list. The initial "just a colour" decision becomes a four-line annex that keeps every future page conformant — this is the normal shape of colour accessibility work at brand level.

## 8. Common mistakes

- **Eyeballing contrast** — perception adapts; "it looks fine" over dark backgrounds or saturated hues is unreliable. Ratios are exact and unrounded [accessed].
- **Checking only text**: the most-missed failures are non-text — faint input borders (1.4.11), focus rings under 3:1, icons at 2:1.
- **Assuming large text starts at 20 px or 24 px bold**: the definition is ≥ 24 px regular or ≥ 18.66 px bold [accessed]; bold 18 px regular text is *not* large.
- **Half-specified styles**: setting only `color` (background defaults to white) or only `background-color` creates automatic failure when combined with a different background [accessed].
- **Colour-only state changes**: hover/selected indicated solely by hue shift fails 1.4.1; visited links by hue alone fail it too [canonical].
- **Disabled look by low contrast alone**: permitted by the exception, but a text label or visual affordance prevents user confusion — an accessibility *usability* issue even when technically conformant.
- **Inverting light-mode palettes for dark mode without re-verification**; dark blues/purples on dark surfaces are a classic silent failure.
- **Testing the average, not the worst case**: gradients, images under text, and scrim overlays must pass at their most contrast-hostile point.
- **Treating the component-state matrix as optional**: states are where non-text contrast dies — the hover fill that dims the border, the selected tint that hides the tick, the focus ring designed against the wrong adjacent colour. Fill the 5.5 matrix per component once; re-check only on redesign.
- **Using "it passed in another tool" as proof**: different tools sample different pixels (declared CSS values vs rendered composites). Understand what each measured before trusting the disagreement — and when in doubt, compute from declared values as 1.4.11 directs [accessed].

## 9. Evaluation checklist

- [ ] Every text/background pair verified numerically: ≥ 4.5:1, or ≥ 3:1 only where text is ≥ 24 px or ≥ 18.66 px bold (1.4.3).
- [ ] Placeholder, hover and focus text states included in the 4.5:1 check.
- [ ] Component boundaries, state indicators and meaningful icons verified ≥ 3:1 against adjacent colours (1.4.11).
- [ ] Focus indicators ≥ 3:1 and visible (2.4.7); sticky elements never obscure them (2.4.11).
- [ ] No information conveyed by colour alone — status, required fields, links, chart series all carry a second cue (1.4.1).
- [ ] AAA targets checked where promised (≥ 7:1 text) and recorded.
- [ ] Exceptions (disabled, logo, decorative) are genuine, not conveniences.
- [ ] Dark mode re-verified pair-by-pair; no pure-white-on-pure-black long reading text unless tested with users; overlays and scrimmed content re-checked.
- [ ] Verified pairs recorded as tokens in [Colour in code](../colour/colour-in-code.md); palette rationale documented in [Colour accessibility](../colour/colour-accessibility.md).
- [ ] The component-state matrix (5.5) exists for every interactive component and was re-checked after the last theme or token change.
- [ ] Chart and diagram colours were tested as graphical objects (3:1) and carry a non-colour differentiator (1.4.1) — see [Data visualisation](../information-design/data-visualisation.md).

## 10. Related topics

- [WCAG fundamentals](wcag-fundamentals.md) — the framework behind 1.4.1, 1.4.3, 1.4.11 and their levels.
- [Accessible typography](accessible-typography.md) — size definitions that decide whether 3:1 large-text applies.
- [Accessibility testing](accessibility-testing.md) — tool-by-tool procedures including WAVE and DevTools contrast checks.
- [Colour accessibility](../colour/colour-accessibility.md) — constructing palettes that pass these rules.
- [Colour theory](../colour/colour-theory.md) — hue, saturation and lightness foundations.
- [Colour in code](../colour/colour-in-code.md) — tokenising verified pairs.
- [UI fundamentals](../ui-ux/ui-fundamentals.md) — component states that 1.4.11 governs.
- [Data visualisation](../information-design/data-visualisation.md) — accessible charts beyond 3:1.
- [Website visual QA](../evaluation/website-visual-qa.md) — review pipeline placement of colour checks.

## 11. References

- W3C, *Understanding SC 1.4.3 Contrast (Minimum)* (WCAG 2.2) — thresholds, luminance formula, exceptions, large-text definition — <https://www.w3.org/WAI/WCAG22/Understanding/contrast-minimum.html> [accessed 2026-11-23]
- W3C, *Understanding SC 1.4.11 Non-text Contrast* (WCAG 2.2) — component/graphical-object rules, adjacent-colour measurement, focus-indicator guidance — <https://www.w3.org/WAI/WCAG22/Understanding/non-text-contrast.html> [accessed 2026-11-23]
- W3C, *Web Content Accessibility Guidelines (WCAG) 2.2* (normative spec, incl. 1.4.1, 1.4.6, 2.4.7, 2.4.11) — <https://www.w3.org/TR/WCAG22> [canonical; verify unfetched criteria before conformance claims]
- W3C WAI, *WCAG 2 Overview* — <https://www.w3.org/WAI/standards-guidelines/wcag/> [accessed 2026-11-23]
- Ratios in Section 5.3: computed by the author from the luminance formula cited above; not independently published values [synthesis]
- Dark-mode halation and off-white/near-black starting points: conventional practitioner guidance, not a standard — verify per project [conventional starting point]
- Congenital colour-vision deficiency prevalence (≈8% of men): widely reported canonical figure [canonical]
