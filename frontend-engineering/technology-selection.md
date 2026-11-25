# Technology Selection

## 1. What is it?

The procedure for choosing a frontend stack from actual requirements — and recording the choice so it can be reviewed. It covers the framework question (vanilla HTML/CSS/JS vs React/Next.js vs Vue/Svelte/Astro vs static-site tooling), TypeScript adoption, Tailwind versus vanilla CSS, the rendering strategy (SSG, SSR, ISR, SPA, islands), state management, and the SEO consequences of each. The library's position, stated as rule: **no stack is prescribed — the choice follows the requirements**, and this file's job is to make that reasoning explicit instead of habitual.

## 2. Why does it matter?

Stack choice is the most expensive decision a frontend makes: everything downstream (components, motion, testing, deployment, hiring, agent-assistance) inherits it. The two dominant failure modes both come from skipping the procedure: defaulting to the most fashionable framework for a page that needed one HTML file, and hand-rolling a bespoke setup for a product that needed an established stack with ecosystem support. Framework defaults also shape design freedom — a stack chosen for convenience can silently forbid the design direction (heavy motion, 3D, editorial layouts) the product actually needs, which is why the selection runs *after* design direction is set ([skills/frontend-design](../skills/frontend-design/SKILL.md) phases 2–5).

## 3. Core principles

**Principle 1 — Requirements first, framework second.** The inputs: content type (static, editorial, app-like, data-heavy), interaction depth, SEO needs, team and agent skill surface, deployment constraints, performance budget, longevity. The framework is the output, never the input.

**Principle 2 — Boring and proven beats new and clever.** For agent-driven work especially: established stacks have the documentation, error messages and community answers that make autonomous work reliable. Novelty is justified by a requirement no proven option meets.

**Principle 3 — The smallest tool that meets the requirements.** A marketing page needs HTML and CSS; a dashboard needs a component framework and state; both need accessibility, performance and tokens — those obligations are stack-independent.

**Principle 4 — TypeScript by default.** For anything beyond a single page: types are executable documentation, and agents (and humans) refactor and integrate dramatically better with them. Typed APIs catch a whole defect class before the browser does.

**Principle 5 — Record the decision.** Every project carries a short decision record: requirements, options considered, choice, reasons, reversibility notes. The record is what turns a default into a decision.

## 4. How it works — the decision paths

**4.1 The framework question.**

| Requirement profile | Choose | Why |
| --- | --- | --- |
| Content page, landing page, one-off site, prototype | Static HTML/CSS (+ light JS) | Zero build, zero dependencies, fastest possible delivery, trivially testable |
| Content-heavy, many pages, SEO-critical, mostly static (docs, marketing, blog) | Astro or Next.js SSG | Build-time rendering, islands for islands of JS, excellent Lighthouse outcomes |
| Web application: auth, dashboards, real-time data, complex client state | React/Next.js, or Vue/Svelte equivalents | Component model, ecosystem depth, established patterns for the hard parts |
| Hybrid: marketing site + app surface | Next.js (SSG/ISR for marketing, app routes for the product) or Astro + embedded app | One deployable, two rendering strategies |
| Extension of an existing project | The project's existing stack | Consistency outranks ideal choice (re-verify this assumption before inheriting) |

React/Next.js notes: the largest ecosystem and agent-training surface; Next.js brings rendering flexibility (SSG/SSR/ISR), routing and image optimisation — with real complexity to manage (server/client boundaries, caching layers). Vue and Svelte are excellent and lighter; choose them when the team's or ecosystem's strength lies there, not for abstract size arguments. Astro wins pure-content cases with minimal JavaScript by default.

**4.2 TypeScript.** Default yes for multi-file projects. No-JS or JSDoc-typed JavaScript is acceptable for single-page static work where a build step itself is the bigger cost.

**4.3 Tailwind vs vanilla CSS.** Tailwind (utility-first) suits: rapid iteration, agent-heavy workflows (its constraints constrain hallucinated CSS), design-system-backed products, teams already fluent. Vanilla CSS per [css-architecture](css-architecture.md) suits: content sites with minimal components, long-lived sites wanting fewer build-time dependencies, designs far from utility conventions. Both are token-compatible; mixing is a project smell. Verified status: tailwindlabs/tailwindcss, 98,780★, MIT, pushed 2026-11-24. [accessed 2026-11-25]

**4.4 Rendering strategy.** SSG (static generation) whenever content is known at build time — fastest, most resilient, best SEO. ISR (incremental static regeneration) for content that changes but not per-request. SSR for per-user or per-request truth (authed surfaces, personalised data). SPA for deeply app-like surfaces behind login where SEO is irrelevant. Islands/partial hydration for mostly-static pages with interactive pockets. Rule: the default is the most static strategy that still meets the requirements.

**4.5 State management.** Server state first (the data lives on the server; use a fetching/query library, don't mirror it into a global store). Client state only for genuinely client-owned state (UI state, wizards, optimistic flows). Reach for a global store (Redux/Zustand/Pinia) when prop-drilling pain is real and scoped state is exhausted — the 2026 default is much less store than the 2019 default.

**4.6 SEO and metadata.** SEO requirements decide rendering (4.4) and mandate: semantic HTML ([../ui-ux/frontend-implementation.md](../ui-ux/frontend-implementation.md)), metadata head discipline (titles, descriptions, Open Graph, canonical), structured data where content types warrant it, sitemaps, and Core-Web-Vitals-quality delivery ([performance](performance.md)). A stack that cannot ship those is the wrong stack for any public-facing page.

## 5. Practical application

**The selection run.** (1) Write the requirement profile against §4.1's table. (2) Pick the candidate; check it against the design direction's needs (motion libraries, 3D, container queries — all stack-agnostic on the modern web, but verify). (3) Verify the ecosystem pieces: component library ([../github-resources/catalogue.md](../github-resources/catalogue.md)), animation library ([../motion-and-interaction/animation-libraries.md](../motion-and-interaction/animation-libraries.md)), form handling ([forms-and-data-display](forms-and-data-display.md)). (4) Write the decision record: requirements, choice, reasons, what would change the decision, reversibility. (5) Scaffold with the stack's official tooling, not a hand-rolled config.

**Agent-specific guidance.** Prefer stacks with strong static analysis (TypeScript), deterministic builds, and clear errors — the agent debugging loop depends on them. Prefer official CLIs and documented conventions over bespoke setups. When the brief names a stack explicitly, the brief wins (record any concerns in the decision record, not as a deviation).

## 6. Decision framework

The five questions, in order, with their outputs:

1. **What is the content and interaction profile?** → §4.1 row.
2. **Is SEO required?** → yes rules out pure client SPA for public surfaces; sets rendering strategy.
3. **Who maintains it — and with what tooling?** → ecosystem weight and TypeScript default.
4. **What is the performance budget?** ([performance](performance.md)) → constrains framework overhead; static-first strategies fit tight budgets.
5. **What is the exit cost?** → favour standard patterns (documented routing, conventional state, platform CSS) over bespoke cleverness.

Any choice failing question 5 (exit cost) is reconsidered regardless of the others.

## 7. Examples

**Example 1 — the one-page brief.** A bakery needs a landing page with hours, menu and a booking form. Requirements: static content, one form, SEO for local search, no team, no auth. Choice: single static HTML file + CSS + 30 lines of JS for the form; hosted statically. Explicitly rejected: Next.js ("will need a CMS eventually" is a speculative requirement — the decision record notes the upgrade path if it becomes real). Result: fastest delivery, perfect Lighthouse, nothing to maintain beyond the file.

**Example 2 — the analytics product.** Requirements: auth, dashboards, real-time charts, per-user data, public marketing site. Choice: Next.js — ISR for marketing pages, SSR/auth for the app surface, server state via a query library, client state minimal (UI-only); TypeScript throughout; Tailwind with a token-backed theme; charts per [forms-and-data-display](forms-and-data-display.md) and [../information-design/data-visualisation.md](../information-design/data-visualisation.md). The decision record notes the reversibility: components are standard React; the Next-specific parts (routing, caching) are isolated and documented.

## 8. Common mistakes

- **Framework as reflex** — React for a static page, no framework for a real app; both from habit.
- **Speculative requirements** — choosing complexity for scale the product may never reach; note it, don't build it.
- **Inheriting a stack without re-verification** — "existing project" as an unexamined default when the project would genuinely benefit from a staged migration.
- **Skipping the decision record** — the choice becomes unreviewable folklore.
- **SEO-blind app choices** — client-only SPAs for public, indexable surfaces.
- **Store-first state design** — mirroring server data into a global store before server-state patterns are exhausted.
- **Bespoke tooling** — hand-rolled Webpack configs in 2026 where official tooling exists.

## 9. Evaluation checklist

- [ ] Requirements profile written before any framework discussion.
- [ ] Chosen stack matches a §4.1 row (or a documented exception).
- [ ] Rendering strategy is the most static one that meets requirements.
- [ ] TypeScript adopted for multi-file work (or JSDoc for single-page).
- [ ] CSS approach decided (Tailwind or vanilla) and recorded with reasons.
- [ ] State design: server state via query patterns; client store justified, not reflexive.
- [ ] SEO obligations achievable in the stack (metadata, structured data, sitemap, performance).
- [ ] Design-direction needs (motion, 3D, containers) verified as stack-compatible.
- [ ] Decision record exists: requirements, choice, reasons, exit cost.

## 10. Related topics

- [CSS architecture](css-architecture.md) — the styling system that any chosen stack hosts.
- [Performance](performance.md) — the budget that constrains the selection.
- [Forms and data display](forms-and-data-display.md) — the app-surface patterns after selection.
- [Frontend implementation](../ui-ux/frontend-implementation.md) — translation craft within the chosen stack.
- [github-resources catalogue](../github-resources/catalogue.md) — the verified ecosystem (Next.js, Tailwind, shadcn/ui and peers).
- [Accessibility fundamentals](../accessibility/wcag-fundamentals.md) — stack-independent obligations.

## 11. References

- Repository statuses verified via GitHub API 2026-11-25: tailwindlabs/tailwindcss (98,780★ MIT), vercel/next.js, and the ecosystem entries catalogued in [../github-resources/catalogue.md](../github-resources/catalogue.md) with full data.
- Next.js documentation (rendering strategies: SSG/SSR/ISR). https://nextjs.org/docs [search-verified, accessed 2026-11-25]
- Astro documentation (islands architecture). https://docs.astro.build [search-verified, accessed 2026-11-25]
- MDN, Client-side web APIs / progressive enhancement framing. [search-verified, accessed 2026-11-25]
- The decision tables and the smallest-tool rule are this library's synthesis of professional practice, not sourced doctrine.
