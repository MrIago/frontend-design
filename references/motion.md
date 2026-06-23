# Motion: values, not vibes

The SKILL.md says motion should serve the subject and that scattered effects read
as generated. When motion *is* called for, these are the concrete values that
make it feel physical instead of random.

## Easing — pick by what's happening

```
entering   ease-out      cubic-bezier(0, 0, 0.2, 1)      decelerate in
exiting    ease-in       cubic-bezier(0.4, 0, 1, 1)      accelerate out
moving     ease-in-out   cubic-bezier(0.4, 0, 0.2, 1)    state change
playful    spring/back   cubic-bezier(0.34, 1.56, 0.64, 1)   1 overshoot, settles
loops      linear        spinners / marquees only
```

Default to ease-out for almost everything; reserve spring for one playful moment.
Nothing should bounce repeatedly or spring past its mark and stay there.

## Duration — by weight, not taste

- Lightweight (icon, badge, hover): ~150ms
- Standard (card, panel, dropdown): ~300ms
- Weighty (modal, page transition): ~400–500ms

Quick reference: button press 100ms, hover 150ms, tooltip 200ms, tab 250ms,
modal 300ms, page 400ms.

## Patterns

- **Orchestrate, don't scatter.** One page-load sequence (hero → text +0.2s →
  CTA +0.4s) lands harder than ten independent effects. Stagger children
  ~0.08–0.1s; perfectly uniform staggers feel robotic, so vary slightly.
- **Reveal on scroll** at ~20% from the bottom of the viewport, once.
- **Animate only `transform` and `opacity`** — they're GPU-composited.
  Animating width/height/margin/top thrashes layout and stutters.

## Slop tells to avoid

Global rotate/skew on hover, scale > 1.05 on hover (reads cheap), fade to/from
opacity 0 with no movement (looks dead), everything springing.

## Library choice (don't mix engines)

- **Motion (`motion/react`)** — the default for UI, bento, and state-change
  motion. `whileInView` for scroll-reveal, `layout`/`layoutId` for shared
  elements, `useMotionValue`/`useTransform` for continuous pointer/scroll values.
- **GSAP + ScrollTrigger** — for full-page scrolltelling and scroll hijacks
  (pin, scrub, horizontal pan). Isolate in a leaf `'use client'` component with
  `gsap.context()` and a `revert()` cleanup.
- **Three.js / WebGL** — canvas backgrounds and 3D, same isolation rule.
- **Never mix GSAP or Three.js with Motion in the same component tree** — they
  fight over the same frames.

## Forbidden in React (these jank or re-render every frame)

- `window.addEventListener("scroll", ...)` driving state — banned. Use
  `useScroll()`, ScrollTrigger, IntersectionObserver, or CSS scroll-driven
  animations (`animation-timeline: view()`).
- Scroll progress computed from `window.scrollY` into React state — re-renders
  the tree every frame; use a motion value.
- `requestAnimationFrame` loops that touch React state — use
  `useMotionValue` + `useTransform`.
- `useState` for continuous input (mouse position, scroll progress, magnetic
  hover) — it re-renders on every change and collapses on mobile.

## Scroll-hijack skeletons (when the direction earns one)

The common failure is the trigger firing mid-scroll instead of pinning at the
viewport top. The fix in every case is `start: "top top"` and `pin: true`.

**Sticky-stack** (cards pin and physically stack):

```tsx
"use client";
import { useRef, useEffect } from "react";
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
import { useReducedMotion } from "motion/react";
gsap.registerPlugin(ScrollTrigger);

export function StickyStack({ cards }: { cards: React.ReactNode[] }) {
  const ref = useRef<HTMLDivElement>(null);
  const reduce = useReducedMotion();
  useEffect(() => {
    if (reduce || !ref.current) return;
    const ctx = gsap.context(() => {
      const els = gsap.utils.toArray<HTMLElement>(".stack-card");
      els.forEach((card, i) => {
        if (i === els.length - 1) return;
        ScrollTrigger.create({ trigger: card, start: "top top",
          endTrigger: els[els.length - 1], end: "top top", pin: true, pinSpacing: false });
        gsap.to(card, { scale: 0.92, opacity: 0.55, ease: "none",
          scrollTrigger: { trigger: els[i + 1], start: "top bottom", end: "top top", scrub: true } });
      });
    }, ref);
    return () => ctx.revert();
  }, [reduce]);
  return (
    <div ref={ref} className="relative">
      {cards.map((c, i) => (
        <div key={i} className="stack-card sticky top-0 min-h-[100dvh] flex items-center justify-center">{c}</div>
      ))}
    </div>
  );
}
```

**Horizontal-pan** (vertical scroll drives a horizontal track): pin the wrapper,
scrub the inner track, `end: () => "+=" + distance` where `distance =
track.scrollWidth - window.innerWidth`, `invalidateOnRefresh: true`.

**Scroll-reveal stagger** (lighter, no pin) — prefer Motion's `whileInView` over
GSAP: `initial={{ opacity: 0, y: 24 }}`, `whileInView={{ opacity: 1, y: 0 }}`,
`viewport={{ once: true, amount: 0.3 }}`, `transition={{ delay: i * 0.06, ease:
[0.16, 1, 0.3, 1] }}`. Gate `initial` on `useReducedMotion()`.

## Non-negotiable

Honor reduced motion — collapse to instant or fade-only. Any motion past a hover
transition must degrade, and infinite loops / parallax / scroll-hijack / magnetic
physics collapse to static:

```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after { animation: none !important; transition: none !important; }
}
```
