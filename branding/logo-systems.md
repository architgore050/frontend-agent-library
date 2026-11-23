# Logo systems

## 1. What is it?

A logo system is the complete set of logo assets and the rules for using them: the primary mark, its variants (monochrome, reversed, symbol-only, lockups), the measurement conventions that govern its placement (clear space, minimum size), the file formats it ships in, and the catalogue of misuses it must be protected from. "System" is the operative word — a logo without variants and rules cannot survive contact with real production, where dark backgrounds, tiny favicons, single-ink print jobs and co-branded layouts are routine.

This file covers the structure and handling of logos themselves. How a logo fits into the wider identity is in [Visual identity](visual-identity.md); how to work with a logo that already exists and may not be changed is in [Fixed-logo analysis](fixed-logo-analysis.md); how multiple brand marks relate to each other (parent, sub-brand, partner) is in [Brand architecture](brand-architecture.md).

## 2. Why does it matter?

The logo is the most repeated and most legally significant visual asset an organisation owns, and it is also the one most often damaged in ordinary use: stretched by someone filling a box, recoloured to match a campaign, dropped onto a photograph where it disappears. Every misuse is small; their sum is a mark that no longer reliably triggers recognition. Rules exist precisely so that the mark means the same thing everywhere.

The system layer also has an unglamorous but decisive role: it removes decisions. If the export set contains the right file for every context — SVG for the web team, transparent PNG for the slide template, EPS/PDF for the printer, reversed white for the dark hoodie — nobody has to improvise, and improvised logos are where brands degrade. Michael Evamy's *Logo* documents how enduring marks are designed as families of forms across contexts, not as single artefacts [canonical].

## 3. Core principles

**The mark is fixed; the system is designed around it.** Once a logo is adopted, its geometry, proportions and colours are frozen. Everything else — spacing conventions, variant logic, file formats — is designed to protect it. This principle does double duty: it also defines the boundary for identities built around an existing logo, where the mark is a given (see [Fixed-logo analysis](fixed-logo-analysis.md)).

**Every variant is a deliberate decision, not an export accident.** A monochrome version is not "the logo printed in black"; it is a designed rendering that may simplify details (fine gradients, multi-line type) for single-ink reproduction. Variants that are merely re-coloured files rather than designed renderings fail on real surfaces.

**Measurement relative to the mark, not to the page.** Clear space and minimum sizes should be defined using elements of the logo itself (the height of a letter, the width of a symbol), so the rule scales with the logo at any reproduction size. Absolute units are then derived for concrete contexts.

**Recognition under constraint.** The system must guarantee recognition in the worst realistic case: smallest permitted size, lowest contrast permitted background, single colour, poor print. If a variant cannot pass that test, its permitted contexts are narrowed until it can.

## 4. How it works

### 4.1 Logo anatomy

Understanding the parts of a mark is prerequisite to every measurement rule:

| Term | Meaning |
|---|---|
| Symbol / mark | The non-verbal graphic element (icon, emblem, glyph). |
| Wordmark | The organisation name set as drawn lettering. |
| Monogram / lettermark | An abbreviation rendered as the mark (initials). |
| Lockup | A fixed arrangement of symbol + wordmark (horizontal, stacked, corner). |
| Cap height / x-height | Height of capitals / of lowercase letters without ascenders — common measuring units. |
| Counter, aperture, stem, terminal | Interior space of letters, openings, main vertical strokes, stroke endings — where letterform character lives. |
| Baseline | The line letterforms nominally sit on. |
| Clear space | The protected empty zone around the mark (see 4.3). |

Anatomy matters practically: clear space is usually defined from a letter height, minimum sizes from cap height, and compatibility judgments (does a companion typeface match the wordmark's letter proportions?) are made in anatomy terms.

### 4.2 Mark types and when to use them

| Type | Strengths | Risks | Typical use |
|---|---|---|---|
| Wordmark | Name recognition; no symbol to explain | Needs strong typographic craft; long names get unwieldy | Organisations whose name is the brand |
| Symbol mark | Works at tiny sizes, cross-language, ownable | Must be learned; weak alone if unknown | Established brands, apps, social profiles |
| Combination lockup | Both recognition paths; flexible split | More variants to manage | Most new organisations and events |
| Monogram/lettermark | Compact; fits badges, stamps | Initials may collide with other organisations | Formal, heraldic, sport-style contexts |
| Emblem | Integrated, authoritative | Poor scaling; hard to use separately | Seals, crests, badges |

Events typically need a combination lockup (symbol or monogram + event name and year) plus a symbol-only form for favicons and wristbands. Which element may appear alone, and in which contexts, is an explicit system rule — never an assumption.

### 4.3 Clear space (exclusion zones)

Clear space is the minimum empty area around the mark that no text, image or other graphic may enter. Its purpose is optical: surrounding content competes with the mark's silhouette and reads as crowding or as a new, unintended lockup. The professional convention — and the definition used in this repository — is to **build the exclusion zone from an element of the logo itself**:

- **Element-based unit.** Choose a salient, measurable element: the cap height of the wordmark's first letter, the height of the symbol, the width of a monogram. The clear space is one (or some fraction) of that unit on all four sides. Real examples: Uber Eats requires clear space "equal to or greater than the height of the 'U' in Uber" [accessed]; University at Buffalo derives each mark's clear space from the height of its interlocking UB (and, for co-branded layouts, from its width) [accessed].
- **Absolute rule for merchandise.** Some organisations add a fixed physical unit for specific contexts: MIT specifies at least 1 inch (25 mm) between the logo and any other graphic on merchandise, more where size demands [accessed].
- **Tighter inner tolerance.** Some systems allow reduced spacing for thin line-work near the mark while keeping the full zone for solid elements (UB permits a reduced measure for linework around its lockups [accessed]).

Practical derivation procedure for a fixed logo: (1) pick the reference element and define it numerically as a fraction of the artwork's height; (2) verify the zone visually at minimum size — it should never look larger than necessary; (3) express the rule once, in the logo's own units, and only then convert to px/mm per format. A CSS example for enforcing the zone in a web layout:

```css
/* Clear space = cap height (measured 24px at base size) => padding: 24px around logo */
.logo-slot {
  display: inline-block;
  padding: 24px;           /* the exclusion zone */
  min-width: calc(96px + 48px);  /* minimum logo width + clear space */
}
.logo-slot > * { pointer-events: none; } /* nothing interactive inside the zone */
```

A worked derivation, start to finish. Given a horizontal lockup whose wordmark cap height measures 20 px at the file's base size: define the clear-space unit as one cap height (20 px at base). The rule reads "clear space = 1 × cap height on all sides". At a reproduction where the logo is rendered 96 px wide, measure or compute the rendered cap height (say 12 px) — the zone around it is 12 px, in any unit the medium uses (12 px, or 3 mm if the logo prints at 30 mm wide with a 3.75 mm cap height). Because the rule is expressed in the mark's own element, it scales without a new decision per size, and the same derivation produces the template padding and the print margin specification.

### 4.4 Minimum size

Minimum size exists because letterforms and fine details collapse below a threshold: counters fill in, thin strokes drop out in print, favicons turn to noise. Specify separate minimums for screen (px) and print (mm or in), and separate minimums per variant (the symbol survives smaller than the lockup). Real published examples: Uber Eats lists web minimums of 30 px width (one variant) and 70 px width (another) with print minimums of 0.7 in and 1.4 in respectively [accessed]. Where no measured data exists, the conventional starting point is: lockup ≥ 24 px tall on screen / ≥ 10 mm wide in print; symbol-only can go roughly half that — then verify on the actual devices and presses and adjust. Digital crispness interacts with rendering: see [Web typography](../typography/web-typography.md) for the screen-rendering issues that also affect fine logo strokes.

### 4.5 Aspect ratio and integrity of the lockup

A lockup's proportions are part of its design: the gap between symbol and word, the optical alignment, the baseline relationships. The system therefore treats the lockup as an indivisible unit with a fixed aspect ratio. Rules that follow: never re-set the lockup from a live typeface (the original lettering is a drawing; re-typesetting changes it); never rearrange components into new combinations (MIT: use lockups as provided, don't rearrange components [accessed]); never re-proportion the spacing to squeeze into a slot — change variant instead (stacked for square/portrait spaces, horizontal for landscape, as Uber Eats prescribes [accessed]).

### 4.6 Background compatibility

Every variant needs a stated background policy: which backgrounds it may sit on, and what happens when the background is not ideal.

- **Contrast requirement.** The mark must read at minimum size on the permitted background. On insufficient contrast, change variant, not the logo: darker backgrounds take the white/reversed logo, lighter backgrounds take the black/colour version (Uber Eats: "Darker backgrounds → use the white logo; lighter backgrounds → use the black version" [accessed]).
- **Reserved-colour policies.** Some organisations restrict background palettes in specific channels: MIT social media requires the logo black or white on palette-coloured backgrounds, excluding black, white and grey backgrounds, which are reserved for flagship accounts [accessed].
- **Busy-background policy.** Over photographs and patterns, use either the reversed mark in a solid overlay panel, a scrim, or forbid the combination. State which, explicitly — improvising scrims per campaign is drift.
- **Colour count policy.** A common professional convention: the logo itself renders in one colour per application (MIT: single colour only, never multiple colours [accessed]); multi-colour marks are the designed exception, not the default.

### 4.7 Monochrome and reversed variants

The monochrome variant is designed for single-ink reproduction (engraving, embroidery, fax-grade print, stamps) and may simplify detail. The reversed variant (white on dark) is a designed rendering too — thin joins sometimes need opening up slightly in negative space. Both variants ship in the export set from day one; they are not derivable reliably on the fly by a non-designer. Deriving *system colours and motifs* from a fixed mark is legitimate and is covered in [Fixed-logo analysis](fixed-logo-analysis.md) — but deriving new *logo renderings* is not.

### 4.8 File formats: vector versus raster

The master file is always vector. Vector formats store geometry and scale infinitely; raster formats store pixels and only look right at their native size.

| Format | Kind | Use for | Caveats |
|---|---|---|---|
| SVG | Vector | Web, apps, favicons (modern), e-mail (inline) | Styling/scripts in SVG can be a security concern; serve simplified, optimised exports |
| PDF / EPS / AI | Vector | Print masters, vendor handoff | EPS legacy but still common in print workflows |
| PNG | Raster | Web fallbacks, slides, docs; transparency supported | Export at exact display size(s) or @2x/@3x; never upscale |
| JPG | Raster | Photos-ready contexts where transparency is not needed | No transparency; avoid for logos on flat colour |

Rules of thumb, consistent with professional practice sources reviewed this session [search-verified]: distribute vector wherever the recipient can use it; create raster derivatives only from the master vector, at exact intended dimensions (Civic Brand: "always create a JPG or PNG for use on the web from this master vector file", saved at exact dimensions [search-verified]); PNG for transparency on the web when SVG is unavailable [search-verified]. Specify colour space per file: RGB for screen exports, CMYK for print masters, plus a Pantone-specified variant where brand-critical match matters (Uber Eats publishes HEX, RGB, CMYK and PMS for its green [accessed]).

### 4.9 Export sets

A complete export set is predictable in structure, so any team member can find the right file without asking. A conventional structure:

```text
brand/logo/
  vector/
    primary-lockup/        (SVG, PDF, EPS, AI — RGB and CMYK print masters)
      logo-primary.svg
      logo-primary-print-cmyk.pdf
    symbol-only/
    monochrome/            (black + white vector)
  raster/
    png-rgb/
      logo-primary@1x.png  logo-primary@2x.png  logo-primary@3x.png
      logo-primary-white@2x.png
    favicon/
      icon-16.png  icon-32.png  icon-48.png  icon-512.png
  README.txt               (one screen: which file for which context)
```

The README matters as much as the files: an export set without usage labels is a misuse generator. Spotify's public media kit shows the delivery-page pattern — components in defined colourways with colour space in the filename (e.g. `Spotify_Full_Logo_RGB_Green.png`) — which is the minimum acceptable labelling [accessed].

### 4.10 Favicon and app-icon crops

The smallest contexts deserve their own design attention because the lockup cannot simply be scaled down: at 16 px, letterforms collapse and the mark becomes noise. The professional approach is a dedicated crop or redraw of the symbol (or a distinctive fragment of it) for favicon and app-icon use, produced as designed assets, not as a scaled lockup. The set commonly covers 16, 32 and 48 px favicons plus 180 px (iOS touch icon) and 512 px (Android/app store) sizes as conventional starting points; each size is verified visually at actual scale, since detail that survives 512 px may vanish at 32 px. For symbol-free wordmark logos, an icon can be derived from a single letterform or monogram — an architecture-level decision, not a design liberty, since it creates a new standalone mark. Background rules matter here too: favicons usually need their own contained background colour or shape, specified once, because the contexts where they appear are never controlled.

## 5. Practical application

### 5.1 Building the variant matrix

Enumerate contexts first (screen dark/light, print 1-colour, tiny sizes, co-branding), then map each context to a variant, then produce only the variants that map to at least one context. A variant matrix avoids both gaps (no reversed logo when the dark theme ships) and waste (a dozen files nobody uses). Verify each variant at its stated minimum size before release: render it on real devices and a printed proof.

### 5.2 Integrating the logo into layout

In web/app layouts, reserve the logo's clear space in the component that hosts it (the `.logo-slot` pattern above), link to the SVG in the export set, and provide the reversed variant to the dark theme explicitly — do not let CSS filters recolour the logo, which is a misuse (see 6). For print templates, place the lockup on the layout grid with its clear-space unit converted to the document's measurement system, and check the minimum size at the smallest expected print run size (a bookmark versus a banner).

### 5.3 Variant matrix example

Mapping contexts to variants before production prevents both gaps and waste. A filled example for a small event brand:

| Context | Variant | File from export set |
|---|---|---|
| Website header (light) | Primary horizontal lockup | `logo-primary.svg` |
| Website header (dark) | Reversed lockup | `logo-primary-white.svg` |
| Favicon / app icon | Symbol only | `icon-32.png`, `icon-512.png` |
| Sponsor banner on dark blue | Reversed, at minimum size or larger | `logo-primary-white@2x.png` |
| One-colour print (wristbands) | Monochrome | `logo-mono-black.svg` |
| Embroidery (staff shirts) | Simplified monochrome, enlarged minimums | `logo-mono-embroidery.svg` |

The last row illustrates variant design rather than re-colour: embroidery loses fine detail, so the monochrome variant is simplified for the process. Every row's file exists in the export set before production starts — the matrix is also a completeness check for the kit.

### 5.4 Logo usage rules template

A fill-in template for the logo rules section of any guideline document. Each blank is a decision, not prose; values come from the analysis in [Fixed-logo analysis](fixed-logo-analysis.md) where the mark already exists.

```markdown
# Logo usage rules — [Organisation]

## Variants (supplied files only — never redraw or re-export)
- Primary: [horizontal lockup] — file: [path]
- Stacked: [vertical lockup] — file: [path]
- Symbol-only: [icon] — file: [path]
- Monochrome: [black / white] — files: [paths]
- Prohibited renderings: [none beyond the above]

## Clear space
- Unit: [element, e.g. height of the letter "U" in the wordmark]
- Value: [1 × unit on all four sides]
- Rule: nothing — text, image or graphic — may enter the zone.

## Minimum sizes
- Screen: lockup ≥ [n] px wide; symbol ≥ [n] px
- Print: lockup ≥ [n] mm wide; symbol ≥ [n] mm

## Backgrounds
- Light backgrounds: [which variant/colourway]
- Dark backgrounds: [which variant/colourway]
- Busy backgrounds (photo/pattern): [panel / scrim / not permitted]
- Reserved colours: [any, and where]

## Lockup integrity
- The lockup is indivisible; do not re-space, re-set or rearrange.
- To fit a space, change variant; do not re-proportion.

## Misuse catalogue (each with its reason)
1. [misuse] — [reason] — [correction]
2. …

## Co-branding
- Lockup recipe: [side-by-side with divider / endorsed]
- Lead brand: [who, per agreement]
- Spacing: [derived unit between mark and divider]
- Approval: [what must be reviewed, by whom, turnaround]
```

Filled in, this template is the logo section of the guidelines ([Brand guidelines](brand-guidelines.md)) and the enforcement basis for [Brand governance](brand-governance.md).

## 6. Logo misuse catalogue

Each item is a failure mode observed in real usage, with the reason it is prohibited and the correction.

| Misuse | Why it fails | Correction |
|---|---|---|
| Stretching/squeezing | Destroys proportions; letterforms visibly distort | Scale uniformly; change variant to fit the space |
| Recolouring ad hoc | Breaks palette ownership and contrast guarantees | Use approved variants only; change background instead |
| Effects (drop shadow, gradients, outlines, bevels, filters) | Adds noise; mark stops matching its registered form | Flat reproduction; use layout and imagery for depth (Uber Eats: no stylised filters [accessed]) |
| Rotation/tilting | Reads as carelessness; harms instant recognition | Keep upright; express energy through layout, not the mark |
| Low-resolution use / upscaling raster | Blur and artefacts signal neglect | Use vector, or raster at ≥ intended pixel density (@2x) |
| Busy backgrounds | Mark disappears; contrast collapses | Solid panel, scrim, or reversed variant per background policy |
| Enclosing in another graphic | Competing container competes with the mark (MIT: don't enclose the logo [accessed]) | Give clear space instead |
| Rearranging/rediscovering lockups | New combinations read as different brands (MIT: don't rearrange components [accessed]) | Use the provided variant set; request new lockups through governance |
| Substituting the mark in text | Logo is not a font; "MIT" in a sentence should be plain text (MIT rule [accessed]) | Set names in the brand typeface |
| Embedding in copy | Neither text nor mark reads cleanly | Separate blocks with clear space |
| Cropping the mark | Silhouette integrity lost | Show whole mark; partial use only if a designed, documented crop variant exists |
| Using as a watermark over imagery | Mark competes with content; both read badly | Place the mark in its layout zone at specified size; commission layout, not stamping |
| Animating with improvised effects | Alters the registered form in time; motion mismatch | Use the approved motion asset if one exists; otherwise keep the mark static |
| Combining with partner marks ad hoc | Uncontrolled lockups imply endorsement | Use documented co-branding lockups (see 7) |

## 7. Co-branding arrangements and lockups

Co-branding puts two or more marks in one layout, and it is governed more strictly than solo use because it implies relationships (partnership, endorsement, sponsorship — see [Brand architecture](brand-architecture.md)).

- **Side-by-side lockups.** The dominant professional pattern for partnership: marks placed side by side, separated by a divider (rule or glyph), with spacing derived from each brand's clear-space unit. Uber Eats specifies side-by-side placement (not stacked), a dividing line, spacing from each logo to the divider equal to the width of the "U", and — notably — that the partner logo appears first and takes the visual lead, with Uber Eats supporting [accessed]. Who leads is a negotiated business point that must be written into the rule.
- **Endorsement lockups.** A parent mark endorsing a sub-brand ("[Parent] presents [Sub]") uses hierarchy of size and position rather than a divider; MIT's endorsed-branding guidance requires spatial separation so neither mark confuses the other, and forbids hiding the endorser mark at page bottom or on back covers [accessed].
- **Alignment axes.** When multiple marks share a layout, align them on a common horizontal or vertical axis (MIT guidance [accessed]) rather than floating them independently.
- **Inter-mark spacing.** Where two marks sit without a divider, use a derived unit — UB uses the width of its interlocking UB between co-branded marks [accessed] — never an arbitrary gap.
- **Approval flow.** Co-branded material usually needs review before launch (Uber Eats: submit co-marketing to the Brand Desk, 3–5 business days turnaround [accessed]). Governance details: [Brand governance](brand-governance.md).
- **Optical equalisation.** When two marks of different visual weight sit side by side, matching measured height can look unequal — a dense slab wordmark next to a light geometric symbol reads as mismatched even when both are 20 mm tall. The professional convention is to equalise *optically* (adjust relative size until the marks feel equal) while never altering either mark's internal proportions. The adjusted relative size is decided once, in the lockup template, not re-argued per artwork; if the partner's mark changes, the template is re-checked.

## 8. Common mistakes

- Defining clear space as an arbitrary fixed number ("10 px") instead of a mark-derived unit, so the rule silently breaks when the logo is resized.
- Shipping one file (a JPG on white) and calling it a logo system; every dark background then improvises a bad solution.
- Setting minimum size without testing at that size — the rule exists on paper, fails on the 16 px favicon.
- Letting the web team recolour the logo with CSS filters to "fit the theme"; this is recolouring misuse in code.
- Treating the wordmark as a typeface and re-typesetting it in documents; lettering is drawing, not text.
- Co-branding by eyeball: unequal optical sizes, missing divider, inconsistent spacing; fix with the lockup template.
- Writing prohibitions without the reason, which invites inventive workarounds; give the rationale (see [Brand guidelines](brand-guidelines.md) on rule-writing).

## 9. Evaluation checklist

- [ ] Primary lockup, symbol-only, monochrome (black and white) and reversed variants all exist and are designed renderings, not re-colours.
- [ ] Clear space is defined from a named element of the logo, stated as a unit, and enforced in templates.
- [ ] Minimum sizes are stated for screen and print, per variant, and verified at that size.
- [ ] Lockup aspect ratio is fixed; no rule or workflow invites re-setting or re-spacing.
- [ ] Background policy covers light, dark, busy and reserved-colour cases with named variants.
- [ ] Master vector files exist (SVG + print PDF/EPS), with RGB raster derivatives at @1x/@2x/@3x and favicon set.
- [ ] Every export file is labelled with variant, colour space and colourway; README maps context → file.
- [ ] Misuse catalogue is published with reasons, covering at least: stretch, recolour, effects, rotation, low-res, busy backgrounds, rearrangement.
- [ ] Co-branding lockup template exists (side-by-side with divider, spacing in derived units, lead brand stated).
- [ ] All rules are documented per [Brand guidelines](brand-guidelines.md) and owned per [Brand governance](brand-governance.md).

## 10. Related topics

- [Visual identity](visual-identity.md) — the full identity system the logo anchors.
- [Fixed-logo analysis](fixed-logo-analysis.md) — analysing and extending an unchangeable logo; motif derivation.
- [Brand architecture](brand-architecture.md) — parent/sub-brand relationships, co-branding and endorsement structures.
- [Brand guidelines](brand-guidelines.md) — turning the rules of this file into documentation.
- [Brand governance](brand-governance.md) — approvals, asset versioning and distribution.
- [Palette development](../colour/palette-development.md) — colour system the logo variants live in.
- [Colour accessibility](../colour/colour-accessibility.md) — contrast requirements for logo-on-background decisions.
- [Typeface selection](../typography/typeface-selection.md) — companion type that must agree with the wordmark.
- [Composition](../foundations/composition.md) — placing the mark on the grid.
- [Brand identity checklist](../evaluation/brand-identity-checklist.md) — evaluation companion.

## 11. References

- [accessed] MIT, "Do/Don't | MIT Brand Guide", https://brand.mit.edu/applying-brand/do-dont, accessed 2026-11-23.
- [accessed] Uber Eats, "Marketing Tools & Brand Guidelines for Merchants" (co-marketing logo rules), https://merchants.ubereats.com/us/en/resources/learning-center/co-marketing-tools, accessed 2026-11-23.
- [accessed] University at Buffalo, "Clear Space — Identity and Brand", https://www.buffalo.edu/brand/identity/usage/Clear-space.html, accessed 2026-11-23.
- [accessed] Spotify, "Logo and Brand Assets", https://newsroom.spotify.com/media-kit/logo-and-brand-assets, accessed 2026-11-23.
- [search-verified] Civic Brand, "Vector, Raster, JPG, EPS, PNG – what's the difference?", https://www.civicbrand.com/insights/articles/vector-raster-jpg-eps-png-whats-the-difference (master-vector rule; appeared in search results, not fetched).
- [search-verified] Uber, "Uber brand guidelines" (user guide PDF), https://assets.uber.com/d/k4nuxdZ8MC7E/user-guide (appeared in search results; full PDF text could not be parsed this session; cap-height-of-U clear-space rule corroborated by the Uber Eats page above).
- [canonical] Michael Evamy, *Logo*, Laurence King Publishing — mark types and symbol design across contexts.
- [canonical] Alina Wheeler, *Designing Brand Identity*, Wiley — logo systems within identity programmes.
- Minimum-size starting points in 4.4 that are not tied to a cited example are conventional practice values, to be verified against the real device and press context.
