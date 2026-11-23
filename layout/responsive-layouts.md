# Responsive layouts

A responsive layout is one that keeps its grid, hierarchy and readability intact across an unknown range of viewport and container sizes. This file covers the *mechanics*: how fluid grids are built with CSS Grid (`fr`, `minmax()`, `repeat()`, `auto-fill`/`auto-fit`), how container queries let components adapt to their own space, how flexible gutters work, how to choose breakpoints from content rather than devices, and how images and media behave inside grids. The *product-level strategy* — mobile-first thinking, content prioritisation, navigation patterns, touch targets — lives in [Responsive design](../ui-ux/responsive-design.md); link there rather than duplicating it. Grid structure and spacing scales are defined in [Grid systems](grid-systems.md) and [Spacing and proportion](spacing-and-proportion.md).

## 1. What is it?

Responsive layout is the set of techniques that lets one layout serve many screen sizes without separate designs. At the layout level it rests on three behaviours working together: **fluidity** (tracks and spacing scale continuously with available space), **reflow** (at certain points the structure re-arranges — columns collapse, zones re-order), and **component adaptivity** (a card or widget adjusts to the space it actually receives, not the space the page designer assumed). Since Ethan Marcotte's formulation of responsive web design — fluid grids, flexible images and media queries — the industry has moved from viewport-only adaptation toward intrinsic layout: components that size and arrange themselves from their content and container [canonical].

The unit of adaptation has also shifted. Media queries ask "how wide is the viewport?"; container queries ask "how wide is the box this component landed in?" (syntax verified on MDN [accessed]). A responsive grid system today is therefore layered: a fluid page grid, content-driven breakpoints between structural arrangements, and container-aware components inside the grid.

## 2. Why does it matter?

An unknown viewer, device or embedding context is the normal case, not the exception. A fixed-width layout built for a 1440 px design file fails on the phone, the half-screen desktop window and the sidebar embed — all real contexts. The costs of getting responsive mechanics wrong are concrete: horizontal scrolling (the most reliable signal of a broken page), text at unreadable measure, grids that collapse to one column far too early or far too late, and components that look right in the design file but wrong wherever they are reused.

For an agent building or evaluating layouts, responsive behaviour is also the cheapest quality check available: resizing the viewport exercises more layout logic than any other single test. And because this library's core use case extends a fixed event logo into a full brand kit, responsive mechanics decide whether the same brand grid can serve the poster's proportions on a story-sized canvas, a desktop landing page and a phone — the mapping exercise in [Grid systems](grid-systems.md) §7.1 depends on this file.

## 3. Core principles

### 3.1 Fluid before breakpoints

The first line of defence is continuous scaling, so that breakpoints are only needed where structure must change. The tools, in increasing order of flexibility:

- **`fr` tracks** distribute free space proportionally: `grid-template-columns: 1fr 3fr` gives one third / two thirds of the space *after* fixed tracks and gutters are deducted (MDN [accessed]). `fr` is the default unit of a fluid grid; percentages largely duplicate what `fr` does with more arithmetic.
- **`minmax(min, max)`** gives a track a floor and ceiling: `minmax(200px, 1fr)` means "never narrower than 200 px, otherwise share free space" (MDN [accessed]: `fr` is valid only as *max*; if max < min, max is ignored and the track is fixed at min).
- **Fluid type and spacing** via `clamp(min, preferred, max)` and viewport/container units keep rhythm scaling between breakpoints, as used in [Spacing and proportion](spacing-and-proportion.md) §5.

The design consequence: express as much of the layout as possible in proportional units, and reserve media queries for *structural* changes (column count, zone re-mapping, navigation form).

### 3.2 Breakpoints: content-driven, not device-driven

A breakpoint is where the layout must change structure. The authoritative guidance from web.dev is to choose them from the content: "Don't define breakpoints based on device classes, or any product, brand name, or operating system" — instead "let the content determine how its layout changes to fit the container", by starting with a small viewport and widening until the layout breaks, then adding a query at that width [accessed]. The method matters more than the numbers: device tables date quickly (new phones, foldables, half-screen desktop windows), while a content-driven breakpoint survives new hardware by construction.

That said, projects still need starting values, and frameworks converge on similar conventions. The table below mixes the verified web.dev example values with common framework conventions — treat the convention rows as "conventional starting point — verify against the current framework or design-system documentation", not as standards:

| Width | Status | Typical structural change |
| --- | --- | --- |
| ~360 px | web.dev example (minor adjustment) | Type scale step; ensure no horizontal scroll |
| ~480–640 px | common convention (conventional) | Cards 2-up → 1-up; stacked zones |
| ~600 px | web.dev example (major breakpoint) | Single column → two-zone layout |
| ~768–820 px | common convention (conventional) | Navigation gains horizontal form; 2-col card grid |
| ~1024 px | common convention (conventional) | Full 12-column grid engages; side navigation |
| ~1200–1440 px | common convention (conventional) | Max content width reached; grid stops growing |

Two content-driven rules worth internalising: add a breakpoint when a *text block* grows past a comfortable measure (web.dev's worked example adds a breakpoint whenever a text block exceeds roughly the target line length — the 45–75 character measure guidance is covered in [Web typography](../typography/web-typography.md)); and never drop content at small sizes — web.dev's caution is explicit: "Don't hide content just because you can't fit it on the screen" [accessed].

### 3.3 Page queries vs container queries

Media queries respond to the viewport; container queries respond to the component's actual container. The distinction changes component design fundamentally: a card styled with container queries adapts wherever it is placed — a wide main column, a narrow sidebar, a dashboard tile — without knowing its destination (the benefit MDN states for container queries [accessed]).

The verified mechanism (MDN [accessed]):

1. Declare a containment context on the parent: `container-type: inline-size` (queries the inline/width axis; `size` also requires block-size control, which is stricter to satisfy). Optional name: `container-name: card-zone`, or shorthand `container: card-zone / inline-size`.
2. Query it from a descendant: `@container card-zone (width > 700px) { … }` — unnamed `@container (width > 30rem)` targets the nearest ancestor containment context.
3. Container query length units (`cqw`, `cqi`, `cqh`, `cqb`, `cqmin`, `cqmax`) express sizes relative to the query container (e.g. `1cqi` = 1% of the container's inline size); they fall back to small viewport units when no eligible container exists [accessed].
4. For browsers without support, MDN's documented fallback strategy is a grid/flex layout with a media query approximating the same effect [accessed].

Division of labour: **media queries own page structure** (how many columns the page grid has, where zones go); **container queries own components** (how a card arranges its internals). Using media queries for component internals is the classic bug that produces a sidebar card styled as if it were a main-column card.

## 4. How it works

### 4.1 The responsive card grid: `repeat()` + `auto-fill`/`auto-fit` + `minmax()`

The single most useful responsive layout pattern, with syntax verified against MDN [accessed]:

```css
.card-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(16rem, 1fr));
  gap: var(--space-5);
}
```

What it does and why it works: `auto-fill` repeats the track pattern as many times as fits without overflowing ("resolves to the largest number of repetitions that does not cause overflow", MDN [accessed]); each track is `minmax(16rem, 1fr)` — at least 16 rem wide, otherwise sharing space equally. Cards therefore wrap from 1-up to N-up with no media query at all.

The two keywords differ in one behaviour, per MDN [accessed]: **auto-fit behaves as auto-fill "except that after placing grid items, any empty repeated tracks are collapsed"** (collapsed tracks act as 0 px, and their gutters collapse too). Practical consequence: with `auto-fill`, empty tracks keep reserving column space (items stay at consistent track width, aligned to an implicit grid); with `auto-fit`, few items stretch to fill the row (three cards on a wide screen each become one-third width). Card grids usually want `auto-fill`; a row that should stretch its few items wants `auto-fit`.

The constraints, all from MDN [accessed]: auto-repeat requires a *fixed-size* track function — a plain `fr` or intrinsic size alone is invalid (`repeat(auto-fill, minmax(16rem, 1fr))` is legal because the min is a fixed length and the max is `1fr`); a declaration may contain at most one `auto-fill`/`auto-fit` repetition; and with subgrid, auto-repeat takes a list of line names instead of track sizes.

### 4.2 Fluid gutters and margins

Gutters that grow slightly with the viewport keep a grid from feeling cramped on large screens and from wasting space on small ones (see [Spacing and proportion](spacing-and-proportion.md) §3.1 for the scale these derive from):

```css
:root { --grid-gutter: clamp(1rem, 2vw, 1.5rem); }   /* 16→24 px */
:root { --grid-margin: clamp(1.5rem, 5vw, 4rem); }   /* 24→64 px */
```

Use `clamp()` so spacing never goes below the compact tier or above the comfortable maximum — this pairs the breakpoint system with the spacing scale instead of overriding it per media query.

### 4.3 Structural breakpoints in practice

For the page shell, re-map the grid's named areas at breakpoints (named-areas syntax per MDN grid basics [accessed]; areas must be rectangular):

```css
.event-layout {
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  gap: var(--grid-gutter);
  grid-template-areas:
    "head head head head head head head media media media media media"
    "intro intro intro intro intro intro . media media media media media";
}

@media (max-width: 599px) {
  .event-layout {
    grid-template-columns: 1fr;
    grid-template-areas: "head" "media" "intro";
  }
}
```

Only the zone map changes; every child keeps its `grid-area` name. This is the payoff of building the page on named spatial zones (see [Grid systems](grid-systems.md) §4.1 step 6): responsive re-architecture becomes re-mapping, not re-writing.

For column-count changes, redefine the template rather than fighting individual items:

```css
@media (min-width: 1024px) {
  .event-layout { grid-template-columns: repeat(12, 1fr); }
}
@media (max-width: 1023px) {
  .event-layout { grid-template-columns: repeat(6, 1fr); }
}
```

Ranges and their rationale: write mobile rules without a query (mobile-first), then add `min-width` queries as the viewport widens — web.dev's "start small, then work up" method [accessed]. Testing should sweep the viewport continuously, not just visit the conventional widths, precisely because content-driven breakpoints live between them.

### 4.4 Media in grids

Images and video are the most common cause of overflow, and the fixes are standard practice (web.dev [accessed]):

- Give every replaced element `max-width: 100%; height: auto;` so it shrinks within its track without growing past its intrinsic size.
- Provide `width` and `height` attributes (or CSS `aspect-ratio`) so the browser reserves space before load and prevents layout shift — an explicit web.dev recommendation [accessed].
- Crop, do not distort: `object-fit: cover` inside a fixed-aspect zone keeps photographs filling their spatial zone regardless of source dimensions.
- Prefer modern responsive-image delivery (`srcset`/`sizes`) so phones do not download poster-sized files; the layout mechanic here is that the *zone* controls size, not the file.
- Decorative full-bleed media (the poster hero) belongs to a 12-column zone that breaks the content margin deliberately — a documented exception, per the breaking-the-grid discipline in [Grid systems](grid-systems.md) §6.3.

## 5. Practical application — four worked patterns

**Pattern 1 — content-first audit.** Take the desktop design and strip it to single column with no queries. Widen the viewport slowly; at each point where content breaks (measure too long, cards too narrow, zones cramped), note the width. Those notes are the breakpoint list — not the framework's defaults. web.dev's worked example lands on a major breakpoint around 600 px with minor adjustments near 360 px and 500 px [accessed]; a real project's numbers will differ with its content.

**Pattern 2 — dashboard tiles.** Fixed vocabulary of tile sizes on a 12-column grid, adapting per breakpoint rather than per tile:

```css
.dash { display: grid; grid-template-columns: repeat(4, 1fr); gap: var(--grid-gutter); }
.tile--kpi  { grid-column: span 2; }
.tile--mini { grid-column: span 1; }
@media (max-width: 767px) {
  .dash { grid-template-columns: repeat(2, 1fr); }
  .tile--kpi { grid-column: span 2; }
  .tile--mini { grid-column: span 1; }
}
```

The tile classes keep their meaning at every width — only the track count changes — which keeps the dashboard's hierarchy intact across sizes.

**Pattern 3 — the self-adaptive card.** Internals switch by container width, not viewport:

```css
.card-zone { container: card-zone / inline-size; }
.card { display: grid; gap: var(--space-3); }
@container card-zone (width > 28rem) {
  .card { grid-template-columns: 1fr 2fr; }   /* image beside text in roomy contexts */
}
```

The same component in a sidebar (narrow container) stays stacked; in the main column it splits — exactly the reuse benefit MDN describes [accessed]. Fallback for non-supporting browsers, following MDN's documented strategy [accessed]: approximate with a media query on viewport width.

**Pattern 4 — hero that scales like a poster.** The event poster's proportions on the web: hero type sized in container or viewport units with `clamp()`, hero zone spanning the full grid:

```css
.hero { grid-column: 1 / -1; }
.hero h1 { font-size: clamp(2.25rem, 6vw, 5rem); }  /* poster display type, bounded */
```

**Pattern 5 — running text that gains columns.** For article-style text (not UI cards) multicol responds to available width directly: `column-width` requests a target column width and the browser adds a column whenever room for another one exists — web.dev's example uses a `column-width` of `200px` and notes a column is added when there is room for another such column [accessed]:

```css
.article { column-width: 20rem; column-gap: var(--grid-gutter); }
```

The trade-off: multicol flows content *down* each column before moving across, which is fine for prose but wrong for interface elements (a form's fields would read out of order), and vertical balancing is the browser's, not yours. For anything interactive or component-shaped, prefer the grid patterns above.

## 6. Decision framework

| Situation | Technique | Why |
| --- | --- | --- |
| Unknown number of repeated cards | `repeat(auto-fill, minmax(min, 1fr))` | Wraps without media queries; consistent track widths |
| Few items should stretch to fill a row | `repeat(auto-fit, …)` | Empty tracks collapse, items expand (MDN [accessed]) |
| Track must never fall below a readable floor | `minmax(min, 1fr)` with a length min | Floor is honoured; `fr` invalid as min (MDN [accessed]) |
| Component reused in different-width contexts | `container-type: inline-size` + `@container` | Adapts to actual placement, not viewport (MDN [accessed]) |
| Page structure must re-arrange | Named-area remap at media-query breakpoints | One structural change point per breakpoint |
| Spacing feels cramped at extremes | `clamp()` on gutter/margin tokens | Continuous scaling between tier bounds |
| Media overflows its zone | `max-width: 100%`, `aspect-ratio`, `object-fit` | Shrink, reserve space, crop — never distort |
| Running prose should gain columns as space allows | Multicol `column-width` (Pattern 5) | Column count follows available width; prose only |
| Cards' internals must align to the page grid | `grid-template-columns: subgrid` on the card | Inherited tracks keep card content on the parent grid |
| Considering a new breakpoint | Widen until content breaks, then add it | Content-driven survives new devices (web.dev [accessed]) |

Anti-patterns to refuse: fixed `px` column templates on fluid pages; device-name media queries; one breakpoint set copied between unrelated projects; hiding content to force fit; styling component internals from viewport media queries when container queries (or the fallback pattern) are available.

## 7. Examples

### 7.1 Exercise: make the event brand grid responsive

Using the 1440 px / 12-column grid defined in [Grid systems](grid-systems.md) §4.3:

1. **Audit.** View the landing page at 360 px with the desktop grid removed. Note every break point as the width grows: hero zones, card minimums, navigation form.
2. **Build the fluid base.** Convert margins and gutters to `clamp()` tokens (§4.2); convert the 12 fixed columns to `repeat(12, 1fr)`; give cards `repeat(auto-fill, minmax(16rem, 1fr))`.
3. **Re-map zones.** At your audited widths, remap `grid-template-areas` so the hero stacks before the media, and the navigation changes form. Keep all zone names stable.
4. **Componentise.** Wrap each card in a named `container-type: inline-size` zone and move its internal layout into `@container` rules; provide the media-query fallback.
5. **Verify.** Sweep the viewport continuously from 320 px to 1600 px: no horizontal scrolling at any width, no text block exceeding the comfortable measure at any width (add a breakpoint if one does), media never distorted, no content missing versus desktop. This sweep is the acceptance test for any responsive layout.

## 8. Common mistakes

- **Device-first breakpoints.** Copying a device table instead of finding where the content breaks; the layout then misbehaves on every device that ships after the table was written (§3.2).
- **Fixed-width grids.** `grid-template-columns: repeat(12, 220px)` overflows any viewport smaller than the sum; fluid `fr`/`minmax()` tracks are the default.
- **`fr` in the wrong argument slot.** `minmax(1fr, 300px)` is invalid — `fr` is permitted only as the *max* in `minmax()` (MDN [accessed]).
- **`auto-fill` vs `auto-fit` confusion.** Using `auto-fit` on a card grid, then wondering why three cards stretch to full width; or `auto-fill` where stretching was wanted. The difference is empty-track collapsing (§4.1).
- **Multiple auto-repeats in one declaration.** At most one `auto-fill`/`auto-fit` repetition is allowed per property value (MDN [accessed]); mixing another `repeat()` requires fixed repetitions only.
- **Media queries on component internals.** A card whose internal layout flips at *viewport* widths looks wrong in the sidebar it also lives in; use container queries (§3.3).
- **Forgetting containment side effects.** `container-type: inline-size` applies containment, so the container's size can no longer depend on the queried content in ways it did not before; declare it on the wrapper, not the component itself.
- **Missing width/height on media.** Without reserved space, images load and shift the grid beneath them (web.dev [accessed]).
- **Hiding content on small screens.** Removing sections because they are awkward to fit — explicitly discouraged by web.dev [accessed]; re-arrange instead.
- **Testing only at conventional widths.** Content-driven breakpoints live between the usual numbers; a continuous viewport sweep is the only reliable check (§7.1 step 5).

## 9. Evaluation checklist

- [ ] No horizontal scrolling at any width from 320 px upward (continuous sweep, not spot checks).
- [ ] Grid tracks are fluid (`fr`, `minmax()`); fixed pixel templates appear only for genuinely fixed elements.
- [ ] Breakpoints were derived from content breaks and documented with the reason for each.
- [ ] Repeated-content grids use `repeat(auto-fill|auto-fit, minmax(...))` correctly, with the right keyword for the intended fill behaviour.
- [ ] Components reused in different contexts use container queries (`container-type`, `@container`) with a documented fallback.
- [ ] Gutters and margins scale via `clamp()` and stay within the spacing scale's tiers.
- [ ] All media has reserved space (`width`/`height` or `aspect-ratio`), never distorts, and uses `object-fit` for cropping.
- [ ] No content disappears at smaller sizes; zones re-arrange instead.
- [ ] Text blocks stay within the comfortable measure at every width (breakpoint added where they do not).
- [ ] The desktop grid is the same grid defined in [Grid systems](grid-systems.md) §4.3 — re-mapped, not redesigned.

## 10. Related topics

- [Grid systems](grid-systems.md) — the column/margin/gutter structure that responsive techniques rearrange.
- [Spacing and proportion](spacing-and-proportion.md) — the token scale that `clamp()` bounds and breakpoints remap.
- [Responsive design](../ui-ux/responsive-design.md) — product-level strategy: mobile-first prioritisation, navigation, touch targets; deliberately not duplicated here.
- [Frontend implementation](../ui-ux/frontend-implementation.md) — shipping these patterns in production code and design tokens.
- [Web typography](../typography/web-typography.md) — measure and fluid type, the main content-driven breakpoint signal.
- [Composition](../foundations/composition.md) — hierarchy decisions that decide what stacks before what.

## 11. References

- MDN Web Docs, *CSS container queries* (`container-type`, `container-name`, `container` shorthand, `@container` syntax, cq units, fallback strategy): https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_containment/Container_queries [accessed 2026-11-23]
- MDN Web Docs, *repeat()* (`auto-fill`/`auto-fit` semantics, fixed-size requirement, one-auto-repeat rule): https://developer.mozilla.org/en-US/docs/Web/CSS/repeat [accessed 2026-11-23]
- MDN Web Docs, *minmax()* (argument rules, `fr` only as max, max < min behaviour): https://developer.mozilla.org/en-US/docs/Web/CSS/minmax [accessed 2026-11-23]
- MDN Web Docs, *Basic concepts of grid layout* (tracks, lines, areas, gap semantics): https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_grid_layout/Basic_concepts_of_grid_layout [accessed 2026-11-23]
- web.dev, *Responsive web design basics* (content-first breakpoint method, fluid grids, flexible images, no-hidden-content caution): https://web.dev/articles/responsive-web-design-basics [accessed 2026-11-23]
- LogRocket Blog, *Using CSS breakpoints for fluid, future-proof layouts* — content-driven breakpoint discussion: https://blog.logrocket.com/css-breakpoints-responsive-design [search-verified]
- Material Design 3 (Google), *Grids & spacing* — per-window-size-class grid specifications: https://m3.material.io/foundations/layout/grids-spacing [search-verified]
- Ethan Marcotte, *Responsive Web Design*, A Book Apart, 2011 — the fluid grids / flexible images / media queries formulation, and the later "intrinsic web design" direction associated with Jen Simmons. [canonical]
- Note: breakpoint ranges labelled "common convention" in §3.2 are conventional starting points, not standards — verify against the current framework or design-system documentation for any real project.
