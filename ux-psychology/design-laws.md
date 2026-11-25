# Design Laws and Psychological Principles

## 1. What is it?

A working catalogue of the psychological effects and "laws" most often cited in interface and experience design, each reduced to six operational parts: what it claims, why it matters, a concrete frontend example, when it applies, how it is misapplied, and the review question that tests a build against it. The set covers the twenty effects named in the library's frontend mission (aesthetic-usability effect, laws of proximity, similarity, common region, uniform connectedness and Prägnanz, Von Restorff effect, Zeigarnik effect, Tesler's law, serial position effect, progressive disclosure, goal-gradient effect, recognition over recall, Pareto principle, Occam's razor, Parkinson's law, paradox of the active user, cognitive load, default effect, peak-end rule). The Gestalt grouping laws (proximity, similarity, common region, uniform connectedness, Prägnanz) are treated fully in [../foundations/gestalt-and-perception.md](../foundations/gestalt-and-perception.md); this file records their interface-facing application and defers the perceptual theory there. The interaction-timing laws (Fitts's law, Hick's law, Doherty threshold) live with motion in [../motion-and-interaction/motion-principles.md](../motion-and-interaction/motion-principles.md); Jakob's law is already covered in [../ui-ux/ux-fundamentals.md](../ui-ux/ux-fundamentals.md) §3.9. This file is the map of what remains.

The canonical reference for most entries is Jon Yablonski's *Laws of UX* (lawsofux.com), a freely accessible compendium that cites the primary psychology for each effect. Where a law is a borrowed heuristic from economics or management rather than an established perceptual or cognitive finding, the entry says so — the library's claim-strength discipline ([../references/source-accessibility.md](../references/source-accessibility.md)) applies here too.

## 2. Why does it matter?

Agents that know the names of laws but not their limits produce cargo-cult interfaces: every third card gets a "Von Restorff accent", every form gets a fake progress bar because "Zeigarnik", every page gets a badge because "aesthetic-usability". The laws are real, but each was established in a specific experimental context, and several are routinely over-claimed. Used honestly, they are the fastest route from "the layout feels wrong" to a specific, fixable diagnosis — they name *why* a dense settings page exhausts users (cognitive load), *why* the last item of a nav bar is over-clicked (serial position), and *why* a default state silently steers the majority of users (default effect).

There is also an evaluation dividend. The review question attached to each law converts a vague aesthetic complaint into a checkable defect: "the pricing table hides the annual discount until the fourth step" becomes a goal-gradient and progressive-disclosure finding with a concrete fix. The catalogue therefore doubles as a checklist vocabulary for [../evaluation/design-quality-framework.md](../evaluation/design-quality-framework.md).

## 3. Core principles — the catalogue

Each entry: **Claim → Why it matters → Frontend example → Applies when → Misapplied when → Review question.** Grouping laws marked \[G\] defer to [../foundations/gestalt-and-perception.md](../foundations/gestalt-and-perception.md) for the perceptual mechanism.

### 3.1 Aesthetic-usability effect

**Claim:** users perceive more-attractive interfaces as easier to use, and tolerate minor usability faults in them. Established experimentally by Kurosu and Kashimura (1995) and replicated by Tractinsky. **Why:** aesthetics set expectations; a confident first impression buys patience for friction elsewhere. **Example:** a beautifully typeset onboarding screen with a slightly awkward stepper still completes; the same stepper on a cluttered screen reads as broken. **Applies when:** forming first impressions, marketing surfaces, choosing between two acceptable layouts. **Misapplied when:** used to excuse real defects ("it's pretty, users won't mind") — the effect does not survive repeated task failure. **Review question:** does the first screen look deliberate enough that users give the flow a chance?

### 3.2 Law of proximity \[G\]

**Claim:** objects near each other are perceived as a group. **Frontend application:** spacing communicates structure — related items sit closer than unrelated ones; a card's label hugs its card. Misapplied when equal spacing everywhere makes unrelated controls read as one group. **Review question:** does every grouping on this page read correctly with the label text hidden?

### 3.3 Von Restorff effect (isolation effect)

**Claim:** the item that differs most from its surroundings is the one remembered. **Why:** distinctiveness drives attention and recall — the basis of the single-accent rule. **Example:** one filled "Pro" card among three outlined pricing cards; one accent colour in an otherwise monochrome palette. **Applies when:** you genuinely want one thing seen first. **Misapplied when:** everything is emphasised (no isolation possible), or when the isolated item is not the actually important one. **Review question:** if only one element on this screen may stand out, is it the one that currently does?

### 3.4 Zeigarnik effect

**Claim:** interrupted or incomplete tasks are remembered better than completed ones (established by Bluma Zeigarnik, 1927, on waiters' unpaid orders; the *motivational* reading — that incompletion creates tension that drives resumption — is the stronger modern claim and is used in product design). **Example:** a profile-completion meter ("2 of 3 steps left"); a draft post marked "unsent"; a partially-filled progress indicator. **Applies when:** a user has begun something and a gentle reminder of the remainder helps them finish. **Misapplied when:** manufacturing false incompleteness (endless gamified meters) — annoyance and distrust follow, and dark-pattern reviews call it out. **Review question:** if a user abandons halfway, does anything honestly show them where they stopped and what remains?

### 3.5 Tesler's law (conservation of complexity)

**Claim:** every system has an irreducible amount of complexity; it can only be moved, between users, designers and engineers — not eliminated. **Why:** it reframes simplification: the question is never "how do we remove this complexity" but "who should carry it". **Example:** a smart default (date inferred from context) moves complexity from every user to the engineer once; a custom-configuration panel moves it to every user. **Applies when:** deciding between flexible-but-configurable and opinionated-but-simple. **Misapplied when:** used to justify hiding necessary control from expert users, or to push complexity onto users who cannot carry it. **Review question:** for each piece of irreducible complexity, have I chosen deliberately who carries it?

### 3.6 Law of Prägnanz \[G\]

**Claim:** people organise ambiguous shapes into the simplest form available. **Frontend application:** ambiguous layouts resolve as the simplest reading — which is why near-misses in alignment (a column 2 px off) are perceived as sloppy rather than unnoticed. **Review question:** at a squint, does every region of this page resolve into a simple, intended shape?

### 3.7 Serial position effect

**Claim:** items at the beginning (primacy) and end (recency) of a sequence are recalled best; the middle is weakest. **Example:** the first and last items of a horizontal nav bar get disproportionate attention; the first two and last option in a long dropdown are chosen most. **Applies when:** ordering nav items, lists, form steps, pricing columns. **Misapplied when:** important actions are buried mid-list, or when recency is the only consideration (primacy still dominates on long pages). **Review question:** are the two most important items in this list or menu at its ends?

### 3.8 Progressive disclosure

**Claim:** show users what they need now, defer the rest behind an explicit step or affordance. Championed in usability practice by the Nielsen Norman Group. **Example:** an advanced-options disclosure on a search form; a checkout that asks for shipping before account details; settings surfaces split by frequency of use. **Applies when:** one flow serves novices and experts, or a form's later fields depend on earlier answers. **Misapplied when:** the hidden layer contains what most users need (disclosure becomes a hiding place), or disclosure depth exceeds three levels. **Review question:** what does the *first-time* user see on each screen, and is everything else behind an honest, labelled affordance?

### 3.9 Law of common region \[G\]

**Claim:** elements inside the same bounded region are perceived as grouped, independent of distance. **Frontend application:** cards, panels and section backgrounds group content without needing tight spacing — the tool for grouping when density is high. **Review question:** does every visual boundary on this page enclose exactly the set of things it should?

### 3.10 Goal-gradient effect

**Claim:** effort toward a goal accelerates as the goal nears (established in animal and human behaviour research; Clark Hull's 1932 work is the canonical anchor; applied reading: members buy faster as they near a reward). **Example:** a loyalty progress bar that is pre-started at 20% ("you're already on your way"); a checkout that shows "one step left". **Applies when:** multi-step flows the user has already entered. **Misapplied when:** the bar lies (pre-started progress that represents nothing real) — this crosses from UX into dark-pattern territory and erodes trust on discovery. **Review question:** does the interface make remaining progress visible and true?

### 3.11 Law of similarity \[G\]

**Claim:** items that look alike (colour, shape, size) are perceived as related. **Frontend application:** one card style for one kind of thing; a shared accent for all interactive elements. Misapplied when similarity is accidental — two unrelated components that look alike are read as the same. **Review question:** do all elements that share a style actually share a behaviour?

### 3.12 Recognition over recall

**Claim:** recognising something seen before is easier than recalling it from memory; interfaces should surface options rather than demand memory. Established in human-factors tradition (Heckel, 1991; Nielsen's heuristics rest on it). **Example:** a visible menu beats a hamburger hiding the primary sections; autocomplete suggestions beat remembering exact search syntax; icons with labels beat icons alone. **Applies when:** any navigation, command surface or form where users must supply information the system could offer. **Misapplied when:** everything is surfaced at once (cognitive overload — see 3.18). **Review question:** what does this interface make the user remember that it could show them instead?

### 3.13 Pareto principle (80/20)

**Claim:** roughly 80% of effects come from 20% of causes — in product terms, a small share of features and content carries most usage. Borrowed from economics (Vilfredo Pareto's land-ownership observations, 1896); the exact ratio is illustrative, not measured per product. **Example:** optimising the three flows analytics shows dominate sessions before polishing the long tail. **Applies when:** prioritising under constrained effort. **Misapplied when:** the ratio is asserted from intuition rather than usage data, or used to abandon minority needs with legal or safety weight (accessibility is a long tail that must not be cut). **Review question:** which 20% of this surface does the usage evidence actually concentrate on, and does the design spend its polish there?

### 3.14 Occam's razor

**Claim:** among competing explanations or solutions, prefer the one with fewer assumptions — in design, the simplest sufficient option. A principle of reasoning (attributed to William of Ockham, 14th century), not a psychological finding. **Example:** a system that works with one modal state beats one needing three coordination rules; CSS that uses platform features beats a custom framework reproducing them. **Applies when:** comparing roughly equal candidates. **Misapplied when:** simplicity is pursued past sufficiency — the simplest option that fails the requirement is not the better one, and "fewer assumptions" is not the same as "fewer features the user asked for". **Review question:** what assumption does each remaining piece of this design exist to satisfy, and could one go?

### 3.15 Parkinson's law

**Claim:** work expands to fill the time available (Cyril Northcote Parkinson, 1955, as satire of bureaucracy). Borrowed from management; in design it is a *process* heuristic, not a UI principle. **Example:** a redesign scoped to "one week" grows to fill the week even where the work needed three days — so scope by deliverable, not duration. **Applies when:** planning iterations and deciding when a design is done. **Misapplied when:** used to excuse rushed interfaces ("more time would not have helped") or to compress genuinely open exploration. **Review question:** is this deadline bounded by a deliverable definition, or is the work simply expanding?

### 3.16 Law of uniform connectedness \[G\]

**Claim:** elements visually connected (lines, containers, shared edges) are perceived as more related than unconnected ones. **Frontend application:** a visible connector between a step and its detail communicates relationship; breadcrumbs connected to the current page read as its path. **Review question:** are visual connections drawn only where a relationship truly exists?

### 3.17 Paradox of the active user

**Claim:** users, wanting to get started, skip reading instructions and orientation material and dive into trial-and-error instead. Established usability research (Carroll and Rosson, 1987). **Example:** nobody reads the "Start here" card; onboarding tooltips are dismissed before being read; a documentation link inside the first screen gets negligible traffic. **Applies when:** designing onboarding, empty states and help. **Misapplied when:** fighting the paradox by forcing tutorials on users (interstitials punish the behaviour), rather than designing the product so trial-and-error succeeds. **Review question:** if users skip every explanation and act immediately, does the first action still lead somewhere sensible?

### 3.18 Cognitive load

**Claim:** working memory is severely limited (Miller's 7±2 chunk estimate is the classic anchor; modern work puts real capacity lower still — Sweller's cognitive-load theory is the design-relevant formulation); interfaces that demand holding many items, modes or decisions at once exceed it. **Example:** a form that asks for twelve fields in one screen versus three grouped steps; a dashboard with sixteen equally weighted widgets versus three primary tiles and a linked detail surface. **Applies when:** always — it is the budget every screen spends. **Misapplied when:** "reducing load" becomes removing necessary information (progressive disclosure, 3.8, is the complement, not the substitute). **Review question:** what must a user hold in mind simultaneously at the worst moment on this screen, and can any of it be externalised?

### 3.19 Default effect (default bias)

**Claim:** people overwhelmingly accept pre-selected options; defaults are powerful steerage. Established in behavioural economics (organ-donation consent-rate studies are the famous natural experiment). **Example:** the pre-checked "annual billing" plan; a default theme; a pre-selected region. **Applies when:** choosing what the majority should experience. **Misapplied when:** defaults are chosen for the vendor's benefit against the user's interest — pre-checked marketing consents are the canonical dark pattern and are illegal in several jurisdictions for essential cookies. **Review question:** does every default in this interface match what the user would most likely choose if asked?

### 3.20 Peak-end rule

**Claim:** people judge an experience by its most intense moment (the peak) and its final moment (the end), not its average. Established by Kahneman and colleagues (the cold-water experiments, 1993). **Example:** the checkout's final confirmation screen and the moment of error recovery weigh disproportionately in how the product is remembered; a delightful success animation after a stressful form repairs the whole flow's reputation. **Applies when:** choosing where to spend motion and copy effort in a flow. **Misapplied when:** decorating the average screens while the peak (the error state!) is unconsidered. **Review question:** what are the peak and final moments of this flow, and are they the best-designed screens in it?

## 4. How it works — separating claim strength

The library's four claim strengths ([README](../README.md) §G) sort the catalogue into three honest tiers:

| Tier | Members | Status |
| --- | --- | --- |
| Established perceptual / cognitive findings | Proximity, similarity, common region, uniform connectedness, Prägnanz, serial position, Von Restorff, Zeigarnik, recognition over recall, cognitive load, peak-end rule, goal-gradient, aesthetic-usability, paradox of the active user, default effect | Experimental bases exist; magnitudes vary by context, so treat as strong defaults, not absolutes |
| Established usability practice | Progressive disclosure, Tesler's law | Grounded in usability research and professional consensus rather than single experiments |
| Borrowed heuristics | Pareto, Occam's razor, Parkinson's law | Productive reasoning tools from economics, philosophy and management — useful for prioritisation, not evidence about users |

Two disciplines follow. First, when writing for users or stakeholders, do not upgrade a borrowed heuristic into psychology: "80% of value comes from 20% of features" is a prioritisation saying, not a measurement of your product. Second, when an effect and the project context conflict, the context wins — a dense trading dashboard serves expert users whose cognitive-load budget differs from a consumer app's; the law describes the average case, not a ceiling on good judgement.

## 5. Practical application — using the catalogue in a build

**During direction.** Pick the three or four laws that will actually shape the build and write them into the plan as named constraints: a checkout inherits goal-gradient, peak-end and default effect; a settings surface inherits progressive disclosure, cognitive load and recognition over recall; a marketing hero inherits aesthetic-usability and Von Restorff. Named constraints can be checked; vibes cannot.

**During implementation.** Each named law becomes a construction rule: default effect → audit every `default`/`selected`/`checked` prop against "what would the user choose?"; recognition over recall → every icon gets a label, every command surface is searchable; Zeigarnik → every multi-step flow carries a truthful progress indicator.

**During review.** The review questions in §3 form a pass that complements the visual QA pass in [../evaluation/website-visual-qa.md](../evaluation/website-visual-qa.md): one is about what the pixels do to perception, this one is about what the flow does to memory, effort and honesty. Both run before delivery; findings merge into one defect list.

## 6. Decision framework

When a screen "feels wrong" but no defect is found, diagnose through the laws in order of likely yield:

1. **Too much at once?** → cognitive load; count simultaneous items, decisions and modes; apply progressive disclosure where depth exists.
2. **Nothing stands out?** → Von Restorff; pick the one element that deserves isolation and demote the rest.
3. **Everything stands out?** → same law, opposite failure; establish the neutral majority.
4. **Groupings misread?** → proximity, similarity, common region; fix spacing and boundaries before adding labels.
5. **Users abandon mid-flow?** → goal-gradient (is progress visible and true?), serial position (is the next step where attention naturally lands?), Zeigarnik (does abandonment leave an honest resumption point?).
6. **Users ignore help?** → paradox of the active user; redesign the first action instead of the explanation.
7. **Users mistrust the flow?** → default effect (are defaults honest?) and Zeigarnik (is the incompleteness real?).

Stop diagnosing when a specific law names the defect; the fix belongs to the domain file for that defect, not to more psychology.

## 7. Examples

**Example 1 — a sign-up flow rebuilt through three laws.** The original: a single screen with nine fields, a pre-checked newsletter consent and a "Submit" at the end. Diagnosis: cognitive load (nine simultaneous decisions), default effect (the consent default serves the vendor, not the user), peak-end (the final screen is a bare "Thanks" after the flow's most stressful screen). Rebuild: three grouped steps with the account question first, defaults set to the user's likely answer (country from locale), and a final screen that states what happened and what happens next, carrying one deliberate moment of visual polish. The laws named the defects; the fixes came from forms and flow practice.

**Example 2 — a pricing page misapplying Von Restorff.** All three plans are visually identical except the middle card, which is filled, larger and accent-coloured — yet the analytics show most users choose the leftmost plan, because the accent card is the *expensive* one and the isolation effect is steering attention to the offer the business wants, not the one most users need. The review question "is the isolated element the one that should stand out?" exposes the mismatch; the fix is to isolate the *recommended* plan or to accept the honest pattern of equal cards with a comparison table.

## 8. Common mistakes

- **Naming a law instead of locating a defect.** "That violates Hick's law" without counting the actual options is vocabulary, not analysis. Every entry here ends in a checkable question; use it.
- **Applying borrowed heuristics as user research.** Pareto and Parkinson describe effort and priority, not users; they carry no experimental evidence about interfaces.
- **Designing for the remembered average.** The peak-end rule says judgement concentrates on peak and end; teams polish the middle screens where no memory forms.
- **Steering with dishonest defaults and fake progress.** The default effect and goal-gradient are the two laws most often converted into dark patterns; both misuses are trust-destroying and, for consent defaults, legally exposed.
- **Fighting the active user.** Interstitial tutorials, forced tours and read-before-use gates punish the documented behaviour instead of designing for it.
- **Stacking emphasis.** Von Restorff requires a background; when every card, badge and CTA is accented, the page has no hierarchy at all — the failure mode the hierarchy rules in [../typography/typographic-hierarchy.md](../typography/typographic-hierarchy.md) exist to prevent.

## 9. Evaluation checklist

- [ ] Three or four applicable laws named in the plan, with the screens they govern.
- [ ] Every pre-selected option matches what the target user would most likely choose.
- [ ] Every multi-step flow shows true, visible progress; no manufactured incompleteness.
- [ ] The most important items of menus and lists sit at their ends, not the middle.
- [ ] Exactly one level of emphasis dominates each screen; the neutral majority is genuinely neutral.
- [ ] Options the system could offer are surfaced (recognition), not demanded from memory (recall).
- [ ] The flow's peak and final moments are deliberately designed, including error recovery.
- [ ] Users who skip all explanation and act immediately reach a sensible outcome.
- [ ] Simultaneous decisions per screen counted; depth deferred through labelled disclosure.
- [ ] Borrowed heuristics (Pareto, Occam, Parkinson) appear only in process reasoning, never as claims about users.

## 10. Related topics

- [Gestalt and perception](../foundations/gestalt-and-perception.md) — the perceptual mechanism behind the four grouping laws.
- [UX fundamentals](../ui-ux/ux-fundamentals.md) — heuristics, mental models and Jakob's law; the broader experience layer.
- [Motion principles](../motion-and-interaction/motion-principles.md) — Fitts's law, Hick's law and the Doherty threshold in their timing context.
- [Design quality framework](../evaluation/design-quality-framework.md) — where these review questions merge with visual findings.
- [UI fundamentals](../ui-ux/ui-fundamentals.md) — component-level implementation of disclosure, defaults and states.
- [Information hierarchy](../information-design/information-hierarchy.md) — the structural counterpart of the emphasis laws.

## 11. References

- Jon Yablonski, *Laws of UX* — compendium pages for the aesthetic-usability effect, common region, Prägnanz, proximity, serial position, similarity, Tesler's law, uniform connectedness, Von Restorff effect, Zeigarnik effect, progressive disclosure, recognition over recall, Pareto principle, Occam's razor, Parkinson's law, peak-end rule and their primary citations. https://lawsofux.com/ [accessed 2026-11-25]
- Kurosu, M. and Kashimura, K. (1995), "Apparent usability vs. inherent usability" — the aesthetic-usability experiment. Cited by lawsofux.com's aesthetic-usability entry. [search-verified, accessed 2026-11-25]
- Kahneman, D., Fredrickson, B., Schreiber, C. and Redelmeier, D. (1993), "When More Pain Is Preferred to Less" — the peak-end experiments. Cited by lawsofux.com's peak-end rule entry. [search-verified, accessed 2026-11-25]
- Carroll, J. and Rosson, M. (1987), "Paradox of the Active User" — the source of the active-user finding. Cited via usability literature. [canonical]
- Sweller, J. (1988), "Cognitive Load During Problem Solving" — cognitive-load theory. [canonical]
- Hull, C. (1932), *Goal Gradient Hypothesis* — the goal-gradient anchor. Cited via lawsofux.com and behavioural literature. [canonical]
- Nielsen Norman Group, "Progressive Disclosure" article corpus — the practice framing. https://www.nngroup.com/articles/progressive-disclosure/ [search-verified, accessed 2026-11-25]
- Parkinson, C. N. (1955), "Parkinson's Law", *The Economist* — the original satirical statement. [canonical]
- The tier table (§4) and the six-part entry format are this library's synthesis; the underlying claims carry the tags above.
