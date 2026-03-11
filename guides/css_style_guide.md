# CSS Style Guide

This document provides rules for creating consistent, accessible, and maintainable CSS. It is optimised for quick scanning and day-to-day use.

## Table of Contents

- [CSS Style Guide](#css-style-guide)
  - [Table of Contents](#table-of-contents)
  - [Principles](#principles)
  - [File structure](#file-structure)
  - [Cascade layers](#cascade-layers)
  - [Naming](#naming)
  - [Selectors and specificity](#selectors-and-specificity)
  - [Tokens](#tokens)
  - [Units and sizing](#units-and-sizing)
  - [Colour and contrast](#colour-and-contrast)
  - [Typography](#typography)
  - [Layout](#layout)
  - [Motion and animation](#motion-and-animation)
  - [Accessibility](#accessibility)
  - [Comments and documentation](#comments-and-documentation)
  - [Performance](#performance)
  - [Browser support](#browser-support)
  - [Linting and tooling](#linting-and-tooling)
  - [Git protocol](#git-protocol)
  - [Example: component skeleton](#example-component-skeleton)

## Principles

- Prioritise clarity and readability over micro-optimisations.
- Ensure styles are accessible by default, respecting user preferences and contrast needs.
- Maintain a predictable cascade using cascade layers, small components, and low specificity.
- Apply progressive enhancement with safe fallbacks for new features.
- Centralise tokens for colour, spacing, typography, and motion as a single source of truth.

## File structure

Load order must proceed from top to bottom: core, layout, components, utilities, and pages.

```text
styles/
  core.css          # @layer declarations, resets, and tokens
  layout.css        # base page layout and common wrappers
  components.css    # reusable components
  utilities.css     # simple one-off helpers
  pages/            # page-specific overrides (last to load)
```

## Cascade layers

Declare the layer stack at the top of the core file. Define all rules inside these layers to ensure predictable overrides.

```css
/* 1) Declare once at the top of core.css */
@layer base, theme, components, utilities, pages;

/* 2) Define inside layers */
@layer theme {
  /* tokens and colours */
}

@layer base {
  /* layout and scaffolding */
}

@layer components {
  /* buttons, cards, etc. */
}

@layer utilities {
  /* .u-text-center, .u-sr-only */
}

@layer pages {
  /* page-specific tweaks */
}
```

## Naming

Keep names short, specific, lower-case, and hyphenated. Use American English for all technical identifiers (e.g., `color`, `center`, `gray`). This maintains consistency with native CSS properties and improves project-wide searchability.

- **Components:** `.c-thing` (e.g., `.c-card`, `.c-modal`).
- **Elements:** `.c-card__header`.
- **Modifiers:** `.c-card--raised`.
- **State:** `.is-open`, `.is-invalid` (added by JavaScript only).
- **Utilities:** `.u-hidden`, `.u-flow-300`.
- **JS hooks:** `[data-js="toggle"]` (never style using `js-` classes).

## Selectors and specificity

- Restrict rules to one class per block where possible.
- Avoid ID selectors for styling; reserve IDs for landmarks and ARIA targets.
- Scope instance variables to a parent to avoid leaks.
- Avoid `!important` except in utility classes, and document its use.

```css
.c-blobs .d1 {
  --dx: 30s;
}
```

## Tokens

Define tokens in the `theme` layer under the `:root` pseudo-class. Use tokens globally and avoid raw values in components.

```css
@layer theme {
  :root {
    /* Colour (HSL preferred for easy theming) */
    --brand-h: 352;
    --brand-s: 50%;
    --brand-l: 53%;
    --brand: hsl(var(--brand-h) var(--brand-s) var(--brand-l));

    /* Spacing scale (4px baseline) */
    --space-100: 0.25rem; /* 4px */
    --space-200: 0.5rem;  /* 8px */
    --space-300: 0.75rem; /* 12px */
    --space-400: 1rem;    /* 16px */

    /* Motion */
    --speed: 1;           /* global animation multiplier */
  }
}
```

## Units and sizing

- Use `rem` for typography and spacing. Use `px` only for borders and hairlines.
- Use `aspect-ratio` where possible and avoid magic numbers.
- Prefer `min()`, `max()`, and `clamp()` for responsive sizing.

```css
.c-hero {
  font-size: clamp(1rem, 1vw + 1rem, 1.5rem);
}
```

## Colour and contrast

- Use tokens and derive variants with HSL or `color-mix`.
- Maintain WCAG AA minimum contrast for text and UI.
- Reserve pure black and white for ink and backgrounds; avoid muddy grays.

```css
.c-button {
  background: var(--brand);
  color: white;
}
```

## Typography

Define typographical scales in the theme using logical properties. Target a line length of 45–85 characters to preserve readability.

```css
@layer theme {
  :root {
    --font-body: system-ui, sans-serif;
  }
}

body {
  font-family: var(--font-body);
}
```

## Layout

- Prefer CSS Grid for complex page layouts and Flexbox for one-dimensional layouts.
- Use content-driven gaps (e.g., `gap: var(--space-400);`).
- Avoid fixed heights; use intrinsic sizing.

## Motion and animation

- Respect reduced motion preferences.
- Use the global `--speed` multiplier.
- Keep UI animation durations between 200–700ms.
- Animate only `opacity`, `transform`, and `filter` to avoid layout thrashing.

```css
@media (prefers-reduced-motion: reduce) {
  * {
    animation: none;
    transition: none;
  }
}
```

## Accessibility

- Always include reduced motion and `focus-visible` rules.
- Ensure hit areas are a minimum of 44x44px for touch actions.
- Do not rely on colour alone; add text, icons, or patterns.

```css
:focus-visible {
  outline: 2px solid currentColor;
  outline-offset: 2px;
}
```

## Comments and documentation

Use a header documentation block per file. Use targeted inline comments only to explain the reasoning behind a rule.

```css
/*
 * Component: Card
 * Purpose: Present content in a contained panel.
 * API: .c-card [--elevation], .c-card__header, .c-card__body
 * Accessibility: Focus states, contrast >= AA.
 * Risks: Long titles overflow -> text-wrap: balance.
 * Changelog: 2025-11-05 Added compact variant.
 */

.c-card {
  /* Push above adjacent image to preserve rhythm at small sizes */
  margin-block-start: var(--space-300);
}
```

## Performance

- Minimise repaint and reflow. Prefer `transform` over `top` or `left` in animations.
- Avoid deep descendant selectors.
- Audit unused CSS and establish coverage checks in CI.

## Browser support

- Target the last two evergreen browser versions and current iOS/Android WebViews.
- Provide fallbacks for features behind flags or with limited support.
- Document any known rendering gaps in the component header.

## Linting and tooling

Use Stylelint with the standard configuration and the following project overrides. Run Prettier for formatting using a 2-space indent, trailing newlines, and LF line endings.

```json
{
  "extends": ["stylelint-config-standard"],
  "rules": {
    "color-function-notation": "modern",
    "alpha-value-notation": "percentage",
    "selector-max-specificity": "0,3,0",
    "selector-max-id": 0,
    "declaration-no-important": true,
    "comment-whitespace-inside": "always"
  }
}
```

## Git protocol

- Limit commits to one structural change.
- Use the imperative mood for short subjects.
- Reference issue/PR IDs and include the scope when helpful.

```text
feat(card): add raised variant and tokens
```

## Example: component skeleton

```css
/*
 * Component: Button
 * Purpose: Primary action trigger.
 * API: .c-button [.c-button--danger] [.is-loading]
 * Accessibility: Focus-visible ring; min target size; reduced motion.
 */
@layer components {
  .c-button {
    background: var(--brand);
    border-radius: 999px;
    color: white;
    display: inline-grid;
    min-height: 44px;
    min-width: 10ch;
    padding-inline: var(--space-400);
    place-items: center;
    transition: box-shadow 200ms, transform 200ms;
  }

  .c-button:focus-visible {
    outline: 2px solid white;
    outline-offset: 2px;
  }

  .c-button:is(:hover, :focus-visible) {
    transform: translateY(-1px);
  }

  .c-button--danger {
    background: color-mix(in oklab, var(--brand), red 40%);
  }

  .c-button.is-loading {
    opacity: 0.7;
    pointer-events: none;
  }
}

@media (prefers-reduced-motion: reduce) {
  .c-button {
    transition: none;
  }
}
```
