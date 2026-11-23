# Frontend Implementation

## 1. What is it?

Frontend implementation is the translation of design decisions into correct, maintainable CSS (with minimal HTML structure and JavaScript where needed): layout patterns that hold at every viewport, positioning that behaves predictably, design tokens expressed as custom properties, motion implemented with transitions and animations, and decorative detail built with pseudo-elements rather than extra markup. This file is the code-level companion to the strategy and component files in this domain — [UI fundamentals](ui-fundamentals.md) defines the components, [Responsive design](responsive-design.md) the strategy, [Interaction design](interaction-design.md) the motion budgets — and it defers general layout mechanics (grid systems, fluid layout theory) to [Grid systems](../layout/grid-systems.md) and [Responsive layouts](../layout/responsive-layouts.md).

Every code example here is syntactically correct modern CSS. The verified behaviours (from MDN: `gap`, `position: sticky`, `clamp()`, `prefers-reduced-motion`) are marked as such; anything that is professional convention rather than verified specification is labelled.

## 2. Why does it matter?

Implementation quality is the difference between a design that exists and a design that works. The same visual comp can be implemented responsively or brittlely; the same component library can be tokenised (one change propagates everywhere) or hardcoded (one change means fifty edits). For AI agents writing frontend code, the CSS layer is also where the most common quality defects live: layouts that break at untested widths, `z-index` wars, inaccessible focus states, animation that ignores reduced-motion users, and interfaces that are syntactically fine but visually generic.

Modern CSS is also powerful enough that most "need a framework/library" moments are unnecessary: flexbox, grid, custom properties, transitions and pseudo-elements cover the overwhelming majority of interface patterns. Knowing them precisely — not approximately — is what lets an implementation be minimal, fast and correct.

## 3. Core principles

### 3.1 Layout: choose the tool by the dimension

The foundational layout decision is one-dimensional versus two-dimensional:

| Need | Tool | Why |
|---|---|---|
| Content flows along one axis (toolbar, nav row, stacked card list, form) | Flexbox | Designed for one-dimensional distribution, with wrapping |
| Content must align in rows *and* columns simultaneously (page skeleton, galleries, tables of cards) | Grid | Designed for two-dimensional placement with named/repeated tracks |

#### Flexbox patterns

```css
/* Toolbar: items on one line, space between groups */
.toolbar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 1rem; /* verified: gap applies to flex containers; shorthand sets row-gap then column-gap */
}

/* Input with trailing button that never collapses */
.field-group { display: flex; gap: 0.5rem; }
.field-group input { flex: 1 1 auto; min-width: 0; } /* min-width: 0 lets the input shrink below its content box */

/* Centering an element in its parent */
.overlay { display: flex; align-items: center; justify-content: center; }

/* Wrapping card row: items take natural width and wrap */
.chip-row { display: flex; flex-wrap: wrap; gap: 0.5rem 0.75rem; }

/* Sidebar layout that stacks on narrow screens */
.sidebar-layout { display: flex; flex-wrap: wrap; gap: 2rem; }
.sidebar-layout > nav  { flex: 1 1 200px; }
.sidebar-layout > main { flex: 3 1 400px; }
```

The `gap` property is the modern replacement for margin hacks between flex/grid items: verified on MDN, it sets gaps ("gutters") between rows and columns on flex, grid and multi-column containers; with two values the first is `row-gap` and the second `column-gap`; unlike margins there is no gap before the first track or after the last, and percentage gaps resolve against the container's content box [accessed]. The classic flexbox gotchas: `flex: 1` expands but can shrink an input to zero width unless content is allowed to shrink (`min-width: 0`), and `margin: auto` on a flex item absorbs free space along the main axis (useful for pushing one item to the far end).

#### Grid patterns

```css
/* Page skeleton: header, sidebar+main, footer */
.page {
  display: grid;
  grid-template-columns: 240px minmax(0, 1fr); /* minmax(0, 1fr) prevents content forcing overflow */
  grid-template-rows: auto 1fr auto;
  grid-template-areas:
    "header header"
    "sidebar main"
    "footer footer";
  min-height: 100vh;
}
.page > header  { grid-area: header; }
.page > nav     { grid-area: sidebar; }
.page > main    { grid-area: main; }
.page > footer  { grid-area: footer; }

/* Responsive card grid: no media query needed */
.card-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(min(240px, 100%), 1fr));
  gap: 1.5rem;
}

/* Explicit placement with line names */
.layout {
  display: grid;
  grid-template-columns:
    [full-start] minmax(1rem, 1fr)
    [content-start] minmax(0, 72ch) [content-end]
    minmax(1rem, 1fr) [full-end];
}
.layout > article { grid-column: content; } /* spans content-start to content-end */
```

`repeat(auto-fill, minmax(min(240px, 100%), 1fr))` is the canonical responsive card grid: it fits as many ≥ 240 px tracks as the container allows and wraps the rest — the `min(…, 100%)` guard prevents overflow on narrower-than-240 px containers (pattern convention; underlying `repeat`/`minmax`/`auto-fill` mechanics in [Responsive layouts](../layout/responsive-layouts.md)). Prefer `grid-template-areas` when the layout reads as regions, line names when items should align to a shared measure (the `72ch` content column above is the typographic-measure pattern from [Web typography](../typography/web-typography.md)).

### 3.2 Positioning and the stacking context

`position` values in increasing departure from normal flow (verified comparison against MDN's reference [accessed]):

| Value | In flow? | Positioned relative to | Notes |
|---|---|---|---|
| `static` | Yes | — | Default; offsets ignored |
| `relative` | Yes | Its own normal position | Space is reserved; origin for absolute children |
| `absolute` | No | Nearest *positioned* ancestor | Removed from flow; will not scroll |
| `fixed` | No | Viewport | Stays put during scroll |
| `sticky` | Yes | Nearest scroll container + its containing block | Relative until a threshold, then fixed within its parent |

`position: sticky` — verified mechanics [accessed]: the element stays in flow and scrolls normally until the set threshold is crossed, then behaves as fixed *within its containing block*; it never leaves that containing block, so a sticky sidebar stops when its parent ends. Two requirements and one trap: at least one inset property (`top`, `right`, `bottom`, `left`) must be non-auto on the sticky axis or it behaves like plain `relative`; and it sticks to the nearest ancestor with a scrolling mechanism — `overflow: hidden` (not just `scroll`/`auto`) on an ancestor captures the sticky element and silently defeats viewport sticking. Sticky also always creates a stacking context.

```css
/* Sticky table header (component behaviour defined in UI fundamentals) */
.table th { position: sticky; top: 0; background: var(--color-surface); z-index: 2; }

/* Classic absolute-in-relative pattern: badge on a card */
.card { position: relative; }
.card .badge { position: absolute; top: 0.5rem; right: 0.5rem; }
```

**z-index discipline.** `z-index` only applies to positioned elements or flex/grid children, and only competes within the same stacking context — a child with `z-index: 9999` inside a stacking context at `z-index: 1` can never escape that context (this is why "z-index 99999 does nothing" happens; MDN's `position` reference documents that `fixed` and `sticky` always create stacking contexts [accessed]). The discipline that prevents wars: define a small, documented z-index scale as tokens (e.g. `--z-dropdown: 1000; --z-sticky: 1020; --z-modal: 1050; --z-toast: 1080;`) rather than ad-hoc integers, and keep stacking contexts shallow.

### 3.3 Custom properties (design tokens in code)

Custom properties are the CSS-native implementation of design tokens — the naming, semantics and governance of tokens are treated in [Design tokens](../design-systems/design-tokens.md); here is the code layer:

```css
:root {
  /* Primitive scales */
  --space-1: 0.25rem; --space-2: 0.5rem; --space-3: 1rem; --space-4: 2rem;
  --radius-s: 0.25rem; --radius-m: 0.5rem;

  /* Semantic tokens: components reference these, not the primitives */
  --color-surface: #ffffff;
  --color-ink: #1a1a1a;
  --color-accent: #0d47a1;
  --font-body: "Inter", system-ui, sans-serif;

  /* Semantic tokens may reference primitives */
  --button-padding: var(--space-2) var(--space-3);
}

/* Themed contexts override the semantic layer only */
@media (prefers-color-scheme: dark) {
  :root { --color-surface: #121212; --color-ink: #f5f5f5; }
}
[data-variant="compact"] { --button-padding: var(--space-1) var(--space-2); }

.button {
  padding: var(--button-padding);
  background: var(--color-accent);
  color: var(--color-surface);
  font-family: var(--font-body);
  border-radius: var(--radius-m);
}
```

The two-layer pattern (primitives + semantics) is what makes themes, density variants and rebrands cheap: components consume semantic names (`--color-surface`), and an override rewrites only the semantic layer. Custom properties also *cascade* and can be scoped to a component subtree, which pure preprocessor variables (Sass) cannot do — a token override on one card affects only that card. `var()` accepts fallbacks (`var(--color-accent, #0d47a1)`) for defensive library code.

### 3.4 Responsive CSS patterns

**Fluid type and spacing with `clamp()`** — verified: `clamp(MIN, VAL, MAX)` resolves as `max(MIN, min(VAL, MAX))`, so the preferred value applies only within the bounds [accessed]:

```css
h1 { font-size: clamp(1.75rem, 1rem + 3vw, 3.5rem); } /* min is exactly half of max: zoom-safe per MDN's WCAG 1.4.4 note */
html { font-size: clamp(1rem, 0.9rem + 0.25vw, 1.125rem); }
section { padding-block: clamp(1.5rem, 4vw, 4rem); }
```

The mixed-unit preferred value (`1rem + 3vw`) grows slower than raw `vw` and never drops below the rem floor — the standard fluid-type recipe (scaling rationale in [Responsive design](responsive-design.md); fluid layout mechanics in [Responsive layouts](../layout/responsive-layouts.md)).

**Container queries — the concept.** Media queries respond to the *viewport*; container queries respond to the *container* the component actually sits in, which is what component-based design needs: a card that widens its internal layout when its own column is wide, regardless of viewport. The pattern: mark a wrapper with `container-type: inline-size`, then write `@container (min-width: …)` rules for descendants. This changes responsiveness from page-level to component-level; the full mechanics, syntax details and browser support notes live in [Responsive layouts](../layout/responsive-layouts.md).

**Media query conventions.** Prefer `min-width` (mobile-first) so base styles are the simple case ([Responsive design](responsive-design.md)); query only the property you need (`prefers-color-scheme`, `prefers-reduced-motion`); never hardcode device widths — breakpoint values are design decisions.

### 3.5 Transitions and animations

Transitions interpolate property changes automatically (state-driven); keyframe animations run authored sequences (time-driven). Rules for correct, cheap motion: transition only compositing-friendly properties (`transform`, `opacity`) and layout-cheap ones (`color`, `background-color`); avoid animating `width`/`height`/`top`/`left` (they trigger layout on every frame — use `transform: scale()`/`translate()` instead); always specify the property list rather than the bare `all` keyword (prevents accidental animation of unrelated properties); and pair every transition with its reduced-motion variant.

```css
/* Component transition (budgets and purposes in Interaction design) */
.modal-panel {
  transition: transform 200ms ease-out, opacity 200ms ease-out;
  transform: translateY(8px);
  opacity: 0;
}
.modal-panel[data-open="true"] { transform: none; opacity: 1; }

/* Keyframe animation for entrance choreography */
@keyframes fade-up {
  from { opacity: 0; transform: translateY(12px); }
  to   { opacity: 1; transform: none; }
}
.list-item { animation: fade-up 300ms ease-out both; }
.list-item:nth-child(2) { animation-delay: 60ms; }
.list-item:nth-child(3) { animation-delay: 120ms; }

/* Verified pattern: honour the OS reduced-motion setting.
   Same specificity, later in source order, so it wins. */
@media (prefers-reduced-motion: reduce) {
  .modal-panel { transition: opacity 200ms ease-out; transform: none; }
  .list-item   { animation: none; }
}
@media (prefers-reduced-motion) { /* shorthand form, equivalent to (prefers-reduced-motion: reduce) [accessed] */
  * { scroll-behavior: auto !important; }
}
```

`prefers-reduced-motion: reduce` matches when the user has enabled their OS's reduce-motion setting (widely available since January 2020); MDN's guidance is to reduce or replace motion-based animation, keeping the variant at equal specificity but later in source order [accessed]. The standard recipe: fade-only transitions under reduce, `animation: none` for decorative keyframes, and `scroll-behavior: auto` so smooth-scrolling anchors stop swooping.

### 3.6 Pseudo-elements for decorative layers

`::before` and `::after` inject presentational children without extra markup; `::marker`, `::selection` and `::placeholder` style existing parts (content is required — often `content: ""` — and pseudo-elements cannot be selected by users, so they must never carry real information):

```css
/* Decorative underline accent on a heading */
.accent::after {
  content: "";
  display: block;
  width: 3rem; height: 4px;
  margin-top: 0.5rem;
  background: var(--color-accent);
}

/* Card overlay gradient: media at bottom, text over it */
.card-media { position: relative; }
.card-media::after {
  content: "";
  position: absolute;
  inset: 0;
  background: linear-gradient(to top, rgb(0 0 0 / 0.6), transparent 50%);
}

/* Tooltip built from data-attribute + pseudo-elements (no JS, no extra markup) */
[data-tip] { position: relative; }
[data-tip]:hover::after,
[data-tip]:focus-visible::after {
  content: attr(data-tip);
  position: absolute;
  bottom: calc(100% + 6px);
  left: 50%;
  transform: translateX(-50%);
  padding: 0.25rem 0.5rem;
  background: var(--color-ink);
  color: var(--color-surface);
  border-radius: var(--radius-s);
  white-space: nowrap;
}
```

Use pseudo-elements for what a user can see but not read as content: accent rules, gradients, badges, count annotations (`::before { content: attr(data-count); }`). Keep real text in real elements — screen readers and copy/paste ignore pseudo-element content.

### 3.7 Tailwind CSS: utility-first, token-integrated

Tailwind CSS inverts component CSS: instead of authoring semantic classes, you compose utilities directly in markup (`class="flex gap-2 rounded-lg bg-blue-600 px-4 py-2"`). When it helps: rapid composition with guaranteed consistency (utilities map to a fixed scale, so spacing stays rhythmic without discipline), no naming burden, dead-code elimination by construction (unused utilities are never generated), and low cognitive distance for small-to-medium component trees. When it hurts: long utility chains in markup become hard to read and hard to reuse — the standard remedy is extracting repeated chains into component classes; and teams lose the semantic layer unless they re-introduce it deliberately.

Token integration is the key discipline: Tailwind's theme layer — in v4, theme variables are CSS variables defined with the `@theme` directive, and the utilities the project can use are generated from them [search-verified] — maps design tokens (from [Design tokens](../design-systems/design-tokens.md)) to utility names, so `bg-brand-600` or `text-ink-secondary` reference the same single source of truth a plain-CSS implementation would via custom properties. The pattern to avoid is arbitrary values sprinkled through markup (`w-[347px]`, `text-[#3b82f6]`) — each one is an untokenised decision escaping the system. Tailwind versus hand-written CSS is a team-level, context-dependent choice, not a correctness question: both produce identical rendered results when disciplined.

## 4. How it works

A reliable implementation workflow:

1. **Tokens first.** Establish the custom-property layers (3.3) before components, so components never hardcode values.
2. **Structure, then layout.** Write semantic HTML (headings, landmarks, real buttons/inputs — accessibility attributes per [WCAG fundamentals](../accessibility/wcag-fundamentals.md)), then apply flex/grid per 3.1.
3. **States, then style.** Implement each component's state table (`:hover`, `:focus-visible`, `:active`, `:disabled`, data-attributes for async states — the state inventory is from [UI fundamentals](ui-fundamentals.md)).
4. **Responsive behaviour.** Fluid primitives (`clamp()`, flexible tracks) first; content-driven breakpoints only where the design breaks; container queries where components must adapt to their slot.
5. **Motion.** Transitions on state changes, keyframes for entrances, the `prefers-reduced-motion` variant alongside (3.5).
6. **Detail pass.** Pseudo-element decoration, elevation, spacing rhythm — the "avoiding generic" pass of section 5.
7. **Verify** at the viewport matrix and against the checklists of [Website visual QA](../evaluation/website-visual-qa.md).

## 5. Practical application

### 5.1 Avoiding generic-looking interfaces

Technically correct interfaces can still look like everyone else's — default framework components at default sizes on a default palette. The escape is not decoration but *decisions*, applied at four levels:

- **Elevation and depth.** Give the page a deliberate elevation language: one shadow recipe family, expressed as tokens (`--shadow-1: 0 1px 2px rgb(0 0 0 / 0.08); --shadow-2: 0 4px 12px rgb(0 0 0 / 0.12);`), used sparingly — elevation means "this layer is above that one", not decoration. Over-shadowed cards on grey backgrounds is the single most recognisable "generated" look.
- **Spacing rhythm.** Use one spacing scale and let sections breathe asymmetrically by intent: generous padding-block on hero and summary sections, tighter on dense data sections — rhythm read top-to-bottom, not uniform padding everywhere.
- **Type contrast.** Push the scale: a display weight and size clearly apart from body (ratio ≥ ~2× between display and body sizes), restrained line lengths, and one distinctive typographic voice ([Typeface selection](../typography/typeface-selection.md), [Typographic hierarchy](../typography/typographic-hierarchy.md)). Uniform mid-size type everywhere flattens any design into template-land.
- **Purposeful colour.** One accent, used where attention must go (primary action, key data), on a disciplined neutral field — versus the generic look of pastel gradients everywhere. Colour meaning per [Colour theory](../colour/colour-theory.md) and contrast per [Colour accessibility](../colour/colour-accessibility.md).

The test: hide the logo. Could this page pass as any company's? If yes, it has no decisions in it — apply the four levels until a point of view is visible, without breaking the conventions users rely on (heuristic 4, consistency and standards [accessed]).

### 5.2 A worked component: card with states and motion

```css
.card {
  container-type: inline-size;           /* container-query hook (concept; see Responsive layouts) */
  background: var(--color-surface);
  border-radius: var(--radius-m);
  box-shadow: var(--shadow-1);
  transition: box-shadow 150ms ease-out, transform 150ms ease-out;
}
.card:hover,
.card:focus-within { box-shadow: var(--shadow-2); transform: translateY(-2px); }
.card[data-loading="true"] { opacity: 0.6; pointer-events: none; }
@media (prefers-reduced-motion: reduce) {
  .card { transition: box-shadow 150ms ease-out; }
  .card:hover, .card:focus-within { transform: none; }
}
```

One component carrying: tokens (no hardcoded values), both pointer and focus affordance (`:focus-within` covers keyboard entry), an async state, motion with a reduced-motion variant, and a container-query hook.

## 6. Decision framework

1. **One axis or two?** Flexbox for one-dimensional flow, grid for two-dimensional alignment (3.1).
2. **In flow, out of flow, or sticky?** Prefer flow; use `absolute` for overlays on a positioned parent; `sticky` for in-scroll anchoring; `fixed` sparingly (viewports and stacking). Check ancestors' `overflow` before blaming sticky [accessed].
3. **Viewport media query or container query?** Page-level layout responds to the viewport; component-internal adaptation responds to the container.
4. **Transition or animation?** Transition state *changes*; animate *sequences*. Compositor-friendly properties only; always with a reduced-motion variant [accessed].
5. **Token or literal?** Any value used twice, or carrying meaning (colour, spacing, z-level, radius), becomes a token; literals are allowed only inside throwaway prototypes.
6. **Utility class or semantic class?** Team-scale decision (3.7) — but whichever is chosen, arbitrary one-off values stay out.
7. **Does the result have a point of view?** Run the hide-the-logo test (5.1) before declaring done.

## 7. Examples

**Sticky sidebar with a stop.** `position: sticky; top: 1rem;` on an `aside` inside a taller grid row: the aside scrolls with the page, pins 1 rem from the viewport top, and releases when its parent's bottom edge passes — no JavaScript. Failure mode to check: an ancestor with `overflow: hidden` (often a wrapper div added for another fix) captures the stickiness; the repair is removing the overflow or restructuring the wrapper [accessed].

**Token-driven dark mode.** Components referencing `var(--color-surface)`/`var(--color-ink)` need zero changes for dark mode: an `@media (prefers-color-scheme: dark)` block (or a `[data-theme="dark"]` attribute for a user-controlled switch) redefines the semantic layer only (3.3). Contrast of the redefined pairs must still be verified ([Colour accessibility](../colour/colour-accessibility.md)).

**The responsive card grid, end to end.** `grid-template-columns: repeat(auto-fill, minmax(min(240px, 100%), 1fr)); gap: 1.5rem;` gives three columns at desktop, two at tablet, one on phones — with no media query and no content orphaned, because the grid tracks, not breakpoints, do the adapting. Each card internally adapts by container query when its own slot is narrow (3.4 concept; mechanics in [Responsive layouts](../layout/responsive-layouts.md)).

**The escaped-modal pattern.** Open: panel transitions from `opacity: 0; transform: translateY(8px)` to visible (200 ms ease-out); close reverses; under `prefers-reduced-motion: reduce` the transform is dropped and only opacity animates (3.5). Focus moves in on open and returns to the trigger on close — the behavioural contract from [UI fundamentals](ui-fundamentals.md) implemented in a handful of lines.

## 8. Common mistakes

- **Margin-based gutters.** Negative-margin hacks or per-child `margin-right` rules instead of `gap`; every layout change re-touches every child. `gap` applies to flex, grid and multi-column containers [accessed].
- **Sticky that silently fails.** Missing inset (`top: 0` forgotten) or an ancestor's `overflow: hidden` capturing the scroll container; the element then behaves like `relative` or never sticks [accessed].
- **z-index arms race.** Escalating integers instead of a token scale, and confusion about stacking contexts (a `transform`ed or `sticky` parent confines its children's z-order [accessed]).
- **Hardcoded values.** Colours, spacings and sizes inline in components; the theme change then requires a search-and-replace audit instead of a one-line override.
- **Animating layout properties.** Transitioning `width`/`height`/`top` causes per-frame layout and jank; transition `transform`/`opacity`.
- **`transition: all`.** Accidentally animates unrelated properties (including layout ones); list properties explicitly.
- **No reduced-motion variant.** Shipping motion without the `prefers-reduced-motion` block excludes users with vestibular disorders [accessed].
- **Removing focus outlines.** Deleting `:focus-visible` styling for aesthetics strands keyboard users; style it, never remove it (WCAG 2.4.7 [canonical]).
- **Pseudo-elements carrying content.** Real text inside `::before`/`::after` is invisible to assistive technology and unselectable; keep meaning in real elements.
- **Arbitrary Tailwind values everywhere.** `w-[347px]`-style escapes put untokenised decisions in markup and defeat the scale the framework exists to enforce (3.7).
- **Media-query-only thinking.** Adapting every component to the viewport instead of letting containers adapt themselves — the fit between component and slot breaks whenever the slot size changes without the viewport changing.

## 9. Evaluation checklist

- Layout tools chosen by dimension: flex for one axis, grid for two; `gap` used for gutters, not margins.
- Every sticky element: inset set on the sticky axis, no `overflow` ancestor defeating it, release behaviour at parent's end verified [accessed].
- A documented z-index scale exists; no ad-hoc high integers; stacking contexts intentional.
- Semantic token layer defined; components reference tokens, not literals; theme/density overrides touch only the semantic layer.
- Fluid sizing via `clamp()` with min ≤ preferred ≤ max verified; type maxima ≥ 2× minima for zoom safety [accessed].
- All transitions list properties explicitly; layout properties not animated; durations within the budgets of [Interaction design](interaction-design.md).
- `prefers-reduced-motion` variant present beside every motion pattern [accessed].
- Pseudo-elements used for decoration only; no real content hidden in `::before`/`::after`.
- Tailwind (if used): theme-configured tokens; no arbitrary-value escapes in production markup.
- Focus styles visible and styled via `:focus-visible`; hover has keyboard/touch equivalents.
- The hide-the-logo test (5.1) passes: elevation, spacing rhythm, type contrast and purposeful colour are deliberate decisions, not defaults.

## 10. Related topics

- [UI fundamentals](ui-fundamentals.md) — the component contracts these patterns implement
- [Responsive design](responsive-design.md) — the strategy behind the responsive patterns here
- [Responsive layouts](../layout/responsive-layouts.md) — fluid layout and container-query mechanics in depth
- [Grid systems](../layout/grid-systems.md) — layout vocabulary and page-structure theory
- [Interaction design](interaction-design.md) — motion purpose, durations and timing bands
- [Design tokens](../design-systems/design-tokens.md) — token naming, semantics and governance above the code layer
- [WCAG fundamentals](../accessibility/wcag-fundamentals.md) — the accessibility requirements behind focus, contrast and motion rules
- [Colour theory](../colour/colour-theory.md) / [Colour accessibility](../colour/colour-accessibility.md) — palette decisions and contrast verification
- [Web typography](../typography/web-typography.md) — type implementation details
- [Spacing and proportion](../layout/spacing-and-proportion.md) — the scale systems the spacing tokens encode
- [Website visual QA](../evaluation/website-visual-qa.md) — systematic post-implementation verification

## 11. References

- MDN Web Docs, CSS `gap`, https://developer.mozilla.org/en-US/docs/Web/CSS/gap [accessed 2026-11-23] — flex/grid/multi-column gutters, row-gap/column-gap shorthand order, percentage resolution, availability since October 2017
- MDN Web Docs, CSS `position`, https://developer.mozilla.org/en-US/docs/Web/CSS/position [accessed 2026-11-23] — sticky requirements and `overflow` capture, stacking contexts, value comparison
- MDN Web Docs, CSS `clamp()`, https://developer.mozilla.org/en-US/docs/Web/CSS/clamp [accessed 2026-11-23] — resolution as `max(MIN, min(VAL, MAX))`, fluid typography, WCAG 1.4.4 zoom note
- MDN Web Docs, `prefers-reduced-motion`, https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-reduced-motion [accessed 2026-11-23] — values, vestibular rationale, availability since January 2020, OS settings
- Ethan Marcotte, *Responsive Web Design*, A Book Apart, 2011 [canonical]
- Tailwind CSS, "Theme variables", https://tailwindcss.com/docs/theme and "Styling with utility classes", https://tailwindcss.com/docs/styling-with-utility-classes [search-verified 2026-11-23] — utilities driven by theme variables (CSS variables defined with the `@theme` directive in v4), mapping tokens to utility names
- W3C, WCAG 2.2 [canonical] — focus visible 2.4.7, resize text 1.4.4
- Dan Saffer, *Microinteractions*, O'Reilly, 2013 [canonical]
- Duration and easing conventions in 3.5 are conventional starting points from platform style-guide practice; verify per project
