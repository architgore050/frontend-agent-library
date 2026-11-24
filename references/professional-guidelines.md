# Professional Brand Guidelines as Case Studies

## 1. What is this file?

This file analyses publicly accessible brand and design guidelines from seven real organisations — two universities, one
technology company, one government design system, and three open-source projects — and extracts the rules they actually
document. For each rule, it asks the question that a mere PDF collection never answers: *what does this rule
accomplish?*

Rules exist to prevent specific, historically observed failures; understanding the reasoning lets an agent apply the
same principle to a new brand (for example, an event identity being extended from a fixed logo) rather than copying
surface conventions. Every factual claim below is tied to a page fetched this session, or is explicitly marked as
synthesis. Where a guideline's detailed specifications live on subpages that were not fetched, that limitation is
recorded in the case study itself and in Section 9.

## 2. Why analyse guidelines rather than just use them?

A brand guideline document is the most honest artefact in design practice: it states, in rules, what an organisation
believes visual consistency requires.

Reading several across sectors reveals recurring rule *archetypes* — minimum sizes, master-artwork requirements,
endorsement bans, tooling-based governance — that reappear regardless of sector, because they solve universal problems:
degradation, ambiguity, dilution, drift. An agent that has internalised the archetypes can diagnose which problems a new
brand kit needs to defend against, and can write its own guideline section rather than imitating wording.

There is also a governance lesson. The most mature guidelines here (GOV.UK, IBM) are not PDFs at all but living systems
with contribution criteria, release notes and versioning. Guidelines are infrastructure, and the design of the guideline
— who maintains it, how assets are distributed, how requests are handled — matters as much as the rules inside it.

## 3. How the case studies were read

Seven systems were fetched and read this session (all URLs in Section 11, tagged `[accessed]`). The claim-bearing pages
(UW–Madison, Exeter, IBM, GOV.UK, plus the UCLL and RISD programme pages in [Academic curricula](academic-curricula.md))
were re-fetched and re-verified against the live pages on 2026-11-24; no discrepancy remained after one quotation was
corrected. For each, the accessible page's documented rules were extracted under the mission's categories: logo usage,
colour, typography, layout, photography, graphic elements, accessibility, co-branding, digital/print applications and
governance.

Two reading cautions apply throughout:

- **Homepage ≠ handbook.** For several systems the fetched page is the entry page of a multi-page guideline. Where it
  names rule categories without stating the rules (UW–Madison's hex values, IBM's palette), that gap is stated rather
  than filled from memory.
- **Policy ≠ brand book.** The open-source cases document *trademark policy* (who may use a mark and how), which is the
  legally enforceable subset of a brand guideline. Their rules accomplish protection of meaning; visual specs are
  frequently deferred to separate brand pages, and this is noted per case.

## 4. Case studies

### 4.1 University of Wisconsin–Madison — campus brand programme

**Source:** `https://brand.wisc.edu/` (programme homepage; detailed subpage
specifications not fetched).

#### Structure as documented

The guideline is organised into: About the Brand (brand platform, messaging, commitment to diversity); Visual Identity
(logos, colours, typography, graphic elements and icons, photography, videography); Applying the Brand (print, web,
social media, email, stationery and promotional items); Tools & Templates (downloads); plus Brand News and Communities
of Practice.

This taxonomy alone is instructive — it is the standard "platform → identity → applications → tools" architecture that a
well-organised brand kit follows (compare [Brand guidelines](../branding/brand-guidelines.md)).

#### Actual rules visible at this level

- **Brand platform as the anchor of visuals.** The site states the brand promise "Can't stop a Badger" and grounds the
  brand in the Wisconsin Idea, "a simple but profound belief that our work here should improve lives everywhere", with
  illustrative brand stories (the first observatory in space and in Antarctica; "pinning poverty and dance on the
  academic map"). *What this accomplishes:* every downstream visual choice has a narrative justification; designers
  argue from stories, not taste.
- **A compressed entry point.** A short-form guide, "The brand in brief," covers "logos, colors, fonts, and more"
  (source's wording). *What this accomplishes:* the 90-second path for casual users protects the full handbook from
  being ignored.
- **A signature-look formula.** The core look is summarised as "Badger Red to the W Crest" — one named colour plus one
  mark. *What this accomplishes:* recognisability through a tiny, memorisable rule set; no hex or Pantone values are
  given on the fetched page (they live on the colours subpage).
- **Centralised icon distribution.** A centralised UW Icon Library replaces earlier Box folders, and a WordPress plugin
  adds icons through a dedicated UW Icon block. *What this accomplishes:* consistency through tooling — assets arrive
  pre-vetted inside the creator's workflow instead of being policed afterwards. This is governance-by-pipeline (see
  [Governance](../design-systems/governance.md)).
- **Application coverage.** Guidance spans print, web, social media, email, and stationery/promotional items. *What this
  accomplishes:* no major surface is left to improvisation, which is where brand drift usually starts.
- **Named governance owner.** The programme is owned by the Office of Strategic Communication, with published contact
  details, vendor guidance via an "Internal and External Vendors" page, and accessibility resources linked
  (accessible.wisc.edu). *What this accomplishes:* accountability and a single adjudication point for exceptions.
- **A living changelog.** Brand News operates as an updates log. *What this accomplishes:* the guideline can evolve
  without silence — consumers know when rules changed.

**Not accessible at this level:** specific colour values, font names, logo clearance-space dimensions and photography
direction (stated on subpages not fetched).

### 4.2 University of Exeter — visual identity rules

**Source:**
`https://www.exeter.ac.uk/departments/communication/communications/design/visualidentity`
(visual identity page of the Communications department; the fuller Brand
Portal at `https://brand.exeter.ac.uk` is a JS-based guide viewer that was
not parsed).

#### Stated rules and what each accomplishes

- **Logo versus crest separation.** The page states: "The University logo should be used for all internal and external
  communication and identity purposes," while the crest is "retained for certain legal and ceremonial purposes, eg
  degree certificates and some memorabilia." The crest may appear graphically in marketing materials, particularly
  international ones, but "not as the main identifying logo," and the page states verbatim: "The use of the crest
  alongside or instead of the University logo is not permitted." *What this accomplishes:* the crest carries legal and ceremonial weight precisely because it
  is scarce; the logo carries everyday recognition precisely because it is universal. Mixing the two erodes both — an
  ancient-accreditation symbol used on posters stops signalling authority and starts signalling decoration. This is the
  cleanest documented example in the survey of a *hierarchy of marks*, directly relevant when extending a fixed event
  logo (which plays the "crest" role) into a working mark set ([Logo systems](../branding/logo-systems.md)).
- **Minimum reproduction sizes.** Full crest minimum 20 mm deep; line version 15 mm deep. *What this accomplishes:* a
  legibility floor. Below a size threshold, fine detail fills in and the mark reads as a smudge; a numeric floor
  converts a perceptual judgment into a checkable rule. Note it is size-relative-to-depth, the correct metric for
  proportional marks.
- **Master artwork rule.** Reproduction only from master artwork, which must be requested from the Design Studio. *What
  this accomplishes:* it prevents tracing, re-drawing, screenshots and degraded exports — the historical causes of
  mutated logos. Funneling reproduction through master files guarantees fidelity better than any wording about "not
  distorting" the mark.
- **Email signature standardisation.** Outlook users must use the automated signature system that pulls data from the
  user directory; other clients require manual updates to a defined layout — contact details at 11 pt, disclaimer at 8
  pt. Staff must not build their own signature from the provided image; accreditations and partner logos must sit
  outside the main signature image (above or below); pronouns (e.g. she/her, they/them) go below the name and above the
  job title; social-media links are hyperlinks below contact details and above the disclaimer; a standard
  confidentiality disclaimer is supplied. *What this accomplishes:* this single dense block shows four rule archetypes
  working together: (a) *automation over policing* — the signature is generated, so compliance is the default; (b)
  *numeric specs* (11 pt / 8 pt) instead of adjectives; (c) *co-branding containment* — partner logos placed outside the
  signature image cannot be mistaken for endorsement and cannot contaminate the signature's rendering; (d)
  *identity-inclusive conventions* — pronoun placement is specified as a house rule, folding inclusivity into the
  standard rather than leaving it personal.
- **Identity scope statement.** The university aims for a cohesive image "recognisable globally as 'University of
  Exeter'" applied across "film, animation, websites, powerpoints, prospectuses, brochures" and display. *What this
  accomplishes:* it defines the *test* of the identity (global recognisability) rather than only its parts.

**Not accessible at this level:** the named fonts and colour values (deferred to the Brand Portal, not fetched this
session).

### 4.3 IBM Design Language — a technology company's system approach

**Source:** `https://www.ibm.com/design/language/` (site homepage; colour
values and per-section rules live on subpages not fetched).

#### Structure as documented

The design language covers: Philosophy (point of view, principles); Typography (typeface, type basics, type scale);
Colour; the "2x Grid" (IBM's layout grid, including a variant for video); IBM logos (the "8-Bar" and "Rebus" marks);
Iconography (overview, UI icons, app icons, pictograms, each with a library); Illustration (overview, tips, and four
named styles — Line, Flat, Isometric, Hybrid UI — plus a People section); Photography; Data visualisation; Infographics;
Layout; Animation ("classic principles" and techniques); plus Gallery, Resources and Help.

#### Rules and approaches visible at this level

- **A proprietary multi-script typeface.** IBM Plex is the house typeface, with releases continuing to extend its script
  coverage — the site lists IBM Plex Sans Chinese SC (December 2024), IBM Plex Math (September 2024) and IBM Plex Sans
  Chinese TC (September 2024). *What this accomplishes:* a single typographic voice across languages and use cases
  (including mathematics), which is only possible when the organisation controls the typeface itself. For any brand
  operating multilingually, this is the model: consistency is achieved by extending one family, not by licensing many.
- **Naming the graphic languages.** Four illustration styles are given distinct names and libraries. *What this
  accomplishes:* choice becomes a controlled decision — "which named style fits this context?" — instead of an
  open-ended drawing brief; the People section signals that depicting humans is a separate craft with its own rules.
- **Grid as a product.** The 2x Grid is documented with a dedicated video variant. *What this accomplishes:* layout
  rules are engineered to the medium; a grid tuned for screens is explicitly not assumed to work for motion.
- **An ethos statement above rules.** The site presents "Build Bonds" as the ethos behind "IBM's design philosophy and
  principles", with a "Think → Guide" framing. *What this accomplishes:* principles are positioned as the justification
  layer that rules derive from — the same principle-first architecture design-system documentation recommends (see
  [Documentation](../design-systems/documentation.md)).
- **Tooling and ecosystem.** The site distributes Plex downloads, colour specifications, the 2x Grid for video, icon and
  pictogram libraries, illustration starter kits and Carbon design kits (Figma), and links the wider ecosystem: IBM
  Brand Center, Carbon Design System, Enterprise Design Thinking, IBM Accessibility, Design for AI, Design Research and
  Experience Standards. *What this accomplishes:* the guideline ships as assets and kits inside designers' tools —
  again, governance-by-pipeline.
- **Currency signals.** A visible "last updated" (November 2026) and a "What's new" section. *What this accomplishes:*
  trust through visible maintenance.

**Not accessible at this level:** hex values and palette logic (behind "IBM color specifications", source's wording),
per-section do's and don'ts.

### 4.4 GOV.UK Design System — government at scale

**Source:** `https://design-system.service.gov.uk/` (maintained by a team at
the Government Digital Service; content licensed under the Open Government
Licence v3.0).

#### Purpose as stated

The system exists to "make government services consistent with GOV.UK", letting teams "Learn from the research and
experience of other service teams and avoid repeating work that's already been done." It follows the Government Design
Principles and the GOV.UK Service Manual, plus the GOV.UK style guide.

*What this accomplishes:* consistency here is not aesthetic vanity but service usability — citizens crossing many
government services should meet the same interaction conventions — and the justification is explicitly knowledge reuse.

#### Documented rule layers

- **Styles.** Page structure (page template, layout, spacing, section break); Typography (typeface, type scale,
  headings, paragraphs, links, lists, font-override classes); Visual elements (colour, images). *What this
  accomplishes:* the visual layer is deliberately thin and token-like; the weight sits in interaction.
- **Components.** Roughly 37 reusable components are documented with usage guidance — accordion, back link, breadcrumbs,
  button, character count, checkboxes, date input, error message/summary, file upload, header/footer, inset text,
  notification banner, pagination, panel, radios, select, skip link, summary list, table, tabs, task list, text input,
  textarea, warning text, and others. *What this accomplishes:* each component bundles visual, behavioural and
  accessibility rules into one reviewable unit, so teams inherit tested decisions rather than restyling controls
  (compare [Component systems](../design-systems/component-systems.md)).
- **Patterns.** Task-level guidance organised by user need: "Ask users for…" (addresses, bank details, dates, email
  addresses, equality information, names, National Insurance numbers, passwords, payment card details, phone numbers);
  "Help users to…" (check answers, complete multiple tasks, confirm contact details, create accounts/usernames, navigate
  a service, recover from validation errors, start using a service, exit a page quickly); and named page types
  (confirmation, cookies, interruption, page-not-found, question, service-unavailable, step-by-step navigation). *What
  this accomplishes:* this is the deepest insight of the GOV.UK model — rules are indexed by *user need*, not by
  component name, because that is how the design question actually arrives ("how do I ask for a date?").
- **Accessibility as a first-class section.** The site carries an accessibility overview, an accessibility strategy
  ("outlines our principles and work to improve accessibility"), and guidance on addressing accessibility issues —
  though the fetched page names no specific WCAG level (the underlying standard is documented elsewhere; see [WCAG
  fundamentals](../accessibility/wcag-fundamentals.md)). *What this accomplishes:* accessibility is governed as ongoing
  work with a strategy, not a checkbox.
- **Community governance.** Roadmap, upcoming components/patterns, contribution criteria, component lifecycle statuses,
  research participation, Design System Day events, and a Code of Conduct. *What this accomplishes:* change is openly
  scheduled and gated; lifecycle statuses tell consumers which components are safe to depend on. This is the most
  complete public governance model in the survey.
- **Release discipline.** Latest release noted: GOV.UK Frontend v6.6.0 (15 October 2026); a GOV.UK brand refresh began
  in June 2025 with Frontend releases to help teams update services. *What this accomplishes:* versioned, dated change
  distribution — a brand refresh is shipped as releases, not announcements.

### 4.5 Rust Foundation — open-source trademark policy

**Source:** `http://rustfoundation.org/policies/logo-policy-and-media-guide/`
(the canonical Rust media guide; reached via redirect from
`https://www.rust-lang.org/policies/media-guide`).

#### Ownership and licence structure

The Rust Foundation owns and protects the Rust and Cargo trademarks — two word marks and two logos. The logos are
distributed under the Creative Commons Attribution licence (CC-BY), which permits reuse and modification for any purpose
provided distributors "give appropriate credit, provide a link to the license, and indicate if changes were made" — but
logo use is *additionally* governed by trademark law, not just the licence.

*What this accomplishes:* the dual layer solves an open-source dilemma. CC-BY keeps the marks free enough to circulate
(the community requires this), while trademark law retains the right to stop uses that misrepresent origin — which a
content licence alone cannot do.

#### Permitted uses without approval (as enumerated)

- accurately stating software is written in Rust, compatible with it, or contains Rust code, for commercial and
  non-commercial cases;
- using "Rust" in crate or repository names when indicating compatibility;
- naming tools "cargo-foobar" when they run as "cargo foobar" subcommands, so long as they are not implied to be
  official;
- publicly distributing modified Rust/Cargo versions only for porting to another platform/architecture/system or for
  packaging-system integration;
- hosting a fork intended for upstreaming improvements if it is not marketed or promoted;
- unmodified trademarks on merchandise for personal or small community use where items are not sold;
- free, non-profit events (meetups, tutorials) with no implication of official endorsement;
- unmodified trademarks in publications ("Rust Journal," "Rust Cookbook"), websites, brochures, documentation, academic
  papers, books and packaging.

#### Prohibited or restricted uses (as enumerated)

- any use that appears official, affiliated with, or endorsed by the Rust Project or Foundation without written
  permission;
- endorsement-suggesting terms such as "official," "original," or "only" (the policy's own example of unacceptable
  wording is "The only Rust conference in the USA");
- using the marks for other programming languages or for modified versions beyond minor porting changes;
- misleading users into associating unrelated modules, tools or documentation with Rust;
- uses that confuse the community about whether Rust is open source and free;
- unapproved modifications must be clearly disclosed at distribution.

#### Permission workflow (as stated)

Written permission is required to:

- distribute a modified build under the Rust/Cargo name with changes beyond porting (usually granted if changes are
  small and clearly communicated to users);
- sell merchandise bearing the logo (usually granted if non-official status and profit destination are clearly stated);
- embed Rust trademarks inside another trademark (conditions and possibly a usage fee may apply);
- use the event names "RustCamp," "RustCon," and "RustConf";
- run commercial or sponsored events, which should contact the Foundation first.

Official code and binaries come only from rust-lang.org, crates.io, rustup.rs (and subdomains) and the GitHub
organisation "rust-lang" — with the caveat that not everything on those domains is official.

#### Enforcement and provenance

Suspected misuse should be reported to the Foundation; community members are asked not to confront trademark users
directly (a de-escalation rule that protects community tone). Questions go to contact@rustfoundation.org. The policy
states it is partly derived from the Python Software Foundation's trademark policy — itself evidence that good policy
documents are adapted, not invented.

*What the rule set accomplishes overall:* it protects *meaning*. Every clause defends the same asset — the community's
ability to trust that "Rust" means the actual Rust project. The naming reservations protect the event namespace; the
endorsement bans protect source attribution; the merchandise and event carve-outs keep goodwill uses free while the
commercial edge cases route through a human.

**Not included in this document:** colour specifications, sizing or clear-space rules — a separate "Brand Guide" is
linked but its contents were not fetched. For an agent, the lesson is that a complete brand kit needs both layers: this
*usage-rights* layer and a visual-spec layer.

### 4.6 GNOME Foundation — marks of a free-software community

**Source:** `https://foundation.gnome.org/legal-and-trademarks/`.

#### Stated rules

The GNOME Foundation acts as the legal owner of project assets — the GNOME name and the GNOME foot logo — because, as
the page states, "We must protect these trademarks in order to keep them." Registered word marks include GNOME®, GTK®,
Flatpak® and Flathub®; logos include the GNOME foot and the GTK box.

Permitted use covers statutory fair use (the page notes trademarks "typically may be used without permission in magazine
and book reviews"), situations covered by published third-party usage guidelines (a dedicated trademark-guidelines
page), and user-group use under "a standard agreement" covering "many common situations". Uses beyond the guidelines
require approval via licensing@gnome.org. Logo details and the SVG file are deferred to a separate logo & trademarks
page; no colour specifications appear on the fetched page.

#### What this accomplishes

Three distribution channels for permission — fair use by default, published guidelines for the common cases, a standard
user-group agreement for organised groups — keep the volume of individual permission requests low while reserving
case-by-case review for genuinely novel uses. Publishing the criteria (instead of deciding in email) is what makes a
policy scale; it is the same philosophy as GOV.UK's contribution criteria.

**Not accessible at this level:** visual specs, clear space, misuse examples (on subpages not fetched).

### 4.7 Canonical / Ubuntu — values-anchored brand entry point

**Source:** `https://design.ubuntu.com/` (design site landing page; the
detailed rules live on `/brand` and `/font` subpages not fetched this
session).

#### Stated content

The page states the guideline's aim: "The Canonical and Ubuntu Brand Guidelines exist so we can all communicate Ubuntu
with the same precision we use to make it." The brand rests on four named values — "freedom, reliability, precision and
collaboration". Official logos for all of Canonical's products are downloadable via the Resources page; a dedicated Font
section covers the Ubuntu typeface; the footer notes Ubuntu and Canonical are registered trademarks of Canonical Ltd.
with legal information at ubuntu.com/legal. The site also documents the Vanilla Framework, described as a "lightweight,
composable and open-source component library" that can be used to "build any website or product".

#### What this accomplishes

The landing page demonstrates the *value-to-visual* contract in one sentence — precision in communication mirrors
precision in engineering — and shows a guideline site doubling as a design-system hub (brand + font + component library
in one place).

**Not accessible at this level:** colour values, wordmark and U-bmark rules, co-branding terms (on the unfetched
`/brand` subpage).

### 4.8 Attempted but not accessible

WordPress's logo-and-usage page (`https://wordpress.org/about/logos/`) was
attempted twice this session and returned HTTP 429 (rate limited) both times
via fetch and direct request; a further attempt on 2026-11-24 also returned
HTTP 429. No rule content from it is cited. It is recorded here so a future
pass can add it, completing the open-source trio of visual-spec +
trademark-policy cases.

## 5. Cross-system comparison

| System | Sector | Guideline form | Strongest layer | Governance signal |
| --- | --- | --- | --- | --- |
| UW–Madison | University | Multi-page site, platform→identity→applications | Concrete asset rules + tooling | Named owner; vendor page; changelog |
| University of Exeter | University | Portal + identity page | Numeric, enforceable mark rules | Design Studio adjudicates; master-artwork funnel |
| IBM | Technology company | Design-language site with typeface and grid products | Multi-script type system; named graphic languages | Visible maintenance; kit distribution |
| GOV.UK | Government | Living design system with releases | User-need-indexed patterns; component lifecycle | Contribution criteria; versioned releases |
| Rust Foundation | Open source | Trademark policy document | Usage-rights and endorsement wording | Published permission workflow; community reporting |
| GNOME Foundation | Open source | Trademark policy + linked guidelines | Permission channels at three levels | Standard agreements; published criteria |
| Canonical/Ubuntu | Open source | Design hub (brand + font + components) | Value-to-visual framing | Trademark notice; open-source component library |

Read the table by column: no single system is strongest everywhere. The universities excel at enforceable specifics; IBM
and GOV.UK at governance architecture; the open-source policies at protecting meaning under uncontrollable distribution.

## 6. Cross-system patterns: what each rule archetype accomplishes

This section is original synthesis of the seven case studies above. The recurring rule archetypes, their purpose and
their failure mode when omitted:

| Rule archetype | Seen in | Accomplishes | Failure mode without it |
| --- | --- | --- | --- |
| Separation of ceremonial and everyday marks | Exeter (logo vs crest) | Protects the authority of the legal/ceremonial mark and the utility of the workhorse mark | Ceremonial symbol degrades into decoration; everyday use looks unofficial |
| Numeric minimum sizes | Exeter (20 mm / 15 mm) | Legibility floor; a checkable rule instead of a judgment call | Mark becomes illegible smudge in small placements |
| Master-artwork-only reproduction | Exeter | Prevents tracing, re-drawing, screenshot degradation | Logo mutates gradually across uses |
| Tooling-based distribution | UW icon library + WordPress plugin; IBM Carbon kits; GOV.UK Frontend | Compliance becomes the default path inside creators' tools | Policing after the fact; constant exceptions |
| Automation over enforcement | Exeter email signature system; UW user-directory pull | Consistency without surveillance | Signature/logo drift across thousands of staff |
| Endorsement and wording bans | Rust ("official/original/only"); GNOME approval layer; Exeter partner logos outside signature | Protects source attribution and prevents implied affiliation | Third parties trade on the brand's reputation; legal exposure |
| Named-permission channels | Rust workflow; GNOME (fair use / guidelines / user-group agreement / email) | Scales adjudication; reserves human review for novel cases | Either permission fatigue or blanket bans that break goodwill |
| Values → principles → rules layering | IBM "Build Bonds"; Ubuntu's precision statement; UW Wisconsin Idea | Every rule has a justifiable rationale; disputes resolve at the principle level | Arbitrary-feeling rules; rule-lawyering without purpose |
| User-need indexing of patterns | GOV.UK "Ask users for… / Help users to…" | Guidance matches the question a designer actually has | Correct but unusable documentation |
| Versioned change and lifecycle | GOV.UK releases, lifecycle statuses; IBM "What's new"; UW Brand News | Change is predictable; consumers know what is current | Silent drift; stale guidelines actively followed |
| Single extensible type system | IBM Plex script releases; Ubuntu font section | Multilingual/global consistency from one family | Cacophony of licensed faces across locales |
| Accessibility as strategy, not stamp | GOV.UK accessibility strategy; UW accessible resources link | Inclusion is maintained continuously | Retro-fit accessibility, checklists passed then forgotten |

Two observations deserve emphasis. First, the *university* cases (UW–Madison, Exeter) are strongest on concrete,
enforceable visual rules (sizes, formats, placements, automation), while the *system* cases (IBM, GOV.UK) are strongest
on governance architecture; a complete brand kit needs both halves. Second, the open-source cases show that when an
organisation cannot control distribution (community-made merchandise, events, forks), it moves its rules from the visual
layer to the *language and attribution* layer — words like "official" are regulated more tightly than pixels. An agent
writing guidelines for a distributed community should follow that move.

## 7. Anatomy of a guideline document (reconstructed template)

Derived from the structures observed above (original synthesis), a complete brand guideline contains these layers in
this order. Each layer answers a question; omitting it leaves that question to improvisation:

1. **Platform** — what the brand promises and why it exists (UW's Wisconsin Idea; Ubuntu's four values). Question
   answered: *how should every rule feel justified?*
2. **Marks** — hierarchy of marks, construction, clear space, minimum sizes, master artwork, misuse examples (Exeter's
   crest/logo split). Question: *what may carry the brand, and how small/degraded may it get?*
3. **Colour** — palette with roles and values, functional states, accessibility pairs. Question: *what colours exist and
   where may each appear?*
4. **Typography** — families, hierarchy, multilingual coverage (IBM Plex's script releases). Question: *what does text
   sound like visually?*
5. **Graphic elements** — icons, illustration styles, patterns, each named and versioned (IBM's four illustration
   styles; UW's icon library). Question: *what supporting visuals are allowed?*
6. **Imagery** — photography direction, treatment, rights ([Photography](../imagery/photography.md), [Image
   rights](../imagery/image-rights.md)). Question: *what does the brand look like in pictures?*
7. **Applications** — named surfaces with per-surface adaptations, digital and print (UW's
   print/web/social/email/stationery; GOV.UK's patterns). Question: *how does the identity behave in the wild?*
8. **Co-branding and third-party use** — placement rules, endorsement bans, permission channels (Exeter's signature
   containment; Rust's policy). Question: *what happens when other marks appear?*
9. **Accessibility** — standards referenced, contrast pairs, inclusive conventions (GOV.UK strategy; Exeter pronoun
   rule). Question: *who is the identity designed for?*
10. **Governance** — owner, contact, changelog, permission workflow, vendor guidance (UW's OSC; GOV.UK's community
    section). Question: *who decides and how does the document change?*

For implementation guidance on writing the document itself, see [Brand guidelines](../branding/brand-guidelines.md) and
[Documentation](../design-systems/documentation.md); the tokens layer is covered in [Design
tokens](../design-systems/design-tokens.md).

## 8. Decision framework: applying these models to a new brand kit

When extending a fixed event logo into a complete brand kit (the repository's flagship scenario), use the surveyed
systems as templates by role:

1. **Structure the kit like UW–Madison.** Platform → visual identity → applications → tools and templates → governance
   contact. Every section links to assets, not just descriptions.
2. **Adopt Exeter's mark hierarchy for the fixed logo.** Decide explicitly what the fixed event logo is (ceremonial
   anchor or workhorse), which derived marks may carry everyday use, and write the prohibition sentence that separates
   them — Exeter's "alongside or instead of" formulation is a good pattern. Add numeric minimum sizes and a
   master-artwork rule from day one.
3. **Layer reasoning like IBM/Ubuntu.** Each visual section should open with a one-sentence principle (the "why") before
   its rules, so that an agent applying the kit in an unseen context can extrapolate rather than break.
4. **Distribute assets like the tooling cases.** Ship the kit with actual files (logo SVGs, colour tokens, type files)
   and, if the output is web-based, tokens or components rather than screenshots ([Design
   tokens](../design-systems/design-tokens.md)).
5. **Regulate attribution like the open-source policies.** If the event brand will be used by sponsors, volunteers or
   press (it will), write the permitted/prohibited-use list and the endorsement wording rules — the Rust case shows the
   exact clauses needed.
6. **Index application guidance by need.** Follow GOV.UK's pattern of organising rules by the task ("design the
   certificate", "make the social banner") rather than by asset type, mirroring the repository's
   [Applications](../applications/event-collateral.md) directory.
7. **Make accessibility a strategy.** Include contrast-paired colour specs and accessible-typography rules from the
   start, citing a standard ([WCAG fundamentals](../accessibility/wcag-fundamentals.md)).

A worked synthesis of this process on a real event identity belongs in [Case studies](case-studies.md); the reusable
method is documented in [Brand guidelines](../branding/brand-guidelines.md).

### 8.1 Practical notes for agents

- **Quote rules, cite systems.** When justifying a design decision to a client, citing the archetype ("master-artwork
  rule, as universities require") carries more authority than a bare preference — but cite the system honestly (name +
  URL), never fabricate its contents.
- **Rules have boundaries.** A minimum-size rule protects legibility but does not mandate artistic restraint; an
  endorsement ban does not restrict nominative use ("made with X"). Apply rules to the failure mode they name, not
  further.
- **Policy text is copyrighted.** The documents above are quoted only in short attributed fragments ("The use of the
  crest alongside or instead of the University logo is not permitted."; "Build Bonds"). When reusing guideline language,
  paraphrase and attribute; when following guideline *rules*, no attribution is needed — rules are not owned ideas.
- **Verify before copying numbers.** The only numeric values safely transferable from this survey are structural
  (Exeter's size-floor *concept*, the 11 pt / 8 pt signature hierarchy *concept*). Colour values and current platform
  sizes must be re-verified per project and per brand.

## 9. Common mistakes and limitations of this survey

### 9.1 Common mistakes

- **Collecting PDFs instead of extracting rules.** The mission's warning in practice: a folder of 30 guideline PDFs with
  no analysis yields no reusable knowledge. Extract the rule, its rationale and the failure mode.
- **Confusing trademark policy with visual guidelines.** The Rust and GNOME pages say almost nothing about colour or
  layout — and should not be cited as though they did. Match the source to the claim type.
- **Reading one page as the whole system.** Every case here has unfetched subpages; claiming "Brand X specifies no
  colours" when the values simply live elsewhere is an access error, not a finding.
- **Copy-pasting values across brands.** A university's 20 mm crest minimum does not transfer to a start-up's wordmark;
  what transfers is the *floor-setting practice*, recalculated for the new mark's detail level.
- **Treating governance as an afterthought.** The most durable systems here spend as much design effort on contribution,
  release and permission workflow as on visuals. A kit with no named owner, no changelog and no permission channel will
  decay.

### 9.2 Limitations of this survey

- All seven systems were read at their entry/main pages; detailed subpages
  (UW–Madison colour/logo specs, Exeter Brand Portal fonts and colours, IBM
  colour specifications, GOV.UK per-component pages, Rust's visual "Brand
  Guide", GNOME logo page, Canonical `/brand`) were not fetched this
  session. No specification from those subpages is asserted anywhere above.
- `https://brand.exeter.ac.uk` is a JavaScript-based guide viewer that did
  not yield rule text to the fetch tool; the university-level visual
  identity page was used instead.
- `https://wordpress.org/about/logos/` returned HTTP 429 twice and could
  not be read.
- The GOV.UK page names no WCAG conformance level on the fetched page; the
  standard claim was left to the dedicated accessibility files.
- The survey under-represents cultural institutions and large
  events/conferences (no such system was fetched); the sector patterns in
  Section 6 for those categories should be treated as unverified.

## 10. Related topics

- [Brand guidelines](../branding/brand-guidelines.md) — how to author the guideline document itself.
- [Logo systems](../branding/logo-systems.md) and [Fixed logo analysis](../branding/fixed-logo-analysis.md) — extending
  a fixed mark, the scenario these patterns serve.
- [Brand governance](../branding/brand-governance.md) and [Governance](../design-systems/governance.md) — the ownership,
  changelog and permission models extracted above, in depth.
- [WCAG fundamentals](../accessibility/wcag-fundamentals.md) — the standard behind the accessibility sections.
- [Design tokens](../design-systems/design-tokens.md) — the tooling-based distribution model in implementation form.
- [Academic curricula](academic-curricula.md) — the education-facing companion file.
- [Bibliography](bibliography.md) — canonical works referenced across the library.
- [Image rights](../imagery/image-rights.md) — the rights layer beneath trademark and co-branding rules.

## 11. References

[accessed] Office of Strategic Communication, University of
Wisconsin–Madison, "University Relations — Brand and Style Guidelines"
(brand.wisc.edu). https://brand.wisc.edu/ (accessed 2026-11-23).

[accessed] University of Exeter, Communications, "Visual identity".
https://www.exeter.ac.uk/departments/communication/communications/design/visualidentity
(accessed 2026-11-23).

[accessed] IBM, "IBM Design Language". https://www.ibm.com/design/language/
(accessed 2026-11-23).

[accessed] Government Digital Service, "GOV.UK Design System".
https://design-system.service.gov.uk/ (accessed 2026-11-23).

[accessed] Rust Foundation, "Logo Policy and Media Guide".
http://rustfoundation.org/policies/logo-policy-and-media-guide/
(accessed 2026-11-23; reached via redirect from
https://www.rust-lang.org/policies/media-guide).

[accessed] GNOME Foundation, "Legal and Trademarks".
https://foundation.gnome.org/legal-and-trademarks/ (accessed 2026-11-23).

[accessed] Canonical Ltd., "Ubuntu and Canonical design — Brand Guidelines"
(design.ubuntu.com). https://design.ubuntu.com/ (accessed 2026-11-23).

[search-verified] University of Exeter, "Brand Guidelines" portal
(JavaScript viewer, not parsed). https://brand.exeter.ac.uk

[search-verified] University of Exeter, "Our logo".
https://www.exeter.ac.uk/about/ourstory/logo (not opened).

[accessed-failed] WordPress.org, "Logos and Graphics".
https://wordpress.org/about/logos/ (HTTP 429 on two attempts, 2026-11-23 —
no content cited).
