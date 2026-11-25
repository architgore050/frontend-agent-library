# UI Sound Sources

## 1. What is it?

The verified sources for UI sound effects and the licence/usage rules for shipping audio in interfaces: what each library provides, licence positions, the integration craft (Web Audio, preloading, debouncing), and the design rules that keep sound a feedback channel rather than a nuisance. The design theory — when to use sound at all, the <200 ms rule, mute discipline — is [Microinteractions](../motion-and-interaction/microinteractions.md) §5.2; this file is the sourcing and plumbing layer.

## 2. Why does it matter?

Sound is the most neglected feedback channel: most products ship silent interfaces that could carry genuine usability (eyes-busy confirmation, error salience, brand signature) — and the few that add sound ship it thoughtlessly (autoplaying, unmuted, on every click). The difference is sourcing discipline and a small set of rules. The sources below were resolved from the library's frontend brief and verified: two purpose-built UI-SFX libraries (one open-source, one commercial-free-tier), plus the general libraries.

## 3. The sources

### 3.1 UISFX — https://github.com/romainsimon/uisfx [accessed 2026-11-25; verified via GitHub API]

**Provides:** an open-source UI sound-effects library built *specifically for interfaces* — click, hover, toggle, success, error families packaged for direct web use (npm package `uisfx`; repo includes usage docs).
**Licence:** MIT (per repository) — free including commercial use; the cleanest licence position in this catalogue.
**Character:** purpose-designed micro-sounds at the right durations — the first place to look for a coherent product family.
**Verification:** romainsimon/uisfx — listed in the GitHub catalogue ([../github-resources/catalogue.md](../github-resources/catalogue.md) sweep notes); site access verified 2026-11-25.

### 3.2 Bencho sounds — https://bencho.dev/sounds [accessed 2026-11-25]

**Provides:** a curated UI sound-effect library — "UI Sound Effects Library — 182 Interaction Sounds" — browsable and downloadable by interaction type.
**Licence:** Bencho's terms state free use for interfaces (verify the current terms page before shipping; record in the manifest).
**Character:** interaction-organised (toggles, notifications, successes) — the largest curated UI-specific catalogue found in the research pass.
**Limits:** licence terms are the site's own, not a standard open licence — the one to read most carefully.

### 3.3 Mixkit Sound Effects — https://mixkit.co/free-sound-effects/ [accessed 2026-11-25]

**Provides:** free SFX catalogue (UI clicks, notifications, transitions, game sounds) under the Mixkit licence family — free commercial use, no attribution, no redistribution-as-is ([video-and-motion.md](video-and-motion.md) documents the same licence family for video).
**Character:** broad and searchable; quality good; not UI-organised but rich in the needed families.

### 3.4 Freesound — https://freesound.org/ [accessed 2026-11-25]

**Provides:** the collaborative sound library (hundreds of thousands of clips) with **per-clip licence display** (CC0, CC-BY, CC-BY-NC) — the rights-transparent source.
**Licence:** per clip — filter CC0 for zero-attribution needs; CC-BY clips require recorded credit.
**Character:** everything and anything; curation burden on you. The UI-specific quality bar requires patient filtering.

### 3.5 Zapsplat — https://www.zapsplat.com/ [search-verified, accessed 2026-11-25]

**Provides:** a large free-SFX library (account required).
**Licence:** Zapsplat's own terms (free tier with account; attribution per their current terms — verify).
**Limits:** account-gated; commercial terms need the per-project read.

## 4. The comparison table

| Source | Licence | Attribution | UI-specific | Position |
| --- | --- | --- | --- | --- |
| UISFX | MIT | None | Yes — purpose-built | First choice for product families |
| Bencho | Site terms (verify) | Per terms | Yes — 182 interaction sounds | Largest curated UI catalogue |
| Mixkit SFX | Mixkit licence | None | Partly | Broad free fill |
| Freesound | Per clip (CC0/CC-BY/NC) | Per clip | No | Rights-transparent depth |
| Zapsplat | Site terms (account) | Per terms | No | Depth fallback |

## 5. Practical workflow

1. **Decide sound's job first** ([Microinteractions](../motion-and-interaction/microinteractions.md) §6): which moments get audio (usually success, error, notification, toggle — 4–8 sounds, not 40).
2. **Source one family** (UISFX or Bencho) — one synthesis character, consistent loudness; mixing libraries' families reads as collage.
3. **Process to budget:** trim to <200 ms, normalise loudness (≈ -20 dB under content), export compact (Opus where supported, MP3 fallback), total library <100 KB ([Microinteractions](../motion-and-interaction/microinteractions.md) §5.2).
4. **Plumb it right:** preload the tiny set (`preload='auto'`), trigger via debounced handlers, Web Audio for overlapping needs, and gate on the persisted mute preference; silent by default in productivity contexts.
5. **Licence + manifest per clip** (source URL, creator where known, licence, date) ([licensing-and-provenance.md](licensing-and-provenance.md)).
6. **Accessibility:** sound is never the only signal (colour-and-text rule extends to audio — WCAG 1.4.1 use of colour / 1.4.2 audio control); provide the mute toggle; silent under `prefers-reduced-motion` as a sensible default.

## 6. Common mistakes

- **Sound on everything** — the "40-sound library shipped whole" failure; 4–8 semantic sounds is the design.
- **NC-licensed clips in a product** — Freesound's non-commercial filter ignored; filter CC0/CC-BY before downloading.
- **Loudness roulette** — clips from three libraries at three volumes; normalise the family.
- **No mute control** — the fastest route to users disabling the site's audio (or the site).
- **Sound as the only signal** — a success tone with no visual change; feedback is multi-channel by rule.

## 7. Evaluation checklist

- [ ] Sound's job defined: 4–8 semantic moments, one family, consistent character.
- [ ] Licence per clip verified and recorded (MIT/Bencho terms/CC0/CC-BY); NC clips excluded from products.
- [ ] Clips trimmed <200 ms, normalised, compressed; total library <100 KB.
- [ ] Preload, debounce, persisted mute preference implemented; silent-by-default contexts honoured.
- [ ] No sound-only signals; mute toggle reachable; reduced-motion quiet.
- [ ] Haptics considered for mobile where supported ([Microinteractions](../motion-and-interaction/microinteractions.md) §5.3).

## 8. Related topics

- [Microinteractions](../motion-and-interaction/microinteractions.md) — the design rules this plumbing serves.
- [Video and motion](video-and-motion.md) — Mixkit's video side and the licence family.
- [Motion principles](../motion-and-interaction/motion-principles.md) — the accessibility floors.
- [Design laws](../ux-psychology/design-laws.md) — peak-end rule: the success sound is the flow's final-moment craft.
- [Licensing and provenance](licensing-and-provenance.md) — the manifest.

## 9. References

- UISFX repository — https://github.com/romainsimon/uisfx [accessed 2026-11-25]
- Bencho sounds — https://bencho.dev/sounds [accessed 2026-11-25]
- Mixkit SFX licence family — https://mixkit.co/license/ (verify current). [search-verified, accessed 2026-11-25]
- Freesound licence model — https://freesound.org/help/licenses/ [search-verified, accessed 2026-11-25]
- Zapsplat — https://www.zapsplat.com/ [search-verified, accessed 2026-11-25]
- W3C WCAG 2.2 — 1.4.2 (Audio Control), 1.4.1 (Use of Colour). [canonical]
- Loudness and duration targets are professional conventions of this library.
