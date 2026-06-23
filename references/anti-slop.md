# Anti-slop: the tells, and restraint you can measure

The SKILL.md names the three AI-default *looks*. This goes one level lower: the
component-level reflexes that read as generated regardless of look, and how to
make "spend your boldness in one place" verifiable instead of aspirational.

## The reflexes to catch (don't ship these by default)

- **Inter / Roboto / Poppins / Space Grotesk by reflex.** Fine when the brief
  asks for them; never as the unexamined default. Pick a face for a reason.
- **Purple/blue gradient** on the primary background, or gradient text on a
  headline. The single most recognizable "AI made this" signal.
- **Everything centered.** A hero centered in a full-viewport column, then the
  next section centered, then the next. Asymmetry and a real grid read as
  designed.
- **Uniform border-radius** (12–16px) on every card, button, input, and image.
  Vary it or commit to one radius *intentionally* (incl. 0).
- **The SaaS-blue CTA** (`#3B82F6`) on white. A default, not a choice.
- **Glassmorphism + soft drop-shadow on everything** to fake depth. Depth comes
  from spacing and hierarchy first.
- **Card grid of identical cards nested in more cards.** Structure should come
  from spacing and rhythm, not from boxing every element.
- **Emoji as section icons**, "Welcome to our platform" copy, three feature
  cards with a generic line-icon each.

## The production tells (the specific patterns models reach for)

These came out of real LLM landing-page tests: the signatures the model defaults
to when it tries to "look designed." Each is a default dressed as a choice. Ban
them unless the brief explicitly earns one.

- **Em-dash (`—`) and en-dash (`–`) — the #1 tell. Zero in shipped page copy.**
  It is the model's signature stylistic crutch and the most reliable giveaway in
  production tests. There is no "sparingly" allowance. Replace with a period, a
  comma, parentheses, or a colon; or split into two sentences. Applies
  everywhere a user reads: headlines, eyebrows, pills, body, quotes, attribution,
  captions, buttons, alt text. The only dashes left on the page are the regular
  hyphen (compounds, `2018-2026` ranges) and the math minus. Audit before ship;
  a single visible `—` fails the check. (This rule is about *output*, the page
  you ship — not about prose in docs like this one.)
- **An eyebrow above every section.** The small uppercase wide-tracking label
  (`SELECTED WORK`, `THE HARDWARE`) over every headline produces the exact same
  templated rhythm on every AI page. Cap it at roughly **one per three
  sections** (the hero counts as one); count the instances mechanically. The
  headline usually carries the section alone, and the section's place on the
  page already categorizes it.
- **Generic step labels** ("Stage 1 / Phase 01 / Step 3 / Pass One"). The step's
  actual content is the label. Use the verb or the name directly (Install,
  Briefing), never "Stage 1: Install".
- **Section-number eyebrows** ("001 · Capabilities", "06 · how it works",
  "No. 01"). If the reader can count, the number adds nothing.
- **Decorative status dots** before nav items, list rows, or badges. A colored
  dot earns its place only when it signals real state (a live server, an open
  slot), and then one per section at most. Zero by default.
- **A decoration text strip at the hero bottom** ("BRAND. MOTION. SPATIAL.",
  "DESIGN · BUILD · SHIP") — agency-portfolio cliché. Only if the strip carries
  real navigable links or real status.
- **Div-based fake product UI** — a fake dashboard, terminal, or task list built
  from styled `<div>`s to simulate a screenshot. The #1 structural tell. Use a
  real screenshot, a generated image, a real mini-component, or skip the preview.
- **Pills/labels overlaid on images** ("Plate · 02", "Field notes — journal").
  Let the image speak, or caption directly below it (outside the image).
- **Version labels and footers on marketing pages** ("v0.6 BETA" hero eyebrow,
  "Build 0048" / "last sync 4s ago" footer). Devtool fixtures, not landing copy.
- **Locale / time / weather strips** ("Lisbon 14:23 · 18°C"). Decoration unless
  the brand is genuinely place- or timezone-driven. A plain footer address is fine.
- **Scroll cues** ("Scroll ↓", "Scroll to explore", animated mouse-wheel). The
  reader is looking at the hero; they know scrolling exists.
- **The middle-dot `·` as the universal separator** ("foo · bar · baz · qux").
  Ration it to ~1 per metadata line; prefer line breaks, hairlines, or columns.
- **`border-t` + `border-b` on every row** of a long list or spec table. The
  laziest layout. For more than ~5 items, group into 2-3 chunks with sparse
  dividers, or move to a card grid / tabs / accordion / scroll-snap.
- **Decorative hairline or crosshair grid** drawn only to make the page "feel
  designed." Use rules only when they organize real content.
- **Three identical feature cards in a row** (or any N-identical-card grid,
  repeated section after section). Vary the rhythm: a hero cell plus smaller
  ones, a 2-column zigzag, an asymmetric grid, a horizontal scroll.

## Copy tells (the words give it away too)

- **Fake-precise numbers** ("92%", "4.1×", "5.8 mm") that aren't from real or
  explicitly-labeled mock data. Don't fake precision the brand doesn't claim.
- **Generic names and brands** (John Doe, Sarah Chan; Acme, Nexus, SmartFlow).
  Use specific, realistic, locale-appropriate names and invented brands that
  sound real.
- **Filler verbs** (Elevate, Seamless, Unleash, Next-Gen, Revolutionize) and
  performative-craftsman labels ("Field notes", "Quietly trusted by", "From the
  bench"). Concrete verbs and plain functional labels only.
- **Self-audit pass:** before shipping, re-read every visible string. Flag
  anything grammatically broken, with an unclear referent, or cute-but-wrong
  wordplay, and rewrite it as a plain functional sentence. Boring beats clever-wrong.

## The three Locks (consistency, audited before ship)

A page has exactly one of each. Drifting mid-page reads as broken, not designed.

- **Color lock** — one accent, used identically across every section. A
  warm-grey page does not grow a blue CTA in section 7.
- **Shape lock** — one corner-radius system (all-sharp, all-soft, or all-pill),
  or a documented rule (`buttons pill, cards 16px, inputs 8px`) followed
  everywhere. Round buttons in a square layout is broken.
- **Theme lock** — one theme (light, dark, or auto) for the whole page. No
  light-warm section sandwiched between dark ones, unless it's a single
  deliberate color-block device with a real transition.

## Hero discipline

The hero is a single moment, not a feature list, and it fits the initial
viewport: headline ≤ 2 lines, subtext ≤ ~20 words and ≤ 4 lines, the primary CTA
visible without scrolling, top padding ≤ ~6rem so the content doesn't float
halfway down. Max four text elements total (an eyebrow *or* brand strip; the
headline; the subtext; the CTAs). Trust logos, taglines, pricing teasers, and
social-proof rows move to sections below. A four-line hero headline is a
font-size error, not a copy-length problem. If you can't state the value in 20
words, the value prop is unclear, not the rule too tight.

## Restraint you can measure

"Keep everything around the signature quiet" is checkable:

- **Color budget.** Primary/neutral ≈ 60–70% of the canvas, one accent ≤ ~15%,
  a rare tertiary ≤ ~5%. **Remove test:** desaturate the accent to gray — the
  design should still read as intentional. If it collapses, the color was
  carrying weight the structure should carry.
- **Type budget.** One display face (≤ 3 sizes), one body face, ≤ 3 weights in
  use, ≤ 2 line-lengths. More than that is usually indecision, not range.
- **Chanel test.** Before shipping, remove one element. If nothing breaks, it was
  decoration.
- **Convergence check.** Re-run the brief in your head as a generic prompt. If
  you'd arrive at the same palette/face/layout for *any* similar brief, you
  picked a default — change the part that converged and say why.

## Vanity to avoid in the build itself

Over-engineering reads as slop too: a "design system" defined but used once,
custom-built components for solved problems (use shadcn/Radix/established
primitives), one component abstracted on its first and only use, config longer
than the code it configures. Build the concrete thing; abstract on the second
real use.
