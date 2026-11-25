# Photography Sources

## 1. What is it?

The verified catalogue of free and libre photography sources for frontend projects: what each provides, how to search it effectively, its licence reality (the part most often assumed wrongly), quality characteristics, and the practical limits. The selection craft (which photo belongs in which slot) is [Image selection](../imagery/image-selection.md); family-treatment craft is [Image treatment](../imagery/image-treatment.md).

## 2. Why does it matter?

Photography is the highest-impact asset class on most marketing surfaces — and the one with the most legal traps. "Free to download" ≠ "free to use commercially" ≠ "no attribution needed"; each source below is documented with its actual licence position, and the default advice is: read the current licence page at integration time, because these terms change. Generic stock photography is also a design failure ([../evaluation/ai-design-failures.md](../evaluation/ai-design-failures.md)): the sources below are how to avoid it — by searching with specificity, curating against a coherent art direction, and treating the chosen images as one family.

## 3. The sources

### 3.1 Unsplash — https://unsplash.com/ [accessed 2026-11-25; site returns 401 to anonymous automated fetches — browser or API access]

**Provides:** a large curated photography community collection; strong on lifestyle, product, interior, nature and "editorial-feeling" imagery.
**Licence:** the Unsplash Licence — free for commercial and non-commercial use, no attribution *required* (attribution appreciated), no permission needed; restrictions: no compiling as a competing stock service, no selling unaltered copies, no identifiable people in sensitive contexts (implicit model-consent limits). **Read the live licence page before shipping — the terms have changed historically.**
**Search craft:** searches match tags and descriptions — try scene words ("marble desk top-down", "workshop hands tools"), pick a photographer and browse their catalogue for family coherence; the Plus/editions tier and API exist (API requires attribution and has rate limits).
**Quality:** high aesthetic curation; consistent 2K+ resolution on most picks.
**Limits:** curation skews "aspirational lifestyle" — beware generic-startup-look; identifiable people carry implied-consent limits for sensitive uses.

### 3.2 Pexels — https://www.pexels.com/ [accessed 2026-11-25; 403 to automated fetches — browser/API access]

**Provides:** free stock photos *and* video (https://www.pexels.com/videos/), broad subject coverage, generous coverage of non-Western subjects and business contexts.
**Licence:** Pexels Licence — free for commercial use, no attribution required, modification allowed (including its AI-image-hosting rules for synthetic content); cannot compile as a competing service or imply endorsement.
**Search craft:** strong keyword and colour filters; collections for curation; API available with key.
**Quality:** good-but-varied; check per candidate — the catalogue mixes excellent and mediocre shots more than Unsplash.
**Limits:** quality variance; check for the "stocky" look per candidate.

### 3.3 Openverse — https://openverse.org/ [accessed 2026-11-25; 403 to automated fetches — browser/API access]

**Provides:** the open-licence search engine (WordPress/Creative Commons) across CC-licensed images and audio — the tool when you need *verifiable* CC licensing (CC BY, CC BY-SA, CC0, public domain) with per-work licence display.
**Licence:** per-work CC licences shown in results — the point of the tool; filter by licence type; attribution requirements vary by work and must be recorded.
**Search craft:** filter licence type first (CC0/PD for zero-attribution), then subject; quality varies widely — it is a rights-first tool, not a curation tool.
**Limits:** not a curated aesthetic source; treat as the rights-safe fallback and the CC0 specialist.

### 3.4 Pixabay — https://pixabay.com/ [accessed 2026-11-25; 403 to automated fetches — browser access]

**Provides:** large mixed catalogue (photos, illustrations, video, SFX) under its own content licence (free for commercial use, no attribution; selling/redistributing as-is prohibited).
**Search craft:** wide subject coverage, good for quick filler and niche subjects; quality varies — curate.
**Limits:** the most "generic stock" of the four large sources; use with the strongest treatment discipline ([Image treatment](../imagery/image-treatment.md)) or for non-hero slots.

### 3.5 Shopify Burst — https://www.shopify.com/stock-photos [accessed 2026-11-25]

**Provides:** commerce-oriented free photography (products, retail, entrepreneurship) aimed at online shops.
**Licence:** free for commercial use (Shopify's terms; verify the current page).
**Limits:** commerce-flavoured curation; smaller catalogue than the big three.

## 4. The comparison table

| Source | Licence | Attribution | Quality ceiling | Best for |
| --- | --- | --- | --- | --- |
| Unsplash | Unsplash Licence (commercial OK) | Optional | High (curated) | Editorial, lifestyle, product-adjacent hero imagery |
| Pexels | Pexels Licence (commercial OK) | Optional | Medium-high | Video + photo in one place; broad subjects |
| Openverse | Per-work CC (shown per result) | Per-work (record it) | Varies | Rights-verifiable needs; CC0/public-domain slots |
| Pixabay | Pixabay Content Licence | None required | Medium | Quick filler, niche subjects, illustrations |
| Burst | Shopify's free-commercial terms | None required | Medium | Commerce/product contexts |

Automated-fetch status recorded honestly: Unsplash 401, Pexels/Openverse/Pixabay 403 to unauthenticated bots (2026-11-25) — use official APIs (all three offer one) or interactive browsing, never block circumvention.

## 5. Practical workflow

1. **Art direction first** (from the project's direction): mood, palette temperature, subject families, ratio needs — written down before searching ([Image selection](../imagery/image-selection.md) §5).
2. **Search with scene specificity**, not abstractions: "barista pouring latte art side light" beats "coffee".
3. **Collect 3–5 candidates per slot**, evaluate against the criteria in [acquisition-workflow.md](acquisition-workflow.md) §5 (composition, subject placement, lighting, colour compatibility, crop, ratio, resolution, relevance).
4. **Check the licence page of the chosen source at integration time** (it is a volatile fact) and record the manifest entry ([licensing-and-provenance.md](licensing-and-provenance.md)).
5. **Treat the family**: apply the project's treatment (grade, overlay, crop grammar) so five sources read as one brand ([Image treatment](../imagery/image-treatment.md)).
6. **Optimise at integration**: modern formats, `srcset`, lazy loading ([../frontend-engineering/performance.md](../frontend-engineering/performance.md) §5.1).

## 6. Common mistakes

- **Assuming "free" means "any licence"** — each source's terms differ and change; the licence page is read at integration, every project.
- **Generic hero stock** — the handshake/whiteboard skyline photo family; specific scene searches and honest curation are the cure ([../evaluation/ai-design-failures.md](../evaluation/ai-design-failures.md) §6).
- **One photographer's catalogue ignored** — browsing a single strong photographer's work buys family coherence for free.
- **No manifest** — the photo ships, nobody remembers the source; provenance is recorded at download time.
- **Treating five sources' output as one family** — without a shared treatment, mixed-source imagery reads as a collage of brands.

## 7. Evaluation checklist

- [ ] Art direction written before searching.
- [ ] Candidates evaluated per slot against the nine criteria, not picked first-hit.
- [ ] Current licence page of the chosen source read at integration; manifest entry recorded (URL, creator, licence, date).
- [ ] Identifiable-person images checked against sensitive-use limits.
- [ ] Family treatment applied across all photography on the project.
- [ ] Optimisation applied (format, sizes, lazy loading) before ship.

## 8. Related topics

- [Image selection](../imagery/image-selection.md) — the slot-level decision.
- [Image treatment](../imagery/image-treatment.md) — the family treatment.
- [Image rights](../imagery/image-rights.md) — the full rights theory.
- [Illustrations](illustrations.md) — the drawn alternative to photography.
- [Licensing and provenance](licensing-and-provenance.md) — the manifest and licence table.
- [Acquisition workflow](acquisition-workflow.md) — the nine-step procedure these files serve.

## 9. References

- Unsplash Licence — https://unsplash.com/license [accessed 2026-11-25 (via site status + search verification of terms)]
- Pexels Licence — https://www.pexels.com/license/ [search-verified, accessed 2026-11-25]
- Openverse documentation — https://openverse.org/about/ [search-verified, accessed 2026-11-25]
- Pixabay Content Licence — https://pixabay.com/service/license-summary/ [search-verified, accessed 2026-11-25]
- Shopify Burst terms — https://www.shopify.com/stock-photos [accessed 2026-11-25]
- Licence terms are volatile facts: every integration re-reads the live page. The access statuses in §3 were measured on 2026-11-25 from this sandbox; see [../references/frontend-phase-sources.md](../references/frontend-phase-sources.md).
