# Brand governance

## 1. What is it?

Brand governance is the system of roles, processes and tools that keeps a visual identity consistent after launch: who approves brand-affecting work, how assets are versioned and distributed, how changes are documented, how drift is detected and corrected, and how exceptions are handled without becoming precedents. Guidelines ([Brand guidelines](brand-guidelines.md)) state the rules; governance makes the rules actually hold across teams, vendors and time.

Governance operates on three layers: **people** (owners and custodians with named responsibilities), **processes** (approval flows, versioning, audits, exception handling) and **infrastructure** (the single source of truth for assets — a brand portal or digital asset management system, often abbreviated DAM — with permissions and lifecycle control). Vendor sources describe the DAM layer as the mechanism that centralises assets, publishes guidelines alongside them and checks compliance at scale [search-verified], which matches how the mature public systems observed this session work in practice.

## 2. Why does it matter?

Identities decay by default. Every project adds files, every new vendor improvises, every expired campaign lingers in a template, and none of it looks wrong on any single day — but six months later the organisation's materials no longer match each other, and the recognition that consistency builds ([Visual identity](visual-identity.md)) quietly stops accumulating. The scenario is concrete and common: a logo is updated and the old version keeps circulating for years because nobody owns retirement; a sub-brand adds a colour; a partner lockup is invented per campaign. Governance exists to make each of these either impossible or deliberate.

Governance also answers the practical questions that stall real projects: who signs off this poster? which logo file is current? may we use last year's template? A governance system with named roles and published turnaround times turns those from interruptions into routine — Uber Eats' published co-marketing flow (submit to the Brand Desk; 3–5 business days standard turnaround) is governance stated as policy, visible to the users who need it [accessed].

For this repository's primary audience — agents and non-designers producing real materials under time pressure — governance is what makes self-service safe. An agent can pick the current file, apply the numbered rule, and justify its decision by citation only when the surrounding system guarantees that the files are current, the rules are numbered, and the exceptions are recorded. Governance is therefore not bureaucracy added to the identity; it is the precondition for trusting anyone, human or machine, to use it without supervision.

## 3. Core principles

**One owner per decision.** Every brand decision type has exactly one accountable role. Shared ownership means no ownership; ambiguity is how drift begins.

**Single source of truth.** There is exactly one canonical location for every asset and every rule. Derivatives (PDF exports, vendor kits, quick-reference sheets) are generated from it and labelled as copies. Anything not in the source of truth is, by definition, not current.

**Review by exception is not governance.** If everything is urgent and approved verbally, nothing is governed. The system must define what requires review and make the routine path fast enough that the review path is not worth bypassing.

**Document the change, not just the artefact.** Every change to the identity (a new colour, a retired logo file, an updated template) is recorded with date, reason and approver. Undocumented changes are indistinguishable from mistakes a year later.

**Exceptions expire.** A permitted deviation is granted for a defined case and time, is logged, and does not silently become the new rule. Permanent changes go through the change process instead.

## 4. How it works

### 4.1 Roles and ownership

A minimal, workable role set scales from a one-person team to an organisation by stacking roles:

| Role | Owns | Typical actions |
|---|---|---|
| Brand owner | The identity and its strategy | Approves structural changes (architecture, palette, typeface), resolves escalations |
| Brand custodian / manager | Day-to-day integrity | Reviews submissions, maintains guidelines and asset library, runs audits, grants exceptions |
| Asset librarian | The asset store | Versions files, retires old assets, maintains naming and metadata |
| Creators (teams, vendors, volunteers) | Their own outputs | Use approved assets, follow guidelines, submit non-standard work |
| Reviewers (legal, accessibility, communications) | Their domain in the review | Sign off within their scope |

Two ownership rules prevent the classic failures. First, ownership is assigned to **roles, not individuals** — a person leaving must not orphan the identity. Second, for a fixed logo the ownership rule is explicit: the custodian owns the mark's files and its prohibited-modifications list ([Fixed-logo analysis](fixed-logo-analysis.md)), and nobody else edits, re-exports or "improves" them.

For agents and tooling, the same role set maps onto permissions: the custodian role is whoever can write to the canonical asset store; creators read and copy from it; and nothing in the store changes without a changelog entry. Mapping the human roles onto access levels keeps human and machine actors inside one governance model — an agent that can only read the canonical store cannot silently introduce a rogue asset, and its outputs are reviewed by the same flow as anyone else's submissions.

### 4.2 Approval processes

A defined flow with a published service level. A standard four-step flow:

1. **Intake.** A short submission: what is being produced, who for, which assets it uses, what deviates from guidelines. Non-standard work (new lockups, new colours, co-branding) requires review; standard template use does not.
2. **Review against criteria.** The custodian checks the submission against the guidelines' rules — not against taste. This is why the rule-writing style of [Brand guidelines](brand-guidelines.md) matters: numbered, quantified rules make review fast and defensible.
3. **Decision with record.** Approve, approve with conditions, or reject with the rule citation and the correct alternative. The record is the audit trail.
4. **Published turnaround.** Users must know the cost of review in advance; Uber Eats publishes 3–5 business days for co-marketing review [accessed], which is the pattern to copy: a committed service level, not a vague "we'll get back to you".

Escalation path: custodian → brand owner for structural disputes; a decision log keeps precedents findable.

A useful discipline is to publish **what needs review and what does not**, so self-service is unambiguous:

| Work type | Review? | Who decides |
|---|---|---|
| Standard template filled with new content | No | Creator (self-check against template) |
| Existing assets on approved layout | No | Creator |
| New lockup, new colour use, off-template layout | Yes | Custodian |
| Co-branded or sponsored material | Yes | Custodian, per architecture tier table |
| Anything containing the fixed logo outside supplied contexts | Yes | Custodian (owner if structural) |
| Change to palette, type, architecture or guidelines | Yes | Brand owner |

The table removes the two classic failure modes at once: creators who over-submit everything (the flow chokes) and creators who never submit anything (drift). A worked example: a volunteer asks to put the event logo on a sponsor's dark-blue banner. Under the flow, that is "fixed logo outside supplied contexts" — custodian review; the custodian checks the background policy, supplies the reversed variant, states the clear-space rule, and records the decision. Total cost: minutes, because the rule was decidable.

### 4.3 Version control of assets

Brand assets need the discipline code gets:

- **Master and derivatives.** Master files (vector logo, palette source, type files, template sources) are immutable once approved; distribution formats (PNG sets, PDF exports) are generated from masters and never edited directly.
- **Naming convention.** A predictable scheme, for example `brand-element_variant_colourspace_size_version.ext` → `logo-primary_rgb_2x_v03.png`. Version in the filename or in metadata, not in folder names like `final_final`.
- **Status lifecycle.** Each asset carries a status: `current`, `deprecated` (do not start new work), `retired` (remove from portals; replace wherever found). Deprecation is the tool that makes logo changes actually propagate.
- **Changelog.** Every version bump is logged: date, what changed, why, approver. The changelog is part of the guideline document's governance section.

Two naming examples show the scheme working in practice. A re-coloured distribution file for a dark theme: `logo-primary-white_rgb_2x_v03.png` — variant, colourway, colour space, density and version all readable without opening it, matching the labelling pattern visible in Spotify's public kit filenames [accessed]. A superseded print master: `logo-primary-print-cmyk_v02.pdf` with its status flipped to `deprecated`, so the next vendor brief pulls `v03` and the sweep eventually retires `v02` everywhere. The test of the scheme is whether a new collaborator can pick the right file from a listing alone — if not, the convention is too clever.

### 4.4 Documenting changes

Changes to the identity itself — new colour role, updated template, altered architecture slot — follow the same record discipline: proposal → approval by the owning role → guideline update → asset versioning → announcement → template/deprecation sweep. The order matters: the guideline and assets change together, or the document and reality diverge (the worst governance state, because the document then lies). For small organisations the whole system can be one changelog table in the guidelines; the discipline matters more than the tooling.

### 4.5 Preventing visual drift

Drift is detected by looking, and prevented by making the correct path the easy path:

- **Templates.** The highest-leverage tool: pre-approved posters, decks, social cards and documents in which the rules are already applied. Drift falls when the template is easier than improvising.
- **Audits.** A scheduled review of live materials (website, social feed, current print, vendor outputs) against the guidelines, scored with the evaluation checklists of this domain. Frequency is a resource decision — quarterly is a common starting point; the fixed point is that someone owns it.
- **Five-second spot checks.** Between audits, custodians check new high-visibility outputs before or shortly after publication.
- **Deprecation sweeps.** When an asset is retired, actively find and replace live uses (site, templates, vendor stock), rather than waiting for natural turnover.
- **Drift triage.** Classify each finding: misuse (correct it, cite the rule), rule gap (the rule did not cover the case — fix the guideline), or outdated asset (retire and replace). Every audit finding should end in one of those three.

A repeatable audit procedure, sized to be actually run:

1. **Sample** — pick the live surfaces: the website home page, the most recent five social posts, one current print piece, one e-mail or newsletter, one vendor-produced item.
2. **Score** — walk the domain checklists ([Brand identity checklist](../evaluation/brand-identity-checklist.md) plus the checklists in this domain's files) and mark pass/fail per item.
3. **Triage** — classify every failure as misuse, rule gap or outdated asset (see above).
4. **Fix and record** — corrections are made and logged; rule gaps become guideline changes through the change process in 4.4.
5. **Report** — a short audit note (date, surfaces checked, findings, actions) joins the changelog, so the next audit can verify that fixes held.

### 4.6 Consistency across teams and vendors

External and non-design audiences need the rules in their own working terms: onboarding material with the quick-reference sheet ([Brand guidelines](brand-guidelines.md) section 4), task-oriented paths in the manual ("making a slide? section…"), and vendor briefs that attach the relevant guideline sections and the exact asset files rather than assuming familiarity. Contractual hooks matter for vendors: which files are permitted, what requires review, what happens on breach. Internally, consistency across teams is mostly a template and review problem (4.5); externally it is mostly a supply problem — vendors misuse the logo most often because the right file was never supplied.

A minimal vendor onboarding pack removes most downstream corrections. It contains: the relevant guideline sections (logo rules, colour, logo-on-background policy for the formats the vendor produces); the exact files the vendor may use, with the context → file mapping from the portal README; the review trigger and turnaround that apply to their deliverables; and a single named contact for brand questions. The pack is assembled once per vendor relationship, not per order — but it must be regenerated whenever the underlying assets change versions, which the deprecation sweep (4.5) catches.

### 4.7 Asset distribution: brand portals and DAM basics

The distribution layer is where governance becomes self-service. A brand portal (public or login-gated) or DAM provides: the canonical asset library with current versions only; usage guidance attached to each asset; search by asset type and context; permissions (who may download masters versus distribution formats); and lifecycle control (deprecation dates, expiry). Commercial platforms in this space — Bynder, Templafy, Adobe Experience Manager Assets — position themselves around exactly these functions: centralising assets, publishing guidelines alongside them, and automating compliance checks [search-verified]. The tool is optional; the functions are not. A shared folder can satisfy the minimum if it has: one canonical tree, status labels, a README mapping context → file, and a named librarian. What it cannot easily provide — permissions, expiry, usage analytics — is what justifies a real DAM as the brand's surface area grows.

The functions any distribution layer must provide, however implemented:

| Function | What it means | Failure without it |
|---|---|---|
| Currency | Only current versions are visible; deprecated ones are hidden or archived | Old logo files keep circulating |
| Guidance adjacency | Usage rules are attached to (or one click from) each asset | Assets downloaded without their rules |
| Findability | Search/browse by asset type, colour, context | Users ask a human or grab whatever is at hand |
| Permissions | Masters restricted; distribution formats open | Uncontrolled master edits |
| Lifecycle | Expiry dates, deprecation status, retirement workflow | Silent deprecation |
| Provenance | Version, date, and owner recorded per asset | Nobody knows which file is authoritative |

Minimum viable portal structure:

```text
brand-portal/
  guidelines/          (canonical manual + quick-reference sheet)
  logo/                (current versions only; deprecated files removed)
  colour/              (palette specs, accessibility pairings)
  typography/          (licensed files or licence instructions)
  templates/           (pre-approved, versioned)
  imagery/             (approved photography, treatment presets)
  README.txt           (context → file mapping; owner contact)
```

### 4.8 Exception handling

Real contexts will not always fit the rules — a heritage venue forbids white walls; a partner agreement mandates a lockup the guidelines never anticipated. Exceptions are handled, not ignored:

1. **Request.** The requester states the constraint, the rule affected, and the proposed deviation.
2. **Decision.** The custodian (or owner, if structural) approves with scope and **expiry**, or rejects with an alternative; where the same exception recurs, convert it into a guideline rule instead (the exception log is a rule-gap detector).
3. **Log.** Exception register: date, requester, rule affected, deviation, scope, expiry, approver.
4. **Expire.** On expiry the deviation ends unless renewed or promoted into the rules. An exception without an expiry is a silent rule change.

The exception register can be a simple table in the governance section of the guidelines:

```markdown
| Date | Requester | Rule affected | Deviation requested | Scope | Expiry | Decision | Approver |
|------|-----------|---------------|---------------------|-------|--------|----------|----------|
| …    | …         | e.g. G1.3 clear space | …            | this venue only | 2027-06-30 | approved | custodian |
```

Reviewing the register quarterly answers a question pure enforcement cannot: are our rules wrong? Three or more similar exceptions against the same rule is evidence that the rule, not the users, needs to change — which is how governance feeds back into [Brand guidelines](brand-guidelines.md).

## 5. Practical application

Setting up governance for a small organisation or event in one sitting: name the owner and custodian (roles can stack); publish the guidelines with the governance section filled (owner, approval flow, turnaround, changelog); create the portal structure above with current assets only; state the review triggers (non-standard lockups, new colours, co-branding, anything affecting the fixed logo); publish the turnaround commitment; start the changelog and exception register as two tables in the guidelines document; schedule the first audit. That is the whole minimum system — every later addition (DAM tooling, more roles, formal SLAs) is scaling the same functions.

For the custodian, the recurring routine is deliberately small enough to run alongside other work: keep the library current (every new or changed asset gets version, status and metadata on entry); answer submissions against the rules with citations; do the periodic audit per 4.5; run the deprecation sweep whenever anything is retired; and close expired exceptions. Everything else — templates, onboarding, vendor briefs — is built once and maintained, not rebuilt per project. Agents acting as custodians or creators should follow the same routine mechanically: check the rule, cite it, record the decision, and leave the audit trail where the next actor will find it.

## 6. Decision framework

| Situation | Governance response |
|---|---|
| Standard template use | No review needed; self-service from the portal |
| Non-standard application (new lockup, off-template layout) | Custodian review; decision with rule citation; record kept |
| Co-branded or sponsored material | Review against the architecture tier table; published turnaround |
| Change to identity structure (palette, type, architecture) | Brand owner approval; guideline + assets updated together; changelog entry |
| Rule cannot be satisfied in a real context | Exception process with scope and expiry; recurring cases become rules |
| Old asset found in circulation | Deprecation sweep; replace with current file; log the find |
| Repeated audit failures by one team or vendor | Onboarding/targeted brief before enforcement; templates supplied |

When deciding how much governance a project needs, scale by risk: the fixed logo and anything co-branded or public-facing is high-risk (strict review); internal documents on approved templates are low-risk (self-service). Uniform heavy review punishes the low-risk 80% and gets bypassed; uniform light review loses the high-risk 20%.

Decisions worth recording are decisions someone will ask about again. The decision log — a table in the governance section — is the lightweight alternative to process tools:

```markdown
| Date | Item | Decision | Rule cited | Decider |
|------|------|----------|-----------|---------|
| …    | sponsor banner, reversed logo use | approved with conditions | G1.4, G8.3 | custodian |
| …    | proposal: secondary palette colour | rejected — use existing pair | G2.1 | owner |
```

For agents and external collaborators the log has a second value: it shows how past similar cases were decided, so a new case can be decided consistently without asking. A governance system whose precedents are findable behaves like a well-run court — predictable, fast, and self-consistent — while one whose precedents live in memory behaves like taste.

## 7. Examples

**Uber Eats** ([accessed](https://merchants.ubereats.com/us/en/resources/learning-center/co-marketing-tools)). Governance published to its users: co-marketing featuring the logo must be submitted to the Brand Desk before launch, with a standard 3–5 business-day turnaround; approved CTA phrases are enumerated; the partner-lead lockup rule is stated as policy. Demonstrates that approval flows work when they are written down where users will read them.

**MIT** ([accessed](https://brand.mit.edu/applying-brand/do-dont)). Decentralised governance with central control: sub-brand files are distributed on request via a named contact channel; users must use them "as provided"; violations of the mark hierarchy (sub-brands outside the permitted entity types) are ruled out by policy; specific channels (social media) carry stricter rules than general collateral. Demonstrates scaling an identity across hundreds of autonomous units through supply control plus explicit boundaries.

**University at Buffalo** ([accessed](https://www.buffalo.edu/brand/identity/usage/Clear-space.html)). Distributed governance with named human contacts for merchandise decisions, and rules that prevent informal mark combinations ("repeatedly placing a word or short phrase near the master brand lockup... is not permitted") — governance anticipating the specific improvisations users actually attempt.

## 8. Common mistakes

- **Ownerless identity.** Nobody is accountable, so nothing is enforced. Fix: named roles from day one, even if one person holds two of them.
- **Review as taste dispute.** Approvals argued by preference. Fix: review against numbered, quantified rules ([Brand guidelines](brand-guidelines.md)); cite the rule in the decision.
- **Everything requires review.** The flow bottlenecks and users route around it. Fix: template self-service for standard work; review only what deviates.
- **Versioning by folder.** `logo_final_v3_NEW` circulates; wrong files win. Fix: masters, generated derivatives, status labels, a librarian.
- **Silent deprecation.** Old logo files stay downloadable after a refresh. Fix: deprecation status, portal purge, active sweep of live uses.
- **Exceptions without expiry.** One-off deviations harden into informal rules. Fix: exception register with expiry; recurring exceptions become rules.
- **Guidelines and reality diverging.** The manual says one thing, templates do another. Fix: guideline and asset updates are one atomic change with a changelog entry.
- **Vendor onboarding skipped.** Suppliers get a logo JPG and their best guesses. Fix: vendor briefs attach guideline sections plus the exact permitted files.
- **Governance by enthusiasm.** Early volunteers enforce everything; six months later nobody does. Fix: the system is the roles, flows and records defined in this file — not the energy of whoever happens to care this month.
- **Audits without consequences.** Findings are noted, nothing changes, the same failures return. Fix: triage to a decision (misuse / rule gap / outdated asset) with a named owner and a logged action for each finding.

## 9. Evaluation checklist

- [ ] Owner and custodian roles are named (by role, with a person currently holding each).
- [ ] Approval flow is published: triggers, steps, decision records, turnaround commitment.
- [ ] Review decisions cite guideline rules; a decision log exists.
- [ ] Master files are immutable and derivatives are generated, labelled with version and colour space.
- [ ] Asset lifecycle states (current / deprecated / retired) are in use; retired files are removed from the portal.
- [ ] A changelog records every identity change: date, change, reason, approver.
- [ ] A brand portal or equivalent single source of truth exists with a README mapping context → file.
- [ ] Scheduled audits run against the domain evaluation checklists; each finding is triaged (misuse / rule gap / outdated asset).
- [ ] Teams and vendors receive onboarding material and task-oriented guideline paths; vendor briefs attach permitted files.
- [ ] Exceptions are logged with scope and expiry; the register is reviewed for rule gaps.
- [ ] The fixed logo's prohibited-modifications list is enforced: no edits by anyone but the custodian.
- [ ] A decision log exists and recent decisions are findable by subject.
- [ ] The vendor onboarding pack is current with the latest asset versions.
- [ ] Audit reports are written, and the next audit verifies that previous fixes held.
- [ ] The review scope table (what needs review, what does not) is published where creators will see it.

## 10. Related topics

- [Brand guidelines](brand-guidelines.md) — the rule set governance enforces and versions.
- [Visual identity](visual-identity.md) — the identity being kept consistent.
- [Logo systems](logo-systems.md) — the assets and misuse catalogue at the centre of governance.
- [Fixed-logo analysis](fixed-logo-analysis.md) — prohibited-modifications documentation and immutable-asset ownership.
- [Brand architecture](brand-architecture.md) — structural decisions that require owner-level approval.
- [Brand strategy](brand-strategy.md) — upstream decisions governance protects.
- [Brand identity checklist](../evaluation/brand-identity-checklist.md) — audit instrument for drift detection.
- [Design critique](../foundations/design-critique.md) — review method that complements rule-based approval.

## 11. References

- [accessed] Uber Eats, "Marketing Tools & Brand Guidelines for Merchants", https://merchants.ubereats.com/us/en/resources/learning-center/co-marketing-tools, accessed 2026-11-23 (published approval flow, turnaround, phrase governance).
- [accessed] MIT, "Do/Don't | MIT Brand Guide", https://brand.mit.edu/applying-brand/do-dont, accessed 2026-11-23 (central supply via contact channel, use-as-provided rule, channel-specific restrictions).
- [accessed] University at Buffalo, "Clear Space — Identity and Brand", https://www.buffalo.edu/brand/identity/usage/Clear-space.html, accessed 2026-11-23 (named contact, anti-combination rules).
- [search-verified] Bynder, "AI-powered DAM platform for inspiring brands", https://www.bynder.com/en/solutions/teams/brand-management (DAM functions: centralise, publish guidelines, compliance checks; appeared in search results, not fetched).
- [search-verified] Templafy, "What is brand asset management? Tools, workflow", https://www.templafy.com/brand-asset-management (brand asset management definition; appeared in search results, not fetched).
- [canonical] Alina Wheeler, *Designing Brand Identity*, Wiley (multiple editions) — governance and management as the sustaining phase of identity programmes.
- The four-step approval flow, lifecycle states, portal structure and exception process are this repository's synthesis of the sources above with standard asset-management practice; they are professional conventions to be adapted, not researched constants.
