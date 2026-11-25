# Microinteractions

## 1. What is it?

The quiet layer of interface motion and feedback: the small, single-purpose interaction moments — hover lifts, press states, toggle switches, like animations, pull-to-refresh, form validation shakes, notification pulses, and their sonic counterparts — defined by Dan Saffer's model (trigger → rules → feedback → loops and modes, 2008). The library's interaction-design layer ([../ui-ux/interaction-design.md](../ui-ux/interaction-design.md)) covers feedback timing and latency budgets; this file covers the *design* of the small moments themselves, including UI sound — the most neglected feedback channel, with the verified sources (UISFX, Bencho, Mixkit) catalogued in [../assets/sound.md](../assets/sound.md).

## 2. Why does it matter?

Microinteractions are where users actually live: a product is thousands of small moments and a handful of page loads. They carry disproportionate perceived quality — the toggle that snaps with a satisfying arc, the button that presses, the input that shakes politely — and they are the cheapest craft available: each is a few lines of CSS or a small component. Done badly they are equally visible: dead buttons, silent failures, hover states missing on touch, sounds that fire on every keystroke. The distinction between a product that feels considered and one that feels templated is mostly made here, at the scale of milliseconds and pixels.

## 3. Core principles

**Principle 1 — One purpose per microinteraction.** Each small moment communicates one thing (enabled, pressed, accepted, rejected, loading, count changed). If a hover animation also serves as a status signal, split it.

**Principle 2 — Trigger → rules → feedback.** From Saffer's model: what starts it, what logic governs it, what the user perceives. All three must be designed — the commonest amateur failure is a trigger and a rule with no feedback (clicking a button that gives nothing back).

**Principle 3 — States are the alphabet.** Every interactive element has default, hover, focus-visible, active/pressed, disabled, loading and (where relevant) error/success states — each designed, distinguishable, and token-driven. The state matrix is checked in visual QA ([../evaluation/website-visual-qa.md](../evaluation/website-visual-qa.md) §5.4); this file designs what those states *feel* like.

**Principle 4 — Sound is feedback, not garnish.** UI sound works when it is sparse, short (<200 ms), semantically consistent (success always the same sound) and user-controlled. It is the feedback channel for eyes-busy moments and the signature layer for brands that use it consistently — and the first thing to strip entirely for a quiet product.

**Principle 5 — Opt-out is mandatory for sound; motion-reduced is mandatory for motion.** A mute toggle (persisted), autoplay blocked on audio beyond tiny feedback blips, and `prefers-reduced-motion` coverage — both floors are non-negotiable.

## 4. How it works — the anatomy of good microinteractions

**Trigger:** user action (hover, press, drag, scroll past threshold) or system state (upload finished, message received). **Rules:** what happens, under what conditions, how it disambiguates (a long-press vs a tap; a drag vs a swipe). **Feedback:** the perceptible response — visual (state change, motion, count), haptic (mobile), sonic (blip). **Loops and modes:** is it one-shot or continuous; does it behave differently in a special mode (long lists, offline).

**The response-time ladder** (from [../ui-ux/interaction-design.md](../ui-ux/interaction-design.md) §5.1, applied to micro scale): instant (<100 ms — press states), fast (100–400 ms — toggles, snaps), moderate (400 ms–1 s — loading shimmer on a card), slow (>1 s — progress, staged feedback). The microinteraction must match the actual latency it covers; a 2-second operation with a 150 ms feedback looks broken, not quick.

**The press physics:** down = scale ~0.97 or translate 1 px + shadow shrink; up = return with ease-out. Underlines draw on hover; cards lift 1–2 px; images zoom 1.02–1.03 inside a fixed frame ([Interface styles](../visual-styles/interface-styles.md) — the hover vocabulary). Icons and labels never move independently of their containers.

## 5. Practical application

**5.1 The standard set.** Every product ships these: button press (visual), link hover (underline/color draw), card hover (lift + image zoom), toggle (animated thumb + track colour), checkbox/radio (tick draw), input focus (border/ring transition), validation error (shake ≤2 iterations + inline message), success confirmation (checkmark draw + optional soft blip), copy-to-clipboard (icon swap + tooltip), loading (skeleton or spinner matched to expected latency), pagination/carousel controls (state + motion), like/favourite (one-draw heart/star, count ticks), pull-to-refresh (mobile), toasts (enter/snooze/exit choreography).

**5.2 Sound design for UI.** Rules from professional practice and the sources in [../assets/sound.md](../assets/sound.md): one consistent family of sounds (same synthesis character); <200 ms per blip; -20 dB under media content; mapped to semantics (success, error, notification, toggle); never on every keystroke; never looping; mute toggle persisted in preferences; respect OS/browser autoplay policies; provide silent mode by default in productivity contexts. Implementation: preloaded short buffers (Web Audio) or `new Audio()` with `preload='auto'`; debounce triggers; total library <100 KB — sourced from UISFX (open-source, purpose-built for interfaces), Bencho's interaction library (182 sounds), or Mixkit's free SFX ([../assets/sound.md](../assets/sound.md) carries licences).

**5.3 Haptics (mobile web where supported).** `navigator.vibrate` (Android; iOS Safari does not expose it) for press and success moments — 10–20 ms taps; never for decorative loops.

**5.4 The no-JS baseline.** Press, hover, focus states work in pure CSS. Anything requiring JavaScript (sound, haptics, complex counters) must fail silently to a still-communicative state — the visual press state alone already communicates.

## 6. Decision framework

For each candidate microinteraction: **(1) Does it communicate state change?** — if purely decorative, cut. **(2) Is it in the standard set or genuinely novel?** — prefer the standard set; novelty is budgeted like any hero moment. **(3) Does it have all its states?** — hover without active is incomplete. **(4) Does it respect the latency it covers?** **(5) Is it interruptible and reduced-motion safe?** **(6) If it makes sound: is it <200 ms, semantic, muted-by-default-able, and silent under reduced motion?**

Deliberately *skip* sound for: dense data-entry products, enterprise tools, accessibility-first contexts (unless opt-in), and anything with continuous audio already playing.

## 7. Examples

**Example 1 — a checkout microinteraction pass.** Pay button: press state + 400 ms→loading state with button spinner (matching true latency); success: checkmark draw + soft single blip (-22 dB) + haptic tap on Android; error: two-iteration shake on the failing field + inline message (never colour alone); all sounds muteable from the footer toggle, persisted. The pass adds ~40 lines of CSS and one 60-line sound module — and moves the flow's peak-end quality measurably ([../ux-psychology/design-laws.md](../ux-psychology/design-laws.md) §3.20).

**Example 2 — a like button done properly.** Trigger: tap. Rule: optimistic count update, one tap = one like, second tap un-likes. Feedback: heart path draws once (250 ms, ease-out, overshoot 1.05), count ticks up 4 px and settles; sound: single soft pop only if sounds are enabled; no confetti burst (novelty budget spent elsewhere). Interruptible: rapid taps debounce to consistent final state.

## 8. Common mistakes

- **Missing states** — hover designed, press forgotten, focus never; the state matrix is the alphabet and teams ship half of it.
- **Sound spam** — clicks on every keystroke, loops on hover; the fastest way to make users mute a product forever.
- **Decorative micro-moments** — bounces with no state meaning; motion without purpose ([Motion principles](motion-principles.md) §3).
- **Latency mismatch** — instant feedback on slow operations or slow feedback on instant ones.
- **Touch-hostile hovers** — hover-only affordances on touch devices; hover is progressive enhancement, never the only path to information.
- **Uninterruptible microanimations** — animations that swallow rapid taps; debounce and retarget.
- **Loud or looping audio** — autoplaying sound, no mute toggle, >200 ms blips.
- **Non-semantic sounds** — random sonic choices; the family must be consistent and mapped to meaning.

## 9. Evaluation checklist

- [ ] Every interactive element has its full state set (default/hover/focus-visible/active/disabled/loading).
- [ ] Each microinteraction communicates one state change; decorative-only ones removed.
- [ ] Press physics consistent product-wide (tokens for scale/translate/shadow).
- [ ] Feedback matches actual latency (ladder respected).
- [ ] Sound: <200 ms, one family, semantically mapped, muteable with persisted preference, silent under reduced motion, never on keystrokes, autoplay-safe.
- [ ] Haptics used sparingly where supported; never decorative.
- [ ] No-JS baseline communicates through CSS states alone.
- [ ] Rapid interaction (double taps, fast hover-through) lands in consistent states.
- [ ] Hover affordances have touch/keyboard equivalents.

## 10. Related topics

- [Interaction design](../ui-ux/interaction-design.md) — feedback timing, latency budgets, interruptible motion.
- [Motion principles](motion-principles.md) — the governing craft (duration bands, easing, hierarchy).
- [Assets: sound](../assets/sound.md) — UISFX, Bencho, Mixkit, Freesound: the sound sources and licences.
- [UI fundamentals](../ui-ux/ui-fundamentals.md) — component anatomy and the state model.
- [Website visual QA](../evaluation/website-visual-qa.md) — where the state matrix is verified.
- [Design laws](../ux-psychology/design-laws.md) — peak-end rule: why the final confirmation moment deserves the best microinteraction in the product.

## 11. References

- Saffer, D. (2013), *Microinteractions: Designing with Details* (New Riders) — the trigger/rules/feedback/loops-and-modes model; his earlier *Designing for Interaction* (2008) frames the interaction-design practice around it. [canonical]
- W3C, WCAG 2.2 — 2.2.2 (Pause, Stop, Hide) for any looping sound/motion; 1.4.1 (Use of Colour) bound by multi-channel feedback. [canonical]
- MDN, Web Audio API / HTMLAudioElement — implementation surface for UI sound. https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API [search-verified, accessed 2026-11-25]
- MDN, `navigator.vibrate` — haptics support surface. https://developer.mozilla.org/en-US/docs/Web/API/Navigator/vibrate [search-verified, accessed 2026-11-25]
- Duration and loudness figures are professional conventions of this library, not sourced laws.
