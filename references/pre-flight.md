# Pre-flight: the last filter before you call it done

Judgment built the page; this catches the reflexes judgment misses under
deadline. Run it as a real pass over the rendered result, not from memory. If a
line can't be honestly ticked, the page isn't done. The point isn't ceremony,
it's that each item is a tell that survives good intentions.

## Identity and consistency
- **Design read stated** — one line naming the subject, audience, and the page's
  one job, declared before the build (not reverse-engineered after).
- **Color lock** — one accent, identical across every section (`anti-slop.md`).
- **Shape lock** — one radius system, applied everywhere.
- **Theme lock** — one theme for the whole page; no section inverts mid-scroll.
- **Convergence check** — the palette/face/layout wouldn't fall out of *any*
  similar brief. If it would, the converged part got changed and you can say why.

## Copy (the fastest tells to ship by accident)
- **Zero em-dashes (`—`) and en-dashes (`–`)** anywhere a user reads. Audit the
  whole page; one visible dash fails (`anti-slop.md`).
- **Every visible string re-read** — nothing grammatically broken, no unclear
  referent, no cute-but-wrong wordplay, no filler verbs (Elevate / Seamless).
- **Names and numbers are real or labeled mock** — no John Doe, no Acme, no
  fake-precise "92%" presented as fact.
- **One label per intent** — "Get started" / "Try free" / "Sign up" are the same
  button; pick one wording and use it in nav, hero, and footer.

## Hero and structure
- **Hero fits the viewport** — headline ≤ 2 lines, subtext ≤ ~20 words and ≤ 4
  lines, primary CTA visible without scroll, top padding ≤ ~6rem, ≤ 4 text
  elements (`anti-slop.md`).
- **Eyebrow count ≤ ceil(sections / 3)** — count the uppercase micro-labels
  above headlines mechanically; the hero counts as one.
- **At least ~4 different layout families** across the page — no two sections
  share the same shape; no 3+ consecutive image+text zigzags.
- **No N-identical-card grids** repeated; bento/feature grids have rhythm and
  exactly as many cells as there is content (no empty tile).
- **Long lists (> ~5 items) use the right component** — grouped chunks, cards,
  tabs, or scroll-snap, not a default `<ul>` with a hairline under every row.

## The production tells (scan for each — `anti-slop.md`)
- No section-number eyebrows, no generic step labels ("Stage 1 / Phase 01").
- No decorative status dots, no hero decoration strip, no scroll cues.
- No version labels/footers, no locale/time/weather strips on a normal brief.
- No pills overlaid on images, no div-based fake product screenshots.
- The `·` is rationed; no `border-t`+`border-b` on every row.

## Visual assets
- **Real images** used (generated, real, or clearly-labeled placeholder slots),
  not pure-text "minimalism" or hand-rolled decorative SVG illustrations.
- **Logo walls** sit under the hero, are logos only (no category labels), and
  render in both themes.
- **Icons** from one library, consistent stroke width, none hand-drawn.

## Motion and interaction
- **Motion is motivated** — each animation conveys hierarchy, sequence,
  feedback, or a state change; none is there because it "looked cool."
- **Motion claimed = motion shown** — if the direction calls for motion, the
  page actually moves (and degrades cleanly); if it can't ship working, drop to
  static rather than half-build it.
- **One orchestrated moment** beats scattered effects; at most one marquee.
- **Reduced motion** honored; no `window.addEventListener('scroll')` driving
  state (use `useScroll` / ScrollTrigger / IntersectionObserver / CSS).

## Quality floor (don't announce it, just hit it)
- **Contrast** — every CTA, label, placeholder, and focus ring passes WCAG AA
  against its actual background. No white-on-white, no CTA text that fails.
- **No CTA label wraps** to two lines at desktop. Nav fits one line, ≤ 80px tall.
- **Both themes tested** in the browser, not just one.
- **Responsive to mobile** — high-variance layouts collapse to a single column;
  `min-h-[100dvh]`, never `h-screen`, for full-height sections.
- **States present** — loading (skeleton in the final shape), empty (composed,
  shows how to populate), error (inline, specific).
- **Keyboard focus visible**, `useEffect` animations cleaned up, z-index sane.
