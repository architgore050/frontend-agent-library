# Social media graphics

## 1. What is it?

Social media graphics are the visual assets a brand or event publishes inside platform feeds: single feed images, multi-image carousels, vertical stories/reels, banners and profile imagery. They are defined less by artistic content than by **constraints** — each platform dictates canvas ratio, pixel dimensions, file weight and (critically) the parts of the canvas that its own interface covers. A working social media practice therefore combines a strict spec discipline with a **template system** that lets dozens of posts ship while staying visually consistent. This page covers the graphic-design layer; copywriting, scheduling and analytics are out of scope.

## 2. Why does it matter?

Social platforms are where most audiences now meet a brand first, and where an event's visual identity is extended the hardest: one logo must live on canvases from a 1:1 feed tile to a 9:16 full-screen story, often reduced to thumbnail size in a feed. Every post also competes in a scroll, so the graphics must communicate at both extremes — recognisable at 200 px wide in the grid, legible at full-screen scale. Without a spec discipline, assets get cropped badly or softened by recompression; without a template system, a feed turns into visual noise and the brand stops compounding recognition. This is the digital counterpart of the print discipline in [Posters](posters.md).

Two economics drive every decision on this page. First, **attention is rented, not owned**: a post has roughly a second to register before the scroll continues, so the hook lives on the image and the detail lives in the caption. Second, **production volume is high**: a campaign feed may need dozens of posts per week, which makes a template system (§4.4) and batch production (§4.8) the difference between a consistent channel and an abandoned one. The visual fundamentals — hierarchy, contrast, type scale — are the same as print; what changes is the delivery mechanism, the specs, and the rate.

## 3. Core principles

- **Design to the ratio, export to the spec.** Build each asset on the platform's real canvas ratio; never design one square and hope the platform crops it well.
- **Respect safe zones.** Platform UI (profile names, captions, reply bars, reaction overlays) covers predictable parts of stories/reels; content there is hidden, not displayed.
- **Legibility at thumbnail scale.** The feed preview is a fraction of full size. If the message requires reading text, that text must be big enough in the preview, or duplicated in the caption.
- **One post, one idea.** Feed graphics are posters at palm scale: a claim, a supporting visual, one action. Depth belongs in carousels, not in cramming one image.
- **Templates over one-offs.** Recurring post types (announcements, speaker cards, countdowns, results) get locked templates: fixed zones, variable slots. Consistency across posts is a system property, see [Visual identity](../branding/visual-identity.md).
- **Accessibility by default.** Alt text on every meaningful image, contrast-checked text, and no critical information conveyed by colour alone (see [Colour accessibility](../colour/colour-accessibility.md)).

## 4. How it works

### 4.1 Platform specification table

The Instagram values below were verified against a current (2026) size guide. Treat every other platform's row as **commonly-published values to re-check** — platforms revise specs frequently, and you must confirm against the platform's own documentation before each production run.

**Instagram (verified)**

| Placement | Dimensions (px) | Ratio | Notes |
|---|---|---|---|
| Feed — portrait (recommended default) | 1080 × 1350 | 4:5 | Fills the most feed space; accepted ratios run from 4:5 to 1.91:1, width 320–1440 px |
| Feed — square | 1080 × 1080 | 1:1 | Crops awkwardly in the 3:4 profile grid preview |
| Feed — landscape | 1080 × 566 | 1.91:1 | Smallest footprint; for repurposed wide assets |
| Carousel | 1080 × 1350 per slide | 4:5 | Up to 20 slides in-app; use one ratio for all slides |
| Stories / Reels | 1080 × 1920 | 9:16 | Keep text/faces in the middle band; see safe zones below |
| Profile picture | ≥ 320 × 320 | 1:1 | Displayed as a circle — centre the mark with margin |
| File limits | JPEG, RGB | — | Under ~8 MB for scheduled posts; video H.264/HEVC MP4/MOV |

Instagram has previewed profile-grid tiles at 3:4 (≈1013 × 1350 px) since a 2025 update, trimming roughly 67 px from each side of a 1080-wide post — keep logos, faces and text away from the left/right edges ([accessed] RecurPost guide).

**Stories/Reels safe zones (verified):** keep essential text and faces out of the **top ~14%** (profile/handle area) and the **bottom ~20%** (caption and reply UI). In practice, design a "middle band" of roughly 1080 × 1250 px and hold graphics inside it. Reels additionally show a centre-cropped slice in the grid, so keep the focal point centred.

**Other platforms (commonly published — re-check before production)**

| Platform | Placement | Dimensions (px) | Ratio |
|---|---|---|---|
| Facebook | Feed link image | 1200 × 630 | 1.91:1 |
| Facebook | Feed square / portrait | 1080 × 1080 / 1080 × 1350 | 1:1 / 4:5 |
| Facebook | Story | 1080 × 1920 | 9:16 |
| X | In-stream image | 1600 × 900 | 16:9 |
| X | Header banner | 1500 × 500 | 3:1 |
| LinkedIn | Feed image | 1200 × 1200 or 1200 × 627 | 1:1 / 1.91:1 |
| LinkedIn | Company page banner | 1584 × 396 | 4:1 |
| YouTube | Video thumbnail | 1280 × 720 | 16:9 |
| YouTube | Channel art | 2560 × 1440 (safe area ≈ 1546 × 423) | ~16:9 |
| TikTok | Video / cover | 1080 × 1920 | 9:16 |

### 4.2 Readability on small screens

Mobile preview shrinks everything: a 1080-wide asset renders at maybe 350–500 px wide in a feed. Conventional starting points for a 1080-px-wide canvas (verify by previewing at feed scale on a real phone):

- Headline text ≥ 60–80 px; body/annotation text ≥ 28–36 px; anything smaller belongs in the caption.
- One to two type sizes per asset; contrast per [Colour accessibility](../colour/colour-accessibility.md).
- The squint test from print applies: zoom the exported image to ~35% — if the message disappears, increase scale or cut text.
- Never bake the *date or call to action* into an image without repeating it in the post copy; images are often skimmed past or re-shared cropped.

### 4.3 Carousels as narrative sequences

A carousel is a storyboard, not a stack of images. A robust conventional structure for an announcement or educational carousel:

1. **Hook slide** — one large claim or question; almost no text beyond the hook; must earn the first swipe.
2. **Context slide** — why the claim matters, one supporting fact or image.
3. **Content slides** — one idea per slide, same layout engine, escalating detail.
4. **Payoff slide** — the concrete answer, result or summary list.
5. **CTA slide** — the action (register, follow, save), plus handle and any partner marks.

Continuity devices make it feel designed: a consistent header zone showing slide progress ("3/8"), a running colour or motif thread, identical margins. All slides share one ratio — 4:5 on Instagram — because mixed ratios cause uneven cropping ([accessed] RecurPost). Deeper visual-storytelling principles are covered in [Art direction](../graphic-design/art-direction.md).

### 4.4 Announcement systems and template consistency

Recurring post types should be defined once as templates with locked and variable zones:

| Template | Locked zones | Variable slots |
|---|---|---|
| Event announcement | Logo position, footer bar, type style | Headline, date/venue block, hero image |
| Speaker / person card | Portrait crop mask, name/role type styles | Photo, name, role, session title |
| Countdown ("5 days to go") | Number style and position, palette | The number, background variant |
| Results / winners | Award tier styles, sponsor footer | Names, categories, photographs |
| Thank-you / recap | Header treatment, image grid layout | Photos, closing line |

Each template specifies: canvas ratio(s), margin grid, logo clear space (see [Logo systems](../branding/logo-systems.md)), colour roles from the palette (see [Palette development](../colour/palette-development.md)), and the type scale from [Typographic hierarchy](../typography/typographic-hierarchy.md). The system is the same discipline as print template systems in [Event collateral](event-collateral.md), with platform ratios added.

### 4.5 Motion and video basics

Stories and reels are video-first, and even feed carousels increasingly carry motion. The design layer that still belongs to this page:

- **Assume muted playback.** Most feed and story video is watched without sound (a widely cited industry figure is the large majority — treat "design for sound-off" as a hard default rather than a statistic). Burn in subtitles or keep captions in the platform's caption sticker; never rely on spoken audio alone to carry the message.
- **Text-safe motion:** hold each on-screen text beat long enough to read (a conventional minimum of ~2 seconds per card of text), and keep text within the same safe zones as static stories.
- **Loop discipline:** reels and stories loop; the first frame and last frame should both make sense as entry points, because many viewers arrive mid-loop.
- **Cover frames matter:** the reel/story cover is what the grid shows — design it as a deliberate still that matches the feed template system, not an arbitrary paused frame.
- Motion graphics craft (easing, transitions, timing) belongs to animation practice; see [Art direction](../graphic-design/art-direction.md) for the visual-language decisions that keep motion on-brand.

### 4.6 Alt text and accessible captions

Alt text is a design deliverable, not an afterthought:

- Describe the *message*, not the pixels: "Two runners crossing the finish line at the spring marathon" beats "photo of people running". Decorative textures get empty alt attributes (`alt=""`), meaningful infographics get a short summary plus the key numbers in the caption.
- Platforms surface alt text in different places (advanced settings, post composer); write it into the template checklist so no post ships without it.
- Avoid text baked into images as the *only* carrier of information — screen readers cannot read it, and cropping or compression can clip it. This overlaps the legibility rules in 4.2: keep facts in captions.
- Caption conventions: front-load the hook (the feed truncates), use line breaks for scanability, and keep hashtag blocks at the end rather than interleaved.

### 4.7 Export practice

- Export PNG for graphics with text and flat colour; high-quality JPEG (80–90) for photographic feeds; MP4 H.264 for motion.
- Supply 1080-px-wide canvases (or the platform's stated dimensions) at 72 PPI — pixel dimensions are what matter, not the PPI metadata.
- Design the master at the largest ratio needed and derive variants: e.g. a 1080 × 1350 master re-frames to 1080 × 1920 (stories) by extending the background, and to 1:1 by re-cropping — not by squashing.
- File naming convention (`2026-05-14_event-announce_carousel-05_4x5_v2.png`) prevents the wrong crop going live.
- Always write alt text; keep it descriptive of the message, not the pixels.

### 4.8 The content calendar and batching

Template systems pay off only if production is batched. A practical cadence for an event or brand channel:

- **Plan the grid before the posts.** Sketch one month of posts as labelled slots on a calendar (announcement, speaker, countdown, recap…) using the templates from 4.4; gaps show which template is missing before it is urgent.
- **Batch by template, not by post.** Designing all speaker cards in one session is several times faster than one per week — the template's locked zones mean only variables change. Photography for a batch is captured in one session under one lighting treatment so crops match.
- **Buffer evergreen content.** Keep 2–3 finished posts without dates in the bank for gaps; time-critical posts (countdowns, announcements) always get calendar priority.
- **Caption and asset together.** Copy, alt text, link and UTM tag travel in the same planning row as the image; a post that ships without its caption discipline is half-shipped.
- **Review cadence:** the monthly grid review (7.4) closes the loop — what the calendar produced is evaluated as a wall, and fixes flow back into templates.

### 4.9 Approval workflow

Recurring content does not need per-post review, but the *templates* and anything off-template do:

- Templates are approved once per event/brand cycle (identity owner signs off zones, palette roles, type scale); populated posts from approved templates ship on the designer's judgement.
- Bespoke posts (launches, sensitive announcements) route through the identity owner — the cost of one approval round is far below the cost of an off-brand moment during a high-visibility window.
- Sponsor content follows the governance in [Brand architecture](../branding/brand-architecture.md): contractual marks appear in contractual slots, and approval for those posts includes whoever owns the contract.
- Keep the approval chain in the asset manifest so the live post can be traced to its approved source file.

## 5. Practical application

A release workflow that survives real production:

1. **Read the current spec sheet** for each target platform (they change; the table above is a dated snapshot).
2. **Build the template set first** — before the first post — covering every recurring post type in 4.4, in every required ratio.
3. **Populate and check**: safe-zone overlay on stories, thumbnail-scale legibility check, contrast check, alt text.
4. **Bundle variants** per post (feed + story + grid-preview crop) and name them per convention.
5. **Review the feed as a whole** every week or month — the unit of quality is the grid, not the post. Compare against the checklist in [Social media checklist](../evaluation/social-media-checklist.md).

### 5.2 Tooling and source of truth

- Keep one master file per template (design tool of choice) with named layer groups for the variable slots — "NAME", "DATE", "PHOTO" — so non-designers can populate without breaking zones.
- Derive ratios from the master with artboards/frames rather than separate files; the 9:16, 4:5 and 1:1 variants of one post stay one file.
- Store exports in a dated, named folder per post, and treat the platform spec table (4.1) as a living document re-checked quarterly — platforms change specs without notice.
- For scheduled tools that re-compress aggressively, export slightly higher quality (PNG for text-heavy graphics) so the platform's compression has headroom to soften.

## 6. Decision framework

- **Which format?** One idea, quickly consumed → single feed graphic. A sequence that teaches or announces in steps → carousel. Urgency, atmosphere, or a talking piece → story/reel. Persistent brand surfaces → profile image and banners.
- **Which ratio leads?** If the audience is feed-first, design 4:5 masters; if story-first (younger audiences, time-limited announcements), design 9:16 and derive the feed version.
- **Text in image or caption?** As little as possible in the image; the image carries the hook, the caption carries detail. Platforms reward captions for search and accessibility.
- **Template or bespoke?** Anything recurring → template. Genuinely new moment (brand launch, championship win) → bespoke art directed within the identity's boundaries (see [Visual identity](../branding/visual-identity.md)).
- **Static or motion?** Motion when the platform rewards watch-time (reels, TikTok) or the message is temporal (countdowns); static when the message is informational (speaker cards, schedules) and must be readable at a glance. Carousels outperform single images for anything with more than one fact.
- **One platform or many?** Design the master for the platform where the audience is densest, derive the rest; never design "for everywhere" by averaging ratios — you get a compromise that crops badly on all of them.
- **How much text on the image?** The hook only. Every fact beyond the hook (prices, full schedule, terms) belongs in the caption or the carousel's later slides.
- **Batch or drip?** Batch production weekly/monthly by template (§4.8); drip only for genuinely time-critical posts, which are exactly the ones worth interrupting a batch for.
- **Who approves?** Approved templates ship without review; off-template and sponsor content routes through the identity owner (§4.9). Write this down once, or every post becomes a negotiation.
- **Grow the template set or prune?** A template that has not been used in a quarter is clutter that dilutes the grid — prune it; a recurring need met twice by bespoke posts is a template waiting to be extracted.

## 7. Examples

### 7.1 Event announcement carousel (Instagram, verified specs)

```text
Canvas:      1080 × 1350 px, 8 slides, PNG
Grid:        60 px margins, 12-column feel; header strip 90 px with logo + "1/8"
Slide 1:     "Registrations open" 96 px headline, date block 40 px, hero photo masked
Slides 2–6:  Programme highlights, one item per slide, 64 px titles / 32 px body
Slide 7:     Speaker montage, 4-up grid with names 36 px
Slide 8:     CTA "Register at …", QR-free (link in bio), handle + sponsor footer 28 px
Safe zones:  n/a in feed; story variant re-framed with top-14% / bottom-20% kept clear
```

### 7.2 Speaker card template spec

- Canvas 1080 × 1350; portrait occupies bottom 55% inside a fixed rounded mask.
- Name 72 px semibold; role + organisation 36 px; session title 40 px italic accent.
- Logo lockup top-left with 40 px clear space; footer bar in palette accent with the event hashtag 30 px.
- Variants: 9:16 story crop (portrait fills, text moves to middle band) and 1:1 grid teaser (head-and-shoulders + name only).

### 7.3 Countdown story variant (9:16)

```text
Canvas:      1080 × 1920, PNG; middle band content only (top 14% / bottom 20% clear)
Frame 1:     "3 DAYS TO GO" — number 320 px in accent colour, centred band
Frame 2:     Programme teaser, 3 lines at 44 px + session names 32 px
Frame 3:     CTA "Link in bio", handle 40 px, date block 48 px
Motion:      optional 3-frame animation; each frame holds ≥ 2 s (§4.5)
Continuity:  same background treatment and footer bar as the 7.1 carousel
```

The story reuses the carousel's palette, footer bar and type scale; only the canvas ratio and the safe-zone geometry change. That is the whole point of the template system: new post types cost a geometry change, not a redesign.

### 7.4 Grid-consistency review

Once a month, view the profile grid as a 3:4 tile wall and check: do recurring templates read as one family (same corner logo positions, same footer bar rhythm)? Are story covers distinguishable from feed posts at a glance? Did any post ship with a drift in colour or type? Fixes go back into the templates, not into re-edited posts — the system is the artefact being maintained.

### 7.5 Profile surface spec

The profile is the only placement the brand fully controls, so it gets its own mini-spec: profile image ≥ 320 × 320 px centred as a circle (the mark's clear space must survive the circular mask — check [Logo systems](../branding/logo-systems.md)); link-in-bio surface reuses the palette and type scale; pinned posts are chosen to represent the three main templates. Highlight/story cover icons, where the platform supports them, use one glyph family at one size from [Iconography](../graphic-design/iconography.md). Treat every one of these as a template decision made once, not a per-quarter improvisation.

## 8. Common mistakes

- **Designing one square and letting the platform crop.** Stories lose their headlines to the reply bar; feed posts lose faces to the grid crop. Correction: build per-ratio masters.
- **Text inside platform UI zones.** Captions, timestamps and reaction icons cover it. Correction: apply the 14%/20% story safe zones and preview on-device.
- **Caption-scale text baked into feed images.** Unreadable at preview scale and illegible for screen readers. Correction: 28–36 px minimum body text on a 1080 canvas, plus alt text and caption copy.
- **Carousel slides with mixed ratios or mixed layouts.** Feels broken mid-swipe. Correction: one ratio, one layout engine, progress indicators.
- **One-off designs for recurring content.** The feed stops compounding recognition and production slows down. Correction: the template system in 4.4.
- **RGB-to-CMYK confusion is not an issue here, but recompression is.** Exporting heavily dithered gradients or re-saving JPEGs repeatedly causes banding; export once from the master at export quality.
- **Brand drift across platforms.** Different logo versions, off-palette colours per network. Correction: one asset source of truth, colour tokens from the palette, lockup rules from [Brand architecture](../branding/brand-architecture.md).
- **Ignoring alt text and contrast.** Excludes low-vision users and violates the checks in [Colour accessibility](../colour/colour-accessibility.md).
- **Copying the competitor's ratio instead of reading the spec.** A screenshot of another brand's post does not tell you their crop survived; it may be cropped badly. Correction: the spec table, re-checked per quarter.
- **Trend-chasing outside the identity.** A meme format that uses none of the palette or type system wins one post and loses the grid. Correction: if a trend is worth joining, express it inside the template system's levers — or skip it.
- **Publishing without the caption discipline.** The image carries the hook and the caption starts mid-thought, or hashtags sit mid-sentence. Correction: front-loaded hook, facts in caption, hashtags at the end (§4.6).
- **Cover frames left to chance.** Reels paused at an arbitrary frame become the grid tile. Correction: design the cover as a deliberate still (§4.5).

## 9. Evaluation checklist

- [ ] Every asset matches the platform's *current* published spec (dimensions, ratio, file weight).
- [ ] Story/reel assets keep all content inside the middle band (top ~14% and bottom ~20% clear).
- [ ] Message survives the 35% thumbnail test.
- [ ] Text minimums hold (≥ 60–80 px headlines, ≥ 28–36 px body on 1080-wide canvases) or copy moved to the caption.
- [ ] Carousel: one ratio, one layout system, hook → payoff → CTA sequence, progress indicator present.
- [ ] Templates cover all recurring post types; no recurring post ships as a bespoke one-off.
- [ ] Logo clear space, colour tokens and type scale match the identity system on every asset.
- [ ] Alt text written for every meaningful image; contrast passes [Colour accessibility](../colour/colour-accessibility.md) checks.
- [ ] Video assets: subtitles present, text beats hold ≥ 2 s, cover frame designed deliberately (§4.5).
- [ ] Post ships with caption, link and UTM tag in the same manifest row as the asset (§4.8).
- [ ] Approval route followed: template-populated posts ship; bespoke and sponsor posts were reviewed (§4.9).
- [ ] The grid, viewed as a whole, reads as one brand — checked against [Social media checklist](../evaluation/social-media-checklist.md).

## 10. Related topics

- [Posters](posters.md) — the print counterpart: same hierarchy logic, different mechanics.
- [Typographic hierarchy](../typography/typographic-hierarchy.md) — the scale system referenced by every template.
- [Palette development](../colour/palette-development.md) — the colour tokens templates consume.
- [Colour accessibility](../colour/colour-accessibility.md) — contrast and colour-independence checks.
- [Visual identity](../branding/visual-identity.md) — keeping the feed on-brand.
- [Logo systems](../branding/logo-systems.md) — clear space and minimum sizes for profile and footer marks.
- [Brand architecture](../branding/brand-architecture.md) — partner and sponsor lockups in post footers.
- [Art direction](../graphic-design/art-direction.md) — image treatment and visual storytelling.
- [Grid systems](../layout/grid-systems.md) — margin and column structure at 1080-px scale.
- [Social media checklist](../evaluation/social-media-checklist.md) — the shared evaluation sheet.

## 11. References

- RecurPost, "Instagram Post Size Guide" — feed/carousel/story dimensions, 20-slide carousel limit, stories safe zones (top 14% / bottom 20%), 3:4 grid preview behaviour, file limits. https://recurpost.com/instagram-scheduler/instagram-post-size-guide [accessed 2026-11-23]
- Social media image-size summaries appearing in search results (Hootsuite-style round-ups, November 2026) confirming 1080 × 1350 feed portrait and 1080 × 1920 stories. [search-verified 2026-11-23, pages not fetched]
- Values in the "other platforms" table are commonly-published figures from general professional knowledge; platforms revise specifications frequently — re-check against each platform's official documentation before production.
- Sections 4.2 (mobile text minimums) and 4.4 (template structures) are synthesis of professional convention and the sources above, labelled as conventional starting points in the text.
