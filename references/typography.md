# Typography: the craft details that separate set type from default type

The SKILL.md says type carries the page's personality. These are the concrete
settings that make it read as *set* rather than dropped in.

## Scale, measure, rhythm

- **Scale by ratio**, not by eyeballing: ×1.25 (calm) or ×1.333 (dramatic). Keep
  the steps consistent across the page.
- **Measure (line length):** 45–90 characters, ~65 ideal. Use `max-width: 65ch`,
  not a pixel guess. Too-wide body text is a slop tell.
- **Line-height:** body 1.4–1.6; display tighter, 0.9–1.1 (tightness adds drama).
- **Fluid sizing** for display: `clamp(2rem, 5vw, 4rem)` so the hero scales
  without breakpoints.

## OpenType settings that should be on

```css
body { font-feature-settings: "kern" 1, "liga" 1;
       text-rendering: optimizeLegibility; }
```

- **Kerning + ligatures** on for body and display.
- **Real small caps** via `font-variant-caps: small-caps` (needs a font with the
  `smcp` feature) — never fake them by scaling capitals.
- **Tracking on ALL CAPS:** add `letter-spacing: 0.05em`–`0.12em`. Caps set at
  0 tracking read as cramped.
- **Tabular numbers** for data/tables: `font-variant-numeric: tabular-nums`.

## Correct characters (a quiet but real tell)

Use the real glyphs, not ASCII stand-ins: `"" ''` (curly quotes), `…` ellipsis
(not `...`), `×` not `x`, `→` not `->`. In JSX text, a literal `'` typed as `’`
renders the escape literally; use the real UTF-8 character in the source, or
`{'’'}`, or an HTML entity (`&rsquo; &ldquo; &hellip;`).

**Dashes are the exception to "use the real glyph."** The em-dash (`—`) and the
en-dash (`–`) are the number-one AI tell and are banned from shipped page copy
(`anti-slop.md`): restructure the sentence instead (period, comma, parentheses,
colon). For ranges use a plain hyphen (`2018-2026`), not an en-dash. The only
dash on the page is the regular hyphen.

## Pairing and emphasis

- Pair a characterful **display** face (used with restraint) with a neutral
  **body** face; add a **utility/mono** face only if data or captions need it.
- Don't reach for the same families you'd use on any project (see
  `anti-slop.md`). Inter / Roboto / Poppins / Space Grotesk as the unexamined
  default is a tell; pick a face for a reason.
- **Pairings to know:** Geist + Geist Mono · Satoshi + JetBrains Mono · Cabinet
  Grotesk + Inter Tight · GT America + IBM Plex Mono · a sans display (Neue
  Montreal, GT Walsheim, Söhne Breit) + a humanist body.
- **Emphasis: bold *or* italic of the SAME family, not both, never a different
  family.** Injecting a random serif word into a sans headline to add interest is
  amateur. In serifs italic is the gentle emphasis; in sans prefer bold (sans
  italics barely register). The scale carries the weight, not a font swap.

## Serif discipline (the single most-tested tell)

"This brief feels creative / premium / editorial, so reach for a serif display"
is the most reliable AI tell in production rounds. Serif is *very discouraged as
a default*. It is justified only when the brand brief literally names a serif, or
the family is genuinely editorial / luxury / publication / heritage AND you can
say why this specific serif fits this specific brand. For creative agencies,
design studios, modern brands, premium consumer, portfolios, lifestyle: default
to a **sans display** (Neue Montreal, GT Walsheim, Cabinet Grotesk Display, Inter
Display, Söhne Breit). Sans display is not boring, it is the default the way
black is the default in fashion.

- **Banned as defaults: Fraunces and Instrument Serif** (the two LLM-favorite
  display serifs). Their appearance is itself the tell.
- **If a serif is genuinely earned,** rotate from a wider pool and don't reuse the
  same one across consecutive projects: PP Editorial New, GT Sectra, Reckless
  Neue, Tiempos Headline, Recoleta, Canela, Domaine Display, Saol Display, EB
  Garamond, Cormorant Garamond.

## Italic descender clearance (audit before ship)

When display italic carries a descender letter (`y g j p q`), `leading-none` /
`leading-[1]` clips it. Use `leading-[1.1]` minimum and add `pb-1`/`mb-1` reserve
on the wrapping element. Audit every italic word in a display headline.
