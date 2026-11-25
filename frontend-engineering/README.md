# Frontend Engineering (domain index)

The engineering companion to the library's design knowledge: how a designed interface becomes a correct, fast, accessible and maintainable implementation — and how to choose the technology honestly. Existing files in [ui-ux/](../ui-ux/frontend-implementation.md) cover translation craft (layout tools, stacking contexts, tokens in code, Tailwind); this domain adds the architecture, stack-selection, performance and data-display layers agents need for real builds.

| File | Contents | Consult when |
| --- | --- | --- |
| [CSS architecture](css-architecture.md) | Modern CSS at scale: cascade layers, custom-property token systems, container queries, fluid typography, logical properties, view transitions, `@supports` strategy | Designing the CSS system before writing components; modernising an existing stylesheet |
| [Technology selection](technology-selection.md) | Choosing the stack from requirements: static HTML vs framework, React/Next.js/Vue/Svelte/Astro, TypeScript, Tailwind vs vanilla, rendering strategy (SSG/SSR/ISR/SPA), state management, SEO implications | Starting any project; the decision is recorded before scaffolding |
| [Performance](performance.md) | Budgets and mechanics: Core Web Vitals, image/video pipelines, font loading, JavaScript cost, rendering behaviour, measurement procedure | Before scaffolding (budgets), during build (choices), at QA (measurement) |
| [Forms and data display](forms-and-data-display.md) | Form architecture and validation patterns; tables at scale; charts in product UI; the interaction patterns for dense data | Any input surface, any tabular or charted data surface |

Sequence: [Technology selection](technology-selection.md) → [CSS architecture](css-architecture.md) → build with [../ui-ux/frontend-implementation.md](../ui-ux/frontend-implementation.md) → verify with [Performance](performance.md) and [../evaluation/website-visual-qa.md](../evaluation/website-visual-qa.md). Accessibility obligations ([../accessibility/wcag-fundamentals.md](../accessibility/wcag-fundamentals.md)) apply throughout, not at the end.
