# Video and Motion Assets

## 1. What is it?

Sourced motion assets — stock video, animated backgrounds, and pre-authored vector animation (Lottie) — as opposed to runtime animation libraries ([Animation libraries](../motion-and-interaction/animation-libraries.md)): what the sources provide, licence positions, the formats and optimisation that keep video from wrecking page weight, and the usage patterns (hero loops, product demos, ambient backgrounds) that work on real pages.

## 2. Why does it matter?

Video is the heaviest media class a page ships — a bad hero loop costs more than every other asset combined — and its licences are less standardised than photography's (each platform has its own terms; some require no attribution, some restrict redistribution). Meanwhile a well-chosen 8-second muted loop is the single most reliable "expensive-looking" move available on a marketing page. The craft is: source libre, compress hard, loop honestly, and never let the poster lie ([../evaluation/ai-design-failures.md](../evaluation/ai-design-failures.md)).

## 3. The sources

### 3.1 Mixkit — https://mixkit.co/ [accessed 2026-11-25]

**Provides:** free stock video clips, video templates, motion backgrounds and sound effects (the SFX side is catalogued in [sound.md](sound.md)) under one licence.
**Licence:** Mixkit Licence — free for commercial use, no attribution required; redistribution-as-is prohibited. (Verify the live licence page per project.)
**Character:** curated, production-quality clips and motion-background loops; the best curated free source for hero-video needs.

### 3.2 Coverr — https://coverr.co/ [accessed 2026-11-25]

**Provides:** free stock video focused on usable website hero footage (abstract, urban, nature loops), searchable by mood.
**Licence:** Coverr terms — free for commercial use via their licence (verify per download; historically no attribution required).
**Character:** hero-loop orientation; quality is strong for backgrounds.

### 3.3 Pexels Video — https://www.pexels.com/videos/ [search-verified, accessed 2026-11-25 (403 to bots; browser/API access)]

**Provides:** the free-stock-video catalogue of the Pexels ecosystem (see [photography.md](photography.md) for the licence family).
**Licence:** Pexels Licence family — free for commercial use, no attribution.
**Character:** breadth over curation; good when a specific subject is needed.

### 3.4 LottieFiles — https://lottiefiles.com/ [search-verified, accessed 2026-11-25 (403 to bots; browser access)]

**Provides:** the Lottie animation ecosystem — a marketplace of JSON vector animations (icons, loaders, empty-state characters, celebratory moments) plus tooling and the lottie-web player ([airbnb/lottie-web](https://github.com/airbnb/lottie-web), MIT).
**Licence:** per animation — marketplace items carry their own terms (many CC-BY with attribution, some commercial licences); check and record per file.
**Craft:** the runtime/craft layer is [Animation libraries](../motion-and-interaction/animation-libraries.md) §4.7 — budget file size like an image, static first frame as fallback, reduced-motion off-switch.
**Limits:** market-place licence variety is the trap — one licence check per animation, recorded in the manifest.

## 4. The comparison table

| Source | Licence | Attribution | Character | Best for |
| --- | --- | --- | --- | --- |
| Mixkit | Mixkit licence (verify page) | None | Curated clips + motion backgrounds | Hero loops, ambient backgrounds |
| Coverr | Coverr terms (verify) | Historically none | Hero-oriented footage | Website heroes |
| Pexels Video | Pexels licence family | None | Broad catalogue | Specific subjects |
| LottieFiles | Per animation (record it) | Often yes (CC-BY) | JSON vector animations | Loaders, empty states, moments |

## 5. Practical workflow

1. **Decide the motion job:** hero loop (page-defining), section ambient (subtle), UI moment (Lottie), demo (product truth) — the motion hierarchy ([../motion-and-interaction/motion-principles.md](../motion-and-interaction/motion-principles.md)) applies to sourced video exactly as to code.
2. **Search by scene and mood**, download the candidates; evaluate like photography (composition, subject, lighting, palette fit — [acquisition-workflow.md](acquisition-workflow.md) §5) plus two video-specific checks: **loop point** (does the cut repeat invisibly?) and **first-frame poster** (does it represent the clip honestly?).
3. **Licence check per source per project**; manifest entry with the licence page URL ([licensing-and-provenance.md](licensing-and-provenance.md)).
4. **Optimise:** hero loops ≤ ~3–5 MB target (conventional), 720p–1080p is enough under overlays, mute by default, `preload="none"` below the fold, poster image always, modern codecs (H.264 baseline compatibility; consider AV1 where support allows), `playsinline muted autoplay` only for ambient loops with the accessibility rules below.
5. **Accessibility and control:** ambient video gets a pause control if it plays continuously (WCAG 2.2.2 — [../motion-and-interaction/motion-principles.md](../motion-and-interaction/motion-principles.md)); `prefers-reduced-motion` swaps video for the static poster; caption or transcribe anything with meaningful audio (usually: keep ambient silent).

## 6. Common mistakes

- **The 15 MB hero** — full-resolution stock video shipped raw; compression and duration discipline are the fix.
- **The lying poster** — poster frame unrelated to content, or autoplay muted-video implying sound.
- **Attribution-free assumption on LottieFiles** — marketplace licences vary; the record-it-per-file rule exists because of this source.
- **Unstoppable loops** — continuous motion without pause controls; the accessibility floor again.
- **Motion without hierarchy** — three videos competing on one page; one hero loop maximum.

## 7. Evaluation checklist

- [ ] Motion job assigned (hero/ambient/UI moment) with the hierarchy respected.
- [ ] Candidates evaluated like imagery + loop point + poster honesty.
- [ ] Licence verified per source per project; manifest records licence-page URL.
- [ ] Video compressed to target, poster always set, `preload="none"` below fold, `playsinline muted` for ambient.
- [ ] Continuous motion has pause control; reduced-motion renders the static poster.
- [ ] Lottie files: size-budgeted, static fallback, reduced-motion off, licence recorded per file.

## 8. Related topics

- [Animation libraries](../motion-and-interaction/animation-libraries.md) — the runtime side (Lottie player §4.7).
- [Motion principles](../motion-and-interaction/motion-principles.md) — the hierarchy and accessibility floors.
- [Photography](photography.md) — the still-image family and licence table.
- [Sound](sound.md) — the audio counterpart (Mixkit SFX included).
- [Performance](../frontend-engineering/performance.md) — the weight budget video must meet.
- [Licensing and provenance](licensing-and-provenance.md) — the manifest.

## 9. References

- Mixkit licence — https://mixkit.co/license/ (verify current). [search-verified, accessed 2026-11-25]
- Coverr — https://coverr.co/ [accessed 2026-11-25]
- Pexels video licence family — https://www.pexels.com/license/ [search-verified, accessed 2026-11-25]
- LottieFiles — https://lottiefiles.com/ [search-verified, accessed 2026-11-25]
- MDN video best practices — https://developer.mozilla.org/en-US/docs/Learn/Performance/video [search-verified, accessed 2026-11-25]
- Weight targets stated as conventional starting points of this library.
