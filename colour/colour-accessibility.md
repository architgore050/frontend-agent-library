# Colour accessibility

## 1. What is it?

Colour accessibility is the practice of building palettes that remain usable by people with colour-vision deficiencies (CVD), low vision, situational impairments, or any viewing condition that degrades colour perception. This file covers the **construction side**: which contrast values to design for, how to avoid encoding meaning in hue alone, and how to test combinations while the palette is being built — not after.

The split of responsibility in this knowledge base: the normative WCAG framework (success criteria, conformance levels, the POUR principles) lives in [WCAG fundamentals](../accessibility/wcag-fundamentals.md), and full tool-based testing procedures live in [Accessibility testing](../accessibility/accessibility-testing.md) and [Accessible colour](../accessibility/accessible-colour.md). Here we stay inside the palette workflow, using the threshold values those files explain in depth.

## 2. Why does it matter?

Colour access failures are the most common accessibility failures because they are invisible to the people who create them: a designer with normal trichromatic vision cannot see their own palette's failure modes. The affected population is large. Colour Blind Awareness estimates colour-vision deficiency affects approximately 1 in 12 men (8%) and 1 in 200 women — roughly 3 million people in the UK (about 4.5% of the population) and around 300 million worldwide [accessed]. Most CVD is inherited, red-green types being the most common; acquired forms arise from conditions such as diabetes and multiple sclerosis, from ageing, and from medication [accessed].

Beyond permanent CVD, every user is situationally impaired at times — sunlight on a phone screen, a dim projector, a glare-washed display — and long-sighted or low-vision users need luminance contrast regardless of hue. Designing the palette correctly is cheap; retrofitting it later means re-deriving ramps, re-testing every component and re-issuing brand guidelines.

There is also an institutional dimension: WCAG-derived contrast requirements are referenced by procurement standards, public-sector regulations and platform review guidelines in many jurisdictions — the details vary and live in [WCAG fundamentals](../accessibility/wcag-fundamentals.md), but the practical pattern is constant. Contrast failures surface late, in audits and procurement reviews, as expensive rework. Building the pair matrix during palette construction converts that late, external audit into an early, internal check.

## 3. Core principles

### 3.1 Design to the contrast thresholds

The WCAG 2.x contrast ratio compares relative luminance — `(L1 + 0.05) / (L2 + 0.05)`, where L1 is the lighter colour — producing values from 1:1 (identical) to 21:1 (black on white) [accessed]. Relative luminance for sRGB is `L = 0.2126·R + 0.7152·G + 0.0722·B` on linearised channel values [accessed]. The design targets:

| Content | AA minimum | AAA minimum |
|---|---|---|
| Body text (< 18pt / < 14pt bold) | 4.5:1 | 7:1 |
| Large text (≥ 18pt ≈ 24px, or ≥ 14pt bold ≈ 18.5px) | 3:1 | 4.5:1 |
| UI component boundaries & state indicators (borders, icons, focus, selected) | 3:1 | — |
| Graphical objects needed to understand content (chart marks, diagram strokes) | 3:1 | — |
| Logotypes / brand name text | no requirement | no requirement |

Source: W3C WAI Understanding pages for SC 1.4.3, 1.4.6 and 1.4.11 [accessed 2026-11-23]. Two details that routinely catch teams out:

- **The thresholds are hard, with no rounding.** The W3C guidance notes 4.499:1 does not pass 4.5:1, and 2.999:1 does not pass 3:1 [accessed]. Design with margin — aim for ≥ 4.6:1 when "AA" is the target.
- **Contrast is measured from the specified colours, not as rendered on screen** (anti-aliasing makes thin strokes fainter than their nominal colours) [accessed].

Because contrast depends on *luminance*, not hue, intuition about "contrasty" colours is unreliable. Measured examples (WCAG 2 formula, computed):

| Pair | Ratio | Verdict |
|---|---|---|
| Pure red `#FF0000` on white | 4.00:1 | fails AA body text |
| Pure red `#FF0000` on black | 5.25:1 | passes AA |
| Pure yellow `#FFFF00` on white | 1.07:1 | fails everything |
| Pure yellow on black | 19.56:1 | passes AAA |
| Pure blue `#0000FF` on white | 8.59:1 | passes AAA |
| Grey `#767676` on white | 4.54:1 | the classic "AA-edge" grey |
| Light blue `#5A9BD4` on white | 2.97:1 | fails even non-text 3:1 |

The lesson is structural: *hue swaps do not fix contrast, value changes do*. A "red error text" that fails AA is not repaired by choosing a different red hue at the same lightness — it is repaired by darkening it (e.g. `#B42318` on white measures 6.57:1).

**About APCA and the future of the metric.** The WCAG 2 ratio has known weaknesses: it treats all colour pairs symmetrically (though a dark line on white is not perceived like white text on dark), and it ignores text size and weight. The W3C's WCAG 3 work has explored **APCA** (the Advanced Perceptual Contrast Algorithm), a perceptually based model that weights lightness polarity, text size, weight and intended use [search-verified]. It is not the conformance standard today — WCAG 2 ratios are what contracts, audits and laws reference. The practical stance for palette construction: build to WCAG 2 values with margin, and keep the pair matrix data tidy (pairs recorded with their ratios) so a future re-scoring under APCA is a re-run, not a rebuild.

### 3.2 Never encode meaning by hue alone

This is the SC 1.4.1 principle applied to palette construction, and it is a hard rule, not a preference: **colour must never be the only visual means of conveying information**. The reason is mechanical, not aesthetic — red-green deficiencies (the most common CVD forms) affect distinguishing any colour containing red or green components, including oranges, browns, pinks and even greys; blue-vs-purple confusions are typical [accessed]. A palette can contain red and green; what it cannot do is make red-vs-green the *only* difference between two meanings.

Build the redundancy into the palette itself:

| Colour-only signal | Accessible replacement |
|---|---|
| Red / green status dots | Icon shape (✗/✓) + text label + colour |
| Red fill = required field error | Error message text + border weight + icon |
| Line chart distinguished by hue | Differing dash patterns, markers, or direct labels |
| Green "success" button vs grey "disabled" | Disabled state keeps 3:1 boundary or explicit "disabled" text |
| Coloured tags only | Tag shape, position, or label text |
| Highlighted table row (background tint only) | Bold row header, leading icon, or left rule + tint |
| Form required indicated by red asterisk | Word "required" + asterisk (asterisk alone fails screen readers too) |

Note the interaction with the semantic palette: semantic colours ([Palette development](palette-development.md)) carry conventional hues *and* mandatory non-colour cues — the hue is reinforcement, not the message.

For charts specifically, the redundancy toolkit has a reliable priority order: **direct labels** (best — the value is written at the data point), then **pattern/shape variation** (dashes, fills, markers), then **position/layout grouping**, with colour last as the enhancement. Pattern fills have their own limits (visual noise, moiré at small sizes), so the strongest data-viz practice is fewer series, labelled directly, in colours that also differ in luminance.

### 3.3 Contrast is a system property, not a colour property

No colour is "accessible" in isolation. Every colour's accessibility is defined by the set of pairs it appears in. During construction, therefore, work with pairs and matrices, not swatches:

- text pairs (body, muted, text-on-primary, text-on-accent, text-on-semantic),
- boundary pairs (component borders vs adjacent backgrounds),
- state pairs (focus ring vs background, selected vs unselected),
- chart pairs (each series colour vs the others' *luminance*, since CVD compresses hue differences).

A palette that "contains accessible colours" but ships an unusable pair is still inaccessible. Section 4 formalises this as a step in construction.

The system view also explains why accessibility work belongs at palette level rather than component level. A component developer who receives "make this text accessible" must reverse-engineer every surrounding colour; a developer who receives a token like `text-muted` with a recorded 7.56:1 ratio against its documented backgrounds inherits correctness for free. The palette is the only place where all the pairs are known at once.

### 3.4 Component states must keep their 3:1

SC 1.4.11 requires the *visual information needed to identify* a UI component and its states (selected, focused, checked) to hold 3:1 against adjacent colours [accessed]. Practical consequences for palettes:

- A ghost button whose only boundary is a 1px border needs that border colour to pass 3:1 against the background *in the hover state too*, if hover is how users identify it.
- Focus indicators cannot rely on colour change alone and must contrast with both the component and the surrounding background.
- Disabled controls are exempt from the requirement [accessed] — but if you rely on greying out alone to signal "disabled", screen-reader users and CVD users get no redundancy; pair it with reduced interactivity and (ideally) an explicit label.
- Toggle and checkbox states are the classic enforcement case: an unchecked box, a checked box and an indeterminate one need visually distinct identification that survives greyscale — fill change *plus* glyph (empty / tick / dash), not fill change alone.
- Sliders and progress bars need their track/thumb separation to hold 3:1 on every surface they appear on, including tinted and image backgrounds.

### 3.5 CVD-aware hue strategy

Hue choice still matters — not for luminance, but for *confusability*: how colours collapse into each other under CVD. Construction guidance (conventional, tool-verified in section 5):

- **Prefer luminance spread over hue spread.** Two chart series at 4:1 luminance separation remain distinguishable under every CVD type; two series differing only in hue can merge completely.
- **Red-green pairs need a partner cue** (lightness gap, dash pattern, icon) because they are the classic collapse.
- **Blue/yellow axes survive better** across CVD types — a conventional reason palettes for data-viz lean on blue plus warm accents.
- **Avoid relying on pure spectral hues** for meaning; slightly desaturated, value-differentiated versions read better and print better.
- **Simulate, do not guess.** Run the palette through deuteranopia/protanopia simulation; see section 5.3 and [Accessibility testing](../accessibility/accessibility-testing.md).

A closing caution on the simulations themselves: they are approximations (most model the dichromat case, while many affected people have anomalous trichromacy — a shifted, not absent, cone response), and they cannot represent the full range of low vision, glare or ageing. Treat simulation as a fast filter that catches gross failures, not as certification. The luminance-spread and redundancy rules above are what actually carry the design; the simulation is the check that they were applied.

### 3.6 Dark themes have their own contrast geometry

The light-theme habit of "dark text on light background" inverts, and naive inversion fails: pure white text on pure black produces perceptual glare and halation for many users (conventional practice; also unnecessary — plenty of luminance headroom exists). Derive dark themes by role: near-black surfaces (e.g. `#111418`), off-white text (e.g. `#E8EAED` — measured 13.74:1 against `#1A1F26`), brand hues shifted lighter as text and darker as fills, and re-run the whole pair matrix, because every ratio changes. See [Palette development](palette-development.md) section 3.5 and [Colour in code](colour-in-code.md) for the theming mechanics.

### 3.7 Links and focus indicators

Two palette decisions are delegated so often that they are worth pinning here:

- **Link colour** must (a) contrast 4.5:1 with its background as text, and (b) be distinguishable from surrounding body text by *more than hue alone* — underline or weight, per the colour-independence rule and long-standing convention. A light-theme link often fails (b) when it shares a hue with the brand but relies on colour alone.
- **Focus indicators** must hold 3:1 against both the component they outline and the background they cross. On multi-colour surfaces (image cards, tinted banners) a single focus colour rarely satisfies both; the robust construction is a two-layer indicator (light ring inside a dark ring, or vice versa) so one of the two always contrasts. Specify focus colours in the palette documentation like any other role — improvised focus styling is a top audit failure.

## 4. How it works — construction order

Build the palette so that accessibility is a property of construction, not a post-hoc audit:

1. **Fix the ground pair first.** Choose text-on-background (e.g. `#111418` on `#FAFAF8` = 18.07:1) and muted text (e.g. `#4B5563` = 7.56:1 on white) before any brand hue — these are the highest-frequency pairs in the product.
2. **Choose brand hues that can pass both directions.** The primary must pass AA as text on white *and* as a filled surface with white text (the example primary `#0F6BAE` measures 5.62:1 both ways). A hue that fails both directions cannot serve as primary without exceptions.
3. **Give every role its contrast-ready step.** Anchor each ramp step's job to the threshold it must meet — [Palette development](palette-development.md) section 3.3 shows a ramp with per-step contrast: step 600 = 5.00:1 (AA text), step 700 = 7.60:1 (AAA text), step 500 = 3.38:1 (large text / non-text only), steps ≤ 400 = decorative/tint only.
4. **Attach redundancy to every meaning-carrying colour** (section 3.2) as a documentation line, so implementers inherit the rule.
5. **Generate the pair matrix and mark it.** Every intentional pair, measured, labelled AA/AAA/fail-role.
6. **Simulate CVD on the real layouts**, adjust at ramp level, regenerate.

The construction order is the point: every step shortens the feedback loop for the next. Ground pairs first mean brand hues are chosen knowing the text environment; ramps with recorded contrast mean component decisions are lookups, not research; the pair matrix exists from the first week, so the final audit confirms rather than discovers.

## 5. Practical application

### 5.1 The combination matrix

Test combinations *during* construction — a minimal matrix for a light theme:

| Pair | Ratio | Target | Verdict |
|---|---|---|---|
| Body text `#111418` / background `#FAFAF8` | 18.07:1 | ≥ 4.5 | pass AAA |
| Muted text `#4B5563` / white | 7.56:1 | ≥ 4.5 | pass AAA |
| Grey `#6B7280` / white (tertiary) | 4.83:1 | ≥ 4.5 | pass AA |
| White / primary `#0F6BAE` (button) | 5.62:1 | ≥ 4.5 | pass AA |
| Near-black `#1A1A1A` / accent `#E8B33D` (badge) | 9.07:1 | ≥ 4.5 | pass AAA |
| Primary border / background | 5.62:1 | ≥ 3 | pass |
| Accent vs primary (adjacent fields) | 2.93:1 | ≥ 3 | **fail — needs border or spacing** |

The last row is the quiet killer: two brand colours that look "obviously different" sit below the 3:1 non-text threshold, so adjacent fields of them (chart segments, badge next to button) need a separating border, spacing, or a lightness adjustment. Compute every claimed number with the formula or a checker — no eyeballing.

The dark theme gets its own matrix, not a copy of the light one:

| Pair (dark theme) | Ratio | Target | Verdict |
|---|---|---|---|
| Body text `#E8EAED` / background `#111418` | 13.74:1 | ≥ 4.5 | pass AAA |
| Muted text `#9AA3AE` / `#111418` | 7.23:1 | ≥ 4.5 | pass AAA |
| Action text `#72BDF3` / `#111418` | 9.05:1 | ≥ 4.5 | pass AAA |
| On-action `#0B2239` / action fill `#72BDF3` | 7.90:1 | ≥ 4.5 | pass AAA |

Notice the same ramp serves both themes with *different steps in the same roles* — that is the role-level derivation of [Palette development](palette-development.md) paying off.

### 5.2 Semantic colours under CVD

The conventional success/warning/error hues (green/amber/red) partially collapse under red-green CVD. Construction remedies, applied in [Palette development](palette-development.md):

- Differentiate by *value* as well as hue (dark green text step vs amber vs red — keep the three text steps clearly unequal in lightness).
- Fix iconography in documentation (check, triangle, cross, info) so the cue ships with the colour.
- Prefer blue for informational semantics — it stays distinct under all common CVD types.

The verification loop is short and worth running whenever a semantic colour changes: simulate, compare the three text steps in greyscale, confirm the icons are specified in the template. Two minutes per change beats an audit finding per release.

### 5.3 Where to verify

Keep verification close to the work — the loop below is minutes, not days:

- WCAG ratios: any contrast checker implementing the published formula; the formula itself is in section 3.1 and in [Colour in code](colour-in-code.md) as runnable code.
- CVD simulation: built into browser devtools and design tools; procedures and tool lists live in [Accessibility testing](../accessibility/accessibility-testing.md) — this file does not duplicate them.
- The full success-criterion text and conformance model: [WCAG fundamentals](../accessibility/wcag-fundamentals.md).

## 6. Decision framework

| Element role | Minimum design target | Source |
|---|---|---|
| Body text | 4.5:1 (AA); 7:1 (AAA) for long-form reading products | SC 1.4.3 / 1.4.6 [accessed] |
| Large text / headings ≥ 24px | 3:1 (AA); 4.5:1 (AAA) | SC 1.4.3 / 1.4.6 [accessed] |
| Component boundaries, icons, focus, states | 3:1 against adjacent colours | SC 1.4.11 [accessed] |
| Meaning-carrying graphics | 3:1, plus non-colour redundancy | SC 1.4.11 + 1.4.1 [accessed] |
| Logotype text | no WCAG requirement; brand legibility still applies | SC 1.4.3 exceptions [accessed] |
| Chart series | 3:1 vs background + luminance spread between series | SC 1.4.11 + CVD practice |
| Decorative colour | none — but never load meaning onto it | SC 1.4.3 incidental [accessed] |
| Link text | 4.5:1 + non-hue distinction from body text | SC 1.4.3 + 1.4.1 practice |
| Focus indicator | 3:1 against both component and background | SC 1.4.11 + 2.4.x practice |

## 7. Examples

- **Failure — hue-only status:** two dashboard chips, red "overdue" and green "on track", identical size and lightness. Under deuteranopia both read as similar muddy tones. Fix: keep the hues, add ✓/! icons and labels, and push the two text steps apart in lightness.
- **Failure — the 2.93:1 adjacency:** a gold badge flush against a blue banner (measured above). Fix: 2px white gap, or darken the badge's border step.
- **Success — ramp-anchored accessibility:** the primary ramp in [Palette development](palette-development.md) pre-assigns steps to roles (600 text/AA, 700 AAA, ≤ 400 tint), so no component can accidentally pair step 300 with body text.
- **Success — dark-theme re-test:** the light theme's primary-as-text step fails on dark surfaces (2.04:1 for step 300 on white — and worse reversed); the dark theme swaps in the same ramp's lighter step against near-black surfaces, restoring ≥ 4.5:1. Same palette, role-level derivation.
- **Print and wayfinding (contrast thinking beyond WCAG):** WCAG applies to web content, but the same luminance logic governs a logo on a lanyard, white text on a poster photo, or floor-signage in a dim hall. Print adds viewing-distance and substrate variables, so verify contrast on the actual stock under the actual lighting — the palette documentation should carry the approved print pairings next to the approved web pairs.
- **The form-validation cascade:** one error state touches text (`#B42318` message at 6.57:1 — pass), border (3:1 against adjacent fields — pass), icon (paired with the message), and the field label ("required" word, not just a red asterisk). Four palette decisions, one documented pattern — and every form in the product inherits it without re-auditing.

## 8. Common mistakes

- **Auditing contrast after launch** instead of building the pair matrix during construction; failures then trace into components and content.
- **Fixing contrast with hue changes** ("try a different red") instead of value changes — hue does not control luminance.
- **Borderline values with no margin:** shipping at 4.5:1 exactly, then an anti-aliasing or palette-tweak pushes it under. Aim ≥ 4.6:1 for AA, ≥ 3.2:1 for non-text.
- **Encoding meaning in hue alone** in charts and status systems — the single most common CVD failure.
- **Treating the logotype exemption as a general exemption.** Brand-name text is exempt; *marketing headlines are not*.
- **Assuming dark themes inherit accessibility.** Every pair's ratio changes; the matrix must be re-run per theme.
- **Grey-on-grey disabled styling** with no other signal — technically exempt from 1.4.11, but users still need to identify the control's state by some means.
- **Testing only the extreme pairs.** Black-on-white passes, so the team assumes everything does; the failures live in the middles — muted text, tint-on-tint, accent-on-image.
- **Exporting the palette without its contrast metadata.** A handoff of hex values alone forces every consumer to re-audit; ship the pair matrix with the colours.
- **Simulating only one CVD type.** Deuteranopia-only review misses protanopia and tritanopia failures — and misses the greyscale test entirely.

## 9. Evaluation checklist

- [ ] Ground text/background pair passes AAA, or at minimum AA, with margin.
- [ ] Primary passes AA in both directions (text-on-white; white-on-fill).
- [ ] Every intentional text pair measured and labelled in the matrix.
- [ ] Component boundaries, icons and focus states hold 3:1 against adjacent colours.
- [ ] No meaning is carried by hue alone; redundancy documented per signal.
- [ ] Chart series separated by luminance and pattern, not hue alone.
- [ ] Semantic text steps distinct in lightness as well as hue; icons specified.
- [ ] CVD simulation (deuteranopia, protanopia, tritanopia) reviewed on real layouts.
- [ ] Both themes measured separately; dark theme not derived by naive inversion.
- [ ] Values in documentation are measured, not estimated.
- [ ] Link colour is distinguishable from body text by more than hue (underline/weight).
- [ ] Focus indicator specified as a palette role and verified against multi-colour surfaces.
- [ ] Contrast metadata travels with the palette at handoff (pair matrix included).
- [ ] Semantic verification loop (section 5.2) has been run after the last semantic change.
- [ ] Component states (hover, selected, disabled, focus) are in the pair matrix, not just static colours.

## 10. Related topics

- [WCAG fundamentals](../accessibility/wcag-fundamentals.md) — the normative framework, success criteria and conformance model behind the values here.
- [Accessibility testing](../accessibility/accessibility-testing.md) — full testing procedures and tool workflows.
- [Accessible colour](../accessibility/accessible-colour.md) — the accessibility domain's colour reference page.
- [Palette development](palette-development.md) — ramps, roles and the construction loop this file plugs into.
- [Colour theory](colour-theory.md) — value vs hue: why luminance, not hue, drives contrast.
- [Colour in code](colour-in-code.md) — computing contrast in JavaScript/CSS and enforcing it with tokens.
- [Design tokens](../design-systems/design-tokens.md) — encoding contrast-safe roles as tokens.

## 11. References

- W3C WAI, "Understanding SC 1.4.3 Contrast (Minimum)" (4.5:1 / 3:1, large-text definition, logotype and incidental exceptions, no-rounding note, ratio formula). https://www.w3.org/WAI/WCAG22/Understanding/contrast-minimum.html [accessed 2026-11-23]
- W3C WAI, "Understanding SC 1.4.11 Non-text Contrast" (3:1 for component visual information and graphical objects; state indicators; relative-luminance formula). https://www.w3.org/WAI/WCAG22/Understanding/non-text-contrast.html [accessed 2026-11-23]
- W3C WAI, "Understanding SC 1.4.6 Contrast (Enhanced)" (7:1 / 4.5:1). https://www.w3.org/WAI/WCAG22/Understanding/contrast-enhanced.html [accessed 2026-11-23]
- Colour Blind Awareness, "About Colour Blindness" (prevalence 1 in 12 men / 1 in 200 women; ~3 million in the UK; ~300 million worldwide; red-green predominance; inherited vs acquired causes). https://www.colourblindawareness.org/colour-blindness [accessed 2026-11-23]
- W3C Silver (WCAG 3) Visual Contrast of Text Subgroup — APCA perceptual contrast model under exploration for future guidance. https://www.w3.org/WAI/GL/task-forces/silver/wiki/Visual_Contrast_of_Text_Subgroup [search-verified 2026-11-23; APCA is a research direction, not the current conformance standard]
- Contrast ratios in tables computed with the WCAG relative-luminance formula (script in the authors' workspace); semantic and brand hexes from the worked examples in [Palette development](palette-development.md). [synthesis]
- WCAG 2 success criterion 1.4.1 (Use of Colour) is referenced throughout this file as the basis of the colour-independence rule; consult [WCAG fundamentals](../accessibility/wcag-fundamentals.md) for its normative text rather than re-quoting it here. [canonical]
- Large-text px equivalents (24px / ~18.5px bold) are the standard CSS conversions of the 18pt/14pt thresholds stated in the W3C Understanding pages. [synthesis]
