# Web Typography

## 1. What is it?

Web typography is the practice of delivering and controlling type in the browser: sizing that responds to screens and user preferences, fonts that load without wrecking the layout, CSS properties that express typographic intent, and accessibility obligations that print never had. It is where the domain's theory becomes code — the files that decide whether the carefully chosen, paired, scaled and set type of [Typography fundamentals](typography-fundamentals.md), [Typeface selection](typeface-selection.md), [Font pairing](font-pairing.md), [Typographic hierarchy](typographic-hierarchy.md) and [Typesetting](typesetting.md) actually reaches the user intact.

This file covers: CSS units and the root-size model; responsive and fluid type scales with a full `clamp()` worked example; the CSS font property system; variable-font CSS (axes, `font-variation-settings`, `font-optical-sizing`); font loading (`font-display`, FOUT/FOIT, subsetting, preload, formats); fallback stacks and metric-compatible fallbacks; and the accessibility of web type at implementation level. The deep WCAG treatment (contrast, minimum size policies, resize behaviour, reduced motion) lives in [Accessible typography](../accessibility/accessible-typography.md); this file links to it and covers the implementation side.

## 2. Why does it matter?

Three properties make web typography unlike print. First, the reader controls part of the environment: they zoom, they set browser font sizes, they may need 200% text scaling — so sizes must be *relative* and layouts must survive scaling, not just look right at one width. Second, the font is a network resource: unlike print, the typeface may not have arrived when the text does, and every loading decision trades visual fidelity against layout stability and speed. Third, the rendering environment varies: different platforms ship different system fonts, so fallbacks and metric behaviour must be designed, not left to accident.

Getting these wrong has measurable costs: layout shifts when fonts swap (Cumulative Layout Shift, a Core Web Vital), invisible text while fonts block, oversized font files on slow connections, and accessibility failures from px-locked sizes. All are avoidable with the mechanisms below — and all are implementation-level mistakes that no design review upstream can fix.

## 3. Core principles

### 3.1 Units and the root-size model

The unit choices are the foundation everything else stands on:

- **rem** (root em) scales with the root element's font size, which is the user's browser preference unless overridden. Set the root size in relative terms (`html { font-size: 100%; }` or leave the default 16 px) and never in px — a px root silently ignores user preferences. All sizes in the type scale ([Typographic hierarchy](typographic-hierarchy.md) 3.4) are expressed in rem so they all scale when the user adjusts settings.
- **em** scales with the *current element's* font size — correct for spacing that should track local type size (letter-spacing, margins tied to a heading's size).
- **ch** measures the width of the "0" glyph — the natural unit for measure ([Typesetting](typesetting.md) 3.3: `max-width: 68ch`).
- **vw** is 1% of viewport width — the fluid ingredient in `clamp()`, never used alone for text (it ignores user settings and zoom).
- **px** remains correct for hairline borders, shadows and alignment details — but not for font sizes or leading, where relative units carry the accessibility behaviour.

### 3.2 Responsive type scales

A fixed scale ([Typographic hierarchy](typographic-hierarchy.md)) needs responsive behaviour: the same nominal steps must preserve their *relative* contrast from a 320 px phone to a wide desktop. Two mechanisms, combinable:

1. **Stepped (media queries)**: redefine the scale at breakpoints — display drops from 88 px to 44 px below 768 px, h1 from 64 px to 32 px. Predictable and debuggable, but discontinuous: text jumps at breakpoints, and every new breakpoint is maintenance.
2. **Fluid (`clamp()`)**: each step interpolates continuously between a floor and a ceiling (3.3). No jumps, no breakpoint list, one declaration per step. The modern default for display sizes; body text often stays near-static (it does not need to grow as fast as headlines).

Whichever mechanism, the invariant is the same: *relative order and contrast between steps must survive* — the responsive failure mode is steps converging until two levels look equal (see [Typographic hierarchy](typographic-hierarchy.md) 5.3).

### 3.3 Fluid typography with clamp(): the worked example

`clamp(min, preferred, max)` resolves as `max(min, min(preferred, max))` — the preferred value is used while it stays between the bounds. [accessed] The preferred expression is where the fluidity lives; the standard construction is a rem-based floor plus a viewport term:

```css
font-size: clamp(1rem, 0.64rem + 1.82vw, 2rem);
```

At small viewports the vw term is too small and the 1 rem floor applies; at large viewports the ceiling applies; between them the size grows linearly with the viewport. [accessed]

**Deriving the numbers.** Choose two anchors: the size at the minimum viewport and at the maximum. For a body step of 16 px at 320 px and 20 px at 1200 px:

- slope = (20 − 16) px ÷ (1200 − 320) px = 16 ÷ 880 ≈ 0.018182 px per px → **0.4545vw** (× 100)
- intercept = 16 px − 0.018182 × 320 px = 10.1818 px → **0.6364rem** (÷ 16)

So `clamp(1rem, 0.636rem + 0.455vw, 1.25rem)`. Repeating the algebra for a full scale (verified by computation this session):

| Step | At 320 px | At 1200 px | Preferred expression |
|---|---|---|---|
| display | 44 px | 88 px | `1.75rem + 5vw` |
| h1 | 32 px | 64 px | `1.272rem + 3.636vw` |
| h2 | 24 px | 40 px | `1.136rem + 1.818vw` |
| body | 16 px | 20 px | `0.636rem + 0.455vw` |

Each with its own min/max: `clamp(2.75rem, 1.75rem + 5vw, 5.5rem)` for display, and so on. (An agent can re-derive any row: `slope = (fmax − fmin) ÷ (vmax − vmin)`; `intercept_rem = (fmin − slope × vmin) ÷ 16`.)

**Caveats that matter:**

- **Spaces around `+` and `-` are required** inside `clamp()`; without them the declaration is invalid. [accessed]
- **Accessibility floor**: when clamping text sizes, make the maximum at least **twice the minimum** (e.g. 1rem → 2rem), so text can still reach 200% scaling under WCAG 1.4.4's Resize Text requirement. Fluid scales that compress the max/min ratio to improve layout quietly break that. [accessed]
- Fluid sizing is for *size*, not for leading or spacing: leading stays unitless and spacing stays on the spacing scale; only the font-size expressions interpolate.
- `clamp()` has been Baseline across browsers since July 2020. [accessed]

### 3.4 The CSS font property system

| Property | Controls | Notes |
|---|---|---|
| `font-family` | The face, via a fallback stack (5.3) | Last value a generic family (`serif`, `sans-serif`, `monospace`...) |
| `font-size` | Size | rem-based; fluid via `clamp()` |
| `font-weight` | Weight; maps to the `wght` axis | Any value 1–1000 with variable fonts [accessed]; also `bolder`/`lighter` relative keywords |
| `font-style` | Upright / italic / oblique | Maps to `ital`/`slnt` axes |
| `font-stretch` | Width; maps to `wdth` | Percentages, e.g. `110%` |
| `line-height` | Leading | Unitless ratios only (see [Typography fundamentals](typography-fundamentals.md) 3.6) |
| `letter-spacing` | Tracking | em units; caps positive, display slightly negative |
| `font-optical-sizing` | Automatic optical size (`opsz`) | `auto` (default) or `none` [accessed] |
| `font-variation-settings` | Low-level axis access | Custom axes; caveats in 4.1 [accessed] |
| `font-feature-settings` / `font-variant-*` | OpenType features | Ligs, tabular figures (`tabular-nums`), small caps, fractions |
| `font-kerning` | Kerning data application | `auto` default; leave on |
| `font-display` *(in `@font-face`)* | Loading behaviour | See 4.2 [accessed] |
| `text-wrap` | Wrapping algorithm | `balance` for headings, `pretty` for prose [accessed] |
| `hyphens` | Hyphenation | Needs `lang`; see [Typesetting](typesetting.md) 3.2 |

## 4. How it works

### 4.1 Variable fonts in CSS

A variable font carries its design space in axes; CSS reaches that space through two routes ([Typography fundamentals](typography-fundamentals.md) 3.4 introduces the concept):

- **The standard properties** are the intended route for the five registered axes: `font-weight` → `wght`, `font-stretch` → `wdth`, `font-style` → `ital`/`slnt`, `font-optical-sizing` → `opsz`. [accessed]
- **`font-variation-settings`** is the low-level escape hatch for custom axes (uppercase tags like `GRAD`) and anything the standard properties cannot express:

```css
.hero {
  font-variation-settings: "GRAD" 88, "opsz" 40; /* custom + override */
  font-weight: 625;                               /* registered axes stay standard */
}
```

The documented caveats, worth internalising: the W3C's intent is that `font-variation-settings` not be used where a standard property exists; values set with it are not inherited as separately adjustable — changing one value means redeclaring *all* of them (the workaround is CSS custom properties per axis: `font-variation-settings: "wght" var(--wght)`); and it bypasses `@font-face` range clamps, so invalid values slip through. [accessed]

**Optical sizing** deserves emphasis because it is automatic and often unnoticed: with `font-optical-sizing: auto` (the default), the `opsz` axis tracks `font-size` — sturdier strokes and more open spacing at small sizes, finer strokes and more contrast at large ones — exactly the display/text behaviour described in [Typography fundamentals](typography-fundamentals.md) 4.3, handled by the browser. Set explicit `opsz` via `font-variation-settings` only to override it deliberately. [accessed]

In `@font-face`, declare the axis *ranges* the file supports (`font-weight: 300 900; font-stretch: 35% 100%;`) so the standard properties can select within them; pair with `font-synthesis: none` where a missing style would otherwise be faked. [accessed]

### 4.2 Font loading: the mechanics

**FOUT and FOIT.** While a web font is downloading, the browser must render text somehow: showing the fallback is a *flash of unstyled text* (FOUT); hiding the text is a *flash of invisible text* (FOIT). Both are bad; the question is which, and for how long — which is exactly what `font-display` decides. [accessed]

**The `font-display` timeline.** Loading has a *block period* (text rendered with an invisible fallback), a *swap period* (fallback rendered visibly; the font swaps in if it arrives), and a *failure period* (the font is treated as failed). The values [accessed]:

| Value | Block period | Swap period | Behaviour |
|---|---|---|---|
| `auto` | UA-defined | UA-defined | Browser default |
| `block` | Short | Infinite | FOIT risk; swaps in whenever loaded |
| `swap` | Extremely small | Infinite | Immediate fallback text; swaps in whenever loaded (FOUT) |
| `fallback` | Extremely small | Short | Quick fallback; swaps only within a short window |
| `optional` | Extremely small | None | Font used only if available almost immediately; no swap, no late reflow |

Approximate durations per web.dev: `block` ≈ 2–3 s block; `fallback` ≈ 100 ms block, ~3 s swap; `optional` ≈ 100 ms block, no swap. [accessed] (MDN notes the exact "short" and "extremely small" durations are user-agent controlled.) The practical pattern from web.dev: **`swap` for branding/headline faces** (fidelity matters, late arrival acceptable) and **`optional` for body text** (no layout shift; the font joins once cached). [accessed]

**Delivery checklist, verified from web.dev's best practices:**

- **Use WOFF2 only** — best compression (roughly 30% better than WOFF via Brotli), universal support; older browsers simply get fallbacks. [accessed]
- **Subset** — Latin fonts carry 100–1,000 glyphs, CJK 10,000+; subsetting strips unused glyphs. Google Fonts serves subsets automatically; self-hosters must do it themselves (tools exist; confirm the licence permits it). Use `unicode-range` so the browser fetches only subsets actually used. [accessed]
- **Preload sparingly** — `<link rel="preload">` for the one or two critical faces (matching the exact file/format), because it bypasses `unicode-range` negotiation and competes with other resources. **`preconnect`** to third-party font origins (two hints: one plain, one with `crossorigin` for the font file's CORS connection). [accessed]
- **Self-host vs hosted** — self-hosting removes a third-party connection but only wins with a CDN, HTTP/2 and replicated optimisations (subsetting, WOFF2); measured results vary, so compare transfer times rather than assuming. Self-hosting via distribution packages (e.g. Fontsource npm packages) is a common middle path. [accessed]
- **Consider system fonts and variable fonts** to reduce total downloads. [accessed]

### 4.3 Fallback stacks and metric-compatible fallbacks

The `font-family` stack is the designed behaviour for every context where the primary face is unavailable: before it loads, on platforms that lack it (licences and subsets vary), and for system-font strategies entirely. Stack rules: name specific faces first, end with the *right generic* (`sans-serif`, `serif`, `monospace`) — the generic picks the platform default, which is better than the browser's last resort; keep stack length modest; and remember that fallback faces differ in x-height and metrics ([Typography fundamentals](typography-fundamentals.md) 4.1), so text may look larger or smaller before the primary loads.

That last problem is now solvable: the `@font-face` metric descriptors — `size-adjust` (scales glyphs and metrics), `ascent-override`, `descent-override`, `line-gap-override` — let you define a *local* fallback face adjusted to occupy the same space as the web font, so the swap causes minimal reflow (Baseline since September 2023; defined in CSS Fonts Module Level 5). [accessed] The pattern:

```css
@font-face {
  font-family: "Inter-fallback";
  src: local("Arial");
  size-adjust: 107%;
  ascent-override: 90%;
  descent-override: 22%;
  line-gap-override: 0%;
}
body { font-family: Inter, "Inter-fallback", sans-serif; }
```

The percentages are derived by comparing metrics between the two faces; tools can compute them. [accessed]

### 4.4 Accessibility of web type: the implementation side

The implementation obligations that belong in every web typography layer (policy, contrast ratios and user-needs analysis live in [Accessible typography](../accessibility/accessible-typography.md)):

- **Relative units everywhere** (3.1) so user font-size preferences and zoom work: px-based type is the classic, invisible accessibility failure.
- **The 2× clamp rule** (3.3): keep max ≥ 2 × min so 200% scaling is reachable within the fluid scale. [accessed]
- **Real text, not text-in-images**, so scaling, restyling and screen readers work.
- **`lang` on `<html>`** (and on foreign-language passages) — required for hyphenation dictionaries, screen-reader pronunciation and spell-checking ([Typesetting](typesetting.md) 3.2).
- **Contrast of text to background** is a colour-system obligation ([Colour theory](../colour/colour-theory.md)) but is enforced here: muted metadata tones must still meet the applicable ratio.
- **Motion/animation restraint** when animating variable-font axes: grade changes reflow-free ([Typography fundamentals](typography-fundamentals.md) 3.4), but weight animation is still motion — respect reduced-motion preferences.
- **`prefers-*` media queries** (`prefers-reduced-motion`, `prefers-contrast`) belong in the same token layer as the type scale.

## 5. Practical application: a complete fluid typographic system

A complete, correct system — scale ([Typographic hierarchy](typographic-hierarchy.md)), setting ([Typesetting](typesetting.md)), loading and fallbacks (4.2–4.3) — in one stylesheet:

```css
/* ---------- tokens ---------- */
:root {
  /* fluid scale: 1.25 ratio, floors @320px, ceilings @1200px, max >= 2x min */
  --fs-display: clamp(2.75rem, 1.75rem + 5vw, 5.5rem);
  --fs-h1:      clamp(2rem, 1.272rem + 3.636vw, 4rem);
  --fs-h2:      clamp(1.5rem, 1.136rem + 1.818vw, 2.5rem);
  --fs-h3:      clamp(1.25rem, 1.05rem + 1vw, 1.75rem);
  --fs-body:    clamp(1rem, 0.636rem + 0.455vw, 1.25rem);
  --fs-caption: 0.8125rem;
  --fs-label:   0.75rem;

  --lh-display: 1.05;
  --lh-heading: 1.2;
  --lh-body: 1.6;
  --measure: 68ch;

  --font-sans: "Source Sans 3", "Source Sans 3-fallback", system-ui, sans-serif;
  --font-display: "Fraunces", system-ui, serif;
  --font-mono: "JetBrains Mono", ui-monospace, monospace;
}

/* ---------- loading ---------- */
@font-face {
  font-family: "Source Sans 3";
  src: url("/fonts/source-sans-3.woff2") format("woff2");
  font-weight: 300 900;                 /* variable range */
  font-style: normal;
  font-display: swap;                   /* text face: always visible, swap late */
  ascent-override: 90%;                 /* metric-matched fallback face below */
  descent-override: 22%;
  line-gap-override: 0%;
  size-adjust: 104%;
}
@font-face {
  font-family: "Source Sans 3-fallback";
  src: local("Helvetica Neue"), local("Arial");
  size-adjust: 104%;
  ascent-override: 90%;
  descent-override: 22%;
  line-gap-override: 0%;
}
@font-face {
  font-family: "Fraunces";
  src: url("/fonts/fraunces.woff2") format("woff2");
  font-weight: 300 900;
  font-display: optional;               /* display face: no late swap, no shift */
}

/* ---------- base ---------- */
html { font-size: 100%; }               /* respects user preference */
body {
  font-family: var(--font-sans);
  font-size: var(--fs-body);
  line-height: var(--lh-body);
  font-optical-sizing: auto;
  text-wrap: pretty;                    /* fewer bad last lines in prose */
}

/* ---------- hierarchy ---------- */
h1, h2 {
  font-family: var(--font-display);
  font-weight: 600;
  line-height: var(--lh-display);
  letter-spacing: -0.01em;
  text-wrap: balance;                   /* balanced heading lines */
  break-after: avoid;
}
h1 { font-size: var(--fs-h1); }
h2 { font-size: var(--fs-h2); }
h3 { font-size: var(--fs-h3); line-height: var(--lh-heading); font-weight: 600; }

.prose {
  max-width: var(--measure);
  hyphens: auto;                        /* requires <html lang="..."> */
}
.prose + .prose { margin-top: 1.5em; }  /* WCAG 1.4.8 AAA floor is 2em */

/* ---------- roles ---------- */
.eyebrow {
  font-size: var(--fs-label);
  font-weight: 600;
  letter-spacing: 0.08em;               /* tracked caps */
  text-transform: uppercase;
}
.metadata { font-size: var(--fs-caption); color: var(--ink-muted, #555); }
.button {
  font-size: var(--fs-body);
  font-weight: 600;
  letter-spacing: normal;
}
.numeric {
  font-variant-numeric: tabular-nums;   /* aligned figures in data */
}
.code, .id {
  font-family: var(--font-mono);
  font-size: 0.9em;
}

/* ---------- variable-font details ---------- */
.hero-display {
  font-family: var(--font-display);
  font-weight: 640;                     /* any point in the range */
  font-variation-settings: "opsz" 72;   /* deliberate optical override */
}
@media (prefers-reduced-motion: reduce) {
  .hero-display { font-variation-settings: "opsz" 72; } /* no axis animation */
}
```

Markup essentials that the CSS depends on: `<html lang="en">`, `<link rel="preconnect">` to font origins when third-party-hosted, `preload` at most the two critical faces, and no text as images.

## 6. Decision framework

| Decision | Default | When to deviate |
|---|---|---|
| Fluid vs stepped scale | Fluid `clamp()` for display steps; near-static body | Debuggable fixed grids; legacy pipelines |
| `font-display` for text faces | `swap` | Layout-shift-critical surfaces → `optional` |
| `font-display` for display faces | `optional` | Brand must render in its face even late → `swap` |
| Self-host vs hosted API | Self-host with CDN + WOFF2 + subsets | Prototype/quick sites → hosted API with its automatic subsetting |
| Variable vs static files | Variable when multiple weights needed | Single-weight use → static file may be smaller |
| rem vs px | rem for sizes, leading unitless | Hairlines and alignment details stay px |
| Fallbacks | Generic + metric-adjusted local face | System-font-first strategy → stack *is* the design |

Explicitly: the loading values and durations are documented browser behaviour [accessed]; the clamp construction and its 2× rule are documented practice [accessed]; the specific scale anchors (320/1200 px, 1.25 ratio) are conventional starting points; the pairing used in the example follows [Font pairing](font-pairing.md) conventions.

## 7. Examples

**Example 1 — the layout-shift fix.** A marketing page's hero reflows when its display font arrives 1.2 s late (CLS penalty). Fix: `font-display: optional` for the display face plus a metric-adjusted fallback for the text face — the hero renders once, in the fallback if needed, and never shifts. The brand face returns on the next load from cache. [accessed]

**Example 2 — the 200% zoom audit.** A fluid scale with `clamp(1rem, 0.9rem + 0.5vw, 1.15rem)` has max/min = 1.15 — text can never double even when the user requests it. Rebuilt with the 2× rule (1rem → 2rem): the preferred expression still grows with the viewport, and scaling works. [accessed]

**Example 3 — the CJK subset.** A site self-hosts a full CJK face (>10,000 glyphs, multi-megabyte) and pages crawl on mobile. Fix: split the face by `unicode-range` subsets for the characters actually used (or use the hosted API's automatic subsetting), cutting the transfer dramatically. [accessed]

**Example 4 — the animation that reflows.** A hover effect animates `font-weight` 400→700 on card titles; every line reflows, jittering the grid. Fix: animate the `GRAD` axis via `font-variation-settings` with a CSS custom property — grade changes density without changing width, so no reflow — and only under `prefers-reduced-motion: no-preference`. [accessed]

**Example 5 — the px root.** A site sets `html { font-size: 14px; }` to shrink "dense" UI; every rem-based size scales down, and a user's browser preference of 20 px is silently ignored. Fix: keep the root at 100% and implement density by *choosing smaller rem steps*, not by breaking the unit system.

## 8. Common mistakes

- **px everywhere.** Sizes, leading and measure locked to px: user scaling and zoom break, and the measure stops being characters ([Typesetting](typesetting.md) 3.3).
- **vw-only fluid type.** `font-size: 4vw` scales to absurd sizes at extremes and ignores user settings; always clamp between rem bounds.
- **Missing spaces in `clamp()`** around `+`/`-` — an invalid declaration that silently falls back. [accessed]
- **`font-display: block` as a default.** Invisible text is the worst outcome for content; `swap`/`optional` serve almost every real case. [accessed]
- **Preloading every font.** Preload competes with critical resources and bypasses `unicode-range`; preload the one or two faces that matter. [accessed]
- **Shipping full character sets.** Unsubsetted files (especially CJK) dominate page weight; subset and use `unicode-range`. [accessed]
- **`font-variation-settings` as the primary control.** Redeclare-all-values semantics and bypassed ranges make it fragile; standard properties first, low-level for custom axes only. [accessed]
- **Unadjusted fallbacks.** Different metrics between primary and fallback fonts mean reflow on every load; use the metric descriptors. [accessed]
- **Synthesised styles.** Calling bold/italic styles the family lacks; browsers fake them. Declare real ranges or `font-synthesis: none` deliberately.
- **Duplicating fonts across origins.** The same face served twice from different hosts doubles downloads and cache misses; consolidate delivery.
- **Forgetting `lang`.** Hyphenation, screen readers and spell-check all depend on it.

## 9. Evaluation checklist

- [ ] Root font size in relative units; no px-based `html { font-size }`
- [ ] All type sizes rem-based; leading unitless; measure in `ch`
- [ ] Fluid expressions have correct `clamp(min, preferred, max)` form and spaced operators
- [ ] Every fluid step has max ≥ 2 × min (200% scaling reachable) [accessed]
- [ ] Relative order of steps survives at 320 px and at 1200 px
- [ ] `font-display` chosen per face role (swap for text, optional for display) [accessed]
- [ ] WOFF2 only; subsets generated; `unicode-range` used where split [accessed]
- [ ] Preload limited to critical faces; preconnect present for third-party origins [accessed]
- [ ] Fallback stack ends in the correct generic; metric overrides applied where shift matters [accessed]
- [ ] Registered axes via standard properties; `font-variation-settings` reserved for custom axes [accessed]
- [ ] Optical sizing left automatic unless overridden deliberately
- [ ] Synthesised bold/italic absent (real styles exist or synthesis disabled deliberately)
- [ ] `lang` set; text not rendered as images; muted tones still meet contrast requirements
- [ ] Axis animations respect `prefers-reduced-motion`

## 10. Related topics

- [Typography fundamentals](typography-fundamentals.md) — anatomy, variable-font concepts and the spacing triad
- [Typeface selection](typeface-selection.md) — licences and format choices that constrain delivery
- [Font pairing](font-pairing.md) — the multi-family loading strategy this file implements
- [Typographic hierarchy](typographic-hierarchy.md) — the scale this file makes fluid
- [Typesetting](typesetting.md) — measure, leading and wrapping controls expressed in CSS
- [Accessible typography](../accessibility/accessible-typography.md) — the full WCAG treatment this file implements
- [Frontend implementation](../ui-ux/frontend-implementation.md) — the wider front-end context (performance, tokens, components)
- [Colour theory](../colour/colour-theory.md) — contrast obligations interacting with text tones

## 11. References

- MDN Web Docs, "font-display" — descriptor values, block/swap/failure periods, example, browser availability. https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face/font-display [accessed 2026-11-23]
- MDN Web Docs, "clamp()" — resolution as `max(MIN, min(VAL, MAX))`, examples, operator-spacing requirement, WCAG 1.4.4 max ≥ 2 × min note, July 2020 baseline. https://developer.mozilla.org/en-US/docs/Web/CSS/clamp [accessed 2026-11-23]
- MDN Web Docs, "Variable fonts" (CSS guides) — registered axes and CSS mappings, `font-optical-sizing`, `font-variation-settings` caveats, `@font-face` ranges, custom-property workaround. https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Fonts/Variable_fonts [accessed 2026-11-23]
- MDN Web Docs, "size-adjust" (`@font-face` descriptors) — `size-adjust`, `ascent-override`, `descent-override`, `line-gap-override`; metric-compatible fallbacks and CLS rationale; September 2023 baseline; CSS Fonts Module Level 5. https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face/size-adjust [accessed 2026-11-23]
- MDN Web Docs, "text-wrap" — `balance` (heading use, 6-line Chromium / 10-line Firefox caps) and `pretty` (body copy, orphan avoidance); March 2024 baseline. https://developer.mozilla.org/en-US/docs/Web/CSS/text-wrap [accessed 2026-11-23]
- web.dev (Google), "Font best practices" — FOUT/FOIT framing, `font-display` period durations and the swap/optional pattern, subsetting and `unicode-range`, self-hosting trade-offs (Web Almanac), preload/preconnect guidance, WOFF2 compression (Bram Stein: "Use only WOFF2 and forget about everything else"). https://web.dev/articles/font-best-practices [accessed 2026-11-23]
- Google Fonts, *google/fonts* repository — licence organisation and redistribution/self-hosting context (with Fontsource packages). https://github.com/google/fonts [accessed 2026-11-23]
- Richard Fink / Steve Matteson et al. on web font formats and `unicode-range` subsetting practice — historical background to the subsetting workflow, summarised from general professional knowledge rather than fetched pages. [canonical]
- Section 3.3's worked table and section 5's stylesheet are synthesis of the [accessed] sources above; scale anchors and spacing values are conventional starting points.
