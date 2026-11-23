# Marketing assets

## 1. What is it?

Marketing assets are graphics built to *persuade and convert*: campaign key visuals, email banners, landing-page hero sections, promotional announcements and calls to action. They differ from the other applications in this domain by having a measurable goal — a click, a registration, a sale — and therefore by being judged on action taken, not only on aesthetics. The craft is funnel thinking rendered visually: each placement (email, feed, landing page) shows one consistent campaign message with one dominant action, adapted to that channel's mechanics (email clients strip and block; landing pages scroll; feeds crop).

## 2. Why does it matter?

Marketing is where design meets its strictest evaluation: a hero that does not convert is a failure regardless of its beauty. The failure modes are predictable and expensive — image-only emails that read as blank rectangles when clients block images, heroes with five competing buttons, campaign placements that look like five different brands. Because every placement is a touchpoint of the same campaign, the discipline here is *consistency under adaptation*: one key visual, many governed crops, one primary action everywhere. For events and product launches this is the final funnel stage that turns the identity built in [Visual identity](../branding/visual-identity.md) into sign-ups.

## 3. Core principles

- **One primary CTA per view.** Every screen, email or panel has exactly one visually dominant action; secondary actions (if any) are typographically demoted (text links, ghost buttons).
- **The image supports the message; the text carries the facts.** Critical information (dates, prices, the offer) must exist as real text wherever the channel allows, because images get blocked, cropped or skimmed past.
- **Consistent campaign surface.** One key visual, palette and headline voice across all placements; placement-specific crops, not redesigns. The system logic mirrors the template sets in [Social media graphics](social-media.md).
- **Anatomy before decoration.** Hero sections and email banners have a fixed job sequence — hook, value proposition, action, reassurance — and each element earns its zone.
- **Design for the channel's failure modes.** Email: image blocking, narrow panes. Landing pages: small screens, scrolling impatience. Feeds: cropping. The asset that ignores the failure mode fails silently.
- **Speed is part of the design.** Hero images and banners load before the message lands; an asset that costs seconds loses the conversion it was designed to win. Weight budgets (§4.2) and responsive image sizing (§4.3) are design constraints, not technical afterthoughts.
- **Truth in the offer.** Deadlines, prices and "free" claims are visual content too — the design must not dress up an offer the campaign cannot honour, or the follow-through (confirmation, ticket, delivery) breaks the trust the asset built.

## 4. How it works

### 4.1 Campaign graphics: the key-visual system

A campaign starts with one **key visual** — the hero composition (image treatment, headline style, colour mood, logo placement) — and a set of adaptations:

| Placement | Adaptation rule |
|---|---|
| Feed / social | Re-crop to each platform ratio from the template set ([Social media graphics](social-media.md) §4.1) |
| Email header | Simplify: fewer elements, text-heavy, ≤ 600 px wide canvas (§4.2) |
| Landing hero | Rebuild natively in HTML/CSS, not as one flattened image (§4.3) |
| Print/banner | Follow print mechanics ([Posters](posters.md), [Event collateral](event-collateral.md)) |

Consistency levers, in order of importance: the colour mood (exact palette roles from [Palette development](../colour/palette-development.md)), the headline's type treatment (face, weight, case), the logo lockup and its clear space ([Logo systems](../branding/logo-systems.md)), and the CTA's visual formula (shape, colour, label voice). If those four survive adaptation, placements feel like one campaign even when crops differ.

### 4.2 Email banners

Email is the most constrained channel: rendering varies by client, images are frequently blocked by default, and layouts are built with tables and fixed widths. Verified conventions:

- **Width: 600 px is the long-standing standard content width** for email templates and banners — it renders safely across major desktop and webmail clients ([search-verified] beehiiv: "keep your email template width as close to 600 px as possible"; template.net lists 600 px width and a 600 × 300 px full-banner image as the compatible standard). Treat 600–640 px as the working band; above that, panes crop or force horizontal scrolling.
- **Header/banner image heights** commonly run 100–300 px tall on the 600 px canvas; a 600 × 300 px hero or 600 × 150–200 px slim header are conventional slots ([search-verified] template.net full-banner figure).
- **Image-to-text balance:** never bake essential facts (date, price, offer, CTA) into an image alone — blocked images leave a blank box. Put the CTA as an HTML button or text link in addition; supply alt text on every image; live text inherits and survives.
- **Retina sharpness:** export banner images at 2× (1200 px wide) and constrain display to 600 px so they stay crisp on high-DPI screens; keep file weight low (a banner should be tens of KB, not MBs — a conventional rule of thumb) so the email loads on mobile data.
- **Above the fold:** the banner + first line of text + primary CTA must appear without scrolling in typical preview panes; the preview text is part of the design system.
- **Dark mode and rendering variance:** dark-mode clients invert backgrounds and sometimes recolour logos — supply logo versions that survive both modes (knockout variants per [Logo systems](../branding/logo-systems.md)), and test the four rough rendering families (Apple Mail, Gmail web, Outlook desktop, mobile clients) before a major send. Outlook's desktop engine is the traditional worst case: expect it to break margins, background images and custom fonts, and design so the message still works when it does.
- **Subject line and preheader are designed surfaces,** not leftovers: they are what the inbox shows before any banner loads, so they carry the hook while the imagery carries the mood.

### 4.3 Landing-page hero design

The hero is the first viewport of a landing page; its job sequence is fixed:

1. **Headline** — the value proposition in one line (what you get, for whom).
2. **Subheadline** — one sentence of specificity (when, where, for whom exactly).
3. **Primary CTA** — one button, verb-first label ("Register free", "Start trial"), high-contrast against the background.
4. **Supporting visual** — product shot, event imagery, or a graphic that makes the promise concrete.
5. **Reassurance strip** — dates, location, trust marks, "no credit card" style friction-killers — small, below the action.

The page is built natively (HTML/CSS), not as a flattened image: text must be selectable, responsive and fast; typography follows [Web typography](../typography/web-typography.md) and the layout system the page inherits is defined in the UI/UX domain (see [UI/UX domain](../ui-ux/)). Responsive behaviour is non-negotiable: the hero must stack cleanly on a phone (headline → CTA → visual), which also matches how most traffic arrives. Buttons follow colour-contrast rules ([Colour accessibility](../colour/colour-accessibility.md)) and remain large enough to tap (conventional minimum touch target ≈ 44–48 px).

### 4.4 Promotional announcements

Announcements (launches, early-bird deadlines, "last seats", results) are time-pressured versions of the campaign system. Patterns that work:

- **Countdown and deadline framing:** the date is the hero element, sized like a headline; everything else is subordinate. Mirrors the countdown template in [Social media graphics](social-media.md) §4.4.
- **Offer-first vs benefit-first:** choose per campaign; do not mix both at equal weight — one idea per view, as everywhere in this domain.
- **Urgency without dark patterns:** state real deadlines; fake countdowns damage trust and, in many jurisdictions, consumer-protection rules.
- Each announcement reuses the campaign key visual's colour mood and CTA formula so the audience recognises the campaign instantly.

### 4.5 Calls to action: visual treatment

- **One per view, visually dominant.** Dominance comes from contrast and isolation: a solid fill in the accent role, surrounded by whitespace, nothing else competing at that weight.
- **Verb-first microcopy.** "Register", "Get the guide", "Join the waitlist" — the label names the action, not the interface ("Submit", "Click here" waste the slot).
- **Secondary actions demoted.** A text link or ghost (outline) button, visibly lighter; if two actions must coexist, the primary keeps solid fill + accent colour, the secondary gets neutral styling.
- **Consistency compounds.** The same button shape, colour and label voice across email, landing page and feed teaches the audience what to look for; changing the accent per placement resets the learning.
- **Placement economics:** the primary CTA appears in the hero/first viewport, and repeats after long content blocks — repetition of the *same* CTA, never new variants.

### 4.6 Measuring and iterating on the visuals

Marketing is the one application where the design can be scored:

- **Change one variable per test.** If two variants differ in headline *and* CTA colour *and* image, the result explains nothing. A/B discipline: one element (CTA label, hero image, subject-line banner) per test, everything else held.
- **What visual work actually moves:** clarity of the offer (a number, a date, a specific benefit) and CTA dominance are the levers that reliably respond; micro-styling (button radius, font swap) rarely does. Spend design iteration on hierarchy, not on ornament.
- **Visual consistency has a measurable cost when broken:** if a channel's click-through collapses on a placement that looks nothing like the campaign, suspect the break in the four consistency levers (§4.1) before the offer.
- **Attribution basics:** tagged links per placement (the UTM discipline named in the asset manifest, §5) let the design team know which placement worked — design iteration without placement data optimises blind.
- Kill or refresh: an announcement graphic that has run for weeks in a feed decays (audience fatigue); the template system exists precisely so a refresh re-crops the key visual instead of redesigning it.

## 5. Practical application

A campaign asset workflow:

1. **Write the message hierarchy first:** the offer, the audience, the one action, the deadline. No visual work until this fits in three lines.
2. **Design the key visual** on the largest canvas (landing hero or poster scale), locking the four consistency levers (§4.1).
3. **Adapt per placement** using each channel's spec table (email 600 px; feed ratios; print mechanics), re-cropping rather than redesigning.
4. **Test the failure modes:** email with images blocked (does the message survive?), the hero at 375 px width (does it stack cleanly?), feed crops at thumbnail scale.
5. **Ship with an asset manifest:** file names, dimensions, alt text, UTM-tagged links per placement, so performance can be attributed and reuse is easy.

## 6. Decision framework

- **Image-led or text-led?** Image-led where the product/event is visually seductive (photography-led campaigns); text-led where the promise is abstract or the channel blocks images (email, B2B).
- **Email banner or full HTML hero block?** Slim image banner (600 × 150–200 px) for regular newsletters where text must dominate; 600 × 300 px visual hero for major announcements — always with a text CTA beside or beneath.
- **One CTA or two?** Default one. Add a secondary only when two audiences genuinely share the page (e.g. "Register" + "View programme"), keeping the primary visually dominant.
- **Which consistency lever may flex?** Crops may flex per placement; palette, type treatment and CTA formula may not. If a placement seems to require breaking a lever, it is a different campaign — escalate, do not improvise.

## 7. Examples

### 7.1 Event promo email banner spec

```text
Canvas:      1200 × 400 px exported, displayed at 600 × 200 px (retina 2×)
Content:     Event lockup left third; "Early-bird ends 30 June" headline 32 px (16 pt-equiv)
             date block as live text beneath; right: 180 × 44 px accent button "Register free"
Below image: HTML text CTA repeated as a link + one-line offer detail (image-block safety)
Files:       JPEG q85 (~40 KB) + alt text "Early-bird registration for Design Days 2027"
```

### 7.2 Landing hero structure (native HTML/CSS)

```html
<section class="hero">
  <h1>Design Days 2027 — two days, forty speakers</h1>
  <p>Early-bird pricing ends 30 June. Amsterdam, 14–15 March.</p>
  <a class="cta-primary" href="/register?utm_source=hero">Register free</a>
  <p class="reassure">No payment until February · Full refund until 1 Feb</p>
</section>
```

The section stacks to a single column at mobile widths, the button exceeds a 44 px touch target, and the headline/CTA contrast passes the accessibility checks referenced in §4.3.

### 7.3 Countdown announcement (feed + email pair)

Same campaign, deadline-first variant: the feed graphic (1080 × 1350 from the social template set) sets "Ends Friday" as the hero element with the offer one line beneath; the email variant re-uses the §7.1 banner geometry with the headline swapped to the deadline and the CTA label kept identical ("Register free"). Only the hero text and hero emphasis change — palette, lockup, button formula and type treatment hold, which is what makes the pair read as one campaign at two touchpoints. Timing pattern: T-7 days (announcement), T-2 days (reminder), T-0 morning (last call), each re-cropped from the same key visual rather than redesigned.

## 8. Common mistakes

- **Image-only emails.** Blocked images leave a blank shell; the campaign never fires. Correction: live-text CTA and facts in addition to imagery (§4.2).
- **Five equal buttons.** Every action equally weighted means no action taken. Correction: one primary, others demoted to links/ghost buttons.
- **Baking facts into imagery.** Dates and prices invisible after blocking or cropping. Correction: text carries facts; images carry mood.
- **The 900-px-wide email.** Cropped panes and sideways scrolling. Correction: the 600–640 px standard band.
- **Hero with no action above the fold.** The visitor scrolls or leaves before the CTA appears. Correction: headline + CTA in the first viewport (§4.3).
- **Redesigned look per placement.** Each channel invents its own palette/CTA; no recognition builds. Correction: the four consistency levers (§4.1).
- **Retina-blindness.** 600 px banners exported at 1× look soft on modern screens. Correction: 2× exports constrained to 600 px display width.
- **Fake urgency.** Countdown timers that reset; trust damage outlasts the campaign. Correction: real deadlines only (§4.4).
- **CTA labels that name the interface.** "Submit", "Click here". Correction: verb-first labels naming the action.
- **Retina-blind landing images.** 600-px-wide product shots stretched across a 1440 px hero. Correction: hero imagery at ≥ 2× display size, compressed to modern formats.
- **Testing two things at once.** A "winning" variant whose CTA label, colour and image all changed explains nothing. Correction: one variable per test (§4.6).
- **No preheader.** The inbox shows "View in browser — unsubscribe" as the preview. Correction: designed subject + preheader pair on every send (§4.2).

## 9. Evaluation checklist

- [ ] The message hierarchy fits three lines before design starts: offer, audience, one action, deadline.
- [ ] One visually dominant CTA per view; verb-first label; secondary actions demoted.
- [ ] Email assets live on the 600 px standard (2× exports for retina), with live-text CTA and alt text for image-blocked rendering.
- [ ] Critical facts (dates, prices, offer) exist as real text in every channel that allows it.
- [ ] The hero presents headline + subhead + primary CTA in the first viewport and stacks cleanly at 375 px width.
- [ ] The four consistency levers — palette roles, headline treatment, lockup, CTA formula — hold across all placements.
- [ ] Buttons pass contrast checks ([Colour accessibility](../colour/colour-accessibility.md)) and meet ≈44 px touch targets.
- [ ] Urgency is truthful; deadlines are real.
- [ ] Subject line and preheader are written as designed surfaces for every send (§4.2).
- [ ] Email renders acceptably across the major client families, including dark mode and image-blocked states.
- [ ] Any test changed one variable at a time and the result was recorded against placement (§4.6).
- [ ] An asset manifest with per-placement files, dimensions and links shipped with the campaign.
- [ ] Feed adaptations re-run the checks in [Social media checklist](../evaluation/social-media-checklist.md).

## 10. Related topics

- [Social media graphics](social-media.md) — feed placements and template logic for campaign adaptations.
- [Posters](posters.md) and [Event collateral](event-collateral.md) — print/physical campaign placements and their mechanics.
- [Certificates and documents](certificates-and-documents.md) — the document family that confirms conversions (tickets, confirmations).
- [Visual identity](../branding/visual-identity.md) — the source system campaigns must express.
- [Logo systems](../branding/logo-systems.md) — lockup and clear-space rules in headers and heroes.
- [Palette development](../colour/palette-development.md) — accent roles that make CTAs dominant.
- [Colour accessibility](../colour/colour-accessibility.md) — contrast for buttons and text.
- [Web typography](../typography/web-typography.md) — hero and email text rendering.
- [UI/UX domain](../ui-ux/) — native landing-page layout systems and interaction patterns.

## 11. References

- beehiiv, "Your 2025 Guide to Email Newsletter Dimensions" — template width close to 600 px. https://www.beehiiv.com/blog/best-email-image-size [search-verified 2026-11-23]
- Template.net, "Email Newsletter Size — Dimension, Inches, mm, cms, Pixel" — 600 px width compatibility and 600 × 300 px full-banner image. https://www.template.net/graphic-design/email-newsletter-sizes [search-verified 2026-11-23]
- Industry discussions of the 600 px standard appearing in search results (email developer forums, September 2024). [search-verified 2026-11-23, pages not fetched]
- Nancy Duarte, *Resonate* (Wiley) — audience-first message hierarchy behind §5.1. [canonical]
- Sections 4.2–4.5 numeric guidance (banner heights, file-weight and touch-target rules of thumb) are conventional professional starting points, labelled as such in the text; hero structure synthesis draws on the sources above.
