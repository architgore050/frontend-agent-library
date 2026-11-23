# Social Media Checklist

## 1. What is it?

A checklist for evaluating social media visual assets: posts, stories, banners and profile assets — usually produced as a *set* from a shared template. It covers platform dimensions and safe zones, readability at feed size, template consistency across the set, identity compliance, text-to-image balance and CTA clarity. It applies the master method of [design-quality-framework.md](design-quality-framework.md) to the social asset's defining conditions: seen small, seen briefly, seen inside a platform interface that adds its own chrome on top.

Social assets are the most constrained artefacts in this library: the designer controls the canvas but not the frame around it. Evaluation therefore starts from what the platform does to the design, not from the design file itself.

## 2. Why does it matter?

Social platforms crop, compress and overlay. A design reviewed only at full size in its source file misses exactly the failures that matter: the headline covered by the platform's username overlay in stories, the CTA cropped by a 4:5-to-1:1 grid preview, the caption text unreadable on a phone held at arm's length. Because social assets are produced in sets (a week of posts, a campaign of twelve), a template error repeats — one wrong safe-zone assumption becomes twelve defective assets.

Social is also a standard application layer when extending a fixed event logo into a brand kit, so this checklist is used on the social mockups during kit evaluation ([brand-identity-checklist.md](brand-identity-checklist.md) section F).

## 3. Core principles

**Principle 1 — Evaluate in platform context.** Render or preview the asset where it will actually appear: feed thumbnail, full post, story with UI overlays, grid preview. The file on disk is the input; the feed rendering is the artefact.

**Principle 2 — Safe zones are objective.** Platform UI overlays (username, timestamp, action icons, caption bars) occupy predictable margins. Keep critical content (text, CTA, logo) out of them. Exact overlay geometry changes with platform updates — treat specific pixel values as conventional starting points and verify against the current platform spec before a campaign.

**Principle 3 — Readability at feed size is a hard gate.** Test the asset at realistic feed size (roughly 150–400 px wide on a phone) before judging it at full size. Body text that needs the zoom gesture has failed for most of the audience.

**Principle 4 — The set is the unit of evaluation.** A campaign or content calendar is judged as a system: template consistency, rhythm of variation, and identity discipline across items — mirroring the consistency dimension in [design-quality-framework.md](design-quality-framework.md).

**Principle 5 — One asset, one message, one action.** Feed attention is measured in fractions of a second. An asset that carries three messages has no message.

## 4. How it works

Evaluate per-asset, then per-set. Per-asset checks: dimensions/safe zones → feed-size readability → hierarchy and CTA → identity compliance → text-to-image balance. Then a set-level pass: template consistency, visual rhythm, and caption/accessory coherence. Classify defects with the standard severity model; the same error repeated across a set is one severity level higher than an isolated instance.

## 5. Practical application — the checklist

### 5.1 Platform dimensions and safe zones

| # | What to check | How | Pass criteria |
| --- | --- | --- | --- |
| S1 | Correct dimensions for the intended placement **[B]** | Compare canvas size/ratio to the platform spec (square feed, portrait 4:5 feed, 9:16 story, event cover, profile) | Exact spec or exportable equivalent; no stretched or padded-to-fit files |
| S2 | Export at 2× where supported **[B]** | Check pixel dimensions vs. display size | Sharp on high-DPI phones (no soft text, no JPEG artefacts on flat colour) |
| S3 | Safe zones respected **[B]** | Overlay the platform UI regions (story: top/bottom UI bands and edges; feed: bottom-left profile/caption overlay area in some placements) | No text, logo, CTA or critical image detail inside any overlay region; exact zones verified against current platform guidance — conventional values only as a fallback |
| S4 | Crop-safe centre | Check the centre crop of the image for the grid/profile preview | Key subject and message survive the automatic crops |
| S5 | Multi-slide assets (carousels) | Check slide count limit, consistent canvas, and that slide 1 carries the message alone | Slide 1 works without the rest; each slide legible at feed size |

### 5.2 Readability at feed size

| # | What to check | How | Pass criteria |
| --- | --- | --- | --- |
| R1 | Headline readable at thumbnail scale **[B]** | Render at ~150–400 px wide (feed simulation) | Headline readable without zoom; at grid-thumbnail size the message still registers |
| R2 | Minimum type sizes | Check smallest text; floor scales with canvas (conventional: ≥ ~24 pt equivalent on a 1080 px-wide canvas for supporting text, headline proportionally larger) | Nothing below the floor; details that cannot meet the floor are moved to the post caption instead |
| R3 | Contrast on every text pair **[B]** | Measure WCAG-style ratios ([../accessibility/wcag-fundamentals.md](../accessibility/wcag-fundamentals.md)) | ≥ 4.5:1 for supporting text, ≥ 3:1 for large headline text; scrim/panel used over imagery |
| R4 | Legibility under compression | Export, upload to a test account or simulate JPEG compression, inspect | Flat colours not banding badly; fine text not smearing |
| R5 | Motion assets (video/GIF) | Check legibility of the opening frame and any text-on-screen duration (conventional: hold text ≥ ~1–2 s) | Message intact without sound or full playback |

### 5.3 Template consistency across a set

| # | What to check | How | Pass criteria |
| --- | --- | --- | --- |
| T1 | Shared template elements identical across the set | Diff logo placement, headline position, footer/sign-off strip, background treatment across all items | Pixel-identical or token-identical; only intended variable slots (headline, image, accent) change |
| T2 | Deliberate variation is rhythmic, not random | Review the set in feed order | Variation (e.g. alternating accent colour) follows a stated pattern; no one-off outliers |
| T3 | Series labelling coherent | Check numbering/labels ("Part 1/3", date chips) | Same format and position everywhere |
| T4 | Set works in profile grid context | View the published/predicted grid | No jarring adjacency (clashing neighbours, repeated identical crops) unless intended |

### 5.4 Identity compliance

| # | What to check | How | Pass criteria |
| --- | --- | --- | --- |
| L1 | Logo correct variant, official asset, unmodified | Compare to kit files ([brand-identity-checklist.md](brand-identity-checklist.md) B-section) | Official file; correct variant per ground |
| L2 | Clear space and minimum size respected | Measure against kit rules | Within stated zones/sizes |
| L3 | Palette discipline | Sample used colours against kit | Zero stray colours; accent used per its role |
| L4 | Type system respected | Check faces and scale against kit | Kit faces only; sizes from the kit's social scale |
| L5 | Platform profile assets consistent with kit | Check avatar/banner render | Icon variant legible at avatar size (~40 px rendered); banner coherent with kit |

### 5.5 Text-to-image balance and CTA clarity

| # | What to check | How | Pass criteria |
| --- | --- | --- | --- |
| B1 | One message per asset | State the message in one sentence; compare with the asset | Match; two co-equal messages is a Major |
| B2 | Text area vs. image area balanced | Inspect layout | Text does not crowd the image into insignificance, nor float lost; no large dead zones (conventional guidance: text occupies a modest, deliberate share of the canvas — many ad platforms penalise text-heavy images) |
| B3 | CTA singular and explicit **[B]** | Identify the action ("Register", "Shop now", "Save the date") | Exactly one primary CTA, visually distinct, outside safe zones |
| B4 | CTA destination accuracy | Check link/QR/username against source of truth | Correct destination — per information-accuracy rule, a wrong link is a Blocker |
| B5 | Caption and hashtag hygiene | Check the post copy that accompanies the asset (in scope: formatting, tagging, mentions) | Mentions/hashtags resolve to the right accounts; copy consistent with asset message |

## 6. Decision framework

Order of priorities for social sets: (1) S1–S3 and B4 — wrong dimensions, cropped messages and wrong destinations are blockers that invalidate the post; (2) R1/R3 — unreadable or low-contrast text defeats the asset's purpose; (3) T1 — template drift across a set (systemic, Major+); (4) L1–L4 identity items; (5) B1–B2 balance; (6) polish. Because sets multiply defects, fix the *template* first, then regenerate all affected items, then re-run the set-level pass (T1–T4) — per-asset patching of a template error is wasted work. Corrections and re-evaluation follow the loop in [design-quality-framework.md](design-quality-framework.md) §6.

## 7. Examples

**Example 1 — 12-post campaign set.** Template: 1080 × 1350, logo bottom-right at 60 px, headline top-left, accent bar colour alternates weekly. Findings: (1) three posts use the old headline position (T1 — Major, fix template and regenerate); (2) post 7's CTA link points to last year's registration page (B4 — Blocker); (3) two posts place the headline inside the story-cross-posting overlay band (S3 — Major, since these are also reused as stories); (4) post 2 headline at 33 px on the 1080 canvas fails R1 at feed size — Major; (5) alternating accent follows a stated 3-colour rotation — Pass (T2). Corrections: template fix → regenerate → re-run set pass.

**Example 2 — event story asset.** 1080 × 1920 with date chip 120 px from bottom — inside the story UI band on common clients. Correction: raise chip into the safe zone; re-check S4 centre crop. Also caught: QR at 180 px on a 9:16 canvas — scans fine (verified by test scan), Pass.

**Example 3 — feed-size test catching a "perfect" design.** At full size, a 46-word supporting paragraph reads beautifully; at 300 px feed width it is a grey smear. Per R2's alternative, the paragraph moves to the post caption, the canvas keeps one short supporting line, and the report records the decision (not a defect) — the distinction between defect and correction-of-scope in [design-quality-framework.md](design-quality-framework.md).

## 8. Common mistakes

- **Reviewing at full size only.** Feed rendering is the artefact; the full-size view hides the failures that matter (R1, S3, S4).
- **Assuming last year's safe zones.** Platform UI changes; verify current overlay geometry before each campaign rather than trusting remembered values.
- **One template, silently mutated.** Hand-duplicated files drift; diff the set before publishing (T1).
- **Three messages per asset.** "Save the date + lineup + tickets + sponsor logos" is a flyer pasted into a feed; choose the one message for the canvas.
- **Tiny text as decoration.** If it cannot meet the feed-size floor, it belongs in the caption, not the canvas.
- **Testing QR/links from the design file only.** Verify the published asset's destination too (B4) — link-shortener swaps and re-uploads break destinations.
- **Ignoring the grid context.** Assets judged one-by-one can clash when shelved together in the profile grid (T4).

## 9. Evaluation checklist

- [ ] Placement list defined; every asset checked against its platform spec (S1) and exported at 2× (S2).
- [ ] Safe zones verified against current platform guidance; overlay bands clear (S3).
- [ ] Centre crops survive grid/profile previews (S4); slide 1 of carousels stands alone (S5).
- [ ] Feed-size simulation passed: headline readable at thumbnail, no text below floor (R1–R2).
- [ ] All text pairs contrast-measured; compression check done (R3–R4).
- [ ] Set-level diff: template elements identical, variation rhythmic, labels coherent (T1–T3).
- [ ] Grid context reviewed (T4).
- [ ] Logo, palette and type per kit (L1–L4); profile assets legible at avatar size (L5).
- [ ] One message, one CTA per asset; destinations verified (B1–B4).
- [ ] Template fixed before per-asset patching; set pass re-run after regeneration.

## 10. Related topics

- [design-quality-framework.md](design-quality-framework.md) — master method, severity model and report template.
- [brand-identity-checklist.md](brand-identity-checklist.md) — kit rules referenced by section 5.4.
- [poster-checklist.md](poster-checklist.md) — sibling glance-based format; shared hierarchy logic.
- [../foundations/principles-of-design.md](../foundations/principles-of-design.md) — hierarchy and emphasis theory.
- [../foundations/design-critique.md](../foundations/design-critique.md) — critique stance for fast-view artefacts.
- [../accessibility/wcag-fundamentals.md](../accessibility/wcag-fundamentals.md) — contrast measurement method.

## 11. References

This checklist is a synthesis of the library's theory files and standard social-media production practice; platform-specific numbers are marked conventional because they change frequently.

- Meta/Facebook and Instagram creator documentation on asset specifications and safe zones — professional convention for dimension/overlay checks (values drift; verify current specs). [canonical]
- W3C, "Web Content Accessibility Guidelines (WCAG) 2.1" — contrast thresholds applied in section 5.2. [canonical]
- W3C Web Accessibility Initiative, "Understanding Success Criterion 1.4.10: Reflow", https://www.w3.org/WAI/WCAG21/Understanding/reflow.html — referenced only for the general principle of testing at constrained sizes. [search-verified, accessed 2026-11-23]
