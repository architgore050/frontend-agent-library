# Iconography

## 1. What is it?

An icon system is a family of small, simplified glyphs that share one construction logic — grid, stroke weight, corner behaviour, optical sizing — and function as the brand's fastest-reading visual elements. Icons compress actions ("close", "share"), objects ("document", "camera") and states ("warning", "success") into marks that are recognised faster than words can be read, which is why they dominate interfaces, signage and wayfinding. The word *system* is doing the work in the phrase: a lone well-drawn icon is a decoration; a family that shares construction rules is a component of the graphic language (see [Graphic language](graphic-language.md)) and behaves like one — constrained, extendable, auditable.

This file covers the construction and management of that family: grids and keylines, stroke versus filled styles, optical versus geometric sizing, corner radii and terminals, consistency rules, naming, accessibility, and the sourcing-versus-custom decision. Icon *usage* inside interfaces (placement, spacing, state behaviour) is an interface concern; the visual construction and identity role are the concern here.

## 2. Why does it matter?

**Icons are the densest recognition surface a brand owns.** A product interface may show hundreds of icons in a single session; an event's wayfinding may repeat a dozen pictograms on every sign. Because they appear so often and so small, tiny inconsistencies — mixed stroke weights, inconsistent corner radii, mismatched optical sizes — accumulate into visible incoherence faster than in any other element class. Conversely, a disciplined icon family quietly communicates "this brand controls its details" at every touchpoint.

**Icon failures are comprehension failures.** An ambiguous icon does not merely look wrong; it misdirects the user — someone taps "delete" believing it means "download". Icons also carry accessibility obligations: meaningful graphics must meet contrast requirements, and every icon-only control needs an accessible name. A pretty icon set that fails these tests is a functional defect, not a stylistic choice (see [WCAG fundamentals](../accessibility/wcag-fundamentals.md)).

**Systems outlive individual icons.** Products and events constantly need new icons — a new feature, a new venue zone, a new category. Without a shared construction logic, every addition re-opens the question "what style are we in?", and the set drifts. With a documented grid and rules, a new icon is an engineering task: build to the grid, check the rules, done.

## 3. Core concepts: icon, glyph, emoji, pictogram

| Term | Meaning | In this file |
| --- | --- | --- |
| Icon | A small functional graphic representing an action, object or state, usually part of an interface or sign system | The system's unit; construction rules below |
| Glyph | An individual character or symbol within a typeface; icon *fonts* deliver icons as glyphs | A delivery format, not a style; SVG sprite or font both viable |
| Emoji | Colourful, platform-rendered pictorial characters from the Unicode set | Not brand-controlled; appearance varies by platform — avoid as brand assets |
| Pictogram | A larger, standardised informative graphic for public information (wayfinding, safety) | The environmental-scale cousin; same construction logic, bigger grid |
| Logo | The brand's identifying mark | Never interchangeable with icons; see [Visual identity](../branding/visual-identity.md) |

Two boundary rules follow. First, emoji are public property with platform-specific renderings, so a brand that needs a guaranteed look must draw its own mark rather than ship an emoji. Second, the logo must never appear inside the icon set as an ordinary icon — that dilutes both — though icons may *share its geometry* as part of the graphic language.

## 4. Core principles of construction

### 4.1 Grid and keyline shapes

Icons are built on a square grid with *keyline shapes* — reference circles, squares and rectangles — that force different geometries onto the same visual footprint. The best-documented public grid is Material Design's: system icons display at 24×24dp, the live area is 20×20dp with 2–4dp padding around it, and the keyline shapes are a square of 18×18dp, a circle of 20dp diameter, a vertical rectangle 16×20dp and a horizontal rectangle 20×16dp — note the circle is *larger* than the square, an optical convention so that round and square icons read as equal in size [accessed]. The grid also fixes stroke weight (2dp throughout), corner radius (2dp, on the silhouette only), touch targets (24dp icon on a 48dp target; dense layouts 20dp icon on 40dp), and permits limited optical corrections within the standard forms [accessed].

The specific numbers matter less than the discipline they encode — which transfers to any grid size:

- Define one base size (24 is the common default; 16, 20, 32 and 48 are common companions) and scale by whole multiples.
- Give every geometry class its keyline target: circles sit on the circle keyline, squares on the square keyline, and so on — never freehand-fit shapes to the bounding box.
- Keep padding between the live area and the trim edge so strokes never clip.
- Document stroke width and corner radius once, apply everywhere.

A brand building its own system writes the same spec at its chosen size (for example: 24px grid, 2px stroke, 2px radius, circle keyline 20px) and treats it as law — exactly the ruleset discipline of [Graphic language](graphic-language.md).

### 4.2 Stroke versus filled

| Property | Stroke (outline) style | Filled (solid) style |
| --- | --- | --- |
| Reads best at | Medium and large sizes | Small sizes; low-resolution screens |
| Perceived weight | Lighter, airier | Heavier, more urgent |
| Detail capacity | Higher (interior lines survive) | Lower (interiors merge) |
| Typical role | Default interface sets | Selected/active states, dense contexts, badges |
| Risk | Thin strokes vanish at small sizes | Blob-like ambiguity if shapes over-fill |

Professional systems usually pick one *default* and one *exception*: for example outline as default with filled reserved for active/selected states, or filled default with outline for disabled. Mixing both freely within one row of icons is the classic amateur signature. A two-weight system (one default, one emphasis) is the sane maximum; three weights demand a strong reason.

### 4.3 Optical versus geometric sizing

Geometric equality (every icon exactly 24px wide) is not perceptual equality: a filled circle at the same box as a filled square looks smaller, sharp shapes look larger than round ones, and dense glyphs look heavier than sparse ones. Professional practice therefore sizes icons *optically* — to their keyline shapes and visual mass, not to their bounding boxes:

- Round shapes overshoot: circles and spheres sit on a slightly larger keyline than squares (the Material 20dp circle against an 18dp square encodes exactly this) [accessed].
- Pointed shapes (stars, arrows, chevrons) pull inward from the box edge so their tips do not read as oversized.
- Horizontal and vertical rectangles swap dimensions so both feel equal (16×20 vs 20×16) [accessed].
- Complex glyphs may take minor local corrections — Material permits stroke reductions (for example 1.5dp) for intricate curves, done only within the standard geometry [accessed].

The evaluation method is the **blur test**: squint or blur the row of icons; if any one reads clearly heavier or lighter, its optical size is wrong regardless of its mathematical size.

### 4.4 Corner radii and terminals

Corners and line endings are where an icon set's personality lives and where inconsistency is most visible. Specify all three in the rules:

- **Corner radius**: outer silhouette radius (Material: 2dp) and whether interior corners share it; note that rounding *stroke terminals* is separate from rounding *corners* [accessed].
- **Terminal style**: flat (butt) caps, round caps, or square-with-radius; one per set. Round caps soften, flat caps sharpen; either is coherent, the mixture is not.
- **Join style**: miter for technical sharpness, round joins for friendliness; again one choice per set.

These three settings plus stroke weight form the "hand" of the set. When sourcing or commissioning icons, verifying the hand against the brand's line family (see [Graphic language](graphic-language.md), lines and borders) is the first quality gate.

## 5. How it works: consistency rules and naming

### 5.1 The consistency rules

A set is consistent when a reviewer can answer "yes" to all of these for any pair of icons:

- Same grid, same live area, same padding discipline.
- Same stroke weight (or same two sanctioned weights with the same role split).
- Same corner radius, terminal and join settings.
- Same optical-sizing behaviour per geometry class.
- Same level of detail (no photorealistic miniature next to a two-stroke glyph).
- Same perspective logic — typically flat and front-facing; mixing isometric with flat views breaks the set.
- Same metaphor vocabulary (one system uses "trash bin" for delete, not sometimes an X).

Enforce by review against the grid template, not by eye alone: overlay the icon on the grid file and check the keylines. Most large sets also run automated checks (stroke-width audits, bounding-box audits) in the build pipeline — a practice worth copying even for small brands.

### 5.2 Naming

Icon names are API. Use a stable pattern — `[set]-[concept]-[variant]` for example `ui-share-outline`, `ui-share-filled`, `event-badge-star` — all lowercase, hyphenated, English, singular concepts, no numbers that encode mere iteration (`calendar-v2` guarantees chaos; semantic names like `calendar-range` survive). Deprecate rather than rename when a metaphor changes, so old references fail visibly instead of silently showing the wrong glyph. The same discipline supports the design-token and asset-pipeline conventions used in [Colour in code](../colour/colour-in-code.md).

### 5.3 Delivery formats

| Format | Strengths | Watch for |
| --- | --- | --- |
| SVG (inline or sprite) | Crisp, recolourable via CSS, accessible | Path bloat; always optimise |
| Icon font | One request; easy text-style sizing | Accessibility labelling; ligature failures; colour limits |
| PNG @2x/@3x | Legacy platforms, email | Fixed colours; heavy asset counts |
| Variable icon font | Weight/axis control across contexts | Platform support; tooling maturity — e.g. Material Symbols packages icons as a variable font [search-verified] |

For web work SVG dominates because the brand can recolour icons with palette tokens (see [Colour in code](../colour/colour-in-code.md)) and control accessibility directly.

### 4.5 Constructing an icon: step by step

The working sequence for a new glyph on a documented grid (using the Material-style 24px numbers as the worked example [accessed]; substitute your own spec):

1. **Start from the concept, not the shape.** Write what the icon must communicate in one phrase ("attach a file"). If the phrase needs two ideas, the concept needs splitting or a label, not a busier glyph.
2. **Choose the metaphor** from the set's established vocabulary (attachment = paperclip, if that is the family's precedent). Metaphor consistency outranks shape elegance.
3. **Build the silhouette on the keyline.** Draw the outer geometry on the matching keyline shape (4.1); check the mass against its neighbours at equal zoom.
4. **Add interior detail within the stroke budget.** Every interior line uses the set's stroke weight (2dp in the example); where detail genuinely cannot fit, apply the sanctioned optical correction (for example 1.5dp) and record it [accessed].
5. **Apply the hand.** Corner radius, terminal style and join style from the spec — no exceptions, no per-icon judgement calls.
6. **Optical check.** Run the blur test against a reference row; adjust size on the keyline (never freehand distortion) until the mass matches.
7. **Accessibility check.** Meaningful icon: 3:1 contrast in both light and dark contexts; icon-only control gets an accessible name; decorative icon gets hidden from assistive technology (6.2).
8. **Grid-file review and naming.** Overlay on the grid template, verify padding, name per the pattern (5.2), and add to the set with its role documented.

Steps 3–6 are craft; steps 1–2 and 7–8 are system. Sets stay healthy because the system steps are never skipped, not because every craftsperson is brilliant.

### 5.4 Set management and versioning

An icon set is a living library, and it needs library discipline:

- **One source of truth.** The grid template plus the current set in version control (SVG sources); exported fonts/PNGs are build artefacts, never hand-edited.
- **Change log.** Every addition, modification and deprecation recorded with date and reason — the log is what lets a future contributor understand why a metaphor changed.
- **Deprecation, not deletion.** Retired icons stay available but flagged, so old documents do not silently change meaning; deletion happens on a published schedule after usage checks.
- **Coverage review.** Before each release or event, walk the product/content inventory and list missing concepts; gaps found by inventory never surface as mid-project scrambles.
- **Contribution gate.** New icons enter only through the step-by-step sequence (4.5) with the grid file attached; the review is mechanical where possible (stroke widths, bounding boxes) and judgemental only where necessary.

### 5.5 The one-page icon spec

Condense the whole system into a single reviewable page — the equivalent of the graphic-language ruleset for icons. It contains: grid numbers (base size, live area, keyline dimensions), the hand (stroke weight, corner radius, terminal and join styles), the style split (default and sanctioned variant, with the role of each), optical-sizing rules per geometry class, touch-target minimums, naming pattern, delivery formats, and the accessibility floor (3:1 contrast, accessible names, hidden decorative icons). One page is the difference between "the icons are in the design files somewhere" and a spec any contributor or vendor can build against; it is also the artefact the audit checks against. Keep it versioned with the set and cite the exact numbers when commissioning (see [Illustration](illustration.md), section 5.1, for the commissioning checklist pattern).

## 6. Practical application

### 6.1 Sourcing versus custom

| Situation | Recommendation | Rationale |
| --- | --- | --- |
| Standard interface actions (close, search, menu) | Source a proven open set, verify licence | These metaphors are solved problems; custom adds risk, not identity |
| Brand- or domain-specific concepts | Custom, built on the same grid | No source set knows your domain |
| Mixed reality (most projects) | Sourced base set + custom extensions on the same grid | Speed where solved, ownership where distinctive |
| Wayfinding and safety pictograms | Follow public standard conventions | Recognisability and legal clarity outrank novelty |

When sourcing, do not just pick a pretty set: check licence (including attribution and embedding terms), stroke weight and corner settings against the brand's line family, coverage of your concept list, and the set's maintenance history. Then adapt: recolour to palette, align radii and terminals to the brand hand, and record which icons were modified — a sourced set with unmanaged local edits becomes unmaintainable. The commissioning discipline for custom sets mirrors illustration commissioning (see [Illustration](illustration.md), section 5.1): style sheet, grid template, deliverable list, review checkpoints.

### 6.2 Accessibility

Icons are graphical objects and inherit the WCAG obligations in full [accessed]:

- **Contrast.** Parts of icons required to understand content must reach 3:1 contrast against adjacent colours — the same threshold as large text — and the threshold is strict: computed values are not rounded, so 2.999:1 fails [accessed]. Icons that merely decorate or duplicate adjacent visible text are exempt from the contrast requirement, as are inactive (disabled) controls and essential-identity graphics such as logos [accessed]. State indicators inside a control (a tick, a filled track) are measured against the control's own colours [accessed].
- **Accessible name.** Every icon-only control needs an accessible name (for example `aria-label` on the button), because the glyph is not text. Decorative icons should be hidden from assistive technology (`aria-hidden="true"` or empty alt text). Paired icon-plus-label is the safest pattern; icon-only needs a compelling space reason.
- **Do not rely on colour or icon alone.** Meaning must survive greyscale viewing and for users who cannot perceive the icon: pair critical icons with text, tooltip, or pattern cues — the general redundant-cue principle of [WCAG fundamentals](../accessibility/wcag-fundamentals.md) and [Colour accessibility](../colour/colour-accessibility.md).
- **Size and hit area.** Visual size is not touch size: keep the icon on its grid but give interactive icons a touch target of conventional 44–48px, and never shrink below the size where strokes survive (at 16px, a 2px stroke at 24-grid scale becomes effectively 1.33px — test before use).

### 6.3 Working with icon fonts, sprites and tokens

Delivery choices affect accessibility and recolouring downstream, so decide them with the engineers:

- **Inline SVG** is the most accessible and most recolourable option: the SVG inherits CSS colour, `aria` attributes sit next to usage, and no extra requests are needed. Cost: markup repetition, solved with a build step.
- **SVG sprite (symbol + use)** trades a little flexibility for cleanliness; external sprite files cannot always be styled across origins — inline the sprite or accept the constraint.
- **Icon fonts** are legacy-friendly and easy to size as text, but screen readers may announce the ligature codepoints, so every glyph needs `aria-hidden="true"` plus a text or `aria-label` alternative — accessibility is never free with fonts.
- **Variable icon fonts** (for example Material Symbols [search-verified]) allow weight and style axes to match the type system's emphasis logic; treat axis values as tokens like colours, not per-usage whims.

Whatever the vehicle, icons should read their colour from palette tokens (see [Colour in code](../colour/colour-in-code.md)) so dark mode, states and campaign recolours resolve centrally, and so the 3:1 contrast checks of section 6.2 remain verifiable in code, not just in design files.

### 6.4 Adapting a sourced set

The adaptation checklist for a sourced or purchased set:

1. Record the set's own hand (stroke, radius, terminals) and the brand hand; list the deltas.
2. Recolour to palette tokens; check every icon against its real adjacent backgrounds at 3:1 [accessed].
3. Adjust radius/terminals only if the licence and format allow editing; otherwise accept the hand and note the exception.
4. Rebuild any icon the brand uses *daily* in the brand hand — high-frequency glyphs earn bespoke treatment.
5. Document in the change log which icons are stock, which are adapted, and which are brand-built, so future contributors know the rules that produced each.

**Build, buy, or blend?** Use the sourcing table in 6.1; when blending, the custom additions must be indistinguishable in construction from the sourced base — same grid, same hand — or users will feel the seam even if they cannot name it. Run the blur test across the blended set as the acceptance gate.

**Which base size?** Match the host system: 24 is the Material-inherited default for product UI; 16 for dense desktop; 32–48 for marketing and print; pictogram grids for signage run far larger (often 100mm-class modules — conventional, verify per signage standard). One system may hold two sizes (a 24 primary and a 16 dense) but each size needs its own documented grid, not a blind scale.

**Stroke or fill as default?** Follow the interface's density and the brand's voice: dense professional tools favour stroke (detail survives); playful, high-contrast consumer surfaces often favour fill. The decisive test is the set's worst case — the smallest size, on the lowest-quality screen, in the weakest contrast context the brand allows.

**When to redraw rather than adapt?** When the concept is brand-defining (a signature pictogram family for an event), when the sourced set cannot meet the accessibility bar in your palette, or when the licence cannot cover your media. Otherwise adapt — ownership of the *system* (grid, hand, naming, process) matters more than ownership of every glyph.

## 7. Examples

**The Material system [accessed].** Google's Material Design publishes the canonical public spec: 24dp grid, 20dp live area, keyline shapes at the dimensions listed in 4.1, uniform 2dp stroke, 2dp silhouette radius, 48dp touch targets, and per-context opacity conventions (87%/54%/38% on light backgrounds, 100%/70%/50% on dark, for active/inactive states) [accessed]. Its later Material Symbols iteration delivers the set as a variable icon font with adjustable weight and style axes [search-verified]. Even brands that never use Material benefit from copying the *documentation pattern*: grid, keylines, stroke, radius, targets, states — one page that makes any future icon reviewable.

**An event pictogram family (illustrative composite).** A sports event builds its venue wayfinding on a 48px grid derived from its logo geometry — every pictogram shares the logo's corner cut and 45° angles, with a 4px stroke matched to the brand's line family. The pictograms pass the blur test as a row, survive greyscale printing on temporary signage, and extend to new venue zones without re-design because the grid and hand are documented. The motif derivation method is the one described in [Graphic language](graphic-language.md) and [Fixed logo analysis](../branding/fixed-logo-analysis.md).

## 8. Common mistakes

- **No grid.** Icons drawn per-case at whatever size felt right; the set never lines up. Correction: adopt or write the grid spec (4.1) and rebuild the ten most-used icons first.
- **Mixed hands.** Round terminals next to flat, two stroke weights in one row, one isometric icon among flat ones. Correction: choose the hand, audit the set, redraw the outliers.
- **Geometric-size blindness.** Every icon at exactly 24px while circles look small and stars look huge. Correction: apply keyline optical sizing; verify with the blur test.
- **Icon-only controls without names.** Buttons that screen readers announce as "button". Correction: accessible names on every icon-only control (6.2).
- **Contrast failures through palette choice.** A brand mid-grey icon on a tinted panel at 2.4:1. Correction: check every meaningful icon against its adjacent colours at 3:1, no rounding [accessed].
- **Emoji as brand marks.** Using platform emoji for brand meanings; rendering varies by device and the look is not owned. Correction: draw the mark on the grid.
- **Set drift.** Icons added over years by different hands with no template. Correction: publish the template, run a stroke/bounding-box audit, and require the grid file in every submission.
- **The logo in the icon set.** Logo-as-icon dilutes the mark and breaks the system's neutrality. Correction: icons may share geometry with the logo, never replace it (section 3).

## 9. Evaluation checklist

- [ ] A written grid spec exists: base size, live area, keyline shapes, stroke weight, corner radius, terminal and join styles.
- [ ] Every icon sits on its keyline; the blur test passes across a representative row.
- [ ] One default style plus at most one sanctioned variant; the role split (outline vs filled) is documented.
- [ ] Meaningful icons meet 3:1 contrast against adjacent colours in both light and dark contexts.
- [ ] Every icon-only control has an accessible name; decorative icons are hidden from assistive technology.
- [ ] Touch targets meet the conventional 44–48px minimum where icons are interactive.
- [ ] Naming follows the documented pattern; deprecated icons fail visibly.
- [ ] Sourced icons are licence-cleared for all deployed media and adapted to the brand hand.
- [ ] New icons can be produced by any trained contributor using the template alone.

## 10. Related topics

- [Graphic language](graphic-language.md) — the vocabulary ruleset that icon construction inherits.
- [Illustration](illustration.md) — the larger-scale drawn imagery and its commissioning discipline.
- [WCAG fundamentals](../accessibility/wcag-fundamentals.md) — the underlying accessibility standard.
- [Colour accessibility](../colour/colour-accessibility.md) — contrast measurement practice.
- [Colour in code](../colour/colour-in-code.md) — recolouring icons with palette tokens in CSS.
- [Fixed logo analysis](../branding/fixed-logo-analysis.md) — deriving icon geometry from a fixed logo.
- [Visual identity](../branding/visual-identity.md) — the system the icon set belongs to.

## 11. References

- Material Design 1 specification (mirror), "Icons" — 24dp system icons; 20dp live area with 4dp padding; keyline shapes: 18dp square, 20dp circle, 16×20 and 20×16 rectangles; 2dp stroke; 2dp silhouette corner radius; 1.5dp optical corrections (paperclip, microphone examples); 48dp touch targets (dense 20dp/40dp); state opacities 87/54/38 light and 100/70/50 dark. https://www.mdui.org/en/design/1/style/icons.html [accessed 2026-11-23]
- Material Design, "System icons" — original documentation of the 24dp icon grid and keylines. https://m2.material.io/design/iconography/system-icons.html [search-verified]
- Material Design 3, "Designing icons" — Material Symbols as a variable icon font with weight and style axes. https://m3.material.io/styles/icons/designing-icons [search-verified]
- W3C WAI, "Understanding Success Criterion 1.4.11: Non-text Contrast" — 3:1 minimum for meaningful UI components and graphical objects; no rounding of computed values; exemptions (inactive controls, essential/logotype graphics, decorative, redundant-with-text); adjacent-colour measurement; state indicators measured against component colours. https://www.w3.org/WAI/WCAG21/Understanding/non-text-contrast.html [accessed 2026-11-23]
- W3C WAI, "Understanding Success Criterion 1.4.3: Contrast (Minimum)". https://www.w3.org/WAI/WCAG22/Understanding/contrast-minimum.html [search-verified]
- Digital A11y, "Understanding SC 1.4.11 Non-text Contrast" — practical notes on hit areas, focus indicators and state contrast. https://www.digitala11y.com/understanding-sc-1-4-11-non-text-contrast [search-verified]
