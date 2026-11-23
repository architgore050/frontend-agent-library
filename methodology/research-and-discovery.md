# Research and discovery

## 1. What is it?

Research and discovery is the set of activities that turns an ambiguous design brief into an informed one: gathering existing knowledge, listening to stakeholders, characterising the audience, scanning the competitive landscape, and auditing the visual material that already exists. It is the Discover/Empathise phase made concrete — see [Design thinking](design-thinking.md) for where it sits in the process.

Discovery is not academic research. Its test is always practical: does this finding change what we will design? A finding that cannot be connected to a design decision is trivia; a finding that changes a decision is evidence.

## 2. Why does it matter?

Design decisions made without discovery are guesses wearing confident typography. Three failure patterns recur: (1) the output targets the wrong audience because nobody checked who actually uses the artefact; (2) the output clashes with an existing brand because nobody looked at the brand's real, current assets; (3) the output reinvents conventions the audience already knows, because nobody scanned what the landscape looks like. All three are cheap to prevent and expensive to repair.

For an agent, discovery is also the antidote to a specific temptation: generating something beautiful immediately. Generation is the cheapest part of the work; a wrong direction discovered late wastes every hour spent on it. One round of focused discovery routinely changes the whole design strategy — for example, discovering that the "modern minimalist" reference the client likes contradicts the brand's heritage positioning.

## 3. Core principles

- **Design-relevance over completeness.** Collect what changes decisions, not everything knowable. Depth where the risk is high, breadth where it is low.
- **Provenance discipline.** Every finding is recorded with its source. An unsourced claim is an assumption wearing a finding's clothes — label it as an assumption.
- **Evidence is decision-specific.** What counts as strong evidence for a colour choice differs from what counts for a navigation choice (see §4.5). Matching evidence strength to decision type is the core skill.
- **Synthesis, not collection.** The deliverable of discovery is not a pile of links; it is a short list of implications. Raw findings only matter once converted ("finding → so what → design implication").
- **Constraints are findings too.** Budget, deadline, fixed logo, mandatory fonts, print partner's capabilities — constraints shape design more than inspirations do. Capture them explicitly.
- **Distinguish facts, conventions and preferences.** "WCAG AA requires 4.5:1 for body text" is a fact; "15px minimum body size is a common web convention" is a convention; "the CEO dislikes green" is a stakeholder preference — real, but a different category with different authority. See the epistemics discipline in [Design critique](../foundations/design-critique.md).

## 4. How it works

### 4.1 Secondary research

Secondary research is gathering existing knowledge before generating new questions. For design work it includes: brand guidelines and past campaign material; the organisation's own analytics and support tickets; published design research (e.g. Nielsen Norman Group articles on reading patterns and usability conventions); accessibility standards (WCAG documents); and platform documentation (social-media image sizes, email client capabilities).

Method: start from the brief's nouns. Each noun (audience, product, event, medium) generates search queries; each result is saved with URL and date. Stop when new searches return material you already have — that is the completeness signal.

### 4.2 Stakeholder input

Stakeholders carry three kinds of information, and the agent should ask for each deliberately: (1) **facts** — budgets, deadlines, mandated assets, technical constraints; (2) **objectives** — what the artefact must achieve, ranked ("this page exists to drive registrations"); (3) **preferences** — likes and dislikes, which are data about taste and politics, not truth about the audience. Record all three, but keep them in separate lists. The classic stakeholder failure is letting one person's preference silently overwrite an objective.

Practical question set: Who is this for? What must it make them do or feel? What exists already and must be respected? What has failed before? What is fixed, and what is open? What does success look like, measurably?

### 4.3 Audience analysis

Audience analysis converts "users" into a characterised group whose perception you can reason about. Working tools:

- **Segments:** 2–4 named groups with distinct needs (e.g. "first-time visitors deciding whether to attend" vs "returning attendees looking for the schedule"). Each artefact can then be judged per segment.
- **Context of use:** device, environment, urgency, prior knowledge. A schedule read on a phone at a crowded venue has different requirements from one browsed at a desk.
- **Literacy and language:** technical vocabulary, reading level, locale conventions (date formats, name order).
- **Accessibility profile:** expected range of vision, hearing, motor ability; this links to the standards in the accessibility domain.

Personas are a synthesis device, not a truth claim: a persona is only useful if it is traceable back to specific findings and is used to test decisions ("would segment B understand this label?").

### 4.4 Competitive and landscape scan

A landscape scan answers: what do comparable organisations do, and where is the opportunity to differ or to conform? Method: pick 5–10 relevant comparators (real competitors for a product, peer events for an event brand); for each, capture the visual facts — palette, typography feel, imagery style, density, tone of voice. Then read the pattern: if 9 of 10 use cool blues and sans-serifs, a warm palette is differentiation and a cool palette is conformity — either can be right, but it is now a *choice* with a stated reason, not a default.

Two cautions. First, popularity is not evidence of quality — only evidence of convention; violating a convention costs comprehension, so name that cost when you accept it. Second, a screenshot of a competitor's homepage is copyrighted material: use it for analysis, never as source imagery.

### 4.5 Evidence quality by decision type

Not all design decisions need the same proof. The table below is the working standard for this repository.

| Decision type | Strong evidence | Weak but usable | Not evidence at all |
| --- | --- | --- | --- |
| Colour (brand palette) | Existing brand guidelines; the fixed logo's actual colours (sampled, not remembered); WCAG contrast mathematics; documented cultural associations for the target locale | Competitor palette scans; long-standing industry conventions | "It looked nice on the moodboard"; unverified hex values quoted by an AI tool (see [AI-assisted design](ai-assisted-design.md)) |
| Colour (UI state colours) | WCAG contrast ratios, verified programmatically; platform conventions (error red, success green) with verified examples | General practice labelled as convention | Aesthetics alone |
| Typography | Mandated brand fonts (with licence status); readability research on size/line-length conventions | Pairing conventions; type classification logic | A model's claim that a font "pairs well" without seeing the rendering |
| Navigation / IA | Usability testing; analytics (search failures, drop-offs); card-sorting results; established conventions (e.g. logo links home) | Expert heuristics | Stakeholder preference alone |
| Imagery | Licence status; brand-fit audit against the attribute rules; real audience testing | Style conventions of the sector | Availability |
| Layout / density | Reading-pattern research; measured viewport behaviour; content-requirements analysis | Grid conventions | Whitespace "feels right" without checking the objective |

The pattern: for **objective, verifiable** decisions, evidence is measurement or a primary standard. For **stylistic** decisions, evidence is alignment with brand attributes and audience expectations — and is honestly labelled as judgment. For **legal** decisions (licences, marks), only primary documents count.

### 4.6 Visual audit

A visual audit is the discovery step specific to brand work — and essential for the repository's reference scenario of extending a fixed event logo. Steps:

1. **Inventory** every existing brand asset: logo files (all variants), fonts in use, colour specifications, photography, illustration, templates, social channels, print collateral.
2. **Sample, do not guess:** extract actual hex values from the logo file; identify the typeface or its closest classification; note spacing and shape language (see [Colour theory](../colour/colour-theory.md)).
3. **Assess consistency:** list contradictions (three different blues in circulation; a serif the guidelines no longer allow).
4. **Classify each element: fixed / flexible / deprecated.** This classification is the contract that the rest of the design must respect.
5. **Write the audit as implications:** "logo uses a deep teal (sampled #16403C) and a geometric sans; therefore the kit's palette must harmonise with that teal, and headline type should stay geometric."

### 4.7 Synthesis techniques

Synthesis converts raw findings into design fuel. Working techniques:

- **Affinity mapping:** write each finding on one note; cluster notes that feel related; name each cluster; clusters become themes ("audience skews mobile-first", "brand assets inconsistent").
- **The implication chain:** for each theme, force the sentence "This means our design must…" — "the audience skews mobile-first" → "the design must be composed for narrow viewports first, with the desktop as the extension". If you cannot finish the sentence, the finding is not yet usable.
- **Insight statements:** one-sentence formulations of a non-obvious truth plus its consequence, e.g. "Attendees use the schedule during the event on phones in noisy rooms, so glanceability outranks completeness."
- **Constraint extraction:** list every fixed, mandated or impossible item as a design constraint, phrased so a designer can act on it.
- **"How might we" prompts:** convert each implication into a generative question for [Ideation](ideation.md).

The discovery deliverable is then short: problem statement, audience characterisation, constraint list, design implications, and open questions — one page, not a binder.

## 5. Practical application

### 5.1 Proportionality

Scale discovery to the decision's cost. Extending a fixed logo into a kit for a known audience: audit the assets, characterise the audience from stakeholder knowledge plus any survey data, scan five peer events — half a day. A new product's first identity: the full set, including competitive scans and audience interviews, over days. The error to avoid is symmetric: over-researching a badge design, or rebranding a hospital on vibes.

### 5.2 Worked micro-example

Brief: "make a landing page for a two-day design conference; we already have a logo."

1. **Stakeholder input:** objective is registrations; deadline is six weeks; logo is fixed; venue announced.
2. **Audience analysis:** segments — design students (price-sensitive, mobile), senior designers (content-judging, skim talks list), sponsors (scanning visibility).
3. **Landscape scan:** five comparable conference sites: dark themes dominate, schedules are tables, early-bird pricing is above the fold.
4. **Visual audit:** logo samples to two colours (#1B2A4A navy, #E8B23A amber — sampled from the supplied file, illustrative); type is a geometric sans.
5. **Implications:** mobile-first composition; contrast must be verified against the amber on light backgrounds; pricing must be visible without scrolling on mobile; differentiation opportunity: light theme with amber accents against the dark-theme convention, justified by the logo's own light-dark balance.
6. **Open question:** are session titles final? (affects placeholder policy).

## 6. Decision framework

| Question | If yes | If no |
| --- | --- | --- |
| Do existing brand assets exist? | Run the visual audit first; treat it as the constraint contract | Discover what the organisation *wants* to signal before generating |
| Is the audience known with evidence? | Characterise segments and contexts | Treat audience assumptions as open questions; flag them in the brief |
| Is this decision objective-verifiable? | Get primary-source evidence or measure it | Use alignment-with-attributes reasoning and label it as judgment |
| Is the finding decision-relevant? | Record it as an implication | Record it as trivia or drop it |
| Do stakeholders disagree? | Return to objectives and criteria (see [Moodboards](moodboards.md) §7 on feedback) | — |
| Is something legal or rights-bearing involved? | Only primary documents count; human approval required (see [AI-assisted design](ai-assisted-design.md)) | — |

## 7. Examples

- **Event kit extension:** the visual audit in §5.2 is the canonical example — a fixed logo turns discovery into a constraint-harvesting exercise, and every later moodboard direction must declare harmony with the sampled colours (see [Moodboards](moodboards.md)).
- **Rebrand with legacy:** an audit finds the logo, a deprecated 2010 wordmark, and a current website using an unlicensed font. Findings: one colour contradiction, one legal risk. Implications: palette must resolve around the logo's sampled colours; the font must be replaced with a licensed alternative — a decision class requiring human approval (see [AI-assisted design](ai-assisted-design.md)).
- **Navigation redesign:** analytics show 30% of site searches are for "prices". Evidence class: strong (measured behaviour). Implication: pricing enters the primary navigation, regardless of stakeholder preference for a minimal menu.

## 8. Common mistakes

- **Research theatre:** collecting thirty links and never writing a single implication. Findings without "this means…" sentences are decorative.
- **Letting a preference masquerade as evidence.** "The director says blue" is a fact about the director, not about the audience. Record it, weigh it, and be explicit when it overrides evidence.
- **Skipping the audit because "the logo is enough".** Without sampling the actual colours and type, every downstream choice harmonises with a memory, not the asset.
- **Copying the landscape.** A competitive scan informs positioning; imitating the top competitor's visual system produces generic work and, at worst, copied trade dress.
- **Unverified "facts" from AI tools.** Sizes, ratios and standards quoted by a model must be re-verified against primary sources (see [AI-assisted design](ai-assisted-design.md)).
- **Asking leading questions.** "Do you like the modern option?" measures politeness. Ask about attributes and behaviour instead.
- **Analysis without deadline.** Discovery has a budget; when new searches stop changing decisions, stop searching.

## 9. Evaluation checklist

- [ ] Every claim that shaped a decision has a source (URL, document, or named stakeholder) or is explicitly labelled an assumption.
- [ ] The audience is characterised into segments with contexts of use, not a single generic "user".
- [ ] Existing brand assets were inventoried and sampled (actual values, not descriptions from memory).
- [ ] A landscape scan was performed and *read* — the pattern is stated, and conform/differ is a stated choice.
- [ ] Each major finding has an implication sentence ("this means the design must…").
- [ ] Facts, conventions and stakeholder preferences are kept in separate lists.
- [ ] Legal/rights items (fonts, imagery, marks) were flagged for human verification.
- [ ] The discovery deliverable fits on roughly one page: problem statement, segments, constraints, implications, open questions.

## 10. Related topics

- [Design thinking](design-thinking.md) — the process frame discovery lives in.
- [Ideation](ideation.md) — what consumes discovery outputs next.
- [Moodboards](moodboards.md) — how implications become visual directions.
- [Brand discovery](../branding/brand-discovery.md) — the branding-domain treatment of stakeholder and attribute discovery.
- [Design critique](../foundations/design-critique.md) — the judgment vocabulary used when weighing evidence.
- [Colour theory](../colour/colour-theory.md) — for sampling and reasoning about palette findings.
- [AI-assisted design](ai-assisted-design.md) — verification duties when AI supplies research summaries.

## 11. References

- This file is a synthesis of the sources below and of standard professional practice; no single source owns the method.
- Nielsen Norman Group, "Design Critiques: Encourage a Positive Culture to Improve Design Work" (2016) — rules and expectations before review; relevant to stakeholder questioning discipline. `[search-verified]` https://www.nngroup.com/articles/design-critiques (accessed 2026-11-23)
- Stanford d.school, *An Introduction to Design Thinking: Process Guide* — empathise mode (observation, engagement, immersion) framing. `[search-verified]` https://web.stanford.edu/~mshanks/MichaelShanks/files/509554.pdf (accessed 2026-11-23)
- IDEO, human-centred design field guides — audience research and "How might we" synthesis methods. `[canonical]`
- W3C, *Web Content Accessibility Guidelines (WCAG)* — the primary standard for contrast and accessibility evidence. `[canonical]`
- Victor S. Johnston / general consumer-research literature on colour association — cultural colour associations should be sourced per locale before use; treat as assumption until verified. `[canonical]` (attribution general; verify per project)
