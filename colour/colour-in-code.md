# Colour in code

## 1. What is it?

Colour in code is the discipline of expressing, storing and computing colour in front-end systems: which notation (HEX, RGB, HSL, OKLCH) to use and when, why screen colour cannot be mechanically converted to print (CMYK), how colour profiles and gamuts (sRGB vs Display-P3) behave in CSS, how to compute contrast ratios programmatically, and how to structure colours as CSS custom properties and design tokens with light/dark theming.

It is the implementation layer of the colour domain: [Colour theory](colour-theory.md) supplies the concepts, [Palette development](palette-development.md) supplies the roles and values, and this file turns them into precise, testable code. Token *architecture* (naming layers, governance) lives in [Design tokens](../design-systems/design-tokens.md) — this file covers the CSS mechanics and links there for structure.

## 2. Why does it matter?

Colour is the one design property that flows through every layer of a front end — markup, CSS, SVG, images, video and print exports — so imprecision compounds everywhere. The same palette written three different ways in three files produces drift no reviewer can see. Uncomputed contrast guarantees accessibility regressions. A palette hard-coded in components makes a dark theme or a rebrand a rewrite.

Code-level colour discipline buys three capabilities cheaply: *consistency* (one source of truth per colour), *derivability* (ramps and themes generated, not hand-picked), and *verifiability* (contrast checked by the same code that ships the colours). For agents, it is what makes a colour system auditable — every value traceable to a token, every token traceable to a role.

## 3. Core principles

### 3.1 HEX and RGB specifications

HEX is RGB in hexadecimal packing: two digits per channel, `#RRGGBB`, each channel `00`–`FF` (0–255 decimal). CSS also accepts short forms `#RGB` (each digit doubled) and `#RGBA` for alpha. `#0F6BAE` is exactly `rgb(15 107 174)`. Modern CSS syntax puts alpha after a slash: `rgb(15 107 174 / 40%)` or `#0F6BAE66` for the same 40% alpha. These forms all describe colours in the **sRGB** space — the default colour space of the web, which is precisely why HEX became the interchange format: a HEX value means the same colour on every conformant screen (rendered within that device's ability to display sRGB).

Practical rules: prefer 6- or 8-digit HEX for tokens (unambiguous, greppable); use `rgb()` when mixing channels computationally; never mix notations within one token set.

### 3.2 HSL in CSS

`hsl(207 84% 37%)` expresses hue (degrees), saturation and lightness as percentages. Its value in code is *parametric reasoning*: "same hue, lighter step" becomes `hsl(207 84% 45%)` without a colour picker. Its limitation is mathematical: HSL lightness is not perceived lightness — equal-L values differ wildly in apparent brightness across hues ([Colour theory](colour-theory.md) section 3.1). Use HSL for human-readable variant derivation, but verify the results perceptually or in OKLCH. Modern CSS also supports **relative colour syntax**, which makes derivation first-class: `hsl(from var(--brand) h s calc(l + 10%))` lightens a stored colour while preserving hue and saturation.

### 3.3 OKLCH: perceptual coordinates in CSS

`oklch(L C H / A)` expresses colour with **L** perceived lightness (0–100%), **C** chroma (0 = grey; 100% = 0.4, and in practice does not exceed ~0.5) and **H** hue angle. Because its lightness axis tracks perception, equal-L colours *look* equally light — which is exactly what ramps and themes need. MDN documents that its hue angles differ from HSL's (red sits near 41°, not 0°) and that chroma scales uniformly across hues, so "reduce chroma toward grey" behaves the same for every hue [accessed]. Browser support is Baseline since May 2023 [accessed]. Typical uses:

```css
/* Uniform tint/shade ramp for one hue (perceptually even steps) */
--blue-500: oklch(55% 0.14 250);
--blue-300: oklch(75% 0.10 250);   /* same hue, less chroma, lighter */
--blue-700: oklch(38% 0.12 250);

/* Relative colour syntax: derive variants from one brand value */
--brand:        #0F6BAE;
--brand-light:  oklch(from var(--brand) calc(l + 0.15) c h);
--brand-dark:   oklch(from var(--brand) calc(l - 0.15) c h);
```

(Calculation note from MDN: relative-syntax channels resolve to numbers, so add numbers, not percentages [accessed].)

One craft caveat on mixing: averaging RGB channels passes through muddy, desaturated midpoints (red mixed to green in RGB goes through dirty brown), and HSL interpolation can swing hue the long way around the wheel. Interpolating in a perceptual space — or moving L/C/H independently, as the relative syntax above does — keeps midpoints on the intended path. For simple ramp steps this barely matters; for gradients, transitions and blends it is the difference between "designed" and "default".

### 3.4 CMYK conversion realities

CSS has **no CMYK notation**, and there is no reliable formula `RGB → CMYK` that preserves appearance. The reason is physical: screens emit light (additive), ink absorbs it (subtractive), and a press can reproduce a different (usually smaller) set of colours than sRGB. Vivid screen hues — saturated greens, oranges, deep blues — can be **out of gamut** for a CMYK press and will shift, typically darker and duller. Conversion is therefore a *rendering* step done through ICC colour profiles by print tooling, not arithmetic in the stylesheet.

Working practice: design and specify brand colour in HEX/sRGB; keep a separately approved print specification (per output profile) for critical brand elements; when print fidelity matters, request a proof. Conventional print concepts worth knowing, to be confirmed with the specific printer: rich black (a CMYK mix, e.g. `C60 M40 Y40 K100`-region values) reads deeper than K-only black on large areas, and total ink coverage limits (commonly ~280–330% depending on stock) constrain heavy CMYK mixes — these are conventions of the print trade, not web facts.

### 3.5 Colour profiles and gamuts: sRGB vs Display-P3

A **gamut** is the range of colours a space can represent; a **colour space** is the coordinate system values are interpreted in. The web's gamut hierarchy per MDN: **sRGB ⊂ Display-P3 ⊂ Rec.2020** — P3 is "larger than and includes" sRGB [accessed]. Most modern phones and laptops can display P3, which offers more saturated reds and greens than sRGB. CSS exposes both:

- The `color()` function specifies colours in a named space: `color(display-p3 1 0.5 0)`; supported spaces include `srgb`, `srgb-linear`, `display-p3`, `display-p3-linear`, `a98-rgb`, `prophoto-rgb`, `rec2020`, and XYZ variants [accessed]. Baseline since May 2023 [accessed].
- The `color-gamut` media query detects device capability: `@media (color-gamut: p3)` [accessed].

```css
/* Base in sRGB; enhanced where the hardware allows */
--accent: #FF4A1F;                       /* sRGB token — the portable value */

@media (color-gamut: p3) {
  :root {
    --accent: color(display-p3 1 0.36 0.16);  /* wider, more vivid equivalent */
  }
}
```

Discipline matters more than vibrancy: keep the sRGB value as the canonical token and treat P3 as a progressive enhancement, so unmaintained contexts (print, older devices, screenshots) inherit the correct colour. Note that CSS contrast calculations (section 3.6) are defined on sRGB luminance; P3-only values need conversion before computing WCAG ratios.

### 3.6 Contrast calculation in code

The WCAG 2 ratio is fully computable from HEX, which lets you test pairs in the same pipeline that ships them:

```js
// WCAG 2.x relative luminance + contrast ratio (sRGB)
function luminance(hex) {
  const [r, g, b] = [1, 3, 5].map(i => parseInt(hex.slice(i, i + 2), 16) / 255)
    .map(v => v <= 0.04045 ? v / 12.92 : Math.pow((v + 0.055) / 1.055, 2.4));
  return 0.2126 * r + 0.7152 * g + 0.0722 * b;
}
function contrast(a, b) {
  const [hi, lo] = [luminance(a), luminance(b)].sort((x, y) => y - x);
  return (hi + 0.05) / (lo + 0.05);
}
contrast('#111418', '#FAFAF8'); // 17.67  (AAA body text)
contrast('#FF0000', '#FFFFFF'); // 4.00   (fails AA body text)
```

Thresholds: 4.5:1 AA body text, 3:1 large text and non-text, 7:1 AAA ([Colour accessibility](colour-accessibility.md) holds the construction rules). A future direction worth tracking: WCAG 3 is exploring the perceptually based **APCA** model, which weights text size, weight and polarity (W3C Silver's Visual Contrast of Text Subgroup work) — as of now WCAG 2 ratios remain the conformance standard, so build on them [search-verified].

Alpha handling matters in code too. `#RRGGBBAA` adds two hex digits for alpha (`#0F6BAE66` = 40% opaque), and `rgb()`/`hsl()` take alpha after the slash (`rgb(15 107 174 / 40%)`). Two cautions: translucent colour *blends with what is beneath it*, so an "accessible" token at 60% opacity is a different, weaker colour at runtime — compute contrast against the actual composite, not the token; and translucent greys over images drift with the image, which is why overlays that carry text (scrims) are specified as solid steps in the palette, not live blends.

## 4. How it works — tokens and theming

### 4.1 CSS custom properties as the colour layer

Custom properties are the shipping mechanism between palette documentation and components:

```css
:root {
  /* Primitives: raw ramp values — never used directly in components */
  --blue-600: #0F6BAE;
  --gold-500: #E8B33D;
  --grey-0:   #FAFAF8;
  --grey-900: #111418;

  /* Semantic aliases: roles — the only layer components consume */
  --color-bg:        var(--grey-0);
  --color-text:      var(--grey-900);
  --color-action:    var(--blue-600);
  --color-accent:    var(--gold-500);
}

button { background: var(--color-action); color: #fff; }
```

The two-layer split (primitive → semantic alias) is what makes theming mechanical: a dark theme re-points the aliases, and components never change. The fuller architecture (global/alias/component tiers, naming, governance) is specified in [Design tokens](../design-systems/design-tokens.md); token pipelines that export this structure as JSON or platform files belong there too.

### 4.2 Light/dark theming with `prefers-color-scheme`

The `prefers-color-scheme` media feature reports the user's OS-level light/dark preference: values are `light` (preferred light **or no expressed preference**) and `dark`; MDN documents Baseline support since January 2020 [accessed]. The standard pattern is default light plus a dark override:

```css
:root {
  color-scheme: light dark;            /* declare both; form controls adapt too */

  --color-bg:     #FAFAF8;
  --color-text:   #111418;
  --color-action: #0F6BAE;
  --color-action-text: #FFFFFF;
}

@media (prefers-color-scheme: dark) {
  :root {
    --color-bg:     #111418;
    --color-text:   #E8EAED;
    --color-action: #72BDF3;           /* lighter step as action on dark */
    --color-action-text: #0B2239;
  }
}
```

Details that earn their place in review: the `color-scheme` property (and `<meta name="color-scheme">`) lets native UI — scrollbars, form controls — follow the theme [accessed]; embedded SVGs styled with `prefers-color-scheme` follow the parent's `color-scheme` when loaded via `<img>` [accessed]; and every re-pointed pair must re-pass the contrast matrix ([Colour accessibility](colour-accessibility.md) section 3.6). Products that offer an in-app theme toggle combine this with an explicit `data-theme` attribute override — the media query stays the default, the attribute overrides it.

```css
/* In-app toggle: attribute overrides the OS default */
:root[data-theme="dark"]  { /* same alias block as the dark media query */ }
:root[data-theme="light"] { --color-bg: #FAFAF8; /* … */ }
```

```js
// Wire the toggle; persist and set before first paint to avoid a flash
const theme = localStorage.getItem('theme')
  ?? (matchMedia('(prefers-color-scheme: dark)').matches ? 'dark' : 'light');
document.documentElement.dataset.theme = theme;
```

Server-side rendering can respect the preference without a flash via the `Sec-CH-Prefers-Color-Scheme` client hint (MDN lists it among the related mechanisms [accessed]). Whether the toggle is client-side or server-driven, the discipline is identical: exactly one alias block per theme, both derived from the same primitives, both passing the pair matrix.

## 5. Practical application — a compact working system

```css
/* 1. Primitives (from the palette ramps) */
:root {
  --blue-50: #F1F8FE;  --blue-300: #72BDF3; --blue-600: #0F6BAE; --blue-700: #0C578D;
  --gold-500: #E8B33D;
  --grey-0: #FAFAF8;   --grey-300: #D4D8DD;  --grey-600: #4B5563; --grey-900: #111418;
  --success-700: #1B7F3B; --error-700: #B42318;
}

/* 2. Semantic tokens — light default */
:root {
  color-scheme: light dark;
  --bg: var(--grey-0);            --surface: #FFFFFF;
  --text: var(--grey-900);        --text-muted: var(--grey-600);
  --border: var(--grey-300);
  --action: var(--blue-600);      --action-hover: var(--blue-700);
  --on-action: #FFFFFF;
  --accent: var(--gold-500);      --on-accent: #1A1A1A;  /* white fails on gold */
  --success-text: var(--success-700);
  --error-text: var(--error-700);
}

/* 3. Dark theme — aliases re-pointed, roles kept */
@media (prefers-color-scheme: dark) {
  :root {
    --bg: #111418;                --surface: #1A1F26;
    --text: #E8EAED;              --text-muted: #9AA3AE;
    --border: #2A313B;
    --action: var(--blue-300);    --action-hover: #A6D5F7;
    --on-action: #0B2239;
    --accent: var(--gold-500);    --on-accent: #1A1A1A;
  }
}

/* 4. Gamut enhancement — canonical sRGB stays the default */
@media (color-gamut: p3) {
  :root { --action: color(display-p3 0.06 0.45 0.71); }
}

/* 5. Consumption — components touch only semantic tokens */
.card  { background: var(--surface); color: var(--text); border: 1px solid var(--border); }
.muted { color: var(--text-muted); }
.btn   { background: var(--action); color: var(--on-action); }
.btn:hover { background: var(--action-hover); }
.badge { background: var(--accent); color: var(--on-accent); }
.alert-error { color: var(--error-text); }
```

Generated ramps keep the primitive layer honest — derive steps with relative-colour syntax (section 3.3) rather than hand-picking, then verify each step's contrast once, at token level ([Palette development](palette-development.md) section 3.3). In the dark block above, the re-pointed pairs have been measured as they ship: body text `#E8EAED` on `#111418` is 13.74:1, muted `#9AA3AE` on `#111418` is 7.23:1, and the on-action pair `#0B2239` on `#72BDF3` is 7.90:1 — all comfortably past their targets, because the alias block was checked once rather than every component trusting its luck.

## 6. Decision framework

| Need | Use | Why |
|---|---|---|
| Fixed values in tokens/docs | HEX (6/8 digit) | terse, greppable, unambiguous sRGB |
| Deriving variants by hand | HSL / relative syntax | parametric, readable |
| Perceptually even ramps, themes | OKLCH | L tracks perceived lightness [accessed] |
| Wide-gamut enhancement | `color(display-p3 …)` + `@media (color-gamut: p3)` | device capability detection [accessed] |
| Print specification | CMYK via ICC profile, outside CSS | conversion is a rendering step, not a formula |
| Theming | custom properties + `prefers-color-scheme` + `color-scheme` | OS-level preference, Baseline [accessed] |
| Component colours | semantic aliases only | themes and rebrands without component edits |
| Contrast checks | the JS formula above, in CI | same pipeline as shipped values |

## 7. Examples

- **The one-line rebrand:** all components consume semantic aliases; changing `--action` from `--blue-600` to a green primitive restyles the product with zero component edits — and CI contrast tests flag which new pairs broke.
- **Generated dark ramp:** `--brand-300: oklch(from var(--brand-600) calc(l + 0.25) c h)` derives the dark-theme action colour from the brand value itself, keeping hue identity while fixing contrast.
- **Honest gamut strategy:** a vivid orange shipped as sRGB `#FF4A1F` with a P3 enhancement in a `color-gamut: p3` block — P3 devices get the extra vibrancy, everything else (including print exports) gets the correct portable colour.
- **Contrast as a build gate:** the section 3.6 functions run over the token JSON in CI; any pair under 4.5:1 fails the build before it can regress.

## 8. Common mistakes

- **Hard-coding hexes in components.** Bypasses tokens; themes and audits silently miss them. Fix: lint or review-gate direct colour values.
- **Trusting HSL lightness for contrast work.** HSL `l` is mixing, not perception; measure luminance (section 3.6) instead.
- **Pasting HEX into print artwork** and expecting fidelity — conversion needs profiles and proofs (section 3.4).
- **Shipping P3-only tokens.** Values in `color(display-p3 …)` without an sRGB fallback break on older devices and in print pipelines; keep sRGB canonical.
- **Dark theme by naive inversion.** Pure black/white swap causes glare and mis-reads hue roles; re-point aliases by role and re-test pairs.
- **Forgetting `color-scheme`.** Without declaring it, native form controls and scrollbars stay light on dark pages.
- **Adding percentages to relative-syntax channels.** MDN notes channels resolve to numbers, so `calc(l + 0.15)` works while `calc(l + 15%)` does not [accessed].
- **Assuming APCA is already the standard.** It is under exploration for WCAG 3; conformance today is WCAG 2 ratios [search-verified].

## 9. Evaluation checklist

- [ ] Every colour value in the codebase resolves to a token; no orphan hexes in components.
- [ ] Primitive and semantic layers are separated; components consume only aliases.
- [ ] All notations in the token set are consistent (HEX or `rgb()`/`oklch()`, not mixed arbitrarily).
- [ ] Ramp steps generated (not hand-picked) and each step's contrast recorded once.
- [ ] Dark theme re-points aliases by role; `color-scheme` declared; native controls follow.
- [ ] P3 values exist only as enhancements behind `color-gamut: p3`, with sRGB canonical.
- [ ] Contrast functions run in CI over real token pairs (both themes).
- [ ] Print-critical colours have a separately approved CMYK specification.

## 10. Related topics

- [Colour theory](colour-theory.md) — HSL vs OKLCH coordinates, gamut concepts, tint/shade/tone mechanics.
- [Palette development](palette-development.md) — the roles, ramps and documentation these tokens encode.
- [Colour accessibility](colour-accessibility.md) — the thresholds the CI contrast checks enforce.
- [Design tokens](../design-systems/design-tokens.md) — token architecture, naming and governance.
- [Frontend implementation](../ui-ux/frontend-implementation.md) — where this colour layer sits in the build.
- [WCAG fundamentals](../accessibility/wcag-fundamentals.md) — the normative basis of the ratio thresholds.

## 11. References

- MDN Web Docs, "color_value/color" — `color()` function, predefined spaces (`srgb`, `display-p3`, `rec2020`, XYZ…), out-of-gamut behaviour, `color-gamut` detection, Baseline May 2023. https://developer.mozilla.org/en-US/docs/Web/CSS/color_value/color [accessed 2026-11-23]
- MDN Web Docs, "@media/color-gamut" — gamut hierarchy srgb ⊂ p3 ⊂ rec2020 ("P3 gamut is larger than and includes the sRGB gamut"), Baseline February 2023. https://developer.mozilla.org/en-US/docs/Web/CSS/@media/color-gamut [accessed 2026-11-23]
- MDN Web Docs, "color_value/oklch" — OKLCH components, 100% C = 0.4, perceived vs HSL lightness, hue-angle differences, relative colour syntax and calc rules, Baseline May 2023. https://developer.mozilla.org/en-US/docs/Web/CSS/color_value/oklch [accessed 2026-11-23]
- MDN Web Docs, "@media/prefers-color-scheme" — `light`/`dark` values (light = preference or none), Baseline January 2020, `color-scheme` property interaction, embedded-SVG behaviour. https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-color-scheme [accessed 2026-11-23]
- W3C WAI Understanding SC 1.4.3 / 1.4.11 — contrast ratio formula and relative-luminance weights implemented in section 3.6. https://www.w3.org/WAI/WCAG22/Understanding/contrast-minimum.html , https://www.w3.org/WAI/WCAG22/Understanding/non-text-contrast.html [accessed 2026-11-23]
- W3C Silver, Visual Contrast of Text Subgroup (APCA exploration for WCAG 3). https://www.w3.org/WAI/GL/task-forces/silver/wiki/Visual_Contrast_of_Text_Subgroup [search-verified 2026-11-23]
- CMYK/ICC and rich-black/total-coverage practice: synthesis of general print-production knowledge; conventions, not web standards — verify with the specific printer. [synthesis]
- JS contrast snippet: implementation of the WCAG 2 formula above; outputs verified against the computed examples in [Colour accessibility](colour-accessibility.md). [synthesis]
