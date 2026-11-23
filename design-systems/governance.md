# Governance

## 1. What is it?

Design-system governance is the set of structures that decide how the system changes: who can contribute, who reviews and approves, how releases are versioned and communicated, how adoption is measured, and how breaking changes and deprecations are managed. It is the operating model around the artefacts — tokens, components, documentation — and it is what separates a system that stays alive from one that ossifies or fragments.

Governance exists because a design system is a shared resource with many consumers and (usually) no single owner of all the use cases. Every question that recurs — "can I add a variant?", "when will this prop be removed?", "who decides the new spacing scale?" — needs a standing answer, or each occurrence becomes a negotiation. The artefacts of governance are deliberately unglamorous: a contribution flow, a decision record, a changelog, a deprecation policy, a metrics dashboard.

This file covers governance of a *product* design system: the tokens, components and patterns an organisation's products are built from. Brand-level governance — how the visual identity, logo usage and brand assets are controlled across an organisation — is a related but distinct discipline, covered in [Brand governance](../branding/brand-governance.md). The two interlock (a brand refresh forces a token change; see [Brand guidelines](../branding/brand-guidelines.md)), but their decision rights usually sit with different people.

## 2. Why does it matter?

**Without governance, the system forks.** When contributing is harder than copying, consumers copy. Each fork severs the single source of truth, and consistency — the system's whole purpose — decays through a hundred individually reasonable decisions. The contribution model is therefore not an administrative detail; it is the consistency mechanism at scale.

**Change must be managed or it breaks consumers.** A component library serving many teams is infrastructure, and infrastructure changes have blast radius. Versioning discipline, deprecation policy and migration support are what let the system evolve without every release becoming an incident.

**Funding depends on evidence.** Design systems are sustained by organisational investment, and investment decisions ask for numbers: adoption, time saved, defect reduction. A system that cannot show measured value is cut in the next budget round, no matter how good the components are.

**Decisions need memory.** "Why is the warning button used sparingly?" — the answer lives in a decision record or research note. Without decision memory, every generation of contributors re-litigates settled questions or, worse, reverses them unknowingly.

**Trust is the real product.** Consumers adopt a system they trust: trust that releases are safe, that status labels are honest, that help is reachable. Governance is how that trust is manufactured and maintained.

## 3. Core principles

1. **Contribution must be the easiest good path.** Compare the effort of a system contribution against the effort of a local workaround, and make sure the good path wins — a clear process, responsive review, a predictable release train. Speed of the *bad* path is the enemy.
2. **Decision rights are explicit.** Every layer has an owner: token semantics, component API, documentation, releases. Ambiguity ("anyone can change anything") produces both bottlenecks (everything escalates) and anarchy (nothing escalates).
3. **SemVer is the trust contract.** Patch releases never change behaviour or appearance; minor releases only add; breaking changes are major, announced, and accompanied by migration guidance. Consumers should be able to upgrade blindly within a major version.
4. **Deprecate, never delete.** Removal happens only in major versions, only after a documented deprecation period with a named replacement, and with the reason recorded.
5. **Decisions are recorded with reasons.** A decision record captures context, options, choice and consequences, so future contributors inherit reasoning rather than folklore.
6. **Measure adoption and outcomes, not vanity.** Track what consumers actually use and what the system saves, and treat low adoption as diagnostic information about the system, not as a failure of the teams.

## 4. How it works

### 4.1 Contribution models

Nathan Curtis's writing on scaling design systems contrasts team models that remain the standard vocabulary — a standalone team (isolated, serving itself), a **centralised** model (one team owns and serves the system) and a **federated** model (decision-making and doing are distributed across the system team and contributing product teams). Each has a workable niche:

| Model | Who decides / builds | Strengths | Watch out for |
| --- | --- | --- | --- |
| Centralised | Dedicated system team | Speed, coherence, consistent quality | Backlog bottleneck; distance from real product needs; single point of failure |
| Federated | System team + contributors from product teams | Scales capacity; contributions carry real-world context; consumer buy-in | Requires strong review standards; risk of inconsistent quality; coordination overhead |
| Standalone / organic | Each team maintains its own patterns | No coordination cost | Divergence; no reuse; usually a pre-system stage |

Practical guidance: most mature systems operate a **centralised core with federated contribution** — a small core team owning foundations, APIs and releases, with product teams contributing components and fixes through a defined flow. The core team's key role shifts from *building everything* to *setting standards and reviewing well*: fast feedback, clear acceptance criteria, and honest status labels.

A typical contribution flow, end to end: (1) proposal via a template (problem, evidence of broader need, proposed API); (2) triage against the roadmap; (3) build with the system's standards (tokens, states, accessibility, docs); (4) review — API review plus design review plus accessibility review; (5) merge with documentation and changelog; (6) release behind the normal versioning. GOV.UK's per-component "Help improve this component" links model the public-facing half: contribution is an advertised, supported route, not a favour.

The proposal template itself is worth standardising, because it forces the questions reviewers would otherwise chase down manually:

```markdown
# Component / change proposal
## Problem              — what can consumers not do today? Who is affected?
## Evidence             — duplicated implementations found, teams requesting,
                          links to the one-off versions in real products
## Proposed API         — props, slots, variants, states (as a sketch, not code)
## Out of scope         — adjacent problems this deliberately does not solve
## Accessibility notes  — keyboard model, semantics, contrast implications
## Maintenance estimate — who maintains it, what its ongoing cost looks like
```

The "out of scope" and "maintenance estimate" rows do the quiet work: they prevent scope creep at the proposal stage and surface the long-term cost that adoption decisions create.

### 4.2 Decision records

A lightweight **decision record** (one short document per decision, numbered, kept in the repo) prevents the most expensive governance failure: re-litigating the past. Content is stable across organisations: *context* (the problem and constraints), *options considered*, *decision*, *reasons*, *status and date*, and *consequences* (what this rules out, what to revisit when). Decisions worth recording: adding or removing a tier of tokens, a component's API shape, a theming approach, an accessibility requirement, a deprecation.

Rules of thumb: record the decision once approved (before implementation, not after the debate is forgotten); link it from the affected documentation; and give records a status (proposed / accepted / superseded) so outdated records are visibly superseded rather than silently contradicting current guidance. GOV.UK's "Research on this component" sections show the public-facing version of the same practice: evidence attached to the decision, visible to every consumer.

A minimal decision-record template, short enough that people actually fill it in:

```markdown
# DR-014 — Semantic tokens resolve themes at runtime
## Status      — accepted, 2026-11-20 (supersedes DR-009)
## Context     — three products need dark mode; build-time theming forces
                 a full CSS rebuild per theme per release
## Options     — (a) build-time themes per brand/mode
                 (b) runtime CSS custom properties re-pointing semantics
                 (c) inline style overrides per component
## Decision    — (b), with theme files declaring semantic tokens only
## Consequences — components must consume tokens (lint enforced);
                  primitives are frozen as the stable inventory;
                  revisit if server-driven theming is ever required
```

Notice what the record buys: six months later, when someone asks why the build does not pre-compile themes, DR-014 answers with the options that were rejected and why — and its "supersedes" line shows that the earlier decision existed and why it was replaced.

### 4.3 Release process

- **Train or per-change?** A predictable release train (e.g. fortnightly minor releases; majors only at announced intervals) beats ad-hoc releases, because consumers can plan upgrades. Emergency patches are the exception, never the rule.
- **What ships in a release:** versioned package(s), changelog entries per component ("Secondary buttons restyled for contrast", not commit dumps), migration notes for anything behavioural, and updated status labels.
- **Pre-release gates:** visual regression against the story gallery, accessibility checks, token-reference validation, and a docs build — the automated layer from [Component systems](component-systems.md) and [Visual consistency](visual-consistency.md).
- **Communication:** release notes where consumers already look, plus a highlighted section for deprecations and behaviour changes. GOV.UK's homepage "What's new" section (e.g. announcing a Frontend release) shows the pattern: release communication is part of the product, not an afterthought.

A pre-release checklist makes the gates concrete:

| Gate | Check | Blocks release if |
| --- | --- | --- |
| Visual | Visual regression against the story gallery | Unintended diffs on any state |
| Accessibility | Keyboard paths, focus order, screen-reader smoke test on touched components | Any regression or new failure |
| Tokens | Reference validation (dangling aliases, cycles, missing types) | Any invalid reference |
| SemVer | Change classified; version bumped correctly | Breaking change outside a major |
| Docs | Changelog entry, guidance updated, status labels current | Missing or stale documentation |
| Migration | Guide (and codemod where mechanical) for any deprecation | Deprecated API without a named replacement |

### 4.4 Adoption metrics

Measure a mix of quantitative and qualitative signals; sources such as component-usage analytics writing (Omlet) and documentation-platform guidance (zeroheight) converge on the same categories:

- **Quantitative:** proportion of components/tokens in use from the system vs bespoke implementations (usage analytics over the codebase); number of consuming teams/products; adoption trend after releases; bespoke-pattern counts as a *gap signal*; issue/PR response times as a service-level signal.
- **Qualitative:** consumer satisfaction (short periodic surveys); time-to-ship a standard screen with vs without the system; design/code review friction; support-question themes (recurring questions expose documentation gaps, not consumer failings).
- **Outcome metrics** (harder but most persuasive): UI-defect rates, accessibility-audit findings trending down, onboarding time for new designers/engineers.

Interpret the numbers honestly. "Design system adoption is a red herring" critiques the frame in which *usage everywhere, always* is the goal — high adoption of bad components is failure, and 100% adoption is neither achievable nor desirable for expressive surfaces. Use adoption as a diagnostic: low adoption in one team is a question (missing capability? poor docs? political?), not a verdict. Report the mix to leadership; single metrics get gamed.

Define each metric precisely enough to be reproduced, or it will be argued instead of read:

| Metric | Definition | Healthy signal |
| --- | --- | --- |
| System usage share | System components ÷ all UI components in the codebase, by count | Rising trend, plateau is fine |
| Bespoke-pattern count | Live implementations of patterns the system provides | Falling; each one triaged |
| Token coverage | Token-consuming style declarations ÷ total style declarations | Near 100%, exceptions documented |
| Review turnaround | Median days from proposal/PR to first substantive review | Days, not weeks |
| Consumer satisfaction | Short quarterly survey of consuming teams | Stable or improving; comments triaged |
| Time-to-ship | Build a standard screen with the system vs without (measured occasionally) | System path visibly faster |

### 4.5 Managing change without breakage

- **Additive-first design.** New capability ships as new props/variants/components; existing ones keep their behaviour. Renames and reshapes are majors, budgeted and planned.
- **Deprecation lifecycle:** mark deprecated (docs + code warning) → state the replacement and the reason → give a removal version or date → keep tests passing through the period → remove in the next major with migration notes. Never skip straight to removal, and never let a deprecation persist forever with no date — an undated deprecation is a promise nobody believes.
- **Migration support:** codemods where the change is mechanical; a migration guide with before/after examples; a support channel during the window. GOV.UK's pattern of announcing Frontend releases with upgrade guidance is the public-sector reference.
- **Behaviour changes are breaking changes.** Focus handling, keyboard behaviour, rendered output — all count. If consumers could depend on it, changing it needs a major (or a deprecation cycle if the old behaviour was documented as supported).
- **Fork management:** when a team forks because the system cannot serve a need, governance's job is to find the *reason* — a gap to close, a contribution to accept, or a documented exception to bless. Punishing the fork preserves the gap.

### 4.6 Deprecation policy

A written policy, published in the docs, containing: the deprecation mark-up used (code warning, doc badge, status label); the minimum window between deprecation and removal (commonly one to two major versions, or a stated time period); where replacements are documented; how consumers are notified (release notes, warnings, dashboard of deprecated usage in their codebase); and the exceptional cases (security or licensing issues may remove immediately). The policy's purpose is to make the system *predictably* safe to depend on — the predictability, more than the window length, is what earns trust.

A concrete lifecycle, tracked as a table in the policy so nothing depends on memory:

| Stage | Version | What happens |
| --- | --- | --- |
| Announce | v3.0 | `size` prop deprecated; warning logged; docs name `sizeVariant` as replacement; removal target announced as v4.0 |
| Migrate | v3.x | Codemod ships; dashboard shows each team's remaining deprecated usage; support channel open |
| Verify | late v3.x | Deprecated usage across the organisation reaches (near) zero; laggards contacted |
| Remove | v4.0 | Prop deleted; migration guide archived; decision record updated |

The dashboard row is the step most systems skip and most consumers want: teams cannot plan migrations around a deprecation they cannot see in their own codebase.

## 5. Practical application

Standing up governance for a system in its first year, in order:

1. **Name the owners.** One accountable system lead; named ownership for foundations (tokens), component API, documentation and releases. Write the names down.
2. **Publish the contribution flow** as a page: proposal template, review criteria (API, accessibility, tokens, docs), expected review time. Make "propose a component" the cheapest respectable path.
3. **Adopt SemVer and a changelog format** from the first release; retrofitting versioning discipline onto a shipped system is painful.
4. **Start decision records** for every cross-cutting choice; number them and link them from docs.
5. **Set the deprecation policy** in writing before the first deprecation happens — policies written during a conflict are conflict-shaped.
6. **Instrument adoption** (usage analytics over the codebase; a quarterly consumer survey). Publish the numbers internally, including the unflattering ones.
7. **Run a quarterly review**: roadmap vs actual, adoption trend, top support themes, deprecated-usage burn-down. Adjust the contribution flow based on where contributions actually stall.

Scale the ceremony to the blast radius: a two-team internal library needs owners, SemVer and a changelog; a forty-team platform adds federated contribution review, a release train and a metrics dashboard.

## 6. Decision framework

**Which contribution model fits?** Decide by (a) capacity — does a central team have throughput for all demand? (b) variation — do products genuinely need to diverge? (c) trust — do product teams believe reviews are fair and fast? Start centralised, open federated contribution once review standards and tooling exist; go standalone only when there is no shared brand or platform to serve.

**Should this change be major or minor?** If any consumer's behaviour, appearance, API or documented dependency can change without action on their part: major (or deprecate first). If purely additive with safe defaults: minor. If invisible: patch. When in doubt, it is major.

**Accept the contribution or absorb it?** Accept when it matches system standards, serves multiple teams and fits the roadmap; absorb the *problem* into the backlog (solving it centrally later) when the contribution is narrowly scoped but the need is broad; decline with reasons when it would fork the system — and record the decline in a decision record so the question stays answered.

**Deprecate now or support forever?** Support forever only for genuinely stable, low-maintenance API. Everything with ongoing maintenance cost (browser work, accessibility fixes) eventually needs a deprecation path; the cost of supporting two generations grows each release, so date the deprecation as soon as the replacement exists.

**Which metric goes in the leadership report?** One outcome metric (time-to-ship or defect/accessibility trend), one adoption metric (system-usage share), one service metric (review turnaround). Three numbers, trended, honestly annotated — more invites metric theatre.

## 7. Examples

- **GOV.UK Design System** — maintained by a team at the Government Digital Service, explicitly community-driven, publishing a 12-month roadmap, per-component research notes, changelogs and contribution routes. A public-sector model of centralised maintenance with open contribution and radical decision transparency.
- **Nathan Curtis's team models** — the standard reference vocabulary (standalone / centralised / federated) for structuring system teams; his EightShapes articles remain the most-cited treatment of the trade-offs.
- **Adoption-measurement practice** — component-usage analytics tooling (Omlet's writing on how leaders measure adoption) and documentation-platform guidance (zeroheight's dev-side metrics) converge on the quantitative/qualitative mix in section 4.4; Luis Ouriach's critique is the standing reminder to interpret adoption as diagnosis.
- **Style Dictionary's versioned releases** — an example of open-source release discipline (SemVer, changelogs, migration guides between major versions) that internal systems can copy directly.

## 8. Common mistakes

- **Bottleneck by design.** A centralised team that reviews slowly teaches teams to fork. Review responsiveness is a governance metric, not a courtesy.
- **Breaking changes in patches.** A "patch" that alters rendered output or behaviour destroys the trust SemVer was meant to buy; every future upgrade then requires a full audit.
- **Undated deprecations.** "Deprecated — will be removed later" with no version or date is ignored by every consumer until removal day.
- **Adoption as a stick.** Mandating adoption percentages while the system lacks capability produces resentful compliance and hidden forks; adoption problems are usually system problems.
- **Decisions with no memory.** Settled questions (why this spacing scale, why this API shape) re-debated annually because nothing was recorded; new contributors inherit folklore and repeat it as fact.
- **Governance theatre.** Committees and templates that never actually ship a contribution; the measure of a governance model is contributions merged per quarter, not its org chart.
- **Silent roadmap.** No published roadmap means consumers cannot plan, and surprise releases get treated as risk; GOV.UK's 12-month published roadmap is the counter-example.
- **Brand and system governance conflated.** Letting the design-system team unilaterally redefine brand assets (or the brand team override component decisions) tangles two different decision rights; keep the split explicit (see [Brand governance](../branding/brand-governance.md)).

## 9. Evaluation checklist

- [ ] Every governance layer (tokens, component API, docs, releases) has a named owner.
- [ ] A contribution flow is published, with a proposal template, review criteria and expected turnaround; contributions actually merge.
- [ ] The library follows SemVer; no behaviour or appearance change has ever shipped outside a major version.
- [ ] Every release has a human-readable changelog; breaking changes come with migration guides (and codemods where mechanical).
- [ ] A written deprecation policy exists: mark-up, minimum window, notification routes, exceptional cases.
- [ ] Cross-cutting decisions are recorded (context, options, decision, consequences) and linked from affected docs.
- [ ] Adoption is measured quantitatively (usage share, bespoke-pattern counts) and qualitatively (surveys, review friction), and reported as trends.
- [ ] A roadmap is published so consumers can plan; status labels in docs match reality.
- [ ] Forks and workarounds are triaged for root cause, and outcomes (contribution, gap closure, blessed exception) are recorded.
- [ ] The boundary between design-system governance and brand governance is written down and respected.

## 10. Related topics

- [Brand governance](../branding/brand-governance.md) — the brand-identity counterpart; decision rights for logos and brand assets live there.
- [Brand guidelines](../branding/brand-guidelines.md) — the documented identity rules that system tokens must respect.
- [Component systems](component-systems.md) — versioning, maturity levels and changelogs for the components governance steers.
- [Design tokens](design-tokens.md) — the source-of-truth layer whose change control matters most.
- [Visual consistency](visual-consistency.md) — the property governance exists to protect at scale.
- [Documentation](documentation.md) — where policies, roadmaps and contribution flows are published.
- [Design system audit](../evaluation/design-system-audit.md) — the evaluation that consumes these governance signals.
- [Design critique](../foundations/design-critique.md) — the review craft that contribution review draws on.

## 11. References

- Nathan Curtis (EightShapes), *Team Models for Scaling a Design System*. https://medium.com/eightshapes-llc/team-models-for-scaling-a-design-system-2cf9d03be6a0 [search-verified 2026-11-23]. Standalone / centralised / federated team-model vocabulary used in section 4.1.
- Nathan Curtis (EightShapes), *Defining Design Systems*. https://medium.com/eightshapes-llc/defining-design-systems-6dd4b03e0ff6 [search-verified 2026-11-23]. Context on systems requiring governance.
- Omlet, *How design system leaders define and measure adoption*. https://www.omlet.dev/blog/how-leaders-measure-design-system-adoption [search-verified 2026-11-23]. Qualitative/quantitative metric mix for section 4.4.
- Luis Ouriach, *Design System "Adoption" is a Red Herring*. https://medium.com/@disco_lu/design-system-adoption-is-a-red-herring-6c6b5a504f43 [search-verified 2026-11-23]. Critique of adoption-as-everywhere framing.
- zeroheight, *How to measure the dev side of a design system*. https://help.zeroheight.com/hc/en-us/articles/36474148202523-How-to-measure-the-dev-side-of-a-design-system [search-verified 2026-11-23]. Dev-side adoption measurement.
- GOV.UK Design System, homepage. https://design-system.service.gov.uk/ [accessed 2026-11-23]. GDS maintenance, community-driven model, 12-month roadmap, "What's new" release communication.
- GOV.UK Design System, *Button component*. https://design-system.service.gov.uk/components/button/ [accessed 2026-11-23]. "Recent changes" changelog table and "Help improve this component" contribution route.
- Style Dictionary. https://styledictionary.com and https://github.com/style-dictionary/style-dictionary [accessed 2026-11-23 / search-verified 2026-11-23]. Versioned-release and migration-guide practice.
- Decision-record format (context / options / decision / consequences) and the maturity-to-governance mappings: synthesis of the sources above with general professional practice.
