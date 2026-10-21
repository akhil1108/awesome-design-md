---
name: audit-design-md
description: Audit existing UI code against a DESIGN.md design system and report or fix drift — off-palette colours, unlisted font sizes, wrong radii, extra shadows, broken usage rules. Use when the user asks whether their UI matches their DESIGN.md, wants a design-consistency review of a diff or component, or asks to bring styles back in line with the design system.
---

# Audit UI against a DESIGN.md

## 1. Load the system

Read the project's `DESIGN.md` (project root first, then search the repo). If there is none, ask which design from the collection it should follow and load it with the `design-md` skill.

Build an allow-list from it: every hex colour, font family, font size/weight/line-height combination, radius, spacing step and shadow. For token-format files take these from the front matter; for prose-format files take them from sections 2-6. Also note the usage rules from Do's and Don'ts (e.g. "accent only on primary CTA", "no shadows on cards", "one filled button per section").

## 2. Scope

Audit what the user pointed at: a diff (`git diff` against the base branch), a directory, or specific components. With no scope given, audit the changed files on the current branch; if there are none, the main layout plus the button, card, input and nav components.

## 3. Find drift

Search the scoped files for hard-coded values and compare them to the allow-list:

- Colours: hex, `rgb()`/`hsl()`, Tailwind colour classes (`bg-blue-500`), named colours. Treat a colour within a tiny distance of an allowed one (e.g. `#533afe` vs `#533afd`) as a typo to snap, not a new colour.
- Typography: `font-size`, `font-weight`, `line-height`, `letter-spacing`, `font-family`, Tailwind `text-*`/`font-*`/`tracking-*`/`leading-*`.
- Shape and depth: `border-radius`/`rounded-*`, `box-shadow`/`shadow-*`.
- Spacing: padding/margin/gap values that fall off the spacing scale.
- Usage rules: check each Do/Don't against the rendered structure (count filled CTAs per section, accent colour on non-CTA elements, shadows where the system says none).

Values that already go through the project's token layer (CSS variables, theme keys) are fine if the token itself maps to an allowed value; check the token definitions once rather than every usage.

## 4. Report

Group findings by severity:

1. **Rule violations**: breaks a Do/Don't or a usage rule.
2. **Off-system values**: a colour, size, radius or shadow the DESIGN.md doesn't define. Give `file:line`, the value found, and the nearest allowed token.
3. **Hard-coded but correct**: allowed value written literally where a token exists. Low priority; mention as a count unless the user wants them listed.

## 5. Fix (when asked)

Replace off-system values with the nearest token, preferring the project's existing token names over raw hex. Don't restyle beyond the findings, and don't change behaviour or markup structure unless a usage rule requires it. Summarise what changed and anything left for the user to decide (e.g. a colour with no reasonable equivalent).
