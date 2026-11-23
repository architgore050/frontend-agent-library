# AI-assisted design

## 1. What is it?

AI-assisted design is the practice of using AI tools — language models, image generators, editing assistants, critique checkers — at defined points in a design process while keeping the responsibility structure explicit: the tool proposes, a human or a verified process checks, and only then is the output applied and evaluated. This file defines *where* AI genuinely helps across the design workflow (research, moodboards, colour, font pairing, image generation and editing, layout ideation, critique, asset production, documentation), which tasks require **human approval or precise manual implementation**, and the operational loop — propose → verify → apply → evaluate — that keeps AI involvement productive rather than hazardous.

It is the methodology counterpart of [AI image generation](../imagery/ai-image-generation.md), which covers the craft of generating imagery; this file covers the process discipline around all AI assistance.

## 2. Why does it matter?

AI tools compress the cost of producing *plausible* design output to nearly zero, and that is both their value and their danger. A model will confidently supply a hex palette, a font pairing, a WCAG claim, or a licence statement — some correct, some subtly wrong, and all delivered in the same confident register. In design, the errors that matter are not always visible: a contrast ratio can be wrong by 1.5:1 and the artefact still looks fine; a licence term can be invented and nothing in the file reveals it; a "standard poster size" can be a hallucinated number that only fails at the print shop. The failure mode is specific: **AI errors survive review precisely because AI output looks finished.**

The discipline this file teaches is therefore not "use AI where it helps" — that is obvious — but "know which of your tasks can absorb AI error and which cannot". Anything verifiable by computation or a primary source (contrast maths, sizes, standards) can absorb AI error if verification is actually performed. Anything whose errors surface late and legally (licences, rights, brand decisions, print production) cannot, and must have a human in the loop.

## 3. Core principles

- **AI proposes; verification disposes.** No AI output becomes a design decision without passing a verification step appropriate to its claim type. Verification is a named step with a method, not a glance.
- **Match trust to claim type.** Mathematical claims (contrast, ratios) → recompute with code. Source claims (standards, sizes, licence terms) → check the primary document. Aesthetic claims (pairings, styles) → human evaluation against attribute rules. Nothing is trusted because it sounds authoritative.
- **Generation is cheap; selection is the work.** Use AI to expand the option pool (see [Ideation](ideation.md)), never to shrink it to one. A single AI output accepted is premature convergence with extra steps.
- **Humans own the irreversible decisions.** Final brand decisions, accessibility sign-off, licensed font choices, anything with legal or rights implications, and final print production files require human approval regardless of how good the AI output looks (see §5).
- **Provenance is recorded.** Every AI-assisted artefact carries a record of what was AI-generated, with what tool, what was verified, what was human-approved (see §6.4). Undocumented AI use is discovered eventually — usually in a rights dispute or a broken production file.
- **The process stays the process.** AI accelerates steps of the same methodology (see [Design thinking](design-thinking.md)); it does not replace the steps. Research still needs implication chains; moodboards still need attribute extraction; critique still runs its eleven steps.

## 4. How it works

### 4.1 The propose → verify → apply → evaluate loop

The loop wraps every AI-assisted task:

1. **Propose** — use the AI tool to generate candidates, summaries, drafts or variants. Prompt for *multiple distinct* options; state the constraints in the prompt so output lands inside them.
2. **Verify** — check each output by the method its claim type demands (see §3). Verification failures are normal and informative: they mark the boundary of the tool's reliability.
3. **Apply** — only verified outputs enter the design. Applied outputs are labelled in the provenance record.
4. **Evaluate** — the applied result goes through the normal evaluation (see [Design critique](design-critique.md)); AI assistance is not a waiver from review, and AI-generated work has some *extra* review duties (right-checking, spec-checking) rather than fewer.

### 4.2 Where AI helps, task by task

| Task area | AI can do | Required verification / human role | Failure mode if skipped |
| --- | --- | --- | --- |
| Research and discovery | Summarise long documents; generate search queries; draft interview questions; map themes | Check every factual claim against a primary source or real document; summaries of unseen sources are *leads*, not findings (see [Research and discovery](research-and-discovery.md)) | Invented statistics and fake "findings" enter the brief |
| Moodboard exploration | Generate reference lists, style descriptors, prompt variants; assemble first-pass boards | Check provenance and rights of every reference; run the attribute extraction yourself (see [Moodboards](moodboards.md)); confirm harmony with the fixed logo | A board of confident, unlicensed, unsourced images |
| Colour exploration | Propose palette candidates from brand attributes and mood words | Recompute all contrast pairs programmatically (WCAG maths, not model arithmetic); sample real brand colours from the actual logo file | Hallucinated hex values; wrong contrast claims; palette that ignores the fixed logo |
| Font pairing assistance | Suggest pairing candidates by classification logic; explain why pairings work | Verify the licence yourself on the foundry/primary site; render the actual pairing and look at it; confirm weights/glyph coverage needed | Unlicensed fonts in production; pairings that fail in real rendering |
| Image generation | Concept imagery, mood imagery, placeholder visuals, stylistic exploration | Rights review (training data, terms of service, model output policies); brand-fit check against attribute rules; human judgment on final imagery (see [AI image generation](../imagery/ai-image-generation.md), [Image rights](../imagery/image-rights.md)) | Legal exposure; off-brand imagery shipped |
| Image editing | Assisted retouching, background removal, upscaling, format conversion, batch operations | Inspect results at 100%+ zoom (artifacts, warped details); verify final dimensions/colour profile | Subtle defects shipped; wrong export specs |
| Layout ideation | Generate multiple layout variants; propose grid/spacing options under stated constraints | Evaluate against composition principles and the brief (see [Composition](../foundations/composition.md)); check at extreme sizes | One polished variant accepted unexamined |
| Design critique | First-pass check against a rubric: hierarchy order, missing alt text, obvious defects, checklist pre-fill | Runs *before* human review, never instead of it; computed checks (contrast) verified with code; final accessibility sign-off is human (see §5) | AI rubber-stamp replaces review; defects survive |
| Asset production | Template generation, repetitive exports, size variants, naming, asset scripts | Spot-check every export at full size; final print files are manually verified (bleed, profiles, fonts outlined) — see §5 | Print run fails on wrong bleed or RGB mode |
| Design system documentation | Draft token descriptions, usage guidance, changelog prose, glossary entries | Verify docs against the actual code/tokens (see [Design tokens](../design-systems/design-tokens.md), [Documentation](../design-systems/documentation.md)); nothing documents a component that does not exist as written | Documentation drifts from reality on day one |

### 4.3 Verification methods by claim type

| Claim type | Example | Verification method |
| --- | --- | --- |
| Mathematical | "this contrast is 4.8:1" | Recompute with code from the actual hex values; never accept the number |
| Standard / specification | "WCAG requires…", "the standard bleed is…", "Instagram size is…" | Open the primary standard or official documentation; a model's quote is a pointer, not a source |
| Licence / rights | "this font is free for commercial use", "this image has no rights issues" | Read the licence on the foundry/source's own site; only primary documents count (see [Image rights](../imagery/image-rights.md)) |
| Factual / research | "studies show users prefer…" | Trace to the real study; if untraceable, treat as assumption and label it |
| Aesthetic / stylistic | "these fonts pair well" | Render and look; judge against the brand's attribute rules |
| Existence | "font X includes weight 300" | Check the foundry's spec; verify the file you actually have |

## 5. Tasks requiring human approval or precise manual implementation

These boundaries are the file's core requirement. AI may *prepare* all of the following; it may not *decide* or *finalise* them:

1. **Final brand decisions** — the choice of logo direction, palette commitment, typeface adoption, brand personality framing. AI explores and documents; a human accountable for the brand decides (see [Visual identity](../branding/visual-identity.md)).
2. **Accessibility sign-off** — computed contrast values and automated checks inform the decision, but conformance judgment and sign-off are human. Automated checking misses contextual accessibility (meaning carried by colour alone, cognitive load, real-user outcomes).
3. **Licensed font choices** — licence verification on the primary site, licence scope for the actual use case (web embedding vs print vs app), and the purchase/activation decision are human. Model summaries of licences are untrusted input.
4. **Anything with legal or rights implications** — image licences, trademark clearance, likeness rights, model-output usage rights, terms-of-service compliance. AI flags and gathers; humans and primary documents decide. Trademark clearance in particular always involves human legal judgment.
5. **Final production files for print** — bleed and trim verification, CMYK conversion decisions, overprint settings, font outlining/embedding, colour-profile choice for the specific print vendor. These are precise manual implementation steps where a silent error is paid for in thousands of units. AI may script the checklist; a human checks the final file against it.
6. **Stakeholder commitments** — presenting directions, negotiating scope, accepting or overriding critique findings. The social layer of design is human; AI drafts the artefacts, not the accountability.

The pattern behind the list: **irreversibility × late failure detection × accountability.** If an error is expensive to reverse, surfaces late, or needs someone to be accountable, a human owns the step.

## 6. Practical application

### 6.1 A complete agent workflow (event kit extension, with AI assistance)

- **Research:** AI summarises the brief and past-campaign material; agent verifies each summary claim against the source documents; AI generates search queries for the landscape scan; agent fetches and reads the real pages.
- **Moodboards:** AI drafts reference-list candidates per direction; agent checks provenance and rights, prunes, annotates with attributes itself, and confirms each direction's harmony with the sampled logo values.
- **Colour:** AI proposes candidate accent extensions; agent samples the logo's actual colours from the file, recomputes every contrast pair with code, and only then applies.
- **Font pairing:** AI proposes candidate secondary faces; agent checks licences on foundry sites, renders the pairings, and evaluates against the type rules.
- **Layout ideation:** AI generates four distinct badge layouts under stated constraints; agent scores them with the criteria table (see [Ideation](ideation.md) §4.4).
- **Critique:** AI runs the rubric pre-check on the built artefact; agent runs the full eleven steps (see [Design critique](design-critique.md) §5.1), computing contrast itself.
- **Asset production:** AI generates export scripts and size variants; agent spot-checks every export; print files get the manual bleed/profile/outline pass with human sign-off.
- **Documentation:** AI drafts token descriptions and guideline prose; agent verifies each statement against the actual tokens and files.

### 6.2 Hallucination risks in design contexts

The recurring hallucination classes, with their signatures:

- **Fake specs:** invented contrast ratios ("4.9:1" for a pair that measures 2.8:1), wrong platform sizes, wrong bleed values, wrong WCAG thresholds ("3:1 is fine for body text"). Signature: a specific number with no source. Defence: recompute or look up; treat every quoted number as a prompt to verify.
- **Fake licence terms:** "free for commercial use" about a font whose actual licence restricts embedding. Signature: licence language without the licence document. Defence: primary documents only.
- **Invented brand facts:** "the brand's official colour is #0057B8" when no such specification exists. Signature: specificity without provenance. Defence: sample from real files; ask when unknown.
- **Confident aesthetics:** pairing or palette justifications that sound like expertise ("the transitional serif balances the geometric sans") and may be true — but are hypotheses to render, not facts to apply.
- **Fabricated references:** citations to studies, guidelines or articles that do not exist, or exist with different content. Defence: never cite a source you have not opened; this rule is also this repository's authoring rule (see [BRIEF-adjacent discipline](../references/index.md) if present in your copy).

The meta-defence is §4.3's table: every claim type has a named verification method, and "it sounded right" is not among them.

### 6.3 Choosing when *not* to use AI

AI assistance has a cost even when free: verification overhead and error risk. Skip it when: the task is already precise and fast by hand (a known token change); the output's verification would cost more than doing the work (verifying a one-line colour tweak); the task is exactly the kind whose failures are legally expensive (licence research still ends in human reading); or the deliverable demands a specific human voice (final stakeholder communication). Use it where the pool-expansion value is high and verification is cheap: ideation breadth, documentation drafts, repetitive production, first-pass critique.

### 6.4 Documenting AI involvement

Every AI-assisted deliverable carries a provenance note. Working format:

```text
AI involvement record — event badge v4
- Tools: LLM (layout ideation, documentation drafts), image gen (mood imagery concepts)
- AI-generated: 4 layout variants (1 used, scored in ideation record);
  6 mood imagery concepts (2 used as placeholders, replaced by licensed
  photography in v4); token description prose (verified against tokens.json)
- Verified: contrast pairs recomputed with code (all AA pass);
  font licence checked on foundry site (OFL — web+print OK);
  export sizes checked against platform docs
- Human-approved: palette commitment, badge direction, accessibility
  sign-off, final print file (bleed 3mm checked, CMYK profile per vendor)
- Open items: licensed photography purchase pending approval
```

The record takes minutes and answers the questions that arrive later: "where did this image come from?", "was the font licensed?", "who checked the contrast?". It is also the raw material for the brand guidelines' decision log (see [Brand guidelines](../branding/brand-guidelines.md)).

## 6.5 Decision framework

| Question | If yes | If no |
| --- | --- | --- |
| Is the output's claim type verifiable by you, cheaply? | Use AI; verify per §4.3 | Use AI only if a human will verify; otherwise skip |
| Does an error surface late or cost irreversibly? | Human owns the step (§5) | AI may apply after verification |
| Does the task need option breadth? | AI to expand the pool; criteria to narrow | Do it directly |
| Is the task social (stakeholders, accountability)? | AI drafts; human speaks and decides | — |
| Is the output rights-bearing or licensed? | Primary documents + human decision | — |
| Would verification cost more than the work? | Skip AI | Proceed with the loop |

## 7. Examples

- **Caught fake spec:** an AI-assisted palette proposal claimed 4.5:1 for amber-on-off-white; recomputation gave 2.1:1. The proposal was corrected before it ever entered a design — the two-minute check that the loop exists to enforce.
- **Caught fake licence:** a proposed pairing included a "free" display font; the foundry's site showed a desktop-only licence excluding web embedding. Substituted under human decision — a rights incident that never happened.
- **Productive breadth:** four AI-generated badge layouts, scored on the criteria table, produced one winner and — unexpectedly — one rule worth keeping ("logo geometry echoes in corner radii"), which no single-output workflow would have surfaced.
- **Documentation drift caught:** AI-drafted token documentation described a spacing scale value that did not exist in the code; verification against the actual tokens file caught it on day one instead of month six (see [Documentation](../design-systems/documentation.md)).

## 8. Common mistakes

- **Accepting polished output as checked output.** Polish is not verification; the loop's verify step is where trust is earned, nowhere else.
- **Trusting model arithmetic.** Contrast ratios, scale ratios, sizing maths — all recomputed. Models do not do WCAG maths reliably.
- **One output accepted = premature convergence.** Prompt for multiple distinct candidates and score them (see [Ideation](ideation.md) §4.3).
- **Citing unopened sources.** If the AI names a study or standard, open it or strike it. Fabricated references are the most damaging hallucination class in documentation.
- **AI in the accountability seat.** AI may draft the stakeholder message, the sign-off summary, the critique record — humans sign and decide.
- **Skipping provenance.** Undocumented AI use surfaces later as a rights question with no answer. Record as you go (§6.4).
- **Verification theatre.** Running checks that cannot fail (asking the same model to check its own factual claims) is not verification; use the claim-type methods in §4.3.
- **Letting AI rewrite the process.** AI accelerates steps; it does not licence skipping research, moodboard discipline, or critique. The methodology files still govern.

## 9. Evaluation checklist

- [ ] Every AI-assisted claim passed the verification method for its claim type before being applied.
- [ ] All contrast and scale maths were recomputed with code from actual values.
- [ ] All standards, sizes and licence terms were checked against primary documents.
- [ ] AI was used to expand option pools, and selection used written criteria.
- [ ] All items in §5 (brand decisions, accessibility sign-off, licensed fonts, rights, print files) had human approval or manual implementation.
- [ ] An AI involvement record exists for the deliverable, listing tools, outputs, verifications and approvals.
- [ ] AI critique ran as a pre-check, with the full human/critique process still executed.
- [ ] No source was cited without being opened.
- [ ] The documentation was verified against the actual tokens, components and files it describes.

## 10. Related topics

- [AI image generation](../imagery/ai-image-generation.md) — the craft of the image-generation task area.
- [Image rights](../imagery/image-rights.md) — the rights framework behind §5.4.
- [Design thinking](design-thinking.md) — the process AI assistance accelerates.
- [Ideation](ideation.md) — pool expansion and selection criteria.
- [Moodboards](moodboards.md) — attribute extraction that AI references must pass.
- [Design critique](design-critique.md) — the evaluation process AI pre-checks feed.
- [Design tokens](../design-systems/design-tokens.md) and [Documentation](../design-systems/documentation.md) — the verification target for documentation tasks.
- [Research and discovery](research-and-discovery.md) — evidence discipline for AI-supplied research.
- [Evaluation: design quality framework](../evaluation/design-quality-framework.md) — the criteria evaluation loop measures against.

## 11. References

- Mission specification §7.5 (this repository) — the ten task areas and the assist-vs-approve requirement; per-area guidance is this file's elaboration.
- Park, H. et al., "AI-Assisted Designers or Designer-Assisted AI? Human–AI…" (Design Research Society / ServDes proceedings, 2025) — study of whether AI functions as an assisting tool or designers supervise AI-driven processes; supports the human-oversight framing. `[search-verified]` https://dl.designresearchsociety.org/cgi/viewcontent.cgi?article=1010&context=servdes (accessed 2026-11-23)
- Design Systems Collective, "AI in Design Systems: Smarter UX, Faster Workflows, and Better Collaboration" (2025) — AI systems generating design solutions "with minimal human intervention" and the need to maintain human oversight. `[search-verified]` https://www.designsystemscollective.com/ai-in-design-systems-smarter-ux-faster-workflows-and-better-collaboration-cfac2cc236cf (accessed 2026-11-23)
- W3C, *Web Content Accessibility Guidelines (WCAG)* — the primary standard that AI contrast claims must be recomputed against. `[canonical]`
- The propose → verify → apply → evaluate loop, the claim-type verification table and the human-approval boundary list are this file's synthesis, built on standard professional practice; they are conventions of this library, to be adapted to a project's risk profile.
