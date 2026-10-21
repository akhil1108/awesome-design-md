---
name: design-md
description: Build or restyle UI in the visual language of a real product (Stripe, Linear, Vercel, Apple, Notion, Claude, Tesla and 80+ more) using a curated DESIGN.md design system. Use when the user asks for a page, component or app that "looks like" / "feels like" / "in the style of" a known brand, wants to pick a design system for a new UI, or asks to install a DESIGN.md into their project.
---

# Use a DESIGN.md from the collection

A DESIGN.md is a plain-markdown design system: palette with roles, type scale, components with states, spacing, elevation, do's and don'ts. This skill picks the right one, puts it in the user's project, and builds UI that follows it exactly.

## 1. Pick the design

- If the user named a brand, find its slug in [catalog.md](catalog.md) (e.g. "Linear" → `linear.app`, "Mistral" → `mistral.ai`, "The Verge" → `theverge`).
- If they described a mood instead ("dark, terminal-like", "warm editorial"), shortlist 2-3 from the catalog's **Look** column, say why each fits, and recommend one.
- If the brand is not in the catalog, say so, offer the closest matches, and mention the `create-design-md` skill for authoring a new one.

## 2. Locate the file

The collection lives at `design-md/<slug>/DESIGN.md` in the awesome-design-md repository. Try, in order:

1. `../../design-md/<slug>/DESIGN.md` relative to this skill's base directory (works when installed as a plugin or used inside the repo).
2. `https://raw.githubusercontent.com/VoltAgent/awesome-design-md/main/design-md/<slug>/DESIGN.md`.

Read the whole file before writing any UI. Don't build from the catalog one-liner.

## 3. Install it (when the user wants it in their project)

Copy it to `DESIGN.md` at the project root unless one already exists. If one exists, show the difference in intent (which brand it describes) and ask before overwriting. If the project has an `AGENTS.md` or `CLAUDE.md`, offer to add one line: `UI follows DESIGN.md — read it before changing styles.`

## 4. Build with it

Files come in two formats (the catalog's **Format** column):

- **tokens**: YAML front matter defines `colors`, `typography`, `rounded`, `spacing` and named components; the prose refers to them as `{colors.primary}`, `{typography.body-md}`, `button-primary-pill`. Turn the front matter into the project's token layer first (CSS custom properties, Tailwind `theme.extend`, or the existing theme file), then build components by name from the **Components** section.
- **prose**: numbered sections 1-9. Take hex values and type sizes from sections 2-3, component specs from section 4, and use section 9 (Agent Prompt Guide) for ready-made component descriptions.

Rules while building:

- Match the project's existing stack (framework, CSS approach, component library). Don't introduce a new one for styling.
- Use only colors, font sizes, radii and shadows the DESIGN.md defines. If you need a value it doesn't have, derive it from an existing token and say so.
- Respect the usage rules, not just the values: "one filled CTA per band", "accent only on primary buttons", "no shadows" matter as much as the hex codes.
- Proprietary fonts (Sohne, SF Pro, Universal Sans, ...) are usually not licensed for the user's project. Use the fallback stack in the file, or suggest the closest free Google Font and state the substitution.
- Don't copy logos, wordmarks, product names or photography. The goal is the design language, not impersonation of the brand.
- Follow **Do's and Don'ts** and **Responsive Behavior** (breakpoints, touch targets) before calling the work done.

## 5. Check the result

Before finishing, run through the DESIGN.md's Do's and Don'ts against what you built and fix violations. For a larger review of existing code, use the `audit-design-md` skill.
