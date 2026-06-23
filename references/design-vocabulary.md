# Design vocabulary: named directions to choose between

AI frontends converge partly because the model reaches for "clean and modern"
every time — it lacks the words a designer uses to mean something specific. This
is a vocabulary to choose *from*, deliberately, during the brainstorm pass. Naming
the direction up front is what keeps a build from drifting back to the defaults.

These are starting points, not a menu to pick at random: choose the one the
*subject* earns, then push it fully (a half-committed direction reads as
generated). Often the strongest move is a dominant direction with one sharp,
contrasting accent.

## Directions (with the gist of each)

- **Neo-Swiss / International** — rigorous grid, restrained palette, razor
  alignment, type does the work.
- **Brutalist / raw** — exposed structure, system fonts, hard edges, zero
  decoration.
- **Editorial / magazine** — strong hierarchy, pull quotes, mixed column widths,
  print rhythm.
- **Monochrome high-contrast** — black/white only, hierarchy from scale and
  weight.
- **Duotone poster** — two-color system, bold overlays, graphic impact.
- **Bauhaus / constructivist** — primary colors, hard geometry, diagonals,
  agit-poster energy.
- **Maximalist** — dense, layered, confident clutter; needs elaborate execution.
- **Kinetic typography** — type as the hero: stretched, oversized, motion-led.
- **Cinematic noir** — moody shadows, spotlighting, grain, suspense.
- **Riso / print artifact** — limited inks, misregistration, grain, tactility.
- **Y2K / vaporwave / synthwave** — chrome gels, neon dusk, grid horizons, faux-3D.
- **Glitch / digital noise** — scanlines, chromatic offsets, compression
  artifacts.
- **Memphis / playful** — squiggles, confetti geometry, upbeat primary pop.
- **Art Deco / geometric luxe** — symmetry, gold accents, stepped forms.
- **High-fashion lookbook** — huge imagery, sparse type, generous negative space.
- **Museum / exhibition** — quiet authority, captions-as-design, vast whitespace.
- **Architectural blueprint** — hairlines, annotations, mono labels, technical
  grid.
- **Data dashboard / scientific** — dense, legible, tabular, function-forward.
- **Nordic calm / wabi-sabi** — muted naturals, soft contrast, restraint as the
  point.
- **Botanical apothecary / coastal / desert modern** — material- and
  place-driven palettes drawn from the subject's world.
- **Skeuomorphic / clay 3D / isometric** — tactile depth, soft shadows, modeled
  forms.

## Per-discipline moves (the impeccable.style lens)

Slop is disciplinary — fix it one axis at a time, the way a reviewer would call
each out:

- **Typeset** — real scale and contrast, a face chosen on purpose (see
  `typography.md`).
- **Colorize** — commit to a hue; clear WCAG; kill the purple-gradient default.
- **Layout** — rhythm from spacing, not a grid of identical cards.
- **Animate** — motion that conveys state and settles (see `motion.md`).
- **Bolder ↔ quieter** — push a timid design toward impact, or calm one that's
  shouting, without losing intent.
- **Distill** — ruthless subtraction; strip to the essence (the Chanel test in
  `anti-slop.md`).
- **Critique / audit** — score the result against hierarchy, type, color,
  spacing, motion, a11y; fix the worst dimension first.

## Calibrate the intensity (three dials)

A direction still needs a level. Before building, set three dials from the brief
so layout, motion, and density decisions are consistent instead of ad hoc. These
are judgment, not config: state the values you chose and why.

- **Variance** (symmetry → asymmetry): how far the layout departs from a tidy
  centered grid. Low for trust-first / public-sector / editorial-calm; high for
  agency / Awwwards / experimental.
- **Motion** (static → cinematic): how much the page moves. Low for editorial
  and B2B-clean; high for premium-consumer and playful. "Motion claimed must be
  motion shown" — if you set it high, the page actually moves and degrades
  cleanly; if you can't ship that, set it low and nail a clean static page.
- **Density** (airy → packed): whitespace versus information. Low for luxury /
  gallery; high for utility / data, where numbers go mono and cards give way to
  hairline rules.

Rough presets: minimalist/Linear-clean = low/low/low · premium consumer =
mid/mid/low · agency/experimental = high/high/low · public-sector = low/low/mid.
On a redesign, read the existing site's dials first and move from there.

## Pattern vocabulary (names to design with, not a menu to sample)

Knowing the names lets you reach for the right structure and talk about it. Pick
the one the subject earns; don't stack three scroll gimmicks because they exist.

**Hero paradigms** — asymmetric split (text one side, asset the other),
editorial manifesto (type-only poster), media-mask (type as a window onto
video), kinetic-type (animated type is the visual), curtain-reveal, scroll-pinned.

**Navigation** — single-line bar (the default, ≤ 80px), dock magnification,
magnetic button, dynamic-island status pill, mega-menu reveal. Keep it one line
at desktop or collapse to a sheet.

**Layout & grid** — bento (asymmetric tiles, exact cell count), masonry,
split-screen scroll, sticky-stack, broadsheet hairline grid. Vary the layout
family per section; no family appears twice (`anti-slop.md`).

**Cards & surfaces** — parallax tilt, spotlight border, glass panel (with real
inner refraction, not just blur), bordered-not-boxed (group with `divide-y` and
space instead of a card).

**Scroll animation** — sticky-stack, horizontal-pan hijack, zoom-parallax,
scroll-progress path, sequence-scroll. Each needs a one-sentence reason
(`motion.md`); at most one marquee per page.

**Typography as hero** — kinetic marquee, text-mask reveal, scramble/decode on
load, circular text path, gradient-stroke. Powerful once; noise if repeated.

**Micro-interactions** — directional hover-fill (enters from the cursor's side),
ripple from click point, skeleton shimmer, animated line-draw, particle-burst on
success. Surprise beats `scale-105`; restraint beats a burst on every element.
