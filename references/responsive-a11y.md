# Responsive & accessibility: the quality floor, made concrete

The SKILL.md commits to "responsive down to mobile, visible keyboard focus,
reduced motion respected." These are the specifics that satisfy it.

## Responsive

- **Breakpoints:** XS 0–479 (small phone) · SM 480–767 (phone) · MD 768–1023
  (tablet) · LG 1024–1439 (laptop) · XL 1440+ (desktop). Let content, not
  devices, decide where a layout actually breaks.
- **Design mobile-first**, then add breakpoints as the content needs room.
- **Test at:** 375, 390, 768, 1024, 1280+. Nothing overflows, overlaps, or
  reflows into nonsense; long words/code blocks scroll rather than break layout.
- **Fluid type** with `clamp()` so headings scale between breakpoints (see
  `typography.md`).
- **Mobile and desktop get different layouts, not one scaled.** A data table is a
  table on desktop and a stack of cards on mobile; a horizontal timeline becomes
  a vertical list. Switch with `hidden md:block` / `md:hidden`, not with a single
  layout that squeezes.

## Component structure for responsiveness (orchestrator + viewport layouts + skeleton)

When a screen's mobile and desktop forms genuinely differ, give it four parts so
each stays single-purpose, instead of one component branching on width inline:

- **`XContent` — the orchestrator.** Owns the data (its own fetch/hook, never
  prop-drilled), and decides what to render: the skeleton while loading, an empty
  state when there's nothing, an error path, and otherwise the layout. It holds no
  layout markup of its own beyond mounting `<XDesktop>` and `<XMobile>`.
- **`XDesktop`** (`hidden md:block` / `md:flex`) — the desktop layout.
- **`XMobile`** (`md:hidden`) — the genuinely different mobile layout (cards,
  stacked, bottom-sheet), not the desktop one shrunk.
- **`XSkeleton`** — the loading shell in the *shape* of the content, rendered by
  the orchestrator. It mirrors both forms (a desktop-shaped skeleton in the
  `md:block` branch, a mobile-shaped one in the `md:hidden` branch), so the page
  never flashes blank or drops a spinner where a view belongs.

```tsx
export function XContent() {
  const { data, isLoading } = useGetX();           // orchestrator owns the data
  if (isLoading || !data) return <XSkeleton />;    // loading → shaped skeleton
  if (data.items.length === 0) return <XEmpty />;  // empty → invitation to act
  return (
    <>
      <XDesktop data={data} className="hidden md:block" />
      <XMobile  data={data} className="md:hidden" />
    </>
  );
}
```

Split only where the two layouts truly diverge. When plain responsive utilities
already do the job (a grid that reflows `grid-cols-1 md:grid-cols-3`, a header
that wraps), keep one component and skip the split: an invented `XDesktop` /
`XMobile` that render nearly the same markup is just duplication. The test is
"would a designer draw mobile and desktop differently here?" If yes, split; if
it's the same layout reflowing, don't.

## Accessibility (WCAG AA as the floor)

- **Contrast:** ≥ 4.5:1 for body text, ≥ 3:1 for large text and meaningful
  graphics/icons. The accent must clear this against its background — pretty but
  illegible is a fail.
- **Touch targets** ≥ 44×44px; add `touch-action: manipulation` to drop the
  300ms tap delay.
- **Keyboard:** every interactive element reachable by Tab in logical order,
  with a *visible* focus ring (don't `outline: none` without a replacement). Use
  `:focus-visible` for a ring only on keyboard focus.
- **Semantics:** real `<button>`/`<a>`/`<nav>`/`<main>`/headings before ARIA;
  add `aria-label`/`role` only where semantics fall short. Every input has a
  label.
- **Motion:** honor `prefers-reduced-motion` (see `motion.md`).
- **States:** design the empty, loading, and error states too — an empty screen
  is an invitation to act, an error says what went wrong and how to fix it.

## A 60-second self-audit before shipping

Hierarchy reads at a glance · spacing rhythm is consistent (no 1–2px drift) ·
alignment holds to the grid · type scale is honored · color budget respected
(see `anti-slop.md`) · focus states visible · contrast passes · 320px mobile
looks intentional, not squeezed. Screenshot it — a picture catches what reading
the code won't.
