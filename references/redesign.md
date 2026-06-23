# Redesign: evolve what exists without breaking it

Reshaping an existing site is a different job from a greenfield build, and
misclassifying it is the biggest source of bad redesign output. A greenfield
brief wants invention; a redesign wants judgment about what to keep. Detect the
mode first, audit before touching, and change the visual layer without
disturbing the things people and search engines depend on.

## Detect the mode (first action)

- **Greenfield** — no existing site, or a full overhaul is approved. Use the
  full judgment in SKILL.md from a blank page.
- **Redesign, preserve** — modernise without breaking the brand. Audit first,
  extract the brand tokens, evolve gradually.
- **Redesign, overhaul** — a new visual language over existing content. Treat
  visuals as greenfield, but preserve the content and information architecture.

If it's ambiguous, ask exactly once: "Should this preserve the existing brand,
or are we starting visually from scratch?"

## Audit before touching

Document the current state before proposing anything:

- **Brand tokens** — primary and accent colors, type stack, logo treatment, radii.
- **Information architecture** — page tree, primary nav, the key conversion paths.
- **Content blocks** — what exists, what's doing real work, what's filler.
- **Patterns to preserve** — signature interactions, a recognisable hero, the
  copy voice.
- **Patterns to retire** — the AI-slop tells (`anti-slop.md`), broken layouts,
  dead links, generic stock imagery, performance traps.
- **The current intensity** — read the existing site's variance, motion, and
  density. That reading is your starting point, not a default baseline.
- **SEO baseline** — ranking pages, meta titles, structured data, OG cards.
  **SEO migration is the number-one redesign risk.**

## Preserve deliberately

- **Don't change the information architecture** unless asked. Keep page slugs,
  anchor IDs, and primary nav labels stable for SEO and muscle memory.
- **Extract brand colors before applying the palette judgment.** A brand that is
  already purple stays purple; the anti-default rule yields to the real brand.
- **Preserve the copy voice** unless a rewrite is requested. Visual
  modernisation is not a content rewrite.
- **Honor existing accessibility wins** — don't regress focus states, alt text,
  keyboard nav, or contrast.
- **Respect analytics** — don't rename buttons, form fields, or section IDs that
  downstream tracking depends on.

## Modernisation levers (in priority order)

Apply in order, and stop when the brief is satisfied. Earlier levers give the
most visual lift per unit of risk.

1. **Typography refresh** — the biggest visual lift for the least risk.
2. **Spacing and rhythm** — increase section padding, fix the vertical rhythm.
3. **Color recalibration** — desaturate, unify the neutrals, keep the brand accent.
4. **Motion layer** — add interaction-appropriate micro-motion to existing
   components (`motion.md`).
5. **Hero and key-section recomposition** — restructure the top of the funnel
   using the pattern vocabulary (`design-vocabulary.md`).
6. **Full block replacement** — only when a block is genuinely unsalvageable.

## Decide the scope

- IA, content, and SEO are sound → **targeted evolution** (levers 1 to 4). Around
  70% of the value at 40% of the risk.
- The visual debt is structural (broken IA, no design system, broken mobile) →
  **full redesign** with strict content preservation.
- The brand itself is changing → **greenfield**.

## Never change silently

These break trust, SEO, or tracking. Change them only with explicit approval:

- URL structure and route slugs.
- Primary nav labels.
- Form field names and order (breaks analytics and autofill).
- The brand logo or wordmark.
- Existing legal, consent, or cookie copy.
