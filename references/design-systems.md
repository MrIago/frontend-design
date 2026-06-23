# Design systems: when the brief is a system, use the real one

Some briefs are an aesthetic to invent; others are a system to adopt. Reaching
for a real design system is an honesty move: if the brief reads as a known
product family, the official package already encodes its tokens, components, and
accessibility. Hand-rolling its look is slower, wronger, and reads as an
imitation. The judgment in SKILL.md is for the aesthetic case; this is for the
system case.

## The honesty rules

- **If the brief is one of the systems below, install and use the official
  package.** Don't recreate its CSS by hand.
- **Don't import a system's tokens and then override most of them.** That's the
  worst of both: you inherit the constraint and lose the coherence.
- **One system per project.** Don't mix Fluent React with Carbon, or drop
  shadcn/ui components into a Material 3 app. They fight over tokens and reset.
- **shadcn/ui is the exception that you own.** It's copied into your repo, so you
  customize radii, color, shadow, and type to the brief. Never ship it in its
  default zinc state, that default *is* a tell.

## Brief → system

| The brief reads as… | Reach for | Why |
|---|---|---|
| Microsoft / enterprise SaaS / dashboards | `@fluentui/react-components` or `@fluentui/web-components` | Official Fluent UI, Microsoft tokens, a11y done |
| Google-ish, Material-flavored product | `@material/web` + Material 3 tokens | Official, theme-able via Material Theming |
| IBM-style B2B / enterprise analytics | `@carbon/react` + `@carbon/styles` | Official Carbon, mature data-density patterns |
| Shopify app surface | Polaris web components / Polaris React | Required for Shopify admin UI |
| Atlassian / Jira-style product | `@atlaskit/*` + `@atlaskit/tokens` | Official Atlassian DS |
| GitHub-style devtool / community page | `@primer/css` or `@primer/react-brand` | Official Primer; Brand variant for marketing |
| UK public-sector service | `govuk-frontend` | Legally / regulatorily expected |
| US public-sector / trust-first | `uswds` | Same |
| Fast local-business / agency MVP | Bootstrap 5.3 | Boring, fast, works |
| Modern accessible React foundation | `@radix-ui/themes` | Primitives plus a polished theme |
| Modern SaaS where you own the components | shadcn/ui (`npx shadcn@latest add ...`) | You own the code; customize it, never ship default |
| Tailwind-based modern SaaS / marketing | Tailwind v4 utilities + `dark:` variant | Default for indie / small-team builds |

For anything that is an aesthetic rather than a system (editorial, brutalist,
premium consumer, agency, portfolio), there is no official package: build with
native CSS + Tailwind + a maintained primitive library, and be honest in code
comments about what is borrowed inspiration versus official material.

## Aesthetic trends are not official systems

These are looks, not packages. Build them honestly and label approximations.

| Aesthetic | Honest implementation |
|---|---|
| Glassmorphism / frosted glass | `backdrop-filter` + layered borders + highlight overlay; solid-fill fallback under `prefers-reduced-transparency` |
| Bento (Apple-style tiles) | CSS Grid with mixed cell sizes; no library owns this |
| Brutalism | Native CSS, monospace, raw borders; no library |
| Editorial / magazine | Serif (when justified), asymmetric grid, generous whitespace |
| Aurora / mesh gradients | Layered radial gradients or SVG; no library |
| Kinetic typography | CSS animations, scroll-driven animations, GSAP for hijacks |
| Apple "Liquid Glass" | Apple documents this for Apple platforms only. There is no official `liquid-glass.css`. Web versions are `backdrop-filter` approximations; label them as such |

## Install commands

```bash
npm install @material/web                              # Material Web (Material 3)
npm install @fluentui/react-components                 # Fluent UI React v9
npm install @fluentui/web-components @fluentui/tokens  # Fluent Web Components
npm install @carbon/react @carbon/styles               # IBM Carbon
npm install @radix-ui/themes                           # Radix Themes
npx shadcn@latest init                                 # shadcn/ui (own the code)
npx shadcn@latest add button card badge separator input
npm install --save @primer/css                         # Primer CSS (GitHub product)
npm install @primer/react-brand                        # Primer Brand (GitHub marketing)
npm install govuk-frontend                             # GOV.UK Frontend
npm install uswds                                       # US Web Design System
npm install bootstrap                                   # Bootstrap 5.3
# Atlassian:
yarn add @atlaskit/css-reset @atlaskit/tokens @atlaskit/button @atlaskit/badge
# Shopify Polaris (apps only) — add to HTML head:
#   <meta name="shopify-api-key" content="%SHOPIFY_API_KEY%" />
#   <script src="https://cdn.shopify.com/shopifycloud/polaris.js"></script>
```

## Canonical sources (read before reinventing)

- Material: https://material-web.dev/ · https://m3.material.io/develop/web
- Fluent: https://fluent2.microsoft.design/ · https://github.com/microsoft/fluentui
- Carbon: https://carbondesignsystem.com/
- Shopify Polaris: https://shopify.dev/docs/api/app-home/web-components
- Atlassian: https://atlassian.design/ · https://atlassian.design/tokens/design-tokens
- Primer: https://primer.style/ · https://github.com/primer/brand
- GOV.UK: https://design-system.service.gov.uk/
- USWDS: https://designsystem.digital.gov/
- Radix Themes: https://www.radix-ui.com/themes/docs
- shadcn/ui: https://ui.shadcn.com/docs
- Tailwind v4: https://tailwindcss.com/blog/tailwindcss-v4 · https://tailwindcss.com/docs/dark-mode
- Apple materials (Apple platforms): https://developer.apple.com/design/human-interface-guidelines/materials
