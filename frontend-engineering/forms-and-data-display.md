# Forms and Data Display

## 1. What is it?

The two densest surfaces in product frontends — input (forms, validation, wizards, settings) and output (tables, lists, dashboards, charts embedded in product UI) — treated as engineering-and-design systems rather than ad-hoc pages. Component anatomy and the state model are [../ui-ux/ui-fundamentals.md](../ui-ux/ui-fundamentals.md); chart-type selection and encoding theory are [../information-design/data-visualisation.md](../information-design/data-visualisation.md); this file covers the product patterns: form architecture, validation UX, data-table design at scale, and how charts behave inside real interfaces.

## 2. Why does it matter?

Forms are where products lose users — every unnecessary field, hidden error and reset-on-failure is measurable abandonment — and tables and dashboards are where products earn trust or destroy it: a wrong number, an unreadable density, a chart that lies. These surfaces are also where accessibility failures concentrate (labels, focus order, contrast in states) and where generic AI-generated frontends look most obviously generic (an unstyled `<table>`, a default form, a chart with its library's theme untouched). The patterns here are the difference between surfaces that work at real data volumes and demos that die on contact with real content.

## 3. Core principles

**Principle 1 — Ask for the minimum, save progress, forgive errors.** Every field must earn its place (data the business actually acts on); multi-step flows show progress truthfully and never lose input; errors preserve everything the user typed.

**Principle 2 — Validation is conversation, not gatekeeping.** Inline, per-field, specific, human-worded messages; validate on blur (not every keystroke), never block submission with a single summary alert; errors are described by text, not colour alone ([../accessibility/wcag-fundamentals.md](../accessibility/wcag-fundamentals.md)).

**Principle 3 — Labels are mandatory; placeholders are not labels.** Every input has a visible, persistent, associated `<label>`; placeholders are examples, never the only name (they vanish on typing and fail contrast routinely — [../accessibility/accessible-typography.md](../accessibility/accessible-typography.md)).

**Principle 4 — Tables serve scanning and comparison; charts serve shape and trend.** Choose by task ([../information-design/data-visualisation.md](../information-design/data-visualisation.md)): exact values → table; trend/composition/distribution → chart. Density is a feature — but only with the typography, alignment and state discipline that keep dense readable.

**Principle 5 — Numbers get typography discipline.** Tabular numerals (`font-variant-numeric: tabular-nums`) in all numeric columns; right-aligned numbers, decimal alignment, consistent units per column; no chart or table invents precision beyond the data's real accuracy.

## 4. How it works — forms

**Structure.** Group related fields into fieldsets with legends; one column for scanning (multi-column only for genuinely paired fields like names/dates); logical tab order equals visual order; `autocomplete` attributes (name, email, tel, cc-*) for the browser's benefit; mobile: appropriate `inputmode` and `type` per field (numeric keypads for numbers, date pickers that respect locales).

**Validation UX.** Real-time constraints (character counts, formats) as gentle inline hints; on blur, validate completed fields; on submit, validate all and focus the first error with its message announced (`aria-live`, `aria-describedby`); errors state *what happened and how to fix it* ("Enter a postcode in the form XX0 0XX"), never "Invalid input". Server-side validation re-runs everything client-side validates, and treats client validation as UX, not security.

**States.** Default, focus-visible, filled, error, disabled, read-only, loading/submitting (button with spinner matching true latency — [../motion-and-interaction/microinteractions.md](../motion-and-interaction/microinteractions.md)); success confirms what happened and what next (the peak-end moment — [../ux-psychology/design-laws.md](../ux-psychology/design-laws.md) §3.20).

**Wizards and long forms.** Progress indicators that are true (goal-gradient honesty — [../ux-psychology/design-laws.md](../ux-psychology/design-laws.md) §3.10); the ability to go back without loss; autosave where sessions can end (drafts); review step before irrevocable submissions.

## 5. Practical application — tables and charts in product UI

**Tables at scale.** Sticky headers on scroll; horizontal scrolling *inside a table container* on narrow screens (never page-level horizontal scroll — the reflow rule, [../evaluation/website-visual-qa.md](../evaluation/website-visual-qa.md) §5.5); column alignment by data type (text left, numbers right, dates ISO or locale-consistent); row states (hover, selected, focused, loading); sortable columns with visible sort state and keyboard operation; pagination or virtualisation for large sets (never render 10,000 DOM rows); row actions visible, not hover-only (touch rule). Empty, loading and error states designed like any component ([../ui-ux/ui-fundamentals.md](../ui-ux/ui-fundamentals.md)).

**Charts in product.** Library theme treated as a starting point, never the ship state: axes labelled, gridlines de-emphasised, colour semantics from the token system ([../colour/palette-development.md](../colour/palette-development.md)), CVD-safe categorical palettes ([../colour/colour-accessibility.md](../colour/colour-accessibility.md)), tooltips readable, legends where needed (direct labelling beats legends at small scale), and an accessible data alternative (table or summary) because canvas/SVG charts are opaque to assistive tech. Interaction: crosshair/tooltip on hover must have a keyboard/pointer-independent path to the same values. Loading: skeleton in the chart's footprint (CLS discipline — [performance.md](performance.md) §5.5). Updating data animates truthfully (bars move between real values — the data-driven style's honesty rule, [../visual-styles/interface-styles.md](../visual-styles/interface-styles.md) §4.13).

**Dashboards.** Hierarchy before density: what is the ONE number that matters on this dashboard? ([../information-design/information-hierarchy.md](../information-design/information-hierarchy.md)); bento composition for mixed-card surfaces ([../visual-styles/interface-styles.md](../visual-styles/interface-styles.md) §4.7); consistent card anatomy (title, value, delta, sparkline, timeframe) so scanning works; refresh semantics visible ("Updated 2 min ago") because stale data read as live destroys trust.

## 6. Decision framework

| Decision | Rule |
| --- | --- |
| Field justified? | The business acts on the data; otherwise cut or defer behind progressive disclosure ([../ux-psychology/design-laws.md](../ux-psychology/design-laws.md) §3.8) |
| Inline or modal form? | Inline for short flows in context; modal for interrupt-protecting focused work (never modal on top of modal) |
| Table or chart? | Exact values/comparison → table; shape/trend/distribution → chart; both when users need both |
| Pagination or virtualisation? | < ~200 rows and export needs → pagination; huge sets → virtualisation with accessible alternatives |
| Library chart or hand-built? | Library (Recharts/visx/Chart.js class) for product charts — accessibility and edge cases are where hand-built fails; hand-built SVG for bespoke brand moments only |
| When to build a wizard? | Steps depend on earlier answers, or > ~7 fields; otherwise one page with grouping |

## 7. Examples

**Example 1 — a checkout form rebuilt.** Nine fields on one page with a submit-only validation became three grouped steps (contact → delivery → payment), each with inline validation on blur, browser autocomplete hints, true progress indicator, and a review step. The single summary alert ("Please fix the errors") became per-field messages with `aria-describedby`; the final confirmation screen (peak-end) states exactly what was ordered and what happens next. Abandonment on the form measurably dropped; support tickets about "where did my data go" vanished with autosaved steps.

**Example 2 — a dashboard table that survived real data.** The demo rendered 12 rows beautifully; production had 8,400. Rebuild: virtualised rows with keyboard navigation, sticky header, ISO dates in a right-aligned column with tabular numerals, per-column sort with visible state, an export path, and an empty state that explains what a user sees when filters match nothing. The chart above the table gained a data-table alternative and honest update animation — the trust pattern that stale-by-default dashboards lack.

## 8. Common mistakes

- **Placeholder-as-label** — vanishing names, failed contrast, unfilledable forms with autofill.
- **Submit-only validation** — a wall of errors after the fact; the conversation model is the fix.
- **Colour-only errors** — red without text; the accessibility floor again.
- **Losing input** — failed submissions that reset fields; unforgivable and common.
- **Hover-only row actions** — invisible on touch and keyboard; visible controls or a menu.
- **Chart junk in product** — library default themes, 3D pies, dual axes without need, legends of eight.
- **Tables without states** — no hover, no focus, no empty/loading/error; the surface dies with real data.
- **Fake precision** — charts showing 87.42% from a survey of 11; numbers carry their real uncertainty.

## 9. Evaluation checklist

- [ ] Every field justified; every input has a visible persistent label and correct `type`/`inputmode`/`autocomplete`.
- [ ] Validation: inline on blur, specific messages, focus first error, announced via live region, preserved input.
- [ ] Server-side validation re-runs all rules; client validation never trusted as security.
- [ ] Full state set per input (default/focus/filled/error/disabled/loading/success).
- [ ] Long flows: true progress, back without loss, autosave/drafts, review before irrevocable actions.
- [ ] Tables: sticky header, contained horizontal scroll, type-correct alignment, tabular numerals, sort state visible, large sets virtualised/paginated, empty/loading/error states designed.
- [ ] Charts: token-driven colour, CVD-safe, labelled axes, accessible data alternative, keyboard path to values, honest update animation.
- [ ] Dashboards: one primary message, consistent card anatomy, visible refresh semantics.

## 10. Related topics

- [UI fundamentals](../ui-ux/ui-fundamentals.md) — component anatomy and the state model these surfaces apply.
- [Data visualisation](../information-design/data-visualisation.md) — encoding theory and chart-type selection.
- [Information hierarchy](../information-design/information-hierarchy.md) — the hierarchy model dashboards apply.
- [WCAG fundamentals](../accessibility/wcag-fundamentals.md) — labels, error identification, contrast, reflow.
- [Colour accessibility](../colour/colour-accessibility.md) — CVD-safe palettes for categorical data.
- [Microinteractions](../motion-and-interaction/microinteractions.md) — the press/validation/success moments.
- [Performance](performance.md) — virtualisation and CLS discipline for these surfaces.

## 11. References

- W3C, WCAG 2.2 — 3.3.1 (Error Identification), 3.3.3 (Error Suggestion), 1.3.1 (Info and Relationships: labels), 1.4.10 (Reflow: contained table scroll). https://www.w3.org/WAI/WCAG22/quickref/ [search-verified, accessed 2026-11-25]
- W3C WAI, "Forms Tutorial" — labels, groupings, validation and multi-page form guidance. https://www.w3.org/WAI/tutorials/forms/ [search-verified, accessed 2026-11-25]
- Nielsen Norman Group, form design and web-reading corpus — validation timing and error-message framing. https://www.nngroup.com/articles/ [search-verified, accessed 2026-11-25]
- MDN, HTML forms guide (`autocomplete`, `inputmode`, constraint validation). https://developer.mozilla.org/en-US/docs/Learn/Forms [search-verified, accessed 2026-11-25]
- Density, alignment and precision rules are stated as professional conventions of this library.
