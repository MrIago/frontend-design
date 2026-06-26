# better-frontend

Personal skill (plain skill, not a plugin). Renamed from `frontend-design` to a
unique name so it never collides with Anthropic's official `frontend-design`
plugin, and to match the `better-*` convention. Does two things at once: distinctive,
intentional frontend visual design, and copy that does not read like AI wrote
it. Strips the "AI made this" look out of UI and the "AI wrote this" tells out
of prose.

`SKILL.md` is an orchestrator: it opens with a "route by what you are here to
do" table, so the same skill handles "fix the copy", "improve the visual style",
"both", "redesign this", "generate reference images", and "pick an aesthetic
direction" - each routing to the right references. Pull in only what the task
needs.

The judgment-first core (design lead at a studio: read the brief, ground it in
the subject, spend the boldness in one place) merged with a mechanical anti-slop
layer for both axes - the visual production tells and the prose tells, the
em-dash ban, the consistency locks, hero discipline, pre-flight, and a copy
scoring rubric. Plus when-to-use-a-real-design-system guidance, a redesign
protocol, concrete aesthetic recipes, image-reference art direction, and
output-completeness discipline.

Built from Anthropic's official `frontend-design` plugin, merged with the best
of the `taste-skill` anti-slop family (visual tells, dials, GSAP skeletons,
aesthetic variants, image-gen art direction, output enforcement) and the
`stop-slop` prose skill (the writing axis), then unified into one skill.

## Layout

- `SKILL.md` - the router, the judgment, the process, and the reference index.

**Visual design**
- `references/design-vocabulary.md` - directions, the intensity dials, the pattern vocabulary.
- `references/aesthetics.md` - concrete kits for minimalist / brutalist / soft-premium directions.
- `references/anti-slop.md` - visual tells, the three locks, hero discipline, measurable restraint.
- `references/design-systems.md` - brief→system map, honesty rules, install commands, sources.
- `references/tokens.md` - token system, dark mode, selector-specificity bug.
- `references/typography.md` - scale, glyphs, serif discipline, pairings, italic descender.
- `references/motion.md` - easing, durations, library choice, forbidden React patterns, GSAP skeletons.
- `references/responsive-a11y.md` - breakpoints, touch targets, contrast, focus, pre-ship audit.
- `references/redesign.md` - detect mode, audit, preserve IA/SEO/voice, modernisation levers.
- `references/image-references.md` - art-directing web/mobile/brand comps, image-first build.
- `references/pre-flight.md` - the mechanical last-pass visual checklist.

**Writing**
- `references/copywriting.md` - core prose rules, interface-copy rules, quick checks, scoring.
- `references/copy-banlist.md` - exhaustive phrase + structure tables to purge.
- `references/copy-examples.md` - before/after rewrites.

**Output**
- `references/output-discipline.md` - full-output enforcement and why models truncate.

Install: clone (or symlink) into `~/.claude/skills/better-frontend`.
