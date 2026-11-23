# Image rights

## 1. What is it?

Image rights is the set of permissions, restrictions and obligations attached to every image a design project uses: who owns it, what uses are licensed, what attribution or releases are required, and what documentation proves all of this. Designers do not need to become lawyers, but they do need to read a licence, classify a use case, and keep records — because the difference between "saw it on the internet" and "cleared for this use" is the difference between a shipped design and a takedown, an invoice or a court letter.

This file covers the practical map: how stock licences work (royalty-free versus rights-managed, editorial versus commercial), what the Creative Commons licence family grants, what public domain means, when model and property releases are needed, the unsettled rights questions around AI-generated imagery, and the documentation habits that keep a library legally auditable. The sourcing decisions these rights constrain are in [Image selection](image-selection.md); the AI-specific discussion is in [AI image generation](ai-image-generation.md).

## 2. Why does it matter?

Rights failures are design failures with legal consequences. A hero image used beyond its licence can force a re-shoot days before launch; an editorial-only photograph in a marketing campaign breaches the licence outright; a recognisable face without a model release can produce a claim from the person photographed; and since imagery is the most visible layer of a brand, rights errors are also public — brands have been publicly embarrassed by stolen or mislicensed images.

Rights also shape design freedom in ways teams forget until late: some licences forbid modification, which quietly invalidates the cropping, grading and duotone work described in [Image treatment](image-treatment.md); some require credit lines that need layout space; some restrict the industries or distribution volume a design may target. Checking rights at selection time — not at export — is what keeps options open.

Finally, the AI layer has made rights a moving target: platform terms differ from each other and change over time, training-data licensing is contested in active litigation, and purely AI-generated images are not copyrightable in the United States under the Copyright Office's March 2023 guidance [search-verified, URL in References]. This area must be treated as evolving: the summaries here were verified on 2026-11-23 and must be re-checked per project.

## 3. Core principles

**A licence is permission, not ownership.** Unless a contract says otherwise, using a licensed image grants specific rights for specific uses. The licence text — not the platform's marketing page, not folklore — defines what is allowed.

**The use case defines the licence class.** "Can I use this image?" is not answerable without the use: commercial versus editorial, print run size, modification, redistribution, territory and duration all change the answer. Classify the use first, then find a licence that covers it.

**Free to view is not free to use.** Every image has a copyright holder by default. The absence of a visible price or a watermark says nothing about permissions.

**Verify per source, per time.** Licences change: platforms restructure their terms, free platforms replaced older CC0-style terms with their own, and AI tools rewrite terms frequently. Record which version of which licence was relied on, and when.

**Document everything.** Provenance that is not written down does not exist. A rights log is cheap insurance and the audit trail clients and legal reviewers actually ask for.

**Synthesis note:** the frameworks in this file are standard professional practice (publishers, stock industry, Creative Commons); the specific licence terms cited are verified examples, not endorsements.

## 4. How it works

### 4.1 Stock licences: royalty-free versus rights-managed

The two dominant models of the stock industry:

| Model | How it works | Typical restrictions | Typical fit |
| --- | --- | --- | --- |
| Royalty-free (RF) | One-time payment (or subscription), then use across many projects without per-use fees | Usually no resale as-is, no standalone redistribution, limits on print runs or merchandise unless an "enhanced" tier is bought | Most brand, web and campaign work |
| Rights-managed (RM) | Price computed per use: territory, duration, print run, media, exclusivity | Each use negotiated; exceeding the scope breaches the licence | High-value campaigns needing exclusivity or precise control |

Most subscription stock platforms operate RF tiers plus an upgrade path. As a verified example, Shutterstock distinguishes Standard and Enhanced image licences plus a separate Editorial licence; its help centre describes the Enhanced tier as covering "Image use on merchandise you are selling", "Unlimited physical print runs" and removal of production-budget restrictions, states that both licences grant "perpetual use of the content you downloaded, even if you no longer have an active plan", and publishes indemnity caps of USD 250,000 for images and USD 25,000 for editorial under its licence agreement [search-verified, URLs in References]. The specific numbers belong to Shutterstock's agreement — the structural lesson is general: check what your tier actually covers before a print run, a merchandising idea or a big-budget campaign.

Free platforms are not licence-free, only price-free. Unsplash, for example, grants what its terms call "a very, very broad copyright license under the Unsplash License", and its licence page states that "attribution isn't required" though photographers appreciate it; the licence still forbids some uses (such as selling unaltered copies as stock or compiling them to replicate the service) [search-verified, URLs in References]. Read each free platform's own licence — they replaced older CC0-style practice with bespoke terms.

### 4.2 Editorial versus commercial use

A distinction most often expressed in stock licences:

- **Commercial use** promotes or sells something: advertisements, product packaging, websites and campaigns for an organisation, brand merchandise. It generally requires images cleared for that purpose — including releases for recognisable people and property.
- **Editorial use** illustrates news, commentary, education and criticism: magazine reportage, blog coverage of an event, textbooks. Editorial licences are cheaper or free, but typically forbid commercial use, require captions crediting source and photographer, and carry no releases — which is precisely why they cannot be reused in marketing.

The classic failure: a designer finds a striking event photograph available only under an editorial licence and uses it in the event's own marketing. The subject overlap makes it feel natural; the licence forbids it. When sourcing, filter to commercial-class imagery for anything a brand publishes about itself.

### 4.3 Creative Commons licences

Creative Commons publishes six licences plus a public-domain dedication, "listed from most to least permissive" [accessed, URL in References]:

| Licence | May distribute and adapt? | Commercial use? | Key conditions |
| --- | --- | --- | --- |
| CC BY | Yes | Yes | "Credit must be given to you, the creator" |
| CC BY-SA | Yes | Yes | Attribution + adaptations shared "under the same or a compatible license" (share-alike) |
| CC BY-ND | Adapted material: no — "copy and distribute the material... in unadapted form only" | Yes | Attribution; no derivatives |
| CC BY-NC | Yes | No — "Only noncommercial use of your work is permitted" | Attribution; noncommercial only |
| CC BY-NC-SA | Yes | No | Attribution, noncommercial, share-alike |
| CC BY-NC-ND | "copy and distribute the material... in unadapted form only, for noncommercial purposes only" | No | Attribution only, no changes |
| CC0 | The creator dedicating the work to the public domain | Yes | No attribution required (credit still courteous) |

Elements: **BY** = attribution, **NC** = noncommercial, defined as work "not primarily intended for or directed towards commercial advantage or monetary compensation", **ND** = no derivatives, **SA** = share-alike [accessed]. Two consequences matter for brand work. First, any NC licence is unusable for a commercial organisation's marketing, product or campaign imagery — a brand's website is commercial even when the brand is a charity. Second, ND licences forbid exactly the treatments (crops, grades, duotones) that [Image treatment](image-treatment.md) describes, and SA licences can impose licence obligations on the adapted work — an awkward inheritance for a brand asset.

**Attribution practice.** CC requires credit when the licence is a BY type; a conventional, robust format (professional practice, not a legal standard) names creator, title, source and licence, with links where the medium allows, for example: `Photo: Jane Doe — "Courtyard at dusk" (example.org/photo), licensed CC BY 4.0 (creativecommons.org/licenses/by/4.0)`. CC0 and most free-platform licences remove the requirement, but recording the source remains mandatory for your own log.

### 4.4 Public domain

Public-domain works carry no copyright (expired term, government dedication, or an explicit waiver such as CC0) and can be used, modified and redistributed without permission. Two cautions: first, confirming public-domain status is the designer's job — a work being old or free to view proves nothing; second, specific reproductions of public-domain works (a museum's scan of a painting) can carry their own terms or claims, so prefer the institution's stated terms. Public domain is the safest rights class available and the right default for historical imagery.

### 4.5 Model and property releases

A **model release** is the signed permission of a recognisable person in a photograph allowing commercial use of their likeness; a **property release** covers identifiable private property (buildings, artworks, designs). The professional convention, reflected in stock-industry practice: commercial and advertising uses of recognisable people require releases; editorial and informational uses generally do not (though sensitivity still applies). Practical rules:

- Commissioned shoots: the photographer or producer collects releases at the shoot; confirm they exist before the images enter the library.
- Stock: platforms mark released imagery; if a licence tier excludes releases, the image is editorial-only — do not use recognisable people from it commercially.
- Testimonials and "customers": besides releases, the people shown must actually be customers — the truthfulness rule from [Image selection](image-selection.md).
- Minors and sensitive contexts: expect stricter consent norms and legal review.

Release status belongs in the rights log next to the licence.

### 4.6 AI-generated imagery: the evolving area

AI imagery sits on four contested layers, all moving:

- **Platform terms differ.** As verified examples: OpenAI's Terms of Use assign output to the user — "you (a) retain your ownership rights in Input and (b) own the Output", with the warning that "output may not be unique and other users may receive similar output from our Services" [accessed]. Midjourney's Terms state "You own all Assets You create with the Services to the fullest extent possible under applicable law", condition ownership for companies over USD 1,000,000 in annual revenue on a Pro or Mega subscription, and note "If you upscale the images of others, these images remain owned by the original creators" [accessed]. Users also grant platforms broad licences over their content under both agreements. Re-read current terms per tool per project.
- **Copyrightability is limited.** Under the U.S. Copyright Office's March 2023 guidance, copyright requires human authorship; purely AI-generated material must be disclaimed on registration, and the *Zarya of the Dawn* review demonstrated that AI-generated images in a human-authored book are unprotectable even while the book's text and arrangement remain protected [search-verified, URL in References]. Human selection, arrangement and substantial editing can add protectable layers. Other jurisdictions treat the question differently and are actively reviewing it — treat "who owns this image?" as jurisdiction- and tool-dependent.
- **Training data is contested.** Generators are trained on vast image collections whose licensing is the subject of active litigation and public debate; outputs can resemble protected works. Mitigations in professional use: describe the properties you want rather than naming living artists, avoid generating trademarks and recognisable characters, and reverse-image-search distinctive outputs before shipping ([AI image generation](ai-image-generation.md), section 5.3).
- **Disclosure expectations are forming.** Where photorealistic synthetic imagery could be mistaken for documentation, disclose its origin — consistent with the truthfulness ladder in [Image selection](image-selection.md); platform policies and regulators are moving towards labelling requirements.

Because all four layers move, the standing rule is: AI rights status is a project-level verification task with a recorded date, never an assumption.

## 5. Practical application

### 5.1 What licence class do you need?

Ask, in order:

1. **Commercial or editorial?** If the image promotes an organisation, product or event → commercial-class imagery only.
2. **Recognisable people or property?** → releases required (confirmed in the log), or choose released/editorial-safe imagery.
3. **Will the image be modified?** → the licence must permit adaptation (excludes ND-type terms and some editorial licences).
4. **Reach and duration?** → check print-run, merchandising and perpetual-use coverage (RF Standard versus Enhanced tiers; RM scope).
5. **Exclusivity needed?** → RM with exclusivity, or commissioned photography; RF and generated imagery generally cannot guarantee exclusivity.
6. **Attribution obligations?** → plan credit lines into the layout where the licence demands them.

### 5.2 Documentation habits

Record, for every image that ships, at selection time:

```text
rights_log entry (one per shipped image):
  asset:        filename / asset ID
  role:         where used (hero, social set, article body)
  source:       platform or creator + URL of the image page
  creator:      photographer / illustrator / generator tool
  licence:      exact licence name + version (e.g. "Shutterstock Standard Image License",
                "CC BY 4.0", "Unsplash License", "Midjourney ToS 2026-05")
  verified_on:  2026-11-23
  release:      model/property release status (yes/no/N-A + reference)
  modifications: grade/crop/treatment applied (checked against licence limits)
  notes:        credit line if required; disclosure flag if synthetic
```

Keep the log in the project repository next to the assets, and carry it forward when files are exported, renamed or handed to other teams — provenance dies in export pipelines unless someone owns it.

## 6. Decision framework

Map the common situations to their minimum safe handling:

| Situation | Minimum handling |
| --- | --- |
| Marketing / campaign imagery | Commercial-class licence; releases confirmed; adaptation permitted |
| Editorial illustration of a topic | Editorial licence acceptable, with credit and caption |
| Image of recognisable people as "customers/staff" | Real people + signed releases, not sourced substitutes |
| Concept art, mood boards, internal exploration | Loosest classes acceptable; still log source |
| Public shipping of generated imagery | Tool terms checked and dated; disclosure where photorealistic; no generated trademarks |
| Adapting (grading, cropping, duotone) | Licence permits derivatives (excludes ND; SA propagates) |
| Historical / archival imagery | Confirm public-domain status or licence; prefer institutional terms |
| Credit required | Layout reserves credit space; credit text lives with the asset |

When two candidate images are equal in design terms, prefer the one with the simpler, better-documented rights trail — rights friction is a real cost.

## 7. Examples

- **The editorial trap.** A news photograph of a festival crowd, licensed editorial-only, looks perfect for next year's event campaign. The licence forbids commercial use — source commercial-class imagery or photograph the real crowd instead.
- **The NC surprise.** A beautiful diagram found via image search carries CC BY-NC. The organisation's website is a commercial context regardless of its mission, so the image is unusable there; it could be used in a genuinely noncommercial internal document.
- **The free-platform win.** A small event brand builds its library on Unsplash — free for commercial use, no attribution required — but still logs source URL and licence per image [search-verified], because the log is what survives team handover.
- **The generated hero.** An AI-generated dusk scene ships as an event hero: the log records the tool, terms version and date, the team confirms no real venue or person is claimed, and the disclosure note reads "synthetic image" in the asset metadata.
- **The release save.** A commissioned shoot's contact sheet includes a passer-by's face in a hero frame; the producer's release covers them. Without the release on file, the frame would have been unusable after the deadline.

## 8. Common mistakes

- **Assuming free-to-view means free-to-use.** Every image is copyrighted by default; only the licence grants use.
- **Editorial imagery in marketing.** The most common stock breach; filter to commercial class for brand publishing.
- **NC licences in commercial contexts.** A charity's fundraising site is still commercial use under CC's definition [accessed].
- **Modifying ND-licensed images.** Grading or cropping ND material breaches the licence; find an adaptable alternative.
- **Sourced faces as testimonials.** A licence permits use of a photo; it cannot turn a stranger into "our customer" ([Image selection](image-selection.md)).
- **Trusting stale terms.** AI platform terms and free-platform licences change; a screenshot from last year is not verification.
- **No log.** Rights that cannot be shown cannot be defended; provenance dies silently in exports.
- **Attribution as an afterthought.** Credit lines discovered at layout time get dropped; plan them with the asset.

## 9. Evaluation checklist

- Every shipped image has a rights-log entry with source, licence name and version, and verification date.
- Commercial uses are covered by commercial-class licences; editorial material never appears in marketing.
- Recognisable people and property in commercial uses have confirmed releases.
- Modification status (grade, crop, duotone) is checked against licence limits (no ND breaches; SA consequences understood).
- Attribution obligations have layout space and the credit text travels with the asset.
- AI-generated images record tool, terms version and date; photorealistic content is disclosed where it could be misread.
- Free-platform images were checked against that platform's own licence, not assumed CC0.
- Exclusivity needs (if any) are met by RM or commissioned work, not by RF or generated imagery.
- The log survives exports and handovers (stored with the assets, not in chat history).

## 10. Related topics

- [Image selection](image-selection.md) — where sourcing decisions happen and the truthfulness ladder is defined.
- [Image treatment](image-treatment.md) — the modification rights constrain.
- [AI image generation](ai-image-generation.md) — the workflow whose output needs clearing.
- [Photography](photography.md) — commissioned shoots where releases are collected.
- [Brand governance](../branding/brand-governance.md) — where rights documentation fits into managing the brand system.
- [Visual identity](../branding/visual-identity.md) — the system the cleared imagery belongs to.

## 11. References

- Creative Commons, "About CC Licences" (six licence types "listed from most to least permissive"; element definitions BY/NC/ND/SA; NC defined as work "not primarily intended for or directed towards commercial advantage or monetary compensation"; "some rights reserved" framing), https://creativecommons.org/share-your-work/cclicenses/. [accessed 2026-11-23]
- W3C WAI, "Images Tutorial" (supporting accessibility obligations on imagery), https://www.w3.org/WAI/tutorials/images/. [accessed 2026-11-23]
- OpenAI, "Terms of Use" (output ownership and non-uniqueness of output), https://openai.com/policies/row-terms-of-use. [accessed 2026-11-23]
- Midjourney, "Terms of Service" (asset ownership, revenue-threshold plan requirement, upscaling clause, licence granted to the platform), https://docs.midjourney.com/hc/en-us/articles/32083055291277-Terms-of-Service. [accessed 2026-11-23]
- Shutterstock, "Terms of Service & License Agreements" (Standard / Enhanced / Editorial licence structure; indemnity caps USD 250,000 images, USD 25,000 editorial), https://www.shutterstock.com/license. [search-verified]
- Shutterstock Help Center, "Shutterstock Standard Image License vs. Enhanced Image License" (perpetual use; enhanced tier covering merchandise and unlimited print runs), https://www.shutterstock.com/help/en/articles/10617089-shutterstock-standard-image-license-vs-enhanced-image-license. [search-verified]
- Unsplash, "License" (attribution appreciated but "isn't required") and "Terms & Conditions" ("a very, very broad copyright license under the Unsplash License"), https://unsplash.com/license and https://unsplash.com/terms. [search-verified]
- U.S. Federal Register, "Copyright Registration Guidance: Works Containing Material Generated by Artificial Intelligence" (March 2023), https://www.federalregister.gov/documents/2023/03/16/2023-05321/copyright-registration-guidance-works-containing-material-generated-by-artificial-intelligence. [search-verified — page bot-blocked at access time]
- U.S. Copyright Office, "Copyright and Artificial Intelligence", https://www.copyright.gov/ai. [search-verified]
- Model/property release conventions, RF/RM structure and attribution formatting are described as standard professional convention; this file is not legal advice — confirm current licence texts and jurisdiction-specific law per project.
