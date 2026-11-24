# Art Direction

## 1. What is it?

Art direction is the discipline of making — and defending — the visual decisions that keep a brand's output coherent: what the imagery shows, how the graphic language is applied, which style register leads on which surface, and what "good" looks like for this project. The art director is the owner and arbiter of the visual system in use: the person (or documented role) who translates brand personality into consistent choices across posters, photography, illustration, interfaces and environments, and who says no to beautiful work that does not fit.

Art direction is not a style (see [Visual styles](visual-styles.md)) and not a set of assets (see [Graphic language](graphic-language.md)). It is the *decision-making layer* above both: the style is a position, the language is a vocabulary, and art direction is the judgement that deploys them, project after project, so the audience experiences one brand rather than a sequence of related experiments. Photographic art direction — casting, lighting, crop conventions — has its craft detail in [Photography](../imagery/photography.md); this file owns the direction discipline itself, which supervises photography, illustration, 3D and graphic treatment alike.

## 2. Why does it matter?

**Consistency is a production problem, not just a taste problem.** Every project invites a hundred small decisions: how cropped can a face be, how loud may the pattern be, which blue is "the" blue under a hot lamp, how much energy may a detail page carry. Without a directing layer, each decision is renegotiated per artefact, and the output drifts — slowly enough that nobody notices a single asset, and unmistakably when twenty are viewed together. Art direction exists to make those decisions *once*, well, and then to enforce them.

**Brands are experienced as aggregates.** The audience never sees the style guide; it sees the poster, then the website, then the venue signage. Coherence across that sequence is what builds recognition and trust (the mechanism behind the graphic-language tests in [Graphic language](graphic-language.md), section 4.4). A brand with strong individual artefacts and weak direction reads as unstable; a brand with modest artefacts and strong direction reads as professional.

**Direction scales scarce attention.** For distributed teams — volunteers, agencies, regional offices, AI generation pipelines — documented art direction replaces per-artefact supervision: people who never meet the art director can still produce work that fits, because the treatment rules and reference boards answer most questions in advance. This is the same logic as the vocabulary ruleset, applied to imagery and campaign choices.

## 3. Core principles

### 3.1 Translate, do not describe

The core skill is translation: turning brand attributes into executable visual instructions. "Warm and local" is not direction; "natural light, medium close crops, real staff and real venue, no stock-office settings, photography warm-biased with palette-consistent grade" is. Every attribute the brand claims should end in at least one *do* and one *don't* that a contributor can follow without taste. The translation table (section 4.1) is the central tool, and its logic is shared with attribute-derived vocabularies in [Graphic language](graphic-language.md), section 4.1.

### 3.2 Define "good" before work starts

Direction is judged work, and judged work needs criteria fixed in advance: reference boards showing the target quality, treatment rules naming the parameters, and acceptance tests stating what passes. Criteria fixed after work starts are rationalisation. The pre-work artefacts (section 4.2) are what make art direction enforceable rather than charismatic.

### 3.3 One voice, assigned registers

Across the brand there is one voice; across surfaces there are assigned registers — loud on the campaign, quiet in documentation, consistent in identity (the mixing logic of [Visual styles](visual-styles.md), section 5, and the tier system of [Graphic language](graphic-language.md)). The art director owns the assignment: which register leads where, and when a surface may borrow energy from another. The failure mode is register leakage — campaign energy showing up in contracts, compliance tone in celebration posts.

### 3.4 Direct every medium with the same criteria

Photography, illustration, 3D, motion and graphic treatment should be reviewable against one set of criteria — subject energy, palette discipline, framing conventions, light behaviour, level of polish — even though each medium's craft differs. When the criteria are shared, a mixed-media campaign feels directed; when each medium has private criteria, it feels commissioned from strangers.

## 4. How it works

### 4.1 The translation table

The foundational document: brand attribute → visual quality → executable rules.

| Brand attribute | Visual quality | Executable rules (example) |
| --- | --- | --- |
| Energetic | Diagonal energy, saturated colour, motion | Diagonal crops allowed; palette accents at full strength; motion 200–400ms brand ease (see [Graphic language](graphic-language.md), motion table) |
| Trustworthy | Stability, restraint, even light | Level horizons; centred or rule-based framing; no heavy filters; palette neutrals dominant |
| Handmade | Texture, irregularity, warmth | 8% paper grain on print grounds (conventional); ±2° tilt bounded; rounded terminals (see [Patterns and textures](patterns-and-textures.md)) |
| Premium | Space, calm, precision | Generous margins from the spacing scale; one subject per frame; no clutter; hairline rules |
| Local | Real people, real places | Cast from the community; shoot the actual venue; document over stock (see [Photography](../imagery/photography.md)) |

Rules in the right-hand column are examples of the *format* required: concrete, checkable, medium-spanning. A brand of any size can produce this table in a day, and it is the single highest-leverage art-direction artefact.

### 4.2 The pre-work artefacts

**Reference boards.** Curated image sets showing the intended quality per domain: one board for photography mood (light, crop, casting), one for graphic treatment (how the language looks in use), one for typography and layout energy, one for motion if relevant. Boards are *calibration*, not instruction — contributors match quality and intent, not composition. Keep them current: a board that has not been revisited since launch is directing a brand that no longer exists.

**Treatment rules.** The written parameters per domain: crop conventions (tight/medium/wide; where faces may sit), palette discipline (which tokens dominate, what is forbidden), light behaviour (direction, warmth, contrast range), energy range (calm to loud per surface), and forbidden territory (stock clichés, inappropriate contexts, off-palette effects). Treatment rules for photography are detailed in [Photography](../imagery/photography.md); the same format extends to illustration ([Illustration](illustration.md)) and 3D.

**The one-page direction brief.** Per project: objective and audience; the register (which tier/style leads); the mandatory elements (logo exclusion zones, motif use); the criteria and acceptance tests; the review checkpoints. One page — long enough to direct, short enough to be read.

### 4.3 Directing the media toward one voice

- **Photography.** Direction supplies casting, location, light, crop and grade rules; the craft execution lives with the photographer per [Photography](../imagery/photography.md). The director's acceptance test is the grade-and-crop check against the treatment rules, not personal preference.
- **Illustration.** Direction sets register and emotional mapping (which states get which tone), then enforces the style definition; craft rules live in [Illustration](illustration.md), section 4.
- **3D and rendered imagery.** Treat as photography's sibling: same palette discipline, same light logic, same crop conventions; specify material and finish vocabulary (matte/gloss balance) so renders and photographs do not clash.
- **Motion and interface.** Direction sets the energy range and choreography rules; the motion language of [Graphic language](graphic-language.md) carries the parameters.
- **AI-assisted imagery.** Direction supplies the reference boards as style anchors and the acceptance criteria as review gates; every output passes the same treatment checks as human work, plus rights review (see [AI image generation](../imagery/ai-image-generation.md)).

### 4.4 Consistency audits

Direction is maintained by scheduled audit, not by hope:

1. **Sample.** Collect 10–20 artefacts across surfaces and time (print, web, social, environment; two time periods if possible).
2. **Check against criteria.** For each: legal palette, legal elements, register appropriate to surface, treatment rules honoured (crop, light, energy), logo zones respected.
3. **Score drift.** Count and classify violations: one-off vs repeated; support-tier vs hero-tier; per-medium clusters.
4. **Correct.** Re-train where the rule was unclear (fix the rule first), re-style where the artefact is wrong, and update the translation table for genuine gaps discovered.
5. **Log.** Keep the audit trail; the next audit compares against it.

A quarterly cadence suits most organisations; event brands audit at milestones (pre-print, mid-campaign) because their timescales compress.

A simple scoring format keeps audits factual and comparable over time:

| Check | 0 = fail | 1 = partial | 2 = pass |
| --- | --- | --- | --- |
| Palette legality | Off-palette colours in use | Near-token colours drifted | All colours from tokens |
| Element legality | Off-ruleset elements present | Sanctioned elements, off-rule treatments | Elements and treatments per ruleset |
| Register fit | Wrong tier/style for the surface | Register slightly loud or quiet | Register matches the surface assignment |
| Treatment rules | Crop/light/energy outside the range | Borderline in one dimension | Inside the documented ranges |
| Accessibility floor | Contrast or motion violations | Passes with caveats | Meets WCAG requirements [accessed] |

Per-audit scores per medium and per team reveal where drift concentrates — usually one medium, one team, or one unclear rule — and the trend across audits shows whether the system is stabilising.

### 4.5 Directing a fixed-logo event kit

The highest-pressure art-direction assignment is the fixed-logo event kit: the mark is locked, the timescale is short, the contributor count is high, and the output spans print, digital and environment. The direction sequence compresses to:

1. **Lock the translation table early.** Event attributes (for example "energetic, local, official") become executable rules the day the logo is fixed — the geometry to derive from is analysed per [Fixed logo analysis](../branding/fixed-logo-analysis.md), and the language built per [Graphic language](graphic-language.md).
2. **Assign registers per surface class** before any design starts: identity surfaces (certificates, stage), campaign surfaces (posters, social), functional surfaces (schedules, maps, signage), environmental surfaces (lanyards, wayfinding). Each class gets its tier and intensity from the pattern and language hierarchies.
3. **Pre-build the guardrails.** Logo exclusion zones, minimum sizes, date-and-venue lock-up rules, and the accessibility floor are the rules most often needed under deadline; document them on one page that survives being the only thing anyone reads.
4. **Template the long tail.** Every repeatable artefact becomes a template with the register pre-applied, so volunteers extend the kit without new decisions; bespoke direction goes only to hero surfaces.
5. **Audit at milestones.** Pre-print (catch palette and logo-zone violations while they are still printable), mid-campaign (catch digital drift), post-event (log findings into the rules for the next edition — an event brand is a living system across years).

The discipline matters because event kits fail publicly and irreversibly: printed signage cannot be patched like a web page. Direction here is less about creative brilliance than about making hundreds of fast decisions safe.

### 4.6 Four directing situations

Most direction questions collapse into a few recurring situations; deciding them in advance removes most per-project argument:

| Situation | Direction |
| --- | --- |
| New surface type appears (first web page, first signage) | Assign its register from the tier system before designing; add it to the surface map; if genuinely new, extend rules deliberately, once (see [Graphic language](graphic-language.md), decision framework) |
| Contributor work clashes with the rules but is strong | Keep the energy, convert the treatment to the rules; if the clash is structural, log it as evidence the rule may need revision — the arbiter decides |
| Campaign needs more energy than the identity allows | Use the subordinate-register mechanism ([Visual styles](visual-styles.md), section 5): energy goes to hero surfaces only, and resolves back before functional surfaces |
| Two contributors produce conflicting versions | The arbiter picks by the written criteria, and the losing direction's lessons go into the log; conflicts are criteria gaps made visible |

## 5. Practical application

### 5.1 Standing up art direction for a brand (the one-week path)

1. **Day 1–2 — translation table.** Workshop the attributes; write the table (4.1); argue every row until the do/don't pairs are checkable.
2. **Day 3 — reference boards.** Build the boards from existing best work and external calibration images; annotate each with *why it is on the board* (one line per image).
3. **Day 4 — treatment rules.** Write the per-domain rules; merge with the graphic-language ruleset so one document governs graphics and imagery (see [Graphic language](graphic-language.md), section 4.2).
4. **Day 5 — the brief template and audit plan.** Draft the one-page brief; schedule the first audit; name the arbiter (who decides disputes and approves exceptions — see [Graphic language](graphic-language.md), decision framework).
5. **Then — prove it.** Run the next real project strictly through the brief; fix the artefacts of the process (not the project) where reality exposed gaps.

### 5.2 Working with contributors and agencies

- **Brief with criteria, not vibes.** Hand over the direction brief, boards and treatment rules; ask the contributor to restate the criteria in their own words before starting — misread briefs surface in one conversation instead of one revision round.
- **Review against the rules.** Feedback cites the specific rule ("crop exceeds the treatment range", "register too loud for a support surface") rather than taste ("I don't like it"). Rule-citing keeps the system honest and teaches contributors the criteria.
- **Log exceptions.** Every approved deviation gets a line in the log with its reason; three exceptions of the same kind mean the rule, not the contributor, needs updating.
- **Give agencies the audit, not just the guide.** A style guide plus the last audit's findings directs better than the guide alone: contributors see where drift actually happens.

### 5.3 Directing with AI in the pipeline

Treat AI generation as a fast, untrained contributor: it needs the same brief (boards as reference, treatment rules as constraints), the same review (acceptance tests before use), and the same log (prompts and outputs that passed). The specific craft of prompting, rights handling and workflow is owned by [AI image generation](../imagery/ai-image-generation.md); the direction layer's contribution is the criteria that make its output reviewable at all.

### 5.4 The review meeting

Reviews are where direction is actually enforced; run them as rule-checks, not taste panels:

1. **Before the meeting**, the contributor self-checks the work against the brief's acceptance criteria and marks any known deviations.
2. **In the meeting**, the reviewer walks the criteria in order — palette, elements, register, treatment, accessibility floor — and cites the specific rule for every comment.
3. **Taste is heard once**: subjective comments are allowed, labelled as preference, and never block work unless the arbiter converts them into a rule.
4. **Decisions and exceptions are written down in the meeting**: what changed, which rule was unclear, which exception was approved and why.
5. **Follow-up is assigned with a date**; work is re-reviewed only against the listed items.

A review run this way takes minutes, teaches contributors the criteria, and produces a growing record of where the rules need work — the same feedback loop the audit uses at system scale.

### 5.5 Small teams: direction without an art director

Not every brand can name an art director. The minimum viable version for a small team or a volunteer-run event:

- **Elect the arbiter anyway.** One person owns decisions, even part-time; the role matters more than the title.
- **Write the translation table and the one-page brief; skip the rest** until scale demands it.
- **Use templates as the direction.** A well-made template embeds hundreds of decisions; volunteers fill content, not design.
- **Review in pairs.** Any two people checking work against the written criteria reproduce most of the audit's value.
- **Schedule one audit per campaign or quarter.** Small systems drift quietly because nobody is watching; a single scheduled hour catches it.

## 6. Decision framework

**Who arbitrates?** One named owner per brand (or per event), with a documented deputy. Committees produce averages; art direction needs a decision-maker. The arbiter's job is defined in [Graphic language](graphic-language.md) (ruleset ownership) and extends to imagery: disputes resolve by criteria, and the arbiter writes down every resolution that changes a rule.

**How loud may this surface be?** Use the tier system: hero surfaces (covers, key visuals) may take statement treatment; support surfaces (content pages, documentation) take subtle treatment; functional surfaces (forms, tables, wayfinding) take minimum treatment consistent with accessibility (see [WCAG fundamentals](../accessibility/wcag-fundamentals.md)). When in doubt, quieter — attention is a budget, and content is the point.

**Consistency vs freshness?** Refresh through re-mastering, not re-styling: re-grade photography, re-balance palette emphasis, sharpen the type scale — while element identity and treatment rules hold. Structural re-styling is a rebrand decision with its own process, never a per-project liberty (the lifecycle logic of [Visual styles](visual-styles.md), section 3.3).

**When does direction fail?** When criteria were never written (opinions substitute), when the arbiter is absent (drift substitutes), or when the translation table has gaps (every new surface re-opens arguments). The fixes are the artefacts of section 4.2 — this is a documentation discipline as much as a creative one.

## 7. Examples

**The translation table in action (illustrative composite).** A community festival with attributes "warm, local, energetic" resolves them: warm → golden-hour light bias and warm palette dominance; local → real volunteers and the actual venue in every photograph, no stock; energetic → diagonal crops and full-strength accent colour reserved for hero surfaces, subtle everywhere else. Every photographer, designer and AI session works from the same three rows; the festival's hundreds of artefacts read as one hand.

**The audit that saved a system (illustrative composite).** A product brand's quarterly audit finds 40% of social images using a retired blue and a forbidden heavy vignette — both introduced by an agency template eight months earlier. Correction: re-style the template, add "no vignettes" explicitly to treatment rules (the gap was the rule's, not the agency's), and add template spot-checks to the audit. The lesson generalises: audit findings usually indict documents, not people.

**One-page brief under deadline (illustrative composite).** An event team with two days before print runs the brief template: objective (sell late tickets), register (hero tier, statement pattern allowed), mandatory elements (logo zone, date lock-up), acceptance tests (passable at poster distance; date readable at 2m; palette legal), and one review checkpoint. The deadline survives *because* the criteria were one page — direction is what makes speed safe.

## 8. Common mistakes

- **Taste-based feedback.** "Make it pop" gives contributors nothing; rules give them everything. Correction: cite the criterion, or write the missing one.
- **Boards without annotations.** Contributors imitate surface, miss intent. Correction: one-line "why" per board image.
- **Guide without audit.** The document exists; the artefacts drift; nobody notices for a year. Correction: scheduled audits (4.4).
- **Arbiter by committee.** Decisions by consensus produce averaged, characterless work. Correction: one named owner; documented exceptions.
- **Register leakage.** Campaign energy in legal documents; compliance tone in celebration posts. Correction: assign registers per surface; check assignment in audit.
- **Direction as decoration.** Treatment rules that only cover logo and colour, leaving imagery and energy free-floating. Correction: the table must reach every medium (4.3).
- **Frozen references.** Boards and rules untouched since launch, directing a brand that has moved. Correction: revisit boards and the translation table at every audit.

## 9. Evaluation checklist

- [ ] A translation table exists: every brand attribute has executable do/don't rules across media.
- [ ] Reference boards are current and annotated with intent.
- [ ] Treatment rules cover photography, illustration, 3D, motion and graphic treatment — not only logo and colour.
- [ ] One named arbiter and deputy are documented; exceptions are logged with reasons.
- [ ] Every project starts from a one-page brief with stated acceptance criteria.
- [ ] Reviews cite rules; contributors can restate the criteria before starting.
- [ ] Audits run on schedule; findings are classified and corrected; documents are updated, not just artefacts.
- [ ] AI-assisted work passes the same criteria as human work, plus rights checks.
- [ ] Mixed-media output passes the shared criteria — a poster, an app screen and a photo from the same campaign are recognisably one voice.

## 10. Related topics

- [Graphic language](graphic-language.md) — the vocabulary and ruleset art direction enforces.
- [Visual styles](visual-styles.md) — the style positions direction chooses between.
- [Photography](../imagery/photography.md) — the craft detail of photographic art direction.
- [Illustration](illustration.md) — style definition and commissioning under direction.
- [AI image generation](../imagery/ai-image-generation.md) — AI imagery workflow and rights.
- [Patterns and textures](patterns-and-textures.md) — intensity rules direction applies per surface.
- [Iconography](iconography.md) — the icon system's construction rules that direction audits.
- [Visual identity](../branding/visual-identity.md) — the complete identity system direction serves.
- [Design critique](../foundations/design-critique.md) — the general critique practice reviews build on.
- [Colour accessibility](../colour/colour-accessibility.md) and [WCAG fundamentals](../accessibility/wcag-fundamentals.md) — the constraints no direction may waive.

## 11. References

- Atlassian Design System, "Illustrations" — role-based usage rules and necessity-first direction, cited as a public example of documented direction replacing per-artefact judgement. https://atlassian.design/foundations/illustrations [accessed 2026-11-23]
- W3C WAI, "Understanding Success Criterion 1.4.11: Non-text Contrast" — the accessibility floor direction enforces for meaningful graphics. https://www.w3.org/WAI/WCAG21/Understanding/non-text-contrast.html [accessed 2026-11-23]
- Synthesis note: this file is this project's synthesis of brand-management and art-direction practice (translation tables, treatment rules, audit method) rather than a summary of one source; the method is compatible with, but not copied from, the design-system documentation patterns cited above.
