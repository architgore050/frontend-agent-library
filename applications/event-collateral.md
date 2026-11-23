# Event collateral

## 1. What is it?

Event collateral is the family of physical (and screen) graphics that carry an event's identity through the venue: banners and stage backdrops, wayfinding signage, attendee badges, merchandise, sponsor boards and award announcements. What distinguishes it from every other application domain is that **viewing distance is a design input with real units** — a badge is read at 1 m, directional signage at 5–30 m, a stage backdrop at 20 m and photographed at 5 m — and each artefact must be sized, weighted and resolved for its own distance. The craft is producing one identity across a dozen formats without letting any single artefact fail at its job.

## 2. Why does it matter?

Collateral is where the brand becomes physical and where production mistakes cost real money: a banner printed without bleed, signage sized for the wrong distance, or a badge nobody can read across a registration desk cannot be fixed on the day. Events are also the classic scenario for extending a fixed logo into a full kit — the mission case this library is built around — and the collateral family exercises every core skill at once: hierarchy under distance constraints, palette on uncoated and fabric substrates, grid discipline at metre scale, and sponsor governance. See the identity foundations in [Visual identity](../branding/visual-identity.md) and the structure in [Brand architecture](../branding/brand-architecture.md).

## 3. Core principles

- **Size for the farthest legitimate viewer.** Every artefact has a design distance: badge 1 m, poster 2–4 m, directional sign 5–30 m, stage backdrop 20 m+. Typography and resolution decisions start there, using the letter-height rule in §4.2.
- **One identity, many substrates.** Fabric, vinyl, paper, lanyards and LED screens each shift colour and legibility; the identity needs substrate-aware variants, not a single exported file reused everywhere.
- **Attendee function first.** Wayfinding exists to answer "where do I go next?"; badges to answer "who is this?"; sponsorship boards to honour commitments without hijacking the event's own message.
- **Sponsors are governed, not improvised.** Tier order, sizes and placement follow contractual rules expressed in a matrix; equal treatment within a tier is both fair and legally safer.
- **Produce from a spec sheet.** Every artefact ships with final size, resolution, bleed, material and finishing notes; a design without a production spec is not finished.

## 4. How it works

### 4.1 The collateral family and its design distances

| Artefact | Typical formats | Design distance | Primary job |
|---|---|---|---|
| Badge | 4 × 3 in (102 × 76 mm), 4 × 6 in, 2.25 × 3.5 in | 1 m | Identify the person |
| Directional signage | A2–A1 boards, hanging signs | 5–30 m | Answer "where next?" |
| Roll-up banner | ≈ 850 × 2000 mm (33 × 79 in) | 3–10 m | Brand presence + one message |
| Stage backdrop | Full stage width (e.g. 4–8 m wide) | 20 m+, photographed at 5 m | Brand the room and the photos |
| Sponsor board | Wall or free-standing panels | 3–15 m | Honour sponsor tiers |
| Merchandise | T-shirts, tote bags, stickers | 0.5–5 m | Identity carried away |
| Award announcements | Slides, printed cards, certificates | varies | Name the winners |

Badge sizes are the trade-standard figures ([search-verified] ConferenceBadge and pcnametag size guides: 2.25 × 3.5 in business-card style and 3 × 4 in / 4 × 3 in conference badges are the most common, with 4 × 6 in for badges carrying agendas and QR codes). Roll-up and stage dimensions are conventional trade sizes — confirm the exact frame with the vendor.

### 4.2 Typography at distance: the letter-height rule

The working rule for signage, verified this cycle: **about 1 inch (25 mm) of capital letter height per 10 feet (3 m) of viewing distance** gives the *maximum* readable distance for normal vision in good conditions — and comfortable reading happens 30–50% closer, so designs for moving or glancing viewers must add 30–50% ([accessed] Pannier Graphics letter-height chart). Key rows from that chart:

| Capital height | Max readable | Comfortable |
|---|---|---|
| 25 mm (1 in) | 3 m / 10 ft | 1.5–2 m |
| 50 mm (2 in) | 6 m / 20 ft | 3–4 m |
| 75 mm (3 in) | 9 m / 30 ft | 4.5–6 m |
| 150 mm (6 in) | 18 m / 60 ft | 9–12 m |
| 300 mm (12 in) | 36 m / 120 ft | 18–24 m |

Modifiers that change the real numbers: **typeface** (plain sans serifs with open letterforms win; condensed, thin and decorative faces lose legibility fastest), **contrast** (weak contrast can compress readable distance substantially — Pannier notes it can fall by half), **lighting and glare** (glossy laminates wash out under venue lights), **viewing angle** (legibility drops as the approach angle moves off head-on), and **viewer state** (moving, older or stressed audiences need the comfortable figure, not the maximum). Context bands from the same source: interpretive panels are read at ~1–2 m, pedestrian wayfinding typically needs 50–100 mm (2–4 in) primary text, safety signage errs larger and follows regulated standards.

For the day: compute each sign's required height as `distance ÷ 10` (in consistent units), then increase 30–50% if viewers are moving, and more if contrast, lighting or angle is compromised.

### 4.3 Banners and stage backdrops

**Roll-up and hanging banners.** One message, governed logo size, contact or QR at reading-adjacent scale. Production notes: keep the bottom 100–150 mm of a roll-up banner free of critical content (the panel curls and sits in the cassette's shadow) — a conventional vendor practice; state bleed per vendor (large-format fabric and vinyl commonly ask for 20–50 mm rather than the print-sheet 3 mm, because edges are hemmed, folded or welded — always confirm).

**Stage backdrops.** Two audiences: the room (20 m+) and the camera (5 m, in every photo). Rules:

- Few words: the event name and primary partners only. A backdrop is not a poster; body text is invisible at distance and unphotographable.
- The logo or lockup is placed for the camera's centre crop — usually centred or slightly above centre, at a size that survives both a wide shot and a speaker-medium shot.
- **Step-and-repeat variants** (media walls) repeat the sponsor lockup pattern at equal size within tier, with spacing that lets each mark read in photos; lockup construction rules come from [Brand architecture](../branding/brand-architecture.md).
- Resolution: at 20 m viewing, print resolution of 30–100 PPI at full size is acceptable (see §4.7), but **photograph-adjacent zones** (the centre where press shots crop) should be supplied at the higher end.
- **LED screen backdrops** are not print: design in the panel's native pixel dimensions (a 4 × 2.25 m wall at 4 mm pixel pitch is 1000 × 562 px), use RGB, and expect the screen operator to map content. Never send a print file to an LED vendor as-is.

**Flags and outdoor hardware.** Feather/teardrop flags and street banners read in motion at distance, so they carry only the logo or event mark at maximum scale — no body copy, ever. Wind-curved surfaces distort fine detail; the mark needs a simplified one-colour version ([Logo systems](../branding/logo-systems.md)). Pole pockets and wind slits consume edges exactly like hems do — same live-area discipline as §4.7. Outdoor durability adds UV-stable inks and heavier substrate to the vendor checklist in §5.2.

### 4.4 Badges

The badge is the highest-frequency read at the event — everyone scans hundreds of them. Hierarchy per professional convention:

1. **First name, prominently; full name large.** The name is the content. As a conventional starting point, first names run 18–30 pt on a 4 × 3 in badge (≈ 6–10 mm cap height, comfortable at 1 m per the §4.2 table).
2. **Affiliation** (organisation/team) second, ~40–60% of name size.
3. **Role/attendee type** third — often as a colour-coded stripe or ribbon rather than text alone; colour coding must be duplicated in text for colour-blind safety ([Colour accessibility](../colour/colour-accessibility.md)).
4. **Functional extras** below: QR for check-in/sessions, agenda strip (on 4 × 6 in badges), meal/house marks.

Practical rules: orientation landscape for 4 × 3; name centred in the upper half so a lanyard clip never covers it; both sides printed (front identity, back agenda/QR) when using 4 × 6 in; type for names never below ~16 pt. Badges double as access control, so badge colour = role mapping belongs in the template system, not decided ad hoc per print batch.

### 4.5 Directional graphics and wayfinding basics

Wayfinding is a system, not a set of signs. Fundamentals from the canon (Arthur & Passini's *Wayfinding* and Kevin Lynch's *The Image of the City* — [canonical]):

- **Sign at every decision point** (junctions, doorways, stairs, split corridors), and nowhere the user never chooses anything. Signage without decisions is clutter.
- **Consistent grammar:** one typeface, one arrow style, one colour code per destination class (e.g. halls, workshops, facilities) applied identically on every sign.
- **Content order:** destination name > direction (arrow) > distance/floor detail. Arrows point in plan view (the direction one will walk), not in perspective.
- **Sizing by the §4.2 rule** with the comfortable-distance adjustment — corridor signs read by people walking need the larger figures.
- **Progressive disclosure:** a directory sign at entry lists all destinations; corridor signs repeat only the reachable ones.
- Accessibility is a code matter: tactile lettering, mounting heights and contrast for permanent rooms follow the local standard (ADA in the US, equivalent national codes elsewhere) — check the code, do not guess.

### 4.6 Sponsor boards, awards and winner announcements

**Sponsor boards.** The tier matrix is the design contract: top tier largest and best-placed (centre band, top band, or lead position on step-and-repeats); lower tiers smaller, flanking or lower; **within a tier, identical size and treatment, ordered alphabetically** unless the contract specifies otherwise. Mark sizes should be specified relative to the board (e.g. top tier 60% of board height band, second tier 45%) rather than eyeballed per sponsor. Never let a lower-tier sponsor's mark out-size a higher tier's — this is the most common sponsor dispute at events, and the fix is a written matrix approved before artwork. Lockup and co-branding rules come from [Brand architecture](../branding/brand-architecture.md) and minimum-size/clear-space rules from [Logo systems](../branding/logo-systems.md).

**Awards and winner announcements.** Clarity of rank and person: category name > winner name (largest, centre) > runners-up (ordered) > sponsor/organiser footer. On slides and screens, one category per frame — never a four-column table of winners nobody can read. The printed pairing (certificate for the winner) follows [Certificates and documents](certificates-and-documents.md), with the winner's name again the apex element.

### 4.7 Production specs for large format

Large-format resolution drops with viewing distance — this is the inverse of the 300-PPI close-view print rule:

| Viewing distance | Conventional effective resolution |
|---|---|
| ≤ 1 m (badges, close posters) | 300 PPI |
| 1–3 m (posters, pop-ups) | 150–300 PPI |
| 3–10 m (banners, boards) | 100–150 PPI |
| 10 m+ (stage, hoardings) | 30–100 PPI |

([search-verified] SpeedPro: 300 DPI close-up standard, 150–200 DPI at 3–5 ft; 4over4: 100–150 DPI for distance-viewed banners; Forest Printing: 150–300 DPI up close down to 15–25 DPI for billboards.) Two production notes: files are still designed at *final physical size* — a 6 m banner at 72 PPI is a 17,000-px-wide canvas, and many RIP workflows prefer scaled-down files with a stated scale factor (e.g. 1:10 at 720 PPI) — check the vendor's pipeline. And **bleed on fabric/vinyl is vendor-specific**: hems, pockets, welds and grommets consume 20–100 mm per edge, so reserve a clear "live area" inside all finishing zones and get the exact figure from the vendor before designing.

### 4.8 Merchandise

Merchandise carries the identity off-site, so it is branding as much as apparel — and it is printed by processes with hard constraints:

| Process | Best for | Artwork requirement |
|---|---|---|
| Screen printing | T-shirts, totes, 1–4 spot colours | Vector art, colours separated to spot inks; halftones need separation skill |
| DTG / direct-to-garment | Full-colour, small runs | Raster 300 PPI at print size, RGB fine, transparent background |
| Embroidery | Caps, polos, premium items | Vector simplified: thin strokes and small text must thicken; minimum letter height ~5 mm (conventional) |
| Heat transfer / vinyl | Names, numbers, one-offs | Vector, weeded cut paths |
| Stickers/labels | Everything | Vector or 300 PPI raster + die-line |

Rules that hold across all processes:

- **Design to the print area.** Each item has a maximum decoration zone (a standard adult-front print area is roughly 30 × 40 cm — conventional; confirm per blank/item). The logo lives inside it with clear space, per [Logo systems](../branding/logo-systems.md).
- **Substrate changes colour.** Ink on heather grey, navy canvas or tech fabric shifts against the palette; request a physical sample for the exact blanks before approving a run, and keep a one-colour knockout logo version for dark grounds.
- **One logo, one colour, bigger.** Merchandise rewards the reduced mark: a single-colour logo at confident scale beats a four-colour lockup shrunk to fit; taglines set at 8 mm disappear on a chest.
- **Tier the items.** Speaker/volunteer items may differ from attendee items via colour of the item or one accent element — the same tier logic as badges, never a different logo.
- **Sponsor marks on merchandise are contractual** — placement and size come from the sponsor matrix (§4.6), and unpaid logos do not appear on paid merch.

## 5. Practical application

### 5.1 Build the kit from one system

1. **Extract the system** from the identity: palette roles, type scale, grid, logo clear space ([Visual identity](../branding/visual-identity.md), [Palette development](../colour/palette-development.md), [Typographic hierarchy](../typography/typographic-hierarchy.md)).
2. **Map artefacts to distances** using §4.1's table; set type sizes from the §4.2 rule per artefact.
3. **Build templates**, not one-offs: badge set, sign set, banner set, sponsor board matrix, award slide set — each with locked zones and variable slots, mirroring the template logic in [Social media graphics](social-media.md).
4. **Write the production spec per artefact**: final size, scaled-file convention, resolution, bleed/hem allowances, material, finishing (laminate, grommets, eyelets), and the vendor's file requirements.
5. **Proof physically**: print one badge at real size, view one sign at its design distance before approving the run; check the palette on the actual substrate (fabric and uncoated board shift colour).

### 5.2 Vendor checklist (per order)

- Final dimensions incl. bleed and hem/pocket allowances; orientation; single- or double-sided.
- Material and finishing (matte laminate for under-lights signage — glossy glare kills legibility per §4.2).
- Resolution rule the vendor's RIP expects (PPI at full size, or scale factor).
- Colour: RGB vs CMYK pipeline; critical brand colours proofed on the actual material.
- Turnaround, install method (hanging points, pole pockets, cable ties) and spares.

### 5.3 Production timeline

Collateral fails most often on logistics, so run the artefacts against an event countdown (conventional lead times — confirm with local vendors):

| Before event | Action |
|---|---|
| 8–12 weeks | Sponsor matrix agreed; merchandise blanks and quantities confirmed; embroidery/screen orders placed |
| 4–8 weeks | Badge data pipeline ready; large-format banners and backdrops ordered; signage audit of the venue done on-site |
| 2–4 weeks | Signage and badges printed; certificates merged and proofed; wayfinding installed plan agreed with venue |
| 1 week | Physical proofs at real size/distance; install kit packed (fixings, spares, tools); contingency reprints identified |
| On the day | Registration spare badges; gaffer-tape-grade fixes documented; LED content handed to operator in native pixels |

The pattern: long-lead items (embroidery, foils, big-format runs) start first because they cannot be rushed; everything visual is frozen before print because reprints at week one cost multiples.

### 5.4 On-site installation checks

Design assumptions meet physical reality on install day, so schedule a venue walkthrough with the checklist:

- **Sightline verification:** stand where the audience will stand. A hanging sign perfectly sized for the corridor may sit opposite a pillar that blocks the approach angle — the §4.2 angle modifier applied to reality.
- **Mounting heights and alignment:** consistent baseline heights across a sign family (venue codes govern minimums; consistency governs everything else), and measure twice on hanging hardware — signs hung on different lengths read as an accident.
- **Lighting check at night:** walk the route after dark (or with the venue's actual lighting state); glare and under-lit signage invalidate the daytime sizing.
- **Photo test on the backdrop:** take the actual press-photo angles — medium shot, wide shot, selfie distance — and confirm the lockup crops well in all of them.
- **Spares and fixings:** one spare badge set, spare fixings for every hanging sign, and the one person who knows where the contingency reprints live.

## 6. Decision framework

- **Which artefact carries the one message?** Choose one hero surface per venue (usually the stage backdrop or a large banner) and let the rest support rather than repeat verbatim; five surfaces shouting the same sentence flattens the identity.
- **Badge size:** 4 × 3 in (102 × 76 mm) for identity-only badges; 4 × 6 in when agendas/QR/meal data must live on the badge; 2.25 × 3.5 in for simple name-only roles ([search-verified] trade sizes).
- **Print or LED backdrop?** Permanent photo branding on a budget → printed backdrop. Dynamic content, dark room, video idents → LED, designed in native pixels.
- **Merchandise process?** Fewer colours, bigger runs → screen printing. Full-colour small runs → DTG. Premium/perishable items (caps, polos) → embroidery with a simplified mark (§4.8 table).
- **Sign density:** sign every decision point; resist decorating non-decision corridors — the grammar stays trustworthy only if signs reliably mean choices.
- **Sponsor inclusion level:** governed by contract tier, expressed in the matrix; if a sponsor's tier is unknown, escalate before artwork, never estimate.

## 7. Examples

### 7.1 Badge template spec (4 × 3 in landscape)

```text
Canvas:     4 × 3 in (102 × 76 mm) + 2 mm bleed, landscape
Zone 1:     Event logo strip top-left, 8 mm high; attendee type ribbon top-right
Zone 2:     FIRST NAME 26 pt bold / full name 22 pt, centred upper half
Zone 3:     Affiliation 14 pt; role 12 pt on colour stripe (colour + text)
Zone 4:     QR 20 mm bottom-right + attendee ID; back side: agenda grid 10 pt
Colour:     Role stripe per palette; both sides; lanyard colour = attendee type
```

### 7.2 Wayfinding sign spec (corridor, 10 m design distance)

Capital height = 10 m ÷ 10 = 1 m → comfortable-distance adjustment +30–50% → use 130–150 mm capitals for primary destinations, 60–75 mm for secondary lines. Plain sans serif, mixed case, matte laminate, high-contrast ink on light ground, arrow at 1.5× capital height, colour band per destination class with the class name spelled out. Mount at the code-compliant height, consistent position across the venue.

### 7.3 Sponsor board tier matrix (wall panel, 4 × 2.5 m)

| Tier | Band on board | Mark height | Order |
|---|---|---|---|
| Platinum (2) | Upper third | 300 mm | Centre-weighted, equal size |
| Gold (6) | Middle band | 180 mm | Alphabetical, equal size |
| Silver (12) | Lower band | 120 mm | Alphabetical, equal size |
| Supporter (n) | Footer strip | 60 mm | Alphabetical, equal size |

Approved by sponsorship lead before artwork; any change re-opens the matrix, not the board.

### 7.4 Attendee tote print spec

Process: 1-colour screen print on natural canvas. Artwork: knockout event mark at 250 mm width, centred in the ~30 × 40 cm print area, single palette colour mixed to the Pantone reference. No taglines, no URLs — a tote is read at 2–5 m and carried for months, so the reduced mark does all the work. Sponsor marks absent by default; if contracted, they enter at 40% of the event mark's height on the reverse face, per the sponsor matrix. Sample printed on the exact blank before the run — canvas tone shifts ink colour more than any other common substrate.

## 8. Common mistakes

- **Sizing signage by feel.** 40 mm capitals expected to read at 15 m. Correction: the distance ÷ 10 rule plus the comfortable-distance uplift (§4.2).
- **Stage backdrops with paragraphs.** Body text invisible at 20 m and unreadable in photos. Correction: name, primary partners, nothing else.
- **Badges with small names.** 12 pt names nobody can scan across a desk. Correction: name as the apex element (§4.4).
- **300-PPI thinking at stage scale.** Multi-gigabyte files the RIP rejects. Correction: the viewing-distance resolution table (§4.7) and the vendor's scale convention.
- **Missing hem/grommet allowances on fabric and vinyl.** Logos half-swallowed by hems. Correction: reserve live area inside finishing zones; confirm vendor bleed before design.
- **Sponsor tier chaos.** A silver mark bigger than a platinum one. Correction: the tier matrix, approved before artwork (§4.6).
- **Colour-only role coding.** Ribbon colours indistinguishable to colour-blind attendees. Correction: colour + text on every coded element.
- **Glossy laminate under venue lights.** Glare erases the sign at its own design distance. Correction: matte finishes for under-lights signage.
- **LED walls fed print files.** Wrong pixel mapping, stretched logos. Correction: design in native panel pixels, RGB.
- **Wayfinding decoration.** Signs where no decision exists, no sign where decisions happen. Correction: the decision-point audit (§4.5).
- **Merchandise with the full lockup shrunk to fit.** Four-colour marks at 40 mm on a chest; taglines at 8 mm. Correction: the reduced one-colour mark at confident scale (§4.8).
- **Skipping the venue walkthrough.** Signage sized for the corridor but installed opposite a pillar, or perfect in daylight and invisible after dark. Correction: the on-site checks in §5.4.
- **Long-lead items ordered late.** Embroidery and foil work quoted for the week before the event. Correction: the production timeline in §5.3 — long-lead first.

## 9. Evaluation checklist

- [ ] Every artefact has a stated design distance and its type meets the distance ÷ 10 rule with the appropriate uplift.
- [ ] Badge names are the apex element and legible at 1 m; role coding is colour + text.
- [ ] Stage backdrop carries only event name and primary partners; centre crop survives medium-shot photography.
- [ ] Large-format files match the vendor's resolution convention and include correct bleed/hem allowances with a reserved live area.
- [ ] Sponsor board follows the approved tier matrix: tiers distinct, equal treatment within tier, alphabetical order.
- [ ] Wayfinding signs sit at decision points only, use one grammar, and code destinations by colour + name.
- [ ] Award announcements state category, winner (largest), runners-up in order — one category per frame.
- [ ] The palette has been proofed on the actual substrates (fabric, board, lanyard).
- [ ] Each artefact ships with a written production spec and passed a physical proof at real size/distance.
- [ ] Merchandise artwork respects the print area, uses the reduced mark, and was sampled on the actual blank (§4.8).
- [ ] On-site checks completed: sightlines, mounting alignment, night-lighting, photo-angle test (§5.4).
- [ ] Poster and screen items re-run the shared checks in [Poster checklist](../evaluation/poster-checklist.md).

## 10. Related topics

- [Posters](posters.md) — bleed, safe-area and 300-PPI mechanics reused for close-view collateral.
- [Certificates and documents](certificates-and-documents.md) — award certificates paired with announcements.
- [Social media graphics](social-media.md) — the digital siblings of banners and award slides.
- [Visual identity](../branding/visual-identity.md) — the source system all templates extract from.
- [Brand architecture](../branding/brand-architecture.md) — sponsor lockups, co-branding and step-and-repeat governance.
- [Logo systems](../branding/logo-systems.md) — clear space and minimum sizes at metre scale.
- [Typographic hierarchy](../typography/typographic-hierarchy.md) and [Typeface selection](../typography/typeface-selection.md) — distance-safe type systems.
- [Colour accessibility](../colour/colour-accessibility.md) — contrast and colour-independence on substrates.
- [Grid systems](../layout/grid-systems.md) — structure for boards and backdrop templates.
- [Poster checklist](../evaluation/poster-checklist.md) — shared print evaluation sheet.

## 11. References

- Pannier Graphics, "Letter Height Visibility Chart" — 1 in per 10 ft maximum-readable rule, comfortable-distance table, typeface/contrast/lighting/angle modifiers, context bands. https://www.panniergraphics.com/blog/letter-height-visibility-chart-for-outdoor-sign-readability [accessed 2026-11-23]
- SpeedPro, "What Resolution is Best for Large Format?" — DPI bands by viewing distance. https://www.speedpro.com/mesa-gilbert/what-resolution-is-best-for-large-format [search-verified 2026-11-23]
- 4over4, "300 DPI Rule and DPI for Large Format Printing". https://www.4over4.com/guide/print-resolution-explained-dpi-settings-for-quality [search-verified 2026-11-23]
- Forest Printing, "DPI vs Viewing Distance: The Complete Guide". https://www.forest-printing.com/guides/dpi-viewing-distance [search-verified 2026-11-23]
- ConferenceBadge, "Event Badge Sizes" — common badge dimensions incl. 2.25 × 3.5 in and 3 × 4 in. https://www.conferencebadge.com/blog/event-badge-sizes [search-verified 2026-11-23]
- pcnametag, "Affordable Full-Color Event Badges" — standard badge size range incl. 4 × 3 in and 4.25 × 6 in. https://www.pcnametag.com/custom-name-tags-event-badges/standard-event-badges.html [search-verified 2026-11-23]
- ConnectMachine, "Name Badge Size: Standard Dimensions" — 4 × 3 in (102 × 76 mm) as the most common conference badge. https://www.connectmachine.ai/blog/name-badge-size [search-verified 2026-11-23]
- Paul Arthur & Romedi Passini, *Wayfinding: People, Signs, and Architecture* — decision-point signage system fundamentals. [canonical]
- Kevin Lynch, *The Image of the City* — legibility of environments. [canonical]
- Roll-up and stage dimensions, hem/grommet allowances, badge type sizes and the tier-matrix percentages in §4.6/§7 are conventional trade starting points, labelled as such in the text; confirm exact values with your vendor and contract.
