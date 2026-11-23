# Spacing and proportion

Spacing is the system of distances between and inside elements; proportion is the system of ratios between sizes. Together they are what makes a layout feel deliberately made rather than assembled: two layouts with identical grids can feel calm or chaotic depending entirely on whether their spaces come from a consistent scale. This file covers spacing systems (4/8 px scales and tokens), the vocabulary of margins, padding and gutters, ratio and proportion systems including an honest assessment of the golden ratio, density management, and alignment as the force that binds a layout together. Grid placement itself is treated in [Grid systems](grid-systems.md); how spacing adapts across viewports in [Responsive layouts](responsive-layouts.md).

## 1. What is it?

A spacing system is a small, closed set of allowed distance values — for example 4, 8, 12, 16, 24, 32, 48, 64 px — from which every margin, padding, gutter and gap in a product or brand kit is drawn. The values are usually named as design tokens (e.g. `--space-4`) and documented in the design system. A proportion system is the complementary set of allowed size *relationships*: the ratio of a heading to body text, the ratio of a content column to the margin, the ratio between zones of a layout.

The core idea is subtraction of freedom: instead of any of infinitely many pixel values, the designer (or agent) chooses from a dozen. This is the same discipline a grid applies to position — applied to distance. Because the values repeat, the layout gains rhythm: equal spaces read as intentional relationships, and the eye learns the system after a few screens.

## 2. Why does it matter?

Spacing is the most quantifiable of the visual decisions, and its inconsistency is the most visible flaw in agent-generated and rushed layouts. Three reasons it deserves systematic treatment:

- **Perceived quality.** When the gap between a heading and its section equals the gap between unrelated sections, the hierarchy collapses — the viewer cannot tell what belongs to what. The Gestalt principle of proximity means perceived grouping is driven substantially by distance, so spacing is literally the syntax of grouping (see [Gestalt and perception](../foundations/gestalt-and-perception.md)).
- **Decisions made once.** A documented scale means every new component, page or canvas inherits spacing for free. When extending a fixed event logo into a full brand kit, the spacing scale is what makes the poster, the website and the slides feel like one organisation made them.
- **Responsive stability.** If spacing is tokenised, adapting to breakpoints is a token change, not a redesign — see [Responsive layouts](responsive-layouts.md) and the CSS patterns in §5.

The limits: a spacing scale disciplines distance, not meaning. Uniform spacing everywhere is as bad as random spacing — the scale must be *used* to create contrast (tight inside a group, generous between groups). And proportion mysticism is a real hazard: claims that one ratio is universally beautiful are not supported by evidence (§3.3), so ratios should be treated as convenient constraints, not laws.

## 3. Core principles

### 3.1 Spacing scales and tokens

The dominant professional convention is a **base-4 or base-8 scale**: all spacing values are multiples of 4 px, with most design distances being multiples of 8 px. Material Design specifies that all components align to an 8 dp square baseline grid, with smaller elements such as icons aligning to a 4 dp grid [search-verified: Material Design metrics & keylines, m1.material.io; spacing methods, m2.material.io]. The reasons the 8 px base won out are practical, and worth teaching rather than reciting:

- **Halving resolves cleanly.** 8 divides to 4, to 2, to 1 — so half-steps, borders and icon sizes inside a spacing unit stay on the scale. 
- **Screen density independence.** On the common 1x and 2x device pixel ratios, multiples of 8 (and 4) map to whole physical pixels, avoiding sub-pixel blur in borders and shadows.
- **Few enough values to be a decision.** A scale of ~10 values is small enough to memorise and audit.

A typical token scale (conventional starting point — adjust per product):

| Token | Value | Typical use |
| --- | --- | --- |
| `--space-1` | 4 px | Hairline breathing room, icon padding |
| `--space-2` | 8 px | Space inside a chip; tight inline gaps |
| `--space-3` | 12 px | Related controls, compact component padding |
| `--space-4` | 16 px | Default component padding; small gaps between items |
| `--space-5` | 24 px | Space between related blocks; card gutters |
| `--space-6` | 32 px | Space between subsections |
| `--space-7` | 48 px | Space between major sections |
| `--space-8` | 64 px | Page margins at desktop; large section separation |
| `--space-9` | 96 px+ | Hero and campaign spacing |

Two refinements matter in practice. First, **the scale must interlock with type**: line-heights should also land on (half-)multiples of the base so text blocks sit on a common rhythm — the baseline-grid discipline described in [Grid systems](grid-systems.md) §3.1 and detailed for the web in [Web typography](../typography/web-typography.md). Second, **naming should be ordinal, not semantic**, at the raw-token level (`--space-5`, not `--space-card-padding`); semantic aliases (`--gap-card`) may map to raw tokens so a product can retune the scale in one place.

Scale discipline beyond the values themselves: keep the whole scale short enough to hold in your head (roughly ten steps, as above). If two steps are so close that a viewer could not tell them apart in context (say 40 px and 44 px), delete one — steps that are perceptually identical reintroduce arbitrariness through the back door. And keep the scale *closed*: the moment a one-off value is tolerated for a "special case", the scale stops functioning as a contract. Genuine exceptions (a platform's imposed spec, a print vendor's rule) are documented next to the scale, not improvised.

Print deliverables use the same logic in absolute units: pick a leading interval (e.g. 12 pt or 13 pt body leading, its multiples for headings), and express margins and gutters in millimetres from the grid spec. The scale's job — few values, repeated everywhere — is identical in both worlds; only the unit changes.

### 3.2 Margins vs padding vs gutters

These three words name different spacing relationships and are not interchangeable:

| Term | Where it sits | Owner | Typical driver |
| --- | --- | --- | --- |
| Margin | Outside an element, separating it from neighbours | The layout / parent | The spacing scale and grid |
| Padding | Inside an element, between its border and its content | The component itself | The component's design |
| Gutter | Between tracks of a grid (columns or rows) | The grid | The grid spec (see [Grid systems](grid-systems.md) §3.1) |

The distinction has a practical consequence for who controls what: a component that hard-codes its outer margin breaks composition — outer spacing belongs to the layout, which is why CSS separates `margin` (outside) from `padding` (inside) and why CSS Grid/Flexbox use `gap` for gutters instead of margins (gap semantics per MDN [accessed]: gap space is deducted before flexible `fr` tracks are sized, and gutters behave as fixed spacing, not elements). A reliable rule: **use `gap` between siblings, `padding` inside a component, and reserve `margin` for exceptional pushes** (e.g. offsetting a pull quote into a margin).

### 3.3 Ratios and proportions — including the honest limits

Ratios constrain *size relationships*. The professional toolkit, roughly in order of evidence strength:

- **Simple integer ratios (1:1, 1:2, 2:3, 3:4).** The workhorse. A two-thirds/one-third split, a heading twice the body size, an image zone spanning half the grid — integer ratios are readable, easy to audit and easy to divide responsively. Most everyday layout proportion should come from here.
- **Root ratios and paper.** The ISO A-series (A4, A3…) is built on a 1:√2 (≈ 1:1.414) sheet ratio so folding preserves proportion — an international standard [canonical: ISO 216]. It is the natural proportion system whenever the deliverable is print on standard paper, and √2 is also a common choice for modular type scales.
- **Modular scales.** A geometric sequence of sizes generated by multiplying a base value by a ratio: e.g. base 16 px × 1.25 → 20, 25, 31.25, 39… Conventional ratio names come from musical intervals: 1.125 (major second), 1.2 (minor third), 1.25 (major third), 1.333 (perfect fourth), 1.414 (√2), 1.5 (perfect fifth), 1.618 (golden ratio). Modular scales are most useful for type ramps and heading steps; their value is *consistency*, not the particular ratio chosen.
- **The golden ratio, honestly.** φ ≈ 1.618 arrives with heavy mystique — claims that it governs beauty in nature, classical art and good design. The critical view is well represented in John Brownlee's Fast Company piece, *The Golden Ratio: Design's Biggest Myth*, which argues the ratio's claimed ubiquity in canonical art and design is largely retrospective myth-making [search-verified]. The defensible position for practitioners: φ is one available ratio among several, occasionally a pleasing choice for a two-zone split or a type-scale step; there is no reliable evidence that golden-ratio layouts are systematically preferred by viewers, and retrofitting φ onto successful designs is storytelling, not design method. Use it as an option; never let it overrule content, grid or measure considerations.

A proportional decision framework that survives scrutiny: fix content-driven constraints first (measure in characters, image aspect ratios, touch-target minimums), then choose the simplest ratio that satisfies them, and reach for φ or other "special" ratios only when a deliberate expressive effect is wanted.

### 3.4 Density management: comfortable vs compact

Density is how much content a canvas hosts per unit area, controlled almost entirely by spacing and type size. The convention in product design is to offer **density tiers**: a comfortable tier (8 px-based spacing, taller rows) for marketing, onboarding and content pages; a compact tier (4 px-based, tighter rows) for data-heavy surfaces like dashboards and tables. Material Design's dense-spacing variants follow exactly this logic [search-verified: m2.material.io].

Conventional row-height ranges to anchor the tiers (starting points, not laws): comfortable table rows ≈ 48–56 px, compact rows ≈ 32–40 px; comfortable component padding `--space-4/5`, compact `--space-2/3`. Density interacts with accessibility: interactive elements must not shrink below the WCAG 2.2 Target Size (Minimum) floor of 24 × 24 CSS pixels (with a spacing exception that allows undersized targets if sufficient space separates them) [search-verified: W3C Understanding SC 2.5.8], and touch-first products conventionally aim higher (Material's 48 dp touch-target guidance is a well-known convention). Compact tiers may tighten *non-interactive* spacing; they must not shrink hit areas below the floor.

When to choose which: comfortable when the user is reading, learning or deciding (more spacing = lower cognitive load per element); compact when the user is scanning many comparable items (more content visible = fewer context switches). Never mix tiers on one surface without a rule — e.g. compact everywhere except empty states and marketing headers.

### 3.5 Alignment as the glue

Alignment is the pattern that turns separate spacings into one perceived system: elements sharing a left edge, a centre or a baseline are read as related even when differently sized. Three kinds, with different jobs:

- **Edge alignment** (left/right in Latin-script layouts) is the strongest grouping cue in text and form layouts; ragged-but-consistent left edges read as organised, while mixed left edges read as noise. This is the perceptual basis of the grid discipline in [Grid systems](grid-systems.md).
- **Centre alignment** is legitimate for singular, display-scale elements (hero statements, poster titles) but fragmenting for multi-line body text because the eye loses its return point — a hierarchy and readability judgement, see [Typographic hierarchy](../typography/typographic-hierarchy.md) and [Composition](../foundations/composition.md).
- **Baseline (optical) alignment** matters when edges are irregular: icons and text should optically centre on the text's x-height, not mathematically on the box; large display glyphs often need manual optical nudges.

Consistent spacing *makes* alignment possible — two elements cannot share an edge unless the distances that lead to that edge are drawn from the same scale. This is why §3.1 and §3.5 are one system, not two topics.

## 4. How it works — choosing and documenting a spacing scale

A scale is decided once, documented, and then enforced. The decision sequence:

1. **Pick the base unit.** 4 px if the product is dense (dashboards, tools), 8 px if it is editorial or marketing (fewer, larger steps). Print equivalents: choose a leading interval (e.g. 12 pt or 13 pt) and derive everything in it.
2. **Grow the scale geometrically, not arithmetically.** Early steps 4–8 px apart, later steps 16–24 px apart (as in §3.1's table). Pure arithmetic scales (4, 8, 12, 16 … 100) produce too many indistinguishable large values and defeat the purpose.
3. **Interlock with type.** Set the type ramp first, then confirm every line-height lands on a half-step or step of the base; adjust one system to fit the other. This is the baseline-grid contract.
4. **Name tokens ordinally**, add semantic aliases where components need stable meaning (§3.1).
5. **Define density variants** explicitly: which tokens map to which compact values (§3.4).
6. **Publish the cross-media mapping.** When the kit spans screens and paper, record which values correspond — not by unit conversion but by *role*: the web gutter and the poster gutter are both "the gutter", even though one is 24 px and the other 5 mm. Example mapping for the event kit of §7.1:

| Role | Web (px) | Poster (mm) | Slide (cm) |
| --- | --- | --- | --- |
| Page margin | 64 | 20 | 2.7 |
| Gutter | 24 | 5 | 0.4 |
| Base unit | 8 | ≈ 4–5 | 0.2 |

The mapping is a design decision (poster margins shrink as a proportion because the viewing distance differs) and it must be written down; it is the spacing-scale counterpart of the grid spec in [Grid systems](grid-systems.md) §4.1.

7. **Document with a specimen**: a visual table of every token rendered at size, plus the canonical pairings (heading-to-body gap, card padding, section spacing). A scale nobody can see is a scale nobody follows.

For an agent audience the documentation step is decisive: the specimen and pairings are what let the agent reproduce the intended spacing in generated code without re-deriving values.

## 5. Practical application — CSS implementation

Tokens as custom properties, with a compact-tier override:

```css
:root {
  --space-1: 0.25rem;  /* 4 px */
  --space-2: 0.5rem;   /* 8 px */
  --space-3: 0.75rem;  /* 12 px */
  --space-4: 1rem;     /* 16 px */
  --space-5: 1.5rem;   /* 24 px */
  --space-6: 2rem;     /* 32 px */
  --space-7: 3rem;     /* 48 px */
  --space-8: 4rem;     /* 64 px */
}

/* Compact density tier for data surfaces */
[data-density="compact"] {
  --space-4: 0.5rem;   /* 8 px */
  --space-5: 0.75rem;  /* 12 px */
  --space-6: 1rem;     /* 16 px */
}
```

Use `gap` for gutters between siblings and `padding` inside components — not margins between flex/grid children (MDN gap semantics [accessed]):

```css
.card-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(16rem, 1fr));
  gap: var(--space-5);            /* gutter from the scale, not a magic number */
}

.card { padding: var(--space-5); }  /* component owns its interior */
.card h3 { margin: 0 0 var(--space-2); }  /* heading-to-body pairing */
```

Fluid spacing for section rhythm across viewports (mechanics detailed in [Responsive layouts](responsive-layouts.md)):

```css
.section { padding-block: clamp(var(--space-6), 5vw, var(--space-8)); }
```

A minimal utility layer over the tokens (kept deliberately small — component styles should consume tokens directly where possible):

```css
.u-gap-2 { gap: var(--space-2); }
.u-gap-4 { gap: var(--space-4); }
.u-stack > * + * { margin-top: var(--space-4); }  /* vertical rhythm between siblings */
```

The `.u-stack > * + *` pattern is worth noting: it encodes "the space between every adjacent pair" once, so new items inherit correct spacing automatically instead of each item carrying its own margin.

Type rhythm tokens belong to the same system — line-heights that keep every text block on the shared baseline rhythm (see the worked ramp in [Grid systems](grid-systems.md) §7.2):

```css
:root {
  --lh-body: 1.5rem;   /* 24 px: body text on the 8 px rhythm */
  --lh-tight: 2rem;    /* 32 px: h3 */
  --lh-heading: 2.5rem;/* 40 px: h2 */
  --lh-display: 3.5rem;/* 56 px: h1 */
}
```

Because the line-heights are multiples of the base half-step, a heading followed directly by body text creates a predictable vertical gap on any surface, and multi-column text stays aligned — provided the project accepts the rem-based line-height trade-off discussed in [Grid systems](grid-systems.md) §7.2.

## 6. Decision framework

| Question | If yes | If no |
| --- | --- | --- |
| Is the surface data-dense (tables, dashboards)? | 4 px base; compact tier default | 8 px base; comfortable default |
| Is the deliverable print on A-series paper? | Derive proportions from √2 sheet logic; set leading interval | Use px/rem scale |
| Is a two-zone expressive split wanted? | Try 1:2 or 2:3 first; φ only if deliberately expressive | Keep integer ratios on the grid |
| Do two elements belong together? | Tighten to the smallest gap that still separates (proximity) | Push to the next scale step up |
| Are two candidate steps indistinguishable in context? | Delete one; the scale stays short and decisive | Keep both |
| Are you choosing a heading-to-body ratio? | Use the type ramp (modular scale), not ad-hoc values | — |
| Is the deliverable a slide or poster in physical units? | Publish the role-based px↔mm↔cm mapping (§4, step 6) | Assume pixels |
| Does compact density shrink an interactive element? | Check against WCAG 2.5.8's 24 × 24 px floor; keep hit area | Fine to compact spacing only |

Rule of thumb for applying the scale: **inside a group, tight; between groups, the next step up; between sections, the step above that.** The absolute values matter less than the *contrast* between the three distances — uniform spacing is a hierarchy failure even when every value is on-scale.

## 7. Examples

### 7.1 Worked example: spacing tokens for an event brand kit

Given a fixed event logo and three deliverables (poster, website, slides), define the kit's spacing in one table and reuse it everywhere:

- Base unit 8 px (event is marketing-led, not data-dense).
- Type ramp: body 16/24 (px/line-height), h3 24/32, h2 32/40, h1 48/56, display 80/88 — every line-height a multiple of 8, so all text sits on the same baseline grid (§3.1; see [Web typography](../typography/web-typography.md) for the measure rules).
- Canonical pairings: heading-to-body gap `--space-2` (8 px); card padding `--space-5` (24 px); grid gutter `--space-5` (24 px, matching the grid spec in [Grid systems](grid-systems.md) §4.3); section spacing `--space-7` (48 px); page margin `--space-8` (64 px desktop, collapsing responsively).
- Poster adaptation: the same proportions expressed in millimetres (gutter 5 mm, margin 20 mm — the printed translation of the 24/64 px pairings at the poster's scale).
- Logo clear-space rule: exclusion zone = the logo cap-height × 1.5, snapped to the nearest token. This is the brand-kit decision that turns the logo into a spacing participant rather than a floating sticker.

### 7.2 Worked example: dashboard row anatomy

Density tiers become concrete when you decompose a row. Take a table row containing 24 px line-height text:

- **Comfortable row:** 12 px vertical padding above + 24 px text + 12 px below = **48 px** row height; borders on the 4 px half-step.
- **Compact row:** 4 px vertical padding above + 24 px text + 4 px below = **32 px** row height.
- **Interactive check:** even compact, the row is a click/keyboard target well above the 24 × 24 CSS px floor of WCAG 2.5.8 [search-verified]; a compact *icon button* inside that row (16 px glyph) still needs its hit area padded to at least 24 px — padding belongs to the target, so spacing tokens can provide it without growing the visible glyph.
- **Horizontal anatomy:** leading cell padding `--space-3` (12 px), column gaps `--space-4` (16 px), trailing `--space-3`; every value on the 4 px sub-scale so a compact switch only changes the vertical paddings.

Do the arithmetic with code (12+24+12, 4+24+4) rather than trusting mental math, and record the results in the density documentation — the decomposed row is the clearest artefact a compact tier can have.

### 7.3 Evaluation exercise

Take any generated layout and audit it with a ruler (in the browser: measure computed styles): list every distinct margin/padding/gap value found; anything not on the scale is a defect unless documented as an exception. Then invert the test: delete the content and look at the whitespace map — you should be able to see groups (tight), pairs (medium) and sections (large) purely from the remaining spaces. If every gap looks equal, rebuild the relationships using the rule of thumb in §6.

## 8. Common mistakes

- **Arbitrary values.** 13 px, 18 px, 37 px gaps that all look "about right" individually but add up to visual noise. Draw every value from the scale.
- **Margin soup in component code.** Each child carrying its own margins to fight its neighbours' margins; total spacing then depends on markup order. Use `gap` between siblings (§3.2) or the stack pattern (§5).
- **Confusing gutter and padding.** Setting card padding as if it were the grid gutter, or vice versa, so cards either touch or float; keep the grid gutter in the grid and the padding in the component.
- **Uniform spacing everywhere.** On-scale but undifferentiated spacing hides grouping; apply the tight/medium/large contrast rule.
- **Treating the golden ratio as a quality switch.** Applying φ to a layout and expecting improvement; no evidence supports it (§3.3). Choose ratios to fit content and grid.
- **Compacting interactive elements below the accessibility floor.** Tightening dashboards until buttons/rows shrink below 24 × 24 CSS px violates WCAG 2.5.8 [search-verified]; compact the *spacing*, not the *targets*.
- **Type on its own rhythm.** A spacing scale that ignores line-heights: text blocks then never sit on the baseline grid and multi-column text misaligns (the baseline-grid contract, §3.1).
- **Undocumented scales.** Tokens defined in CSS but never rendered as a specimen or paired with canonical uses, so every new page re-invents spacing from vibes.

## 9. Evaluation checklist

- [ ] Every margin, padding and gap value in the deliverable belongs to the documented scale (audit computed styles).
- [ ] Base unit, density tier and density variant mapping are written down and visible as a specimen.
- [ ] Line-heights land on half-steps or steps of the base unit; adjacent text columns align on the baseline grid.
- [ ] Sibling separation uses `gap`; component interiors use `padding`; `margin` appears only where composition requires a push.
- [ ] Spacing contrast expresses grouping: within-group < between-group < between-section.
- [ ] Interactive elements respect the 24 × 24 CSS px minimum (or the project's larger touch-target convention) in the compact tier.
- [ ] Proportional decisions (splits, type steps) use simple ratios or a stated modular scale; any φ use is deliberate and explainable.
- [ ] The scale is consistent across the kit's canvases (px on screens, mm on paper) with the mapping documented.
- [ ] New content added to any page lands correctly without bespoke spacing decisions.

## 10. Related topics

- [Grid systems](grid-systems.md) — the positional framework the spacing scale fills; margins, gutters and flowlines defined there.
- [Responsive layouts](responsive-layouts.md) — fluid spacing (`clamp()`), flexible gutters and breakpoint behaviour of the scale.
- [Gestalt and perception](../foundations/gestalt-and-perception.md) — proximity and similarity: why distance creates perceived grouping.
- [Composition](../foundations/composition.md) — alignment, tension and white space as compositional forces.
- [Principles of design](../foundations/principles-of-design.md) — rhythm and hierarchy, which the scale operationalises numerically.
- [Web typography](../typography/web-typography.md) — measure, line-height and vertical rhythm on the web.
- [Typographic hierarchy](../typography/typographic-hierarchy.md) — the type ramp that must interlock with the spacing scale.
- [Responsive design](../ui-ux/responsive-design.md) — product-level responsive strategy, including touch-target guidance.
- [Frontend implementation](../ui-ux/frontend-implementation.md) — engineering conventions for tokens and utilities in production code.

## 11. References

- Material Design (Google), *Metrics & keylines* — 8 dp square baseline grid; 4 dp grid for smaller elements such as toolbar iconography: https://m1.material.io/layout/metrics-keylines.html [search-verified]
- Material Design (Google), *Spacing methods* — baseline-grid-aligned spacing and incremental spacing guidance: https://m2.material.io/design/layout/spacing-methods.html [search-verified]
- John Brownlee, *The Golden Ratio: Design's Biggest Myth*, Fast Company, 2015: https://www.fastcompany.com/3044877/the-golden-ratio-designs-biggest-myth [search-verified]
- W3C, *Understanding SC 2.5.8 Target Size (Minimum)* (WCAG 2.2, Level AA; 24 × 24 CSS px with spacing exception): https://www.w3.org/WAI/WCAG22/Understanding/target-size-minimum.html [search-verified]
- MDN Web Docs, *Basic concepts of grid layout* — gap semantics (gap deducted before `fr` sizing; gutters as fixed spacing): https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_grid_layout/Basic_concepts_of_grid_layout [accessed 2026-11-23]
- Massimo Vignelli, *The Vignelli Canon* — margins, grids and discipline as the basis of consistent output: https://www.rit.edu/vignellicenter/sites/rit.edu.vignellicenter/files/documents/The%20Vignelli%20Canon.pdf [search-verified]
- ISO 216 (A-series paper sizes, 1:√2 sheet ratio) — basis of print proportion decisions. [canonical]
- Note: token values, row-height ranges and pairing suggestions in §3.1, §3.4 and §7.1 are conventional starting points synthesised from the sources above and standard industry practice, not verified standards; the 8 dp/4 dp grid rules and the WCAG 24 px floor are the externally verified anchors.
