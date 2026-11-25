# Icon Sources and Integration

## 1. What is it?

The icon layer of asset intelligence: the verified open-source icon families, the integration frameworks that serve them, and the craft rules — one family per identity, optical consistency, real brand logos, accessible delivery — that separate a considered icon system from a search-and-paste lottery. Icon *design* (building a family) is [Iconography](../graphic-design/iconography.md); this file is the sourcing-and-integration layer.

## 2. Why does it matter?

Icons are the highest-frequency visual asset on any product UI — a dashboard ships hundreds of icon instances — and the easiest place to lose coherence: four families with four stroke weights silently ship because each component chose its own. The catalogue below is built around families (one construction logic each) and the Iconify integration layer, so the coherence rule ("one family, one grammar") is cheap to honour. The taste-skill's harder rule — **real logos for real products, never drawn look-alikes** ([../skills/taste/SKILL.md](../skills/taste/SKILL.md) §6) — is served by Simple Icons.

## 3. The sources

### 3.1 Lucide — https://lucide.dev/ [accessed 2026-11-25]

**Provides:** the community-maintained Feather successor — 2,000+ stroke-consistent icons in one visual grammar (24 px grid, 2 px stroke, rounded joins), packages for React/Vue/Svelte and plain SVG.
**Licence:** ISC-family open licence (icons ISC, project components per repo docs — verify current terms).
**Position:** the default workhorse family for product UI — the library's primary recommendation ([../github-resources/catalogue.md](../github-resources/catalogue.md): 25,987★, pushed 2026-11-24).

### 3.2 Phosphor — https://phosphoricons.com/ [accessed 2026-11-25; direct fetch failed from this sandbox — search-verified]

**Provides:** 9,000+ icons across six weights (thin/light/regular/bold/fill/duotone) in one coherent family — the weight system is the feature: one family can carry display moments (bold/fill) and body UI (regular) with consistent construction.
**Licence:** MIT (per repository phosphor-icons/core).
**Position:** the choice when weight variety across one family matters.

### 3.3 Tabler Icons — https://tabler.io/icons [accessed 2026-11-25]

**Provides:** 5,700+ stroke icons (24 px, 2 px stroke) with web/app packages; part of the Tabler ecosystem ([../github-resources/catalogue.md](../github-resources/catalogue.md): tabler/tabler 42,127★ MIT).
**Licence:** MIT.
**Position:** a strong Lucide alternative; pick one, not both.

### 3.4 Heroicons — https://heroicons.com/ [accessed 2026-11-25]

**Provides:** Tailwind Labs' icon set (outline/solid/mini) — designed to pair with Tailwind-based UI ([tailwindlabs/heroicons](https://github.com/tailwindlabs/heroicons), 23,919★ MIT).
**Licence:** MIT.
**Position:** the natural family on Tailwind projects.

### 3.5 Simple Icons — https://simpleicons.org/ [accessed 2026-11-25]

**Provides:** 3,000+ *brand* SVG icons — GitHub, Stripe, Notion, every real product's actual mark — as single-path SVGs ([simple-icons/simple-icons](https://github.com/simple-icons/simple-icons), 26,260★, CC0-1.0).
**Licence:** the icon code is CC0; **the brands' logos themselves remain subject to each brand's trademark policy** — use them to identify the real product (integrations, "works with" lists, tech stacks), never in ways that imply endorsement.
**Position:** the real-logos layer; the taste-skill's "real icon, never a drawn one" rule is satisfied here.

### 3.6 Iconify — https://iconify.design/ [accessed 2026-11-25]

**Provides:** the universal framework over 150+ icon sets — one syntax/API/components that render any set ([iconify/iconify](https://github.com/iconify/iconify), 6,414★ MIT).
**Licence:** MIT (per-set licences apply to the underlying icons).
**Position:** the integration layer — especially valuable when a project legitimately needs icons from two families, or to search across all sets from one place.

### 3.7 Noun Project — https://thenounproject.com/ [search-verified, accessed 2026-11-25]

**Provides:** the huge multi-artist icon catalogue (millions of glyphs).
**Licence:** free tier requires attribution; paid (Pro) removes it — a paid consideration, not a free default.
**Position:** the depth fallback when no open family covers a niche concept; attribution managed per the manifest.

## 4. The comparison table

| Source | Licence | Character | Position |
| --- | --- | --- | --- |
| Lucide | ISC-family | Stroke, coherent, 2k+ | Default workhorse |
| Phosphor | MIT | Six weights, one family | Weight-variety needs |
| Tabler | MIT | Stroke, 5.7k | Alternative workhorse |
| Heroicons | MIT | Outline/solid/mini | Tailwind projects |
| Simple Icons | CC0 (code); trademarks live on | Real brand marks | Real products' logos |
| Iconify | MIT framework | Universal layer | Multi-set projects |
| Noun Project | Attribution (free tier) | Multi-artist depth | Niche concepts |

## 5. Practical workflow

1. **Choose ONE family per project** (the identity's icon grammar — [Iconography](../graphic-design/iconography.md)); record it in the decision notes. Families may differ per *surface class* (e.g. workhorse UI family + Simple Icons for brand marks) — that is a documented pairing, not a drift.
2. **Serve icons properly:** inline SVG (styleable, no request) or an SVG sprite; sized to the optical grid (16/20/24 px), stroke inherits `currentColor` for theme freedom.
3. **Never mix families' glyphs visually** — if a concept is missing from the family, draw it in the family's construction logic (the Iconography craft) or choose a different family for the whole project.
4. **Accessibility:** every informative icon gets an accessible name (`aria-label` or visible text); decorative icons are hidden (`aria-hidden`); icon-only controls meet target-size rules ([../accessibility/accessibility-testing.md](../accessibility/accessibility-testing.md), [../frontend-engineering/forms-and-data-display.md](../frontend-engineering/forms-and-data-display.md)).
5. **Optimise:** strip metadata, minify paths; a project's icon sprite should be tens of KB, not megabytes.
6. **Manifest** for brand icons (trademark context recorded) ([licensing-and-provenance.md](licensing-and-provenance.md)).

## 6. Common mistakes

- **Family drift** — four stroke weights across four components; the one-family rule prevents it, tokens enforce it.
- **Drawn look-alikes of real logos** — a hand-drawn GitHub mark violates both brand practice and the taste-skill's rule; Simple Icons exists.
- **Missing accessible names** — icon-only buttons no assistive tech can name.
- **Icon soup from search** — concept-first searching across families instead of choosing a family first.
- **Font-icon remnants** — icon fonts ship accessibility and rendering problems; SVG is the 2026 default.
- **Brand icons implying endorsement** — Simple Icons code is CC0 but the trademarks are not; check each brand's policy for "used with" contexts.

## 7. Evaluation checklist

- [ ] One icon family chosen and recorded; brand-mark layer documented as a deliberate pairing.
- [ ] All icons served as inline SVG or sprite, currentColor-driven, optically sized.
- [ ] Every informative icon has an accessible name; decorative ones hidden.
- [ ] Icon-only controls meet target-size and focus-visible rules.
- [ ] Sprite optimised; no icon-font legacy.
- [ ] Brand icon usage checked against each brand's trademark policy; manifest recorded.

## 8. Related topics

- [Iconography](../graphic-design/iconography.md) — designing within a family.
- [Graphic language](../graphic-design/graphic-language.md) — icons inside the identity system.
- [UI fundamentals](../ui-ux/ui-fundamentals.md) — the state model icons live in.
- [github-resources catalogue](../github-resources/catalogue.md) — repository-level data for every family.
- [Licensing and provenance](licensing-and-provenance.md) — the manifest.

## 9. References

- Lucide — https://lucide.dev/ [accessed 2026-11-25]
- Phosphor — https://phosphoricons.com/ [search-verified, accessed 2026-11-25 (sandbox fetch failed)]
- Tabler — https://tabler.io/icons [accessed 2026-11-25]
- Heroicons — https://heroicons.com/ [search-verified, accessed 2026-11-25]
- Simple Icons — https://simpleicons.org/ [accessed 2026-11-25]; trademark notice per its own documentation.
- Iconify — https://iconify.design/ [accessed 2026-11-25]
- Noun Project — https://thenounproject.com/ [search-verified, accessed 2026-11-25]
