# CSS Architecture

## 1. What is it?

How a stylesheet system is designed before components are written: the token layer, the cascade strategy, the layout primitives, and the modern platform features (cascade layers, container queries, fluid typography, logical properties, view transitions) that a 2026 CSS codebase should be built on. The component-level translation craft is [../ui-ux/frontend-implementation.md](../ui-ux/frontend-implementation.md); the token *model* (naming, structure, governance) is [../design-systems/design-tokens.md](../design-systems/design-tokens.md); this file is the architecture that connects them.

## 2. Why does it matter?

Most frontend quality problems are CSS-architecture problems wearing component costumes: magic-number spacing that never matches the scale, z-index arms races, specificity fights fixed with `!important`, dark mode bolted on by duplicating every colour, and a stylesheet where deleting any line feels dangerous. These are not discipline failures — they are the predictable result of writing CSS without an architecture. The modern platform has meanwhile removed most of the historical reasons for utility chaos and specificity hacks: layers, `:where()`, container queries and logical properties make a small, governed stylesheet genuinely practical.

## 3. Core principles

**Principle 1 — Tokens are the only source of truth for values.** Colours, spacing, radii, type steps, durations, easings, shadows and z-index tokens are custom properties on `:root` ([../design-systems/design-tokens.md](../design-systems/design-tokens.md)); components consume tokens, never raw values. Two exceptions, documented: optical-adjustment one-offs and the reset.

**Principle 2 — The cascade is designed, not fought.** Specificity is kept flat (single class selectors; `:where()` for zero-specificity defaults); cascade layers (`@layer reset, tokens, base, components, utilities`) give import-order-independent precedence; `!important` appears only inside a layer strategy, never as a repair tool.

**Principle 3 — One layout primitive set.** Flex for one-dimensional distribution, Grid for two-dimensional composition, container queries for component-responsive design, media queries for page-level responsive strategy ([../layout/responsive-layouts.md](../layout/responsive-layouts.md)). Components query their *own* container — a card looks right wherever it lands, not just in its original column.

**Principle 4 — Theme is a variable swap.** Dark mode, density and brand variants are token remaps under a class or media query — the component code never changes. If adding dark mode requires touching components, the token architecture is wrong ([../colour/colour-in-code.md](../colour/colour-in-code.md)).

**Principle 5 — Progressive enhancement, honest fallbacks.** Every modern feature ships inside `@supports` or accepts its no-support default as the design. The site must be complete with less CSS, not broken.

## 4. How it works — the architecture

**Layer stack.** A canonical `@layer` order: `reset` (platform normalization), `tokens` (`:root` custom properties), `base` (element defaults, typography), `components` (the component library), `utilities` (a small, closed set). Later layers win; utilities can override components without specificity hacks. Unlayered styles (vendor CSS) sit above all layers — which is why third-party CSS gets wrapped into a layer on import.

**Token tiers.** Primitive tokens (`--scale-300`, `--grey-700`) → semantic tokens (`--color-surface`, `--color-text`, `--space-md`, `--radius-card`) → component tokens (`--button-bg`). Components read semantic or component tokens only; themes remap primitives→semantic per mode. Typography uses fluid steps via `clamp()` (`--text-md: clamp(1rem, 0.96rem + 0.35vw, 1.125rem)`) so the type scale breathes between breakpoints without step-jumps ([../typography/web-typography.md](../typography/web-typography.md)).

**Container queries.** The component-responsive shift: a `.card` container queries its own wrapper (`@container (min-width: 24rem)`) so the same card adapts in a sidebar, a grid, or a modal. Wrap components in `container-type: inline-size` wrappers; design the states at known container widths, not viewport widths.

**Logical properties.** `margin-block`, `padding-inline`, `inset-inline-start` — direction-agnostic layout that makes RTL support a `dir` attribute instead of a rewrite ([../accessibility/accessible-typography.md](../accessibility/accessible-typography.md) carries the i18n consequences).

**View transitions.** The View Transitions API (same-document `document.startViewTransition`) for page-level morphs and shared-element moves where supported; treat as enhancement ([../motion-and-interaction/motion-principles.md](../motion-and-interaction/motion-principles.md) governs the motion; respect reduced motion).

## 5. Practical application

**5.1 The minimal architecture (most projects).** ~100 lines: reset → `:root` tokens (~40 custom properties) → base typography → component classes (one per component, flat) → small utility set. No BEM tiers, no utility ocean, no preprocessor needed — layers and nesting handle composition. A product stylesheet of this shape audits in minutes and themes in one block.

**5.2 Scaling rules.** Component classes stay flat; composition via nesting one level maximum; no descendant selectors past two levels; co-locate component CSS with components where the toolchain allows; a stylesheet that needs comment-section organisation is a stylesheet that needs components.

**5.3 Working with Tailwind.** Where a project uses Tailwind ([../ui-ux/frontend-implementation.md](../ui-ux/frontend-implementation.md) §3.7): define design tokens as CSS custom properties and reference them in theme configuration; keep component classes for repeated patterns (`@apply` sparingly or component wrappers); the token-first rule is unchanged — utilities consume tokens, values never inline. The architecture (layers, containers, logical properties) is identical; only the utility vocabulary differs.

**5.4 Browser support strategy.** Write for the modern baseline (Baselines 2023–2025: layers, container queries, `:has()`, nesting, logical properties ship everywhere current); `@supports` guards only for genuinely recent features (view transitions, `text-wrap: balance`); verify the project's actual support matrix from analytics before *dropping* fallbacks — never assume.

## 6. Decision framework

| Question | If yes | If no |
| --- | --- | --- |
| Will the project have a dark mode or theming? | Full token tiers (primitive→semantic) from day one | Still start semantic; migration later is cheap this way |
| Components land in unpredictable containers? | Container queries on component wrappers | Media queries suffice (page-shaped layouts) |
| Multi-language / RTL in scope? | Logical properties only; test `dir="rtl"` early | Still prefer logical properties — the cost is zero |
| Third-party CSS in the build? | Wrap into a cascade layer at import | Keep the unlayered escape hatch in mind |
| Tailwind chosen? | Tokens in theme config; component layer for patterns | Vanilla flat architecture per §5.1 |
| Page-level transitions matter to the product? | View Transitions API behind `@supports` | CSS state transitions suffice |

## 7. Examples

**Example 1 — dark mode as a ten-line change.** A product built on the tier system ships dark mode by remapping ~12 semantic tokens under `@media (prefers-color-scheme: dark)` plus a manual `[data-theme="dark"]` override. Zero component edits; contrast re-verified per pair ([../accessibility/accessible-colour.md](../accessibility/accessible-colour.md)); the token audit confirmed no component reads a primitive directly. The pre-token build had required touching 47 component files for the same result — the architecture *is* the difference.

**Example 2 — one card, three containers.** A content card (image + text + meta) is wrapped in a `container-type: inline-size` wrapper and styles itself from its container: under 20rem it stacks; 20–32rem it shows a row layout; above 32rem it adds a footer row. The card is dropped into a dashboard column, a modal and a 4-up grid with zero prop changes and zero viewport assumptions — the container-query payoff that media queries structurally cannot deliver.

## 8. Common mistakes

- **Raw values in components** — `padding: 14px` instead of `--space-sm`; the scale decays from the first exception.
- **Specificity arms races** — descendant chains and `!important` repairs instead of layers and flat selectors.
- **Media queries inside components** — components styled against the viewport instead of their container; layouts break at every new placement.
- **Theme bolt-on** — dark mode by duplicating rules; token tiers make this impossible by construction.
- **Physical properties everywhere** — `margin-left` patterns that break RTL.
- **Undefined z-index scale** — the arms race again; z-index is a token ladder with documented levels.
- **Modern CSS without fallback strategy** — shipping features whose unsupported state is broken rather than merely plainer.

## 9. Evaluation checklist

- [ ] Every component consumes tokens; raw values exist only in reset and documented optical exceptions.
- [ ] Cascade layers defined with a canonical order; no `!important` outside layer strategy.
- [ ] Component selectors flat; nesting ≤ one level; descendant chains ≤ two.
- [ ] Repeated components use container queries; page-level concerns use media queries.
- [ ] Layout uses logical properties; `dir="rtl"` smoke-tested if multi-language is in scope.
- [ ] Typography steps are fluid (`clamp`) and match the type scale.
- [ ] Theming is a token remap; a dark-mode change touches no component file.
- [ ] z-index drawn from a token ladder.
- [ ] `@supports` fallbacks verified in one non-supporting target; no-JS and no-CSS states complete.

## 10. Related topics

- [Frontend implementation](../ui-ux/frontend-implementation.md) — component translation craft, Tailwind detail, worked examples.
- [Design tokens](../design-systems/design-tokens.md) — the token model this architecture hosts.
- [Colour in code](../colour/colour-in-code.md) — colour notations, gamuts and theme implementation.
- [Responsive layouts](../layout/responsive-layouts.md) — the layout-level responsive strategy.
- [Web typography](../typography/web-typography.md) — the type layer of the architecture.
- [Performance](performance.md) — the runtime consequences of CSS choices.
- [Technology selection](technology-selection.md) — where these decisions sit in stack choice.

## 11. References

- MDN CSS guides — cascade layers, container queries, `clamp()`, logical properties, `:has()`, View Transitions API. https://developer.mozilla.org/en-US/docs/Web/CSS [search-verified, accessed 2026-11-25]
- MDN, "Using CSS cascade layers". https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_cascade/Cascade_layers [search-verified, accessed 2026-11-25]
- MDN, "CSS container queries". https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_containment/Container_queries [search-verified, accessed 2026-11-25]
- W3C CSS Cascading and Inheritance Level 5 (layers) specification. [canonical]
- Open Props (argyleink/open-props) — a verified reference for token-shaped CSS custom property sets (5,587★, MIT, pushed 2026-10-11). [accessed 2026-11-25]
- The architecture's canonical layer stack and tier rules are this library's synthesis of current platform practice.
