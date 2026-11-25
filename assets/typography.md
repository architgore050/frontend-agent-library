# Typography Sources

## 1. What is it?

Where fonts come from: the verified sourcing platforms (free and libre font libraries, packaged distribution, discovery resources), their licence positions, and the loading pipeline that gets the chosen fonts into a page efficiently. The selection craft (which face, which pairing, which hierarchy) is [Typeface selection](../typography/typeface-selection.md), [Font pairing](../typography/font-pairing.md) and [Typographic hierarchy](../typography/typographic-hierarchy.md); browser loading craft in detail is [Web typography](../typography/web-typography.md).

## 2. Why does it matter?

Font licensing is the asset class with the most misunderstood rights (desktop licences do not cover web embedding; "free download" pages are not font licences), and font loading is the most common page-speed self-inflicted wound (blocked paints, megabyte families, subset-less CJK). The sources below are all libre or verifiably licensed, and the pipeline section is the performance-correct default.

## 3. The sources

### 3.1 Google Fonts — https://fonts.google.com/ [accessed 2026-11-25]

**Provides:** the largest libre catalogue (1,800+ families) — sans, serif, display, mono, variable fonts, and the world's major scripts including full CJK coverage.
**Licence:** all families are open-source (OFL or Apache) — free for commercial use, embedding, modification (per family licence file).
**Craft:** the default sourcing platform; variable-font families deliver many weights in one file; subsets served per-script via the CSS API, or self-host downloads.
**Limits:** the ubiquity tax — Inter/Roboto/Poppins everywhere; the distinctive-type direction ([Typeface selection](../typography/typeface-selection.md)) usually goes to Fontshare or the smaller foundries.

### 3.2 Fontshare — https://www.fontshare.com/ [accessed 2026-11-25]

**Provides:** the Indian Type Foundry's free-font platform — professionally designed families (Satoshi, General Sans, Clash Display, Cabinet Grotesk and peers) released free for commercial use, with proper family structures (weights, italics, variable where offered).
**Licence:** the Fontshare ITF Free Font Licence — free for commercial and personal projects; restrictions on resale and standalone redistribution (verify the current licence text per download).
**Position:** the distinctive-typography source — the faces here are the credible route to "typography as the design" without licensing friction ([../typography/typeface-selection.md](../typography/typeface-selection.md)).
**Limits:** catalogue is selective by design; not a UI-fallback ecosystem — pair with a libre workhorse if needed.

### 3.3 Fontsource — https://fontsource.org/ [accessed 2026-11-25]

**Provides:** open-source fonts packaged as npm modules — self-hosting made mechanical (subset bundles, per-weight packages, CSS imports) ([fontsource/fontsource](https://github.com/fontsource/fontsource), 6,301★ MIT).
**Licence:** MIT packaging; underlying fonts keep their OFL/Apache licences.
**Position:** the pipeline layer — the default *delivery* method for Google-ecosystem fonts in build-tool projects ([Web typography](../typography/web-typography.md) §loading).

### 3.4 Fontesk — https://fontesk.com/ [search-verified, accessed 2026-11-25; direct fetch failed from this sandbox]

**Provides:** a free-font news/catalogue blog — discovery for libre display faces and foundry freebies.
**Licence:** per-post (each listing states the licence) — verify per font.
**Position:** discovery, not distribution; always end at the foundry's own licence text.

### 3.5 Fonts In Use — https://fontsinuse.com/ [accessed 2026-11-25]

**Provides:** the typographic reference archive — real projects tagged by typeface, industry, format. Not a download source: a *seeing* source for what faces look like in the wild.
**Position:** the research tool during typeface selection ([Typeface selection](../typography/typeface-selection.md) §research) — search a candidate face, see its real deployments.

### 3.6 Typewolf — https://www.typewolf.com/ [search-verified, accessed 2026-11-25; direct fetch failed from this sandbox]

**Provides:** curated typography recommendations, pairing suggestions and site-of-the-day style references; the "What's Trending" lists are a current-practice barometer.
**Position:** pairing discovery and taste calibration; follow through to the foundry/licence per recommendation.

### 3.7 Paid foundries (a boundary note)

Commercial foundries (Monotype, Klim, commercial Google-foundries, Adobe Fonts) are legitimate and sometimes the right answer — but licensing is per-use-type (web/desktop/app tiers differ) and the terms are contract documents. This library's free-frontend default is the libre layer above; when a paid face is genuinely required, the licence procurement is a project step recorded in the manifest, never an assumption.

## 4. The comparison table

| Source | Licence | Attribution | Position |
| --- | --- | --- | --- |
| Google Fonts | OFL/Apache per family | None | Catalogue + fallback ecosystem |
| Fontshare | ITF free licence (verify text) | None | Distinctive primary faces |
| Fontsource | MIT + OFL/Apache | None | npm self-hosting pipeline |
| Fontesk | Per listing | Per listing | Discovery |
| Fonts In Use | n/a (reference) | n/a | Real-use research |
| Typewolf | n/a (reference) | n/a | Pairing discovery |

## 5. Practical workflow

1. **Select by craft first** — requirement profile, personality axes, pairing ([Typeface selection](../typography/typeface-selection.md), [Font pairing](../typography/font-pairing.md)).
2. **Ssource libre by default** (Google Fonts/Fontshare); verify the family's licence file (OFL, Apache or ITF text) — the licence file ships with the font, read it.
3. **Self-host** (Fontsource package or direct download) over third-party CDN embedding — privacy, resilience, and full caching control; subset to used ranges (latin, latin-ext, actual CJK needs) ([Web typography](../typography/web-typography.md)).
4. **Load for performance:** ≤ 2 families, ≤ 4 files, `font-display: swap`, preload the critical one or two files, variable fonts over multi-weight families ([../frontend-engineering/performance.md](../frontend-engineering/performance.md) §5.2).
5. **Manifest entry per family** (name, version, licence, download URL, date) ([licensing-and-provenance.md](licensing-and-provenance.md)).

## 6. Common mistakes

- **Desktop licence assumptions** — a "free download" page is not a web licence; only the OFL/Apache/ITF terms above (or a purchased web licence) count.
- **CDN-blocking defaults** — the Google Fonts CSS embed that blocks first paint; self-host + swap + preload is the default pipeline.
- **Megabyte families** — shipping six weights and both italics when the design uses three weights.
- **Full CJK subsets** — shipping 5 MB of hanzi when the page uses 200 characters; subsetting is the craft ([Web typography](../typography/web-typography.md)).
- **Ubiquity without intent** — Inter + Poppins because they were first in the list; typography is a design decision ([../evaluation/ai-design-failures.md](../evaluation/ai-design-failures.md) §6).

## 7. Evaluation checklist

- [ ] Faces selected by the selection craft, with licence files read (OFL/Apache/ITF) and recorded in the manifest.
- [ ] Self-hosted via Fontsource or direct files; subsets built to actual use.
- [ ] ≤ 2 families, ≤ 4 files; variable fonts used where fitting.
- [ ] `font-display: swap` + preload of critical files; no font blocks first paint.
- [ ] Fallback stacks metric-compatible (`size-adjust` where tuned).
- [ ] Paid faces (if any) have their procurement and licence tier recorded.

## 8. Related topics

- [Typeface selection](../typography/typeface-selection.md) and [Font pairing](../typography/font-pairing.md) — the craft this sourcing serves.
- [Web typography](../typography/web-typography.md) — loading, rendering and accessibility detail.
- [Accessible typography](../accessibility/accessible-typography.md) — the legibility floors.
- [Performance](../frontend-engineering/performance.md) — the font budget.
- [Licensing and provenance](licensing-and-provenance.md) — the manifest.

## 9. References

- Google Fonts (OFL/Apache catalogue) — https://fonts.google.com/ [accessed 2026-11-25]
- Fontshare licence — https://www.fontshare.com/licenses (verify current text per download) [search-verified, accessed 2026-11-25]
- Fontsource — https://fontsource.org/ [accessed 2026-11-25]
- Fonts In Use — https://fontsinuse.com/ [accessed 2026-11-25]
- Typewolf — https://www.typewolf.com/ [search-verified, accessed 2026-11-25 (sandbox fetch failed)]
- Fontesk — https://fontesk.com/ [search-verified, accessed 2026-11-25 (sandbox fetch failed)]
- SIL Open Font Licence text — https://openfontlicense.org/ [canonical]
