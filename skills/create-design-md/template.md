---
version: alpha
name: <Brand>-Inspired-design-analysis
description: An inspired interpretation of <Brand>'s design language — <one sentence on the signature colour, type and layout moves>.

colors:
  primary: "#000000"
  primary-press: "#000000"
  on-primary: "#ffffff"
  ink: "#000000"
  ink-mute: "#000000"
  canvas: "#ffffff"
  canvas-soft: "#000000"
  hairline: "#000000"

typography:
  display-xl:
    fontFamily: "<Brand Font>, system-ui, -apple-system, sans-serif"
    fontSize: 48px
    fontWeight: 600
    lineHeight: 1.1
    letterSpacing: -0.96px
  heading-md:
    fontFamily: "<Brand Font>, system-ui, -apple-system, sans-serif"
    fontSize: 24px
    fontWeight: 600
    lineHeight: 1.25
    letterSpacing: -0.24px
  body-md:
    fontFamily: "<Body Font>, system-ui, -apple-system, sans-serif"
    fontSize: 16px
    fontWeight: 400
    lineHeight: 1.5
    letterSpacing: 0px
  button-md:
    fontFamily: "<Body Font>, system-ui, -apple-system, sans-serif"
    fontSize: 15px
    fontWeight: 500
    lineHeight: 1
    letterSpacing: 0px
  caption:
    fontFamily: "<Body Font>, system-ui, -apple-system, sans-serif"
    fontSize: 13px
    fontWeight: 400
    lineHeight: 1.4
    letterSpacing: 0px

rounded:
  sm: 4px
  md: 8px
  lg: 12px
  pill: 9999px

spacing:
  xs: 4px
  sm: 8px
  md: 12px
  lg: 16px
  xl: 24px
  xxl: 32px
  section: 96px

components:
  button-primary:
    backgroundColor: "{colors.primary}"
    textColor: "{colors.on-primary}"
    typography: "{typography.button-md}"
    rounded: "{rounded.pill}"
    padding: 8px 16px
  button-primary-pressed:
    backgroundColor: "{colors.primary-press}"
  card:
    backgroundColor: "{colors.canvas}"
    rounded: "{rounded.lg}"
    padding: "{spacing.xxl}"
---

## Overview

<2-3 paragraphs: the design's logic, what it emphasises, what it refuses.>

**Key Characteristics:**
- <signature move 1, with token reference>
- <signature move 2>

## Colors

<Each colour role: token, hex, where it is used and where it is never used.>

## Typography

<Family choices and why; table or list of the scale; tracking and feature-setting rules.>

## Layout

<Grid, max widths, section rhythm, spacing scale usage.>

## Elevation & Depth

<Shadow levels and where each applies; surface hierarchy.>

## Shapes

<Radius usage per component type.>

## Components

### Buttons

**`button-primary`** — <role>.
- Background `{colors.primary}`, text `{colors.on-primary}`, type `{typography.button-md}`, padding 8px 16px, rounded `{rounded.pill}`.
- Pressed: background `{colors.primary-press}`.

### Cards & Containers

### Inputs & Forms

### Navigation

## Do's and Don'ts

### Do
- <rule>

### Don't
- <anti-pattern>

## Responsive Behavior

<Breakpoints, what collapses or stacks, touch-target sizes.>

## Iteration Guide

1. Focus on ONE component at a time.
2. Reference component names and tokens directly (`{colors.primary}`, `button-primary`).
3. Run `npx @google/design.md lint DESIGN.md` after edits.

## Known Gaps

- <values that could not be measured, e.g. hover states, dark mode>
