---
name: create-design-md
description: Write a new DESIGN.md design-system document for a website, product or existing codebase, in the same format as the awesome-design-md collection. Use when the user asks to extract, document or reverse-engineer a site's design system, make a DESIGN.md for their own app, or add a brand that is missing from the collection.
---

# Create a DESIGN.md

The output is one markdown file an AI agent can read to reproduce a visual language: tokens it can copy, rules it can follow, and enough prose to capture the mood. Use the token format in [template.md](template.md); it is the format of most files in the collection and follows the [Stitch DESIGN.md spec](https://stitch.withgoogle.com/docs/design-md/specification/).

## 1. Gather evidence

Work from real values, never from memory of what a brand "usually" looks like.

- **Website**: fetch the page HTML and its stylesheets. Pull CSS custom properties, `font-family`/`font-size`/`font-weight`/`line-height`/`letter-spacing` on headings, body and buttons, `border-radius`, `box-shadow`, `padding` on buttons and cards, and media-query breakpoints. If a headless browser is available, read computed styles of the hero headline, body copy, primary/secondary buttons, nav, cards and inputs, and take screenshots of the top of the page and one content band.
- **Codebase**: read the theme / token files (Tailwind config, CSS variables, theme objects) and the main button, card, input and nav components.

Keep a note of where each value came from. If something can't be measured (hover state, dark mode), mark it in **Known Gaps** instead of guessing.

## 2. Distil tokens

- **colors**: deduplicate near-identical hexes; name by role (`primary`, `primary-press`, `ink`, `ink-mute`, `canvas`, `canvas-soft`, `hairline`, `on-primary`), not by hue.
- **typography**: a scale from `display-xxl` down to `caption`, each with family stack (proprietary font first, then fallbacks), size, weight, line-height, letter-spacing.
- **rounded**, **spacing**: the handful of values actually used, named `xs`…`xxl` and `pill`.
- **components**: the 6-15 elements that define the look (primary/secondary button, nav, hero, card variants, input, badge, footer), each referencing tokens with `{colors.x}` syntax and listing states.

## 3. Write the prose

Fill every section of the template. The **Overview** explains the design's logic (what the brand emphasises and what it refuses), not a list of colours. **Do's and Don'ts** carry the rules that make the look recognisable: what the accent is reserved for, how many filled CTAs per section, where shadows are allowed. Keep any one claim short and specific: "48px weight 300, -0.96px tracking" rather than "large, light headline".

## 4. Check

- Every `{token.ref}` in the prose exists in the front matter, and every front-matter token is used somewhere.
- Hex values are valid 6-digit codes; text/background pairs for body copy meet WCAG AA (4.5:1). Flag any that don't in Known Gaps.
- If Node is available, run `npx @google/design.md lint DESIGN.md` and fix what it reports.

## 5. Deliver

- For the user's own project: write `DESIGN.md` at the project root.
- For this repository: create `design-md/<slug>/DESIGN.md`, then run `python3 scripts/build-skill-catalog.py` so the `design-md` skill's catalog picks it up. Note that CONTRIBUTING.md says new DESIGN.md pull requests are not accepted upstream; contributors should open an issue first.

The name in the front matter follows the collection convention `<Brand>-Inspired-design-analysis`, and the overview describes an "inspired interpretation". These files document a visual language. They should not reproduce logos, copy or imagery.
