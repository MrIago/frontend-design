---
name: better-frontend
description: Use when designing or building any frontend, landing page, portfolio, marketing site, or redesign; when writing or fixing the copy on a page; when UI looks templated, generic, or AI-generated; or when prose reads like AI wrote it. Covers two axes - visual design (aesthetic direction, typography, color, layout, motion, design systems, the redesign protocol, a pre-flight check) and writing (stripping AI tells out of copy, headlines, microcopy, and standalone prose). Routes by what you are here to do, so you can call it to improve the copy, the visual style, or both. Reach for it on "make this look less AI", "design a landing page", "the hero feels generic", "redesign this", "fix this copy", "make this writing sound human", or any deliberate design or copy decision.
license: Complete terms in LICENSE.txt
---

# Frontend Design

Approach this as the design lead at a small studio known for giving every client
a visual identity and a voice that could not be mistaken for anyone else's. This
client has already rejected work that felt templated or AI-written, and is paying
for a distinctive point of view: make deliberate, opinionated choices about
palette, typography, layout, motion, and words that are specific to this brief,
and take one real risk you can justify.

The skill covers two axes. **Visual design** (look, structure, motion, systems)
and **writing** (copy, headlines, microcopy, and standalone prose). They share
one principle: spend your boldness in one place, keep everything around it quiet
and disciplined, and purge the tells that make work read as generated.

## Route by what you are here to do

Read only the rows that match the request. Each points to the references to pull
in. Do not load everything up front.

| You are here to... | Read, in order |
|---|---|
| **Fix or write copy / prose only** (page copy, headlines, microcopy, an essay, a post) | `copywriting.md` → `copy-banlist.md` (when editing hard) → `copy-examples.md`. For a deep humanize pass on long-form prose, invoke the **`/human-text`** skill |
| **Improve or design the visual style only** | This file's design principles → `design-vocabulary.md` → `anti-slop.md` → `typography.md` + `tokens.md` + `motion.md` as the work touches each |
| **Both - a full page or redesign of look and words** | The brainstorm process below, then the visual references, then `copywriting.md` for every visible string |
| **Build a new page / landing / portfolio from scratch** | Process below → `design-vocabulary.md` → `aesthetics.md` (once a direction is chosen) → `tokens.md` → `typography.md` → `motion.md` → `responsive-a11y.md` → `copywriting.md` → `pre-flight.md` |
| **Redesign an existing site** | `redesign.md` first (detect mode, audit), then the levers it points to |
| **Commit to a named direction** (minimalist, brutalist, premium/soft) | `design-vocabulary.md` to choose → `aesthetics.md` for the concrete kit |
| **The brief is a known system** (Material, Fluent, Carbon, GOV.UK, Polaris, Primer, shadcn) | `design-systems.md` - use the official package, stop here for look |
| **Generate reference images** (web comps, mobile screens, brand boards) or build image-first | `image-references.md` for the art direction. To actually produce assets (images, transparent icons, SVG logos, brand palettes, scenes, video), invoke the **`/studio`** skill |
| **Need real images, screenshots, or page data from the live web** | invoke **`/surf`** (screenshot a page or competitor, scrape a listing, pull a reference image, drive a logged-in page) |
| **Make sure a large build ships complete** (no placeholders, full files) | `output-discipline.md` |
| **Final check before shipping** | `pre-flight.md` (visual) + the Quick checks in `copywriting.md` (copy), run over the rendered result in both themes |

When the request is vague ("make this less AI"), it usually means both axes:
fix the copy with `copywriting.md` and the look with `anti-slop.md`.

## How to run this (do not skip)

For anything beyond a one-line tweak, do not work from this file alone. The
SKILL.md body is the map; the depth that makes the difference lives in the
references, so a substantial task that never opens them produces one shallow,
conservative change.

So, for any real page or design task:

1. **Read the reference rows that match the request before proposing anything.**
   "Improve this landing" means open `design-vocabulary.md` + `anti-slop.md` for
   the look and `copywriting.md` + `copy-banlist.md` for the words, then read the
   actual page or copy before diagnosing.
2. **Default to both axes.** A bare "improve the landing" or "make this less AI"
   covers visual and copy. Do only one axis when the user scoped it ("just the
   copy", "only the hero layout").
3. **Diagnose against the references first, then change.** List the concrete
   tells you found (eyebrow on every section, em-dashes, binary contrasts,
   filler) before editing, the way a reviewer would.
4. **Finish with the checks.** Run `pre-flight.md` (visual) and the
   `copywriting.md` Quick checks (copy) over the result before calling it done.

One disciplined signature is right for *style direction*; it is not an excuse to
skip the copy axis or the anti-slop pass.

## Ground it in the subject

If the brief does not pin down what the product or subject is, pin it yourself
before designing or writing: name one concrete subject, its audience, and the
page's single job, and state your choice in one line so the rest of the work has
a fixed point to converge toward. If memory holds the human's preferences or
past work, use it as a hint. The subject's own world - its materials,
instruments, artifacts, vernacular - is where distinctive choices come from, in
both the visuals and the words.

## Use the real thing when the brief is a system, not an aesthetic

Some briefs are a system to adopt, not a look to invent: a Microsoft or
enterprise app, a GitHub-style devtool, a UK or US public-sector service, a
Shopify or Atlassian surface. When the brief is clearly one of these, install
and use the official package (Fluent, Carbon, Primer, GOV.UK Frontend, USWDS,
Polaris, or shadcn/ui when you want to own the code) instead of hand-rolling its
appearance. Don't import a system's tokens and then override most of them, and
don't mix two systems in one tree. `design-systems.md` maps brief to system with
install commands. Everything below is for when the brief is an aesthetic.

## Design principles

For web designs, the hero is a thesis. Open with the most characteristic thing
in the subject's world, in whatever form fits: a headline, an image, an
animation, a live demo. A big number with a small label and a gradient accent is
the template answer; use it only if it is truly best.

Typography carries the personality of the page. Pair display and body faces
deliberately, not the families you would reach for on any project, and set a
clear scale with intentional weights and spacing. Make the type treatment a
memorable part of the design, not a neutral delivery vehicle. Details in
`typography.md`.

Structure is information. Numbering, eyebrows, dividers, and labels should encode
something true about the content, not decorate it. Numbered markers (01 / 02 /
03) only fit when the content is genuinely a sequence. Question every structural
device before adding it.

Leverage motion deliberately. Think about where animation serves the subject: a
page-load sequence, a scroll reveal, a hover micro-interaction. One orchestrated
moment usually lands harder than scattered effects, and extra animation often
just signals "AI-generated". Values and skeletons in `motion.md`.

Match complexity to the vision. Maximalist directions need elaborate execution;
minimal directions need precision in spacing, type, and detail. Elegance is
executing the chosen vision well.

Consider the words as carefully as the pixels. A brief rarely ships real content,
so the copy is yours to write, and generic copy makes a design feel as templated
as a generic layout. Write it with `copywriting.md`.

## Process: brainstorm, explore, plan, critique, build, critique again

For calibration: AI-generated design clusters around three looks - (1) warm cream
background (~#F4F1EA) with a high-contrast serif display and a terracotta accent;
(2) near-black background with one acid-green or vermilion accent; (3)
broadsheet layout with hairline rules, zero radius, dense columns. All are
legitimate for some briefs but are defaults, not choices, and appear regardless
of subject. Where the brief pins a direction, follow it exactly. Where it leaves
an axis free, do not spend that freedom on one of these defaults.

Work in two passes. First, brainstorm a compact plan: a token system of color
(4-6 named hex values), type (2+ roles - a characterful display used with
restraint, a complementary body, a utility/mono face if needed), layout (a
concept in one-sentence prose plus ASCII wireframes), and a signature - the one
element the page will be remembered by. Plan the voice too: who is talking, to
whom, in what register.

Then review the plan against the brief before building: if any part reads like
the generic default you would produce for any similar page, revise it and say
what changed and why. Only after confirming the plan is specific to this brief do
you write code, deriving every color and type decision from the plan. Watch CSS
selector specificity so type-based (`.section`) and element-based (`.cta`) rules
do not silently cancel each other on shared properties like section padding (see
`tokens.md`).

Do most of this planning and iteration in your thinking; show the user ideas only
when confidence is high they will delight.

## Restraint and self-critique

Spend your boldness in one place. Let the signature element be the one memorable
thing, keep everything around it quiet, and cut any decoration that does not serve
the brief. Not taking a risk is itself a risk. Build to a quality floor without
announcing it: responsive to mobile, visible keyboard focus, reduced motion
respected. Critique your own work as you build, taking screenshots if the
environment supports it. Before leaving the house, take one accessory off.

Three consistency locks are non-negotiable: one accent color, one corner-radius
system, one theme, each held across the whole page. And the single highest-
frequency tell, in both copy and shipped UI text, is the em-dash; there is no
sparing use of it. `anti-slop.md` carries the full catalogue of visual production
tells, the locks, and hero discipline; `copywriting.md` and `copy-banlist.md`
carry the writing tells. Before calling a page done, run `pre-flight.md` over the
rendered result in both light and dark, and the copy Quick checks over every
visible string.

## References

The judgment above is the skill. These are the concrete details - pull one in
only when the router or your current step points to it, not all up front.

**Visual design**
- `design-vocabulary.md` - named directions to choose between, the three intensity dials (variance / motion / density), the pattern vocabulary, and the per-discipline lens for fixing slop one axis at a time.
- `aesthetics.md` - concrete kits (fonts, palette, radius, components, motion) for a committed direction: minimalist/editorial, brutalist/industrial, soft/premium-agency.
- `anti-slop.md` - visual production tells (em-dash ban, eyebrow restraint, fake screenshots, decorative dots, ...), the three consistency locks, hero discipline, and restraint made measurable.
- `design-systems.md` - when the brief is a known system, the honesty rules, the brief→system map, install commands, and canonical sources.
- `tokens.md` - primitive → semantic → component token system, dark mode, and the selector-specificity bug.
- `typography.md` - scale ratios, measure, OpenType settings, correct glyphs, serif discipline, and the JSX quote gotcha.
- `motion.md` - easing, durations, orchestration, library choice, forbidden React scroll patterns, GSAP scroll-hijack skeletons, reduced motion.
- `responsive-a11y.md` - breakpoints, the orchestrator + desktop/mobile + skeleton structure, touch targets, WCAG AA contrast, focus, and a pre-ship audit.
- `redesign.md` - the redesign protocol: detect the mode, audit first, preserve IA/SEO/voice, the modernisation levers, and what never changes silently.
- `image-references.md` - art-directing generated comps (web / mobile / brand) and the image-first generate → analyse → code workflow.
- `pre-flight.md` - the mechanical last-pass visual checklist, run over the rendered result in both themes.

**Writing**
- `copywriting.md` - the core prose rules, the interface-copy rules, the Quick checks, and the 1-10 scoring rubric.
- `copy-banlist.md` - the exhaustive phrase and structure tables (throat-clearing, jargon, adverbs, binary contrasts, false agency, passive voice, ...).
- `copy-examples.md` - before/after rewrites showing the rules at work.

**Output**
- `output-discipline.md` - full-output enforcement, the banned placeholder patterns, chunking, and why models truncate. Pull in for large or multi-file builds.

**Related skills (invoke these, they are not files here)**
- `/human-text` - deep humanize pass on prose: strips AI writing tells (em dashes, significance inflation, rule of three, chatbot artifacts) and leaves a human voice. Use for long-form copy beyond the `copywriting.md` quick pass.
- `/studio` - generate and edit real media via OpenRouter: images, transparent icons, SVG logos, brand palettes, scenes from reference photos, voice, music, and programmatic video. Use to produce the assets the design needs.
- `/surf` - access the live web: screenshot a page or competitor, scrape a listing, pull a reference image, drive a logged-in page. Use for real images, screenshots, and page data.
