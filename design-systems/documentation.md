# Documentation

## 1. What is it?

Design-system documentation is the explanatory layer that turns assets (tokens, components, patterns) into a system people can actually use. It answers four questions for every asset: *what is it*, *when should I use it*, *when should I not*, and *how do I use it correctly*. The docs are not a by-product of the system; for most consumers the docs *are* the system, since a component nobody can find or understand effectively does not exist.

Two distinct scopes live under this heading. **Component-level documentation** covers one component: its usage guidance, anatomy, states, accessibility notes and code. **System-level documentation** covers the foundations — colour, typography, spacing, motion, iconography, principles — and the "get started" material that orients new consumers. This file covers both, plus the craft of keeping documentation alive as the system changes.

A useful test of scope: if the content describes a *decision* about values or behaviour, it belongs in tokens or components (see [Design tokens](design-tokens.md), [Component systems](component-systems.md)); if it explains *how to choose and use* those decisions, it is documentation.

## 2. Why does it matter?

**Adoption is gated by comprehension.** Teams adopt a system when using it is faster than not using it. Documentation is the biggest lever on that calculation: clear "when to use / when not to" guidance removes the guesswork that makes consumers fall back to bespoke solutions.

**Consistency depends on it.** Rules that are not written down are not rules; they are habits of whoever happens to be in the room. Publishing guidance (with reasons) is what makes consistency survive personnel changes — see [Visual consistency](visual-consistency.md).

**Reviews speed up.** When guidance answers the common questions in advance, design and code reviews check compliance with documented decisions rather than re-deciding them. The GOV.UK pattern of documenting *why* (including research evidence) is what lets reviewers cite a source instead of arguing taste.

**Agents and tooling read it too.** For an AI agent, well-structured documentation is the context that makes correct output possible: usage rules, do/don't examples and accessibility notes are exactly the constraints an agent needs to generate compliant UI without trial and error.

**Change becomes communicable.** Changelogs, maturity labels and migration notes are documentation too; without them every release is a surprise, and surprises erode trust in the whole system.

## 3. Core principles

1. **Document decisions and reasons, not just properties.** A prop table states *what*; guidance states *why and when*. The GOV.UK Button page warns against multiple default buttons on one page and against relying on colour alone for the warning variant — reasoning a reader can apply to cases the page never mentions.
2. **Show, then tell.** Every guideline is paired with a rendered example (the GOV.UK pages pair each rule with live HTML/Nunjucks examples). Example-first writing forces precision: if you cannot render the rule, you have not defined it.
3. **Say when *not* to use it.** The "when to use this component" section is incomplete without its inverse. GOV.UK's disabled-button guidance ("they have poor contrast and can confuse some users"; use only if research shows they help) is the model: a documented *against* case with a reason.
4. **One source of truth per fact.** If the changelog lives in three places, two will be wrong. Docs should link to the code and the design files rather than duplicating them, and generated content (prop tables, token values) should be generated, not hand-copied.
5. **Write for scanning, then reading.** Consumers arrive with a question, not for a tour. Front-load the answer (usage guidance before implementation detail), use headings that match their questions, and keep paragraphs short.
6. **Keep it alive or kill it.** Stale documentation is worse than none: it actively misleads. Every page needs an owner, and every release needs a doc pass.

**Paired examples beat prose.** The do/don't pattern deserves its own note because it is the most portable documentation device across both audiences. A weak guideline says "don't overload the page with primary buttons"; the documented form is a pair — Do: one primary action ("Save and continue") with secondary actions as links; Don't: three competing primary buttons on one form — each with a one-line reason. The pair renders, the reason transfers, and the reviewer cites it instead of arguing. GOV.UK's "how it works" blocks model the same idea per variant: every rule ships with the rendered thing it governs.

## 4. How it works

### 4.1 Component page anatomy

The GOV.UK Design System's Button page is the reference structure, and its section names are worth adopting almost verbatim:

| Section | Content | Notes from the GOV.UK example |
| --- | --- | --- |
| When to use this component | Purpose and scope of the component | Buttons "help users carry out an action like starting an application or saving their information" |
| How it works | Each variant with a live example and rule | Sub-sections per variant: default, start, secondary, warning, buttons on dark backgrounds, disabled, grouping, double-click prevention |
| Research on this component | Evidence behind decisions | Green start buttons improved click-through rates on GOV.UK |
| Recent changes | Changelog table | Versions and dates (Apr 2023–Jul 2026 in the example) |
| Help improve this component | Contribution links | GitHub discussion/contribution entry points |
| Need help? | Support contact | Route consumers to humans |

Most mature systems extend this skeleton with a few further sections, which fill in what GOV.UK weaves into its guidance:

- **Do / Don't examples** — correct usage beside common misuse, visually marked. The fastest-to-read form of guidance; the image pair teaches more quickly than a paragraph.
- **Anatomy diagram** — the component's parts labelled (container, leading icon, label, trailing element). Labels should use the same vocabulary as the API.
- **States gallery** — default, hover, focus-visible, active, disabled, loading, invalid — every designed state rendered, not just the happy path.
- **Content rules** — what text goes in it (GOV.UK: button labels in sentence case describing the action — "Start now", "Save and continue") and what never does.
- **Accessibility notes** — keyboard behaviour, screen-reader semantics, contrast requirements (GOV.UK: inverse buttons on dark backgrounds need at least 4.5:1 per WCAG 2.2 criterion 1.4.3), and colour-independence rules.
- **Code links and tokens** — import path, live playground, and the tokens the component consumes, linking back to the foundations.

Assembled into a reusable page skeleton, the anatomy becomes a template every new component page starts from:

```markdown
# [Component name]
## When to use this component          <!-- purpose + scope -->
## When not to use it                  <!-- anti-cases, with reasons -->
## How it works                        <!-- one block per variant/prop:
                                            live example + rule + why -->
## States                              <!-- gallery: default, hover, focus-visible,
                                            active, disabled, loading, invalid -->
## Anatomy                             <!-- labelled parts, API vocabulary -->
## Content rules                       <!-- label text, limits, tone -->
## Accessibility                       <!-- keyboard, semantics, contrast -->
## Do / Don't                          <!-- paired examples -->
## Tokens used                         <!-- links to foundations -->
## Recent changes                      <!-- changelog table -->
## Help improve / Need help            <!-- contribution + support -->
```

The template's value is checkability: a reviewer can verify every section exists, an agent can parse the structure reliably, and consumers learn where to look once and apply that knowledge everywhere.

### 4.2 System-level documentation

Foundations pages document the system's cross-cutting decisions. The Atlassian foundations set gives a working taxonomy: **design tokens** (with separate pages for "design tokens explained", "use tokens in code", "use tokens in design", the full token list, and migration), plus style pages for spacing, grid, colour, typography, motion, iconography, elevation, border and radius, and guideline pages for accessibility and content. Two structural lessons follow:

- **Split foundation docs by audience task, not by file format.** Atlassian's split (explained / in code / in design / token list / migration) matches what different consumers *do* — learn the concept, implement it, apply it in design tools, look a value up, or move off a deprecated one. A single monolithic "tokens" page serves none of these tasks well.
- **Maintain a searchable complete list.** The "search and filter the token list" pattern (with a token picker) is what turns the foundations from an essay into a working reference. The same applies to a component index: every component reachable from one page, with status labels.

Also part of system-level docs: **get-started orientation** (install, first component, where to ask questions), **principles** (the values decisions are argued from), **roadmap and what's new** (GOV.UK publishes both on its homepage), and **contribution guidance** (see [Governance](governance.md)).

A get-started page earns its place by answering, in order: what this system is and who it serves; how to get the assets (install, design-tool libraries); how to build one working screen using a component and its tokens; where the complete indexes live (components, tokens, patterns); and what to do when stuck (support route, contribution route). GOV.UK's homepage demonstrates the orientation set — "Get started", "Principles we follow", "Community", "Support" and a roadmap all reachable from the first screen — which is why newcomers can self-serve instead of asking the system team.

### 4.3 Writing for humans and agents

Documentation now serves two reader populations, and good structure serves both at once:

- **For humans**: lead with the question the reader is actually asking; use paired do/don't examples; keep prose short (3–5 sentence paragraphs); put rules in lists and reasoning in prose; name the evidence where it exists.
- **For agents and tooling**: use predictable structure (consistent section names and order across pages, as in 4.1); express rules as enumerable statements ("do X when Y", "never Z") rather than vague exhortation; include machine-readable facts — props with types and defaults, token names and values, maturity status — in the page or its metadata; and keep examples as complete, runnable fragments rather than screenshots-only.
- **Both benefit from**: stable URLs, one fact in one place, explicit version/status labels, and a consistent vocabulary (the word for the same part of the UI must be the same in the API, the docs and the design file).

Vague guidance ("use colours thoughtfully", "keep spacing harmonious") is the boundary case where documentation fails both audiences: it cannot be followed by a human under deadline or parsed by an agent at all. Every guideline should be checkable — by eye, by test, or by lint.

### 4.4 Keeping documentation alive

- **Docs in the same repository as the code**, reviewed in the same pull request: a component change that does not update its page fails review. This is the single most effective aliveness mechanism.
- **Generate what can be generated.** Prop tables, token values, state galleries (from stories — Storybook "auto-generates documentation from those stories") and changelogs are derived data; hand-maintained copies rot first.
- **Every page has a named owner.** Ownership means the owner is notified when the underlying asset changes and is accountable for the page staying true.
- **Docs appear in the definition of done.** A release checklist item: changelog entry written, guidance updated, examples still render, status labels current.
- **Prune deliberately.** Outdated guidance should be corrected or archived, not left to contradict the current system. A "last reviewed" date makes staleness visible.

Changelog entries are decisions, not commit dumps — and they are documentation, published where consumers already read:

```markdown
## v3.4.0 — 2026-11-14
### Button
- Added `loading` prop with inline spinner; secondary actions stay enabled
  while a primary action submits. (Fixes #482)
### Form field
- Error messages are now announced by screen readers via `aria-describedby`.
  No migration needed.
### Deprecated
- `Text input` prop `size` is deprecated in favour of `sizeVariant`
  (matches Button). Removal: v4.0. See the migration guide.
```

The parallel GOV.UK pattern — a "Recent changes" table of versions and dates per component — renders the same content for scanning rather than reading.

## 5. Practical application

Setting up documentation for a small system, in priority order:

1. **One index page** listing every component, token set and pattern with status. This is the highest-value page; write it first.
2. **A component page template** (sections from 4.1) and a rule that no component ships without a completed page. The template makes completeness checkable.
3. **Foundations pages for the four dimensions consumers touch daily**: colour, typography, spacing, and (if theming exists) tokens/theming — each with values, usage rules and do/don't examples.
4. **Get-started page** answering: how to install, how to use the first component, where the docs and support live.
5. **Changelog + status labels**, published where consumers already look, with deprecations naming replacements (see [Governance](governance.md)).
6. **Accessibility and content guidelines** as cross-cutting pages, referenced from every component page rather than repeated.
7. **Review cadence**: a scheduled pass over the highest-traffic pages (analytics or usage signals reveal which), plus the in-review rule from 4.4.

Measure the documentation itself once traffic exists: search queries that return nothing (missing pages), the most-visited component pages (allocate maintenance there), support questions that the docs should have answered (doc gaps phrased in consumers' words), and time-to-first-component for a newcomer during onboarding. Documentation has adoption metrics of its own, and they improve the same way the system's do — by replacing opinion with counts.

Write guidance as if the reader will apply it under deadline pressure without you in the room — because that is exactly when they read it.

## 6. Decision framework

**Docs site, in-repo markdown, or tool-generated?** Start in-repo (markdown beside the code, rendered by the repo or a static-site generator): it forces the same-PR rule and costs nothing. Move to a dedicated docs site when the audience splits (external consumers, non-developers) or the volume makes navigation painful. Tool-generated galleries (Storybook-style) complement prose docs but do not replace usage guidance — a playground shows *how it renders*, not *when to use it*.

**How much guidance per component?** Scale guidance to consequence: high-usage, error-prone components (forms, buttons, modals) warrant full do/don't treatment and content rules; rarely-used components need accurate API docs and states but less usage narrative. A page that restates the prop list in prose adds nothing.

**Who writes it?** The builder writes the first draft (closest knowledge), a docs owner edits for structure and consistency, and researchers/practitioners contribute the evidence sections. Never route all docs through one writer who was not present for the decisions — the reasoning gets lost.

**Document now or later?** Document at the moment the decision is made, in the same PR. Deferred documentation accumulates as unpayable debt, because the reasoning decays fastest.

**What to leave out?** Implementation history, alternatives considered (unless the reasoning matters for contributors), and internal debate. Documentation is for the consumer's question, not the team's diary.

**Free-form pages or templates?** Templates (section 4.1's skeleton) for the repeated cases — component pages, foundation pages, decision records — and free-form for the few pages that genuinely need narrative (principles, get-started). The template/free-form split mirrors component design: structure where the pattern repeats, freedom where it does not.

## 7. Examples

- **GOV.UK Design System component pages** — the fullest public model of component page anatomy: when-to-use, per-variant guidance with live examples, research, changelog, contribution and support sections (verified on the Button page). The site-level structure (Styles / Components / Patterns, plus Get started, What's new, Roadmap, Community) shows the full system-level layer.
- **Atlassian foundations** — the reference for audience-split foundation documentation: tokens explained / in code / in design / complete list / migration, alongside style pages for each visual dimension.
- **Storybook docs** — the reference for generated component documentation: stories per state, args-driven controls, auto-generated prop tables, and an "interactive directory of your UI components and their stories".
- **Material Design 3** — publishes token-to-component mappings at scale; useful as an example of documenting the *relationship* between foundations and components rather than treating them as separate worlds.

## 8. Common mistakes

- **The catalogue mistake: documenting what components are, not when to use them.** A gallery of renderings with prop tables answers nothing a consumer actually asks; usage rules are the payload.
- **Reasoning lost.** Pages that state rules with no why ("use sentence case", "one primary button") get challenged in review and quietly ignored, because nothing anchors them to a rationale or evidence.
- **Screenshots instead of live examples.** Static images rot on every release and cannot be inspected, tested or copied. Rendered examples keep truth and doc in one pipeline.
- **Hand-copied generated facts.** Prop tables and token values typed by hand drift from code within weeks; generate them.
- **No when-not-to guidance.** Without documented anti-cases, consumers apply components everywhere they fit mechanically, including the contexts that motivated the "when not to" section in the first place.
- **Orphaned pages.** No owner, no review date, no doc-in-PR rule — the page silently diverges and starts teaching last year's system.
- **Inconsistent vocabulary.** The docs say "banner", the API says "alert", the design file says "notification"; consumers cannot map guidance to assets, and agents cannot resolve references.
- **All guidance, no entry point.** A pile of excellent pages with no index, no get-started and no search hides the system from exactly the newcomers it was written for.
- **Docs as a separate project.** Treating documentation as a phase ("we'll write the docs before launch") decouples it from decisions; by launch the reasoning has decayed and the docs describe an earlier system. Write at decision time, in the same PR.
- **Unsearchable vocabulary.** Pages that never use the words consumers search for (synonyms, plain-language terms alongside internal jargon) fail discovery; a page findable only by people who already know the answer documents nothing.

## 9. Evaluation checklist

- [ ] Every component, token set and pattern appears in one index with status labels.
- [ ] Every component page covers: when to use, when not to, variants with examples, states gallery, anatomy, content rules, accessibility notes, code links, changelog.
- [ ] Do/don't pairs exist for the highest-usage components; each rule states a reason or cites evidence.
- [ ] Guidance is checkable — each rule is verifiable by eye, test or lint; no unbounded exhortations.
- [ ] Prop tables, token values and state galleries are generated from source, not hand-copied.
- [ ] Docs update in the same PR as the asset change; a release checklist includes the doc pass.
- [ ] Every page has an owner and a visible last-reviewed date.
- [ ] Section structure and vocabulary are consistent across pages (and match the API and design-file names).
- [ ] Deprecations state the replacement, the reason and the removal timeline.
- [ ] A newcomer can go from the index to a working component in under ten minutes using only the docs.

## 10. Related topics

- [Design tokens](design-tokens.md) — the foundations layer whose decisions foundation pages document.
- [Component systems](component-systems.md) — the assets component pages document, including maturity and versioning.
- [Governance](governance.md) — contribution and release processes that documentation must reflect.
- [Visual consistency](visual-consistency.md) — the rules documentation publishes and defends.
- [Brand guidelines](../branding/brand-guidelines.md) — the brand-side counterpart: guideline documents for identity assets.
- [UI fundamentals](../ui-ux/ui-fundamentals.md) — the interface elements the documentation covers.
- [Frontend implementation](../ui-ux/frontend-implementation.md) — the engineering context consumers bring to the docs.
- [Web typography](../typography/web-typography.md) — example of a foundations page topic and its underlying craft.
- [Design system audit](../evaluation/design-system-audit.md) — auditing includes documentation completeness and freshness.

## 11. References

- GOV.UK Design System, *Button component*. https://design-system.service.gov.uk/components/button/ [accessed 2026-11-23]. Section structure ("When to use this component", "How it works", "Research on this component", "Recent changes", "Help improve this component", "Need help?"), per-variant guidance with HTML/Nunjucks examples, sentence-case label rules, disabled-button caution, 4.5:1 contrast note (WCAG 2.2 criterion 1.4.3).
- GOV.UK Design System, homepage. https://design-system.service.gov.uk/ [accessed 2026-11-23]. Site-level structure (Styles / Components / Patterns; Get started, What's new, Roadmap, Community, Support) and GDS maintenance model.
- Atlassian Design System, *Foundations* and *Design tokens*. https://atlassian.design/foundations/ and https://atlassian.design/foundations/tokens [accessed 2026-11-23]. Audience-split token documentation (explained / in code / in design / all design tokens / migrate to tokens), searchable token list, foundations topic taxonomy.
- Storybook, *Why Storybook*. https://storybook.js.org/docs/get-started/why-storybook [accessed 2026-11-23]. Quotes on stories, args, isolated rendering, the interactive component directory, and auto-generated documentation.
- Material Design 3, *Design tokens*. https://m3.material.io/foundations/design-tokens [accessed 2026-11-23; page body did not render in fetch]. Token-to-component mapping practice noted from general professional knowledge [canonical].
- Section 4.3 (writing for agents) and the decision framework: synthesis of the sources above with general professional practice.
