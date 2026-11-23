# Brand guidelines

## 1. What is it?

Brand guidelines (also called a brand book, style guide or identity manual) are the document that records an organisation's visual identity — its components, values and rules — so that anyone, internal or external, human or agent, can produce on-brand work without asking the original designer. The guidelines are the interface between [Visual identity](visual-identity.md) (what the identity is) and [Brand governance](brand-governance.md) (how it is kept consistent in production). An undocumented identity exists only in one person's head; guidelines make it transferable.

Guidelines come in sizes: a full manual (dozens of pages, everything specified), a quick-reference sheet (one or two pages of the rules people actually break), and asset kits (downloadable files with embedded rules, like Spotify's public media kit that ships logo components in defined colourways with colour space labelled in the filename [accessed]). Most organisations need all three layers; they serve different moments — designing, checking, and downloading.

## 2. Why does it matter?

The guideline document is where design decisions become enforceable. Without it, every brief must re-explain the identity, every vendor guesses, and every new team member reintroduces drift; with it, review conversations become citations ("rule 2.3, clear space") rather than taste disputes. For AI agents the document is even more load-bearing: an agent producing brand materials cannot ask a designer mid-task, so the guideline must carry the decisions, the reasons and the evaluation criteria in a form that can be followed mechanically.

Guidelines also encode judgement, not just values. The strongest documents pair every rule with its reason — MIT's do/don't page explains that keeping spatial separation between an endorser's logo and the MIT logo matters because too-close placement "can lead to visual confusion and compromise the clarity of each brand" [accessed] — and a reader who understands the reason can handle the situation the rules did not anticipate, correctly.

## 3. Core principles

**Decisions, not descriptions.** A weak guideline describes ("our brand is modern and friendly"); a useful one decides (exact palette values, exact scale, exact rules). Every line should either specify a value, permit a behaviour, or prohibit a behaviour.

**Do/don't pairs with reasons.** People comply with rules they understand. The professional format is a pair: the correct application, the incorrect application, and one sentence of why. MIT's page is built entirely on this pattern — "Don't redraw, modify, deconstruct, or create your own version of the logo"; "Don't enclose the logo in another graphic"; "Don't substitute the logo for 'MIT' in running text" [accessed]. See the rule-writing style in section 5.

**Quantify wherever real numbers exist.** Clear space in derived units, minimum sizes in px and mm, contrast ratios, spacing scales, file formats per context. Where numbers are conventions rather than verified requirements, the document should say so — honesty about provenance prevents false authority (see the tagging practice in this repository's files, including [Logo systems](logo-systems.md)).

**Organised for the reader's task, not the designer's process.** A vendor looking for the logo file, a student making a poster and an agent checking contrast arrive with different questions; the structure must let each find their section fast. The mission-standard structure in section 6 is organised by component for exactly this reason.

**Kept alive or not written.** A guideline that is never updated drifts from reality and loses authority. Version, changelog and ownership belong in the document itself (see [Brand governance](brand-governance.md)).

## 4. How it works — guideline formats

| Format | Strengths | Limits | Typical use |
|---|---|---|---|
| PDF manual | Portable, complete, printable, vendor-friendly | Static; hard to search at scale; goes stale invisibly | Full identity manuals; hand-off to printers/agencies |
| Web guidelines (microsite) | Always current; searchable; linkable sections; analytics on usage | Hosting and upkeep required; can sprawl | Organisations with many teams and external users |
| Interactive/Figma-based | Templates and components live next to rules; "use the real asset" | Tool-dependent; audience must have access | Design teams and product work |
| Asset kit (download bundle) | Correct files guaranteed; enforces by supply | Only as good as its labelling and coverage | Public media kits, vendor packs |
| Quick-reference sheet | One glance; fits on a wall; catches the top misuses | Cannot carry nuance | Daily use by non-designers |

The formats are layers, not alternatives: the web manual is canonical, the PDF is its export for vendors, the kit supplies the files the manual references, and the quick-reference sheet distils the top ten rules. Each layer must agree with the others; disagreement between layers is itself a governance failure. For agent use, the canonical layer should additionally be machine-readable where possible (stable section anchors, plain-language rules, values in structured lists) so an agent can quote and apply them.

Agents consuming guidelines should work them in a fixed order, which is also the order to write for: (1) load the rules for the sections touched by the task — not the whole manual, which invites selective memory; (2) load the assets from the canonical source, never from copies circulating in conversations; (3) apply rules mechanically and cite them by number when justifying decisions ("G1.2 clear space = cap height of U"); (4) when no rule covers the case, do not improvise silently — state the gap, choose the most conservative nearby rule, and record the decision for the custodian ([Brand governance](brand-governance.md)). A guideline written so an agent can follow those four steps is, by construction, also clear enough for a hurried volunteer.

### 4.1 Keeping layers in sync

The sync rule is one canonical source, generated copies. Concretely: the web manual (or master document) is canonical; the PDF is exported from it; the quick-reference sheet is extracted from its top rules; the asset kit's README is generated from the same values. The change workflow that keeps this true: (1) edit the canonical source; (2) regenerate the derived layers; (3) record one changelog entry listing every layer touched; (4) announce the change through the governance channel. Teams that skip regeneration discover the drift the next time a vendor works from an old PDF. For a small organisation without a web manual, the canonical layer is simply the master document file — the discipline matters more than the technology.

### 4.2 Writing guidelines from an identity (agent workflow)

For an agent authoring guidelines from an identity specification, the sequence is: harvest every decision from the component work ([Visual identity](visual-identity.md) and the files it links to); convert each decision into a numbered rule in the strong form (trigger, decision, citation — section 5); assemble per the eleven-section structure (section 6); generate the quick-reference sheet (7.1); and leave every unfilled decision as a marked, honest gap rather than an invented value — a guideline with a visible gap can be completed; one with an invented value quietly misleads every later user. Where the identity was built from a fixed logo, the prohibited-modifications list and the derivation evidence from [Fixed-logo analysis](fixed-logo-analysis.md) migrate verbatim into sections 1 and 6, preserving their reasons.

## 5. Rule-writing style

Rules are the guideline's working units. A well-formed rule has: subject, condition, prescription, and (for don'ts) a reason. Compare:

```text
Weak:    "Use the logo correctly and keep it looking nice."
Better:  "Keep clear space around the logo."
Strong:  "Keep clear space around the logo equal to the height of the letter
          'U' in the wordmark. Nothing — text, image or other graphic — may
          enter this zone. The zone protects the mark's silhouette from
          visual crowding."
```

Practical style rules, drawn from how strong public guidelines are written [accessed, MIT and Uber Eats examples]:

1. **One rule per statement.** Compound rules ("keep clear space and never recolour") get partially applied.
2. **State the correct behaviour, not only the prohibition.** Pair every don't with the do that replaces it. MIT's page pairs "Don't enclose the logo in another graphic" with treating the logo as standalone [accessed].
3. **Give the reason in one sentence.** Reasons teach the principle; principles transfer to unlisted cases.
4. **Quantify the measurable.** "At least 1 inch between the MIT logo and any other graphics or text" (merchandise) is enforceable; "adequate space" is not [accessed].
5. **Prefer concrete triggers over judgement words.** "On darker backgrounds use the white logo; on lighter backgrounds use the black version" (Uber Eats) is decidable at a glance; "choose the variant that looks best" is not [accessed].
6. **Mark the exception explicitly.** Where merchandise, social media or partner contexts get different rules, name the context in the rule (MIT's social-media background rules differ deliberately from general collateral rules [accessed]).
7. **Number the rules.** Numbered rules can be cited in reviews, tickets and agent instructions ("apply G2.4").

A compact library of rule patterns, showing the form a strong rule takes in each section:

| Section | Weak form | Strong form |
|---|---|---|
| Logo | "Respect the logo." | "Keep clear space around the logo equal to the height of the 'U' in the wordmark; nothing may enter the zone (G1.2)." |
| Logo | "Don't mess with the colours." | "Use the logo only in the supplied variants. To fit a background, change variant or background — never recolour the file (G1.4)." |
| Colour | "Good contrast." | "Body text on background must meet the pairings in table 2.2; if the combination is not listed, it is not approved (G2.2)." |
| Typography | "Use our fonts." | "Headings: Brand Sans Bold. Body: Brand Sans Regular 16/24. If the brand font is unavailable, use the fallback stack in G3.4 — do not substitute another font (G3.1)." |
| Photography | "Nice photos." | "Images: candid, natural light, palette-compatible grade (preset P2). Forbidden: staged stock, heavy filters, images containing other organisations' marks (G5.1–5.3)." |
| Co-branding | "Get approval for partner stuff." | "Any material featuring a partner mark must be reviewed before launch; submit via the portal, standard turnaround 3 working days (G8.4)." |

Note the shared skeleton in every strong row: a trigger (when the rule applies), a decision (what to do, with a value), and a citation (where the rule lives). Rules written this way can be checked by a person in seconds and applied by an agent without interpretation.

## 6. Mission-standard document structure

The following eleven sections are the standard skeleton for a full guideline document in this repository. Each section's job is stated so an author (human or agent) can fill it with decisions rather than prose. The annotated outline in section 7 expands this into a fillable template.

| # | Section | Carries |
|---|---|---|
| 1 | Logo | Variants, clear space, minimum size, backgrounds, misuse, prohibited modifications |
| 2 | Colour | Palette values in all spaces, roles, pairing rules, proportions, accessibility status |
| 3 | Typography | Families and weights, scale, usage rules, fallbacks, licensing note |
| 4 | Layout | Grid, margins, spacing, placement zones per format |
| 5 | Photography | Style, treatment, grading, crop, forbidden list |
| 6 | Graphic elements | Motifs, patterns, iconography style, line weights, usage rules |
| 7 | Accessibility | Contrast requirements, minimum sizes, colour-independence rules for meaning |
| 8 | Co-branding | Architecture slots, partner and sponsor lockups, tier table, prominence rules |
| 9 | Digital | Web, app, social and e-mail specifics; templates; motion basics |
| 10 | Print | Colour reproduction, paper, sizes, bleed handling for identity elements |
| 11 | Governance | Ownership, approval flow, version and changelog, exception process |

Sections 1–6 define the identity; 7–11 define its correct operation in real contexts. A document missing 7–11 still looks complete but fails in production — that is where contrast failures, vendor questions and drift live.

### 6.1 What each section must contain

The skeleton above becomes complete when each section carries the following, all as decisions with values:

> **Reading order for mixed audiences.** Vendors usually need sections 1, 2 and 10; volunteers need 1–4 plus the quick-reference sheet; web and product teams need 2, 3, 7 and 9; agents need the whole document but especially the numbered rules and the governance section for what to do when a rule does not fit. If the document is published as a microsite, these paths can be explicit landing pages; in a PDF, the "how to use this document" section replaces them.

The ordering of sections itself carries a message: logo first because it is the asset with the strictest rules and the most misuse; colour and type next because they define most of every output's surface; layout, imagery and elements after; operational sections (accessibility, co-branding, digital, print, governance) last but never omitted. This mirrors the working order of [Visual identity](visual-identity.md) section 5, so a reader who has built an identity with that file finds the guideline sections already familiar.

- **Logo (1):** every variant as a labelled file; clear space with its derived unit and a diagram; minimum sizes in screen and print units; the background policy (light, dark, busy, reserved); the misuse do/don't pairs with reasons; and, where the mark is fixed, the prohibited-modifications list from [Fixed-logo analysis](fixed-logo-analysis.md).
- **Colour (2):** the full palette table in HEX/RGB/CMYK (+ Pantone where relevant) with one role per colour; the approved pairing table with contrast values; proportion guidance (labelled as heuristic if it is one); and rules connecting colour to the logo variants.
- **Typography (3):** families with weights and licence status; the scale with size/weight/leading per level; casing, alignment and list conventions as do/don't pairs; the fallback stack for contexts where the brand font cannot load; and the explicit statement that logo lettering is not a typeface.
- **Layout (4):** the grid per format (poster, document, web, social); margins and the spacing unit; logo placement zones per format that demonstrably respect clear space.
- **Photography (5):** the style description; grading or treatment values (a preset name counts if the preset is documented); crop and composition conventions; the forbidden list.
- **Graphic elements (6):** each motif with its derivation and files; icon grid, stroke and radii; pattern usage rules (where allowed, where forbidden, minimum opacity rules if any).
- **Accessibility (7):** the adopted standard (for example WCAG contrast levels); the passing pairings; minimum text sizes per medium; the colour-independence rule.
- **Co-branding (8):** the architecture summary; partner lockup recipes; the sponsor tier table; what requires approval and how.
- **Digital (9):** per-channel asset rules (web, social, e-mail), the responsive behaviour of the identity, and pointers to component templates.
- **Print (10):** which file variants for which print processes; minimum logo sizes at common product sizes; special processes (single-ink, embroidery, engraving) mapped to the monochrome variant.
- **Governance (11):** owner, approval flow with turnaround, versioning and changelog, exception process — enough that the document itself explains how it stays true.

## 7. Full annotated outline (fillable template)

The outline below is written so an agent can fill it for a real organisation. Annotations in italics say what to put in each slot; values come from the identity work ([Visual identity](visual-identity.md), [Fixed-logo analysis](fixed-logo-analysis.md)).

```markdown
# [Organisation] Brand Guidelines — version X.Y, [date]

Owner: [role, not just name]        Contact: [channel]
Changelog: [date — what changed — why]   (see brand-governance.md)

## 0. How to use this document
*Italic: two paragraphs — who each section serves (vendor / volunteer /
agent), and the quick path: "making a poster? sections 1, 3, 4, 9 or 10."*

## 1. Logo
1.1 Variants and files — *list each variant with file path; state the
    immutable rule: supplied files only, no redrawing.*
1.2 Clear space — *unit derived from the mark; diagram; the rule sentence.*
1.3 Minimum sizes — *px for screen, mm/in for print, per variant.*
1.4 Backgrounds — *light/dark/busy policies; reserved colours if any.*
1.5 Misuse — *do/don't pairs with reasons; prohibited-modifications list.*
1.6 Co-branding lockups — *pointer to section 8 recipes.*

## 2. Colour
2.1 Palette table — *name, HEX, RGB, CMYK, Pantone, role, usage note.*
2.2 Pairing rules — *approved text/background pairs with contrast ratios.*
2.3 Proportions — *dominance guidance, labelled as heuristic if so.*
2.4 Colour and the logo — *which variants on which backgrounds.*

## 3. Typography
3.1 Families — *display + body (+ web fallbacks); licence status; weights.*
3.2 Scale — *size/weight/leading/tracking per level (H1–H4, body, caption).*
3.3 Usage rules — *case, alignment, lists; do/don't pairs.*
3.4 When the brand font is unavailable — *fallback stack and restrictions.*

## 4. Layout
4.1 Grid and margins — *per format: poster, document, web, social.*
4.2 Spacing system — *unit and scale values.*
4.3 Logo placement zones — *positions per format respecting clear space.*

## 5. Photography
5.1 Style description — *subject matter, composition, treatment.*
5.2 Grading/crop conventions — *values or presets; aspect conventions.*
5.3 Forbidden list — *stock clichés, mismatched grades, sensitive contexts.*

## 6. Graphic elements
6.1 Motif library — *each motif, its derivation, files, usage rules.*
6.2 Iconography — *grid, stroke, radii, family source.*
6.3 Patterns and frames — *where allowed, where forbidden.*

## 7. Accessibility
7.1 Contrast requirements — *the standard adopted and the passing pairs.*
7.2 Minimum sizes — *text sizes per medium.*
7.3 Colour-independence — *meaning never carried by colour alone.*

## 8. Co-branding and sponsors
8.1 Architecture summary — *which entities exist and their slots.*
8.2 Partner lockup recipes — *divider, spacing, lead brand, alignment.*
8.3 Sponsor tier table — *tier → size ratio → positions → exclusivities.*
8.4 Approval requirement — *what must be submitted, to whom, turnaround.*

## 9. Digital
9.1 Web — *logo usage, palette, type, component templates.*
9.2 Social — *per-platform assets and rules (profile imagery, post cards).*
9.3 E-mail — *font fallbacks, logo files allowed in e-mail contexts.*

## 10. Print
10.1 Colour reproduction — *CMYK/Pantone variants, which file for which process.*
10.2 Formats and sizes — *minimum logo sizes at common print sizes.*
10.3 Special processes — *embroidery, engraving, single-ink: monochrome variant.*

## 11. Governance
11.1 Ownership — *who owns the identity and who approves exceptions.*
11.2 Approval flow — *what requires review; how to submit; turnaround.*
11.3 Versioning — *current version, changelog, where the canonical files live.*
11.4 Exceptions — *process, log, expiry (see brand-governance.md).*

## Appendices
A. Quick-reference sheet (one page — top rules per section)
B. Asset kit index — *every downloadable file with its intended context*
C. Templates — *list of ready templates and their sources*
```

A filled outline becomes the PDF or web manual directly; sections map one-to-one onto the component inventory in [Visual identity](visual-identity.md), so nothing can be specified there but missing here.

### 7.1 Internal quick-reference sheet

The one-page distillation for daily use — pinned in studios, attached to briefs, included in agent instructions. It is generated from the full manual and must be regenerated whenever the manual changes:

```markdown
# [Organisation] — brand quick reference (v X.Y)

THE LOGO      supplied files only · clear space = [unit] · min size [X px / Y mm]
              dark background → [white variant] · light background → [dark variant]
              never: stretch · recolour · effects · rotation · crop · re-typeset
COLOUR        primary [name HEX] · secondary [name HEX] · neutrals [names]
              text pairs: use table 2.2 only · accent = links and CTAs
TYPE          headings [family, weight] · body [family, size/leading]
              no brand font available? use fallback [stack], never a new font
LAYOUT        grid [cols / margins] · logo position [per format] · spacing unit [n]
IMAGERY       grade [preset] · crops [convention] · forbidden: [top three]
ASK FIRST     new lockups · partner or sponsor material · anything altering the mark
              → [contact / portal], turnaround [n working days]
FILES         always from [portal URL] — nothing attached to e-mails is current
```

Ten lines carry the rules that prevent ninety per cent of everyday misuses. The sheet's discipline is subtraction: if it cannot fit on one page, it is the manual, not the sheet — choose the top rules from the audit findings (the rules people actually break), not from the manual's table of contents.

## 8. Common mistakes

- **Values without rules.** Palette and type are specified, but nothing says when to use what; the document reads as a specimen sheet. Fix: every value gets a role and a rule.
- **Rules without reasons.** Prohibitions with no rationale get ignored or applied woodenly; the reason is what generalises. Fix: the one-sentence reason per rule (section 5).
- **Judgement words where numbers are possible.** "Sufficient contrast", "appropriately sized" — undecidable at review time. Fix: quantify, or mark the number as a conventional starting point.
- **No quick-reference layer.** The 60-page manual exists; nobody breaking the rules on Tuesday has read it. Fix: one-page sheet with the top rules per section.
- **Assets and rules separated.** The manual describes files that live somewhere unlabelled; wrong files circulate by e-mail. Fix: asset kit with labelled files (the Spotify kit's colourway-and-colour-space filenames are the minimum labelling standard [accessed]) and links from manual to kit.
- **Format sprawl.** PDF, site and kit disagree after an update. Fix: one canonical layer, others generated from it; changelog notes which layers changed.
- **Static document, living identity.** Editions and campaigns change the system; the manual never does. Fix: versioning and changelog owned by governance ([Brand governance](brand-governance.md)).
- **Writing for designers only.** Volunteers, vendors and agents need task-oriented paths, not designer jargon. Fix: the "how to use this document" section and plain-language rules.
- **Examples without files.** The manual shows a beautiful lockup mock but the corresponding file is not in the kit; users rebuild it badly. Fix: every visual example in the manual maps to a file in the kit (and the kit's README points back to the rules).
- **Spine-only updates.** A palette value changes; the quick-reference sheet, templates and portal README still show the old one. Fix: updates are atomic across layers — one changelog entry lists every layer touched.

## 9. Evaluation checklist

- [ ] Every section of the mission-standard structure (1–11) is present and carries decisions, or an explicit "not applicable" with reason.
- [ ] Every rule is numbered, single-statement, and paired do/don't with a one-sentence reason.
- [ ] All measurable values are quantified (clear space, minimum sizes, contrast ratios, spacing) and unverified numbers are labelled as conventions.
- [ ] Palette is specified in HEX, RGB, CMYK (+ Pantone where relevant) with roles and approved pairings.
- [ ] Typography includes fallbacks and licence status; the logo lettering is not offered as a typeface.
- [ ] Accessibility section states the adopted standard and lists passing pairs.
- [ ] Co-branding section includes lockup recipes and the sponsor tier table.
- [ ] Governance section names the owner, approval flow, current version, changelog and exception process.
- [ ] Asset kit files are labelled with variant, colour space and intended context, and the manual links to them.
- [ ] A one-page quick-reference sheet distils the top rules.
- [ ] The document has an owner and a changelog; layers (PDF/site/kit) agree with the canonical version.

## 10. Related topics

- [Visual identity](visual-identity.md) — the identity the guidelines document.
- [Logo systems](logo-systems.md) — the logo rules the guidelines must carry.
- [Fixed-logo analysis](fixed-logo-analysis.md) — analysis outputs (motifs, constraints, prohibited modifications) that populate sections 1, 2 and 6.
- [Brand governance](brand-governance.md) — who approves, versions and enforces what the guidelines state.
- [Brand architecture](brand-architecture.md) — the structure behind section 8.
- [Palette development](../colour/palette-development.md) — building the palette the colour section specifies.
- [Colour accessibility](../colour/colour-accessibility.md) — the contrast work behind section 7.
- [Typeface selection](../typography/typeface-selection.md) and [Typographic hierarchy](../typography/typographic-hierarchy.md) — inputs to section 3.
- [Graphic language](../graphic-design/graphic-language.md) — inputs to section 6.
- [Brand identity checklist](../evaluation/brand-identity-checklist.md) — evaluation companion.

## 11. References

- [accessed] MIT, "Do/Don't | MIT Brand Guide", https://brand.mit.edu/applying-brand/do-dont, accessed 2026-11-23 (rule-writing patterns, quantified merchandise rule, context-specific social-media rules, quoted reason on spatial separation).
- [accessed] Uber Eats, "Marketing Tools & Brand Guidelines for Merchants", https://merchants.ubereats.com/us/en/resources/learning-center/co-marketing-tools, accessed 2026-11-23 (decidable conditional rules, approval flow with turnaround).
- [accessed] Spotify, "Logo and Brand Assets", https://newsroom.spotify.com/media-kit/logo-and-brand-assets, accessed 2026-11-23 (asset-kit labelling pattern).
- [canonical] Alina Wheeler, *Designing Brand Identity*, Wiley (multiple editions) — guideline documents as the deliverable stage of identity programmes.
- [canonical] Wally Olins, *The Brand Handbook*, Thames & Hudson — identity communication to organisations.
- The eleven-section structure is this repository's mission-standard synthesis of the public guideline examples above; the annotated outline is an original template built on that structure.
