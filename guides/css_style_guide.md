# CSS Style Guide

> Concise rules for consistent, accessible, and maintainable CSS. Written in
> plain English. Optimised for quick scanning and day‑to‑day use.

---

## Table of Contents

- [CSS Style Guide](#css-style-guide)
  - [Table of Contents](#table-of-contents)
  - [1. Principles](#1-principles)
  - [2. File structure](#2-file-structure)
  - [3. Cascade layers](#3-cascade-layers)
  - [4. Naming](#4-naming)
  - [5. Selectors \& specificity](#5-selectors--specificity)
  - [6. Tokens (custom properties)](#6-tokens-custom-properties)
  - [7. Units \& sizing](#7-units--sizing)
  - [8. Colour \& contrast](#8-colour--contrast)
  - [9. Typography](#9-typography)
  - [10. Layout](#10-layout)
  - [11. Motion \& animation](#11-motion--animation)
  - [12. Accessibility](#12-accessibility)
  - [13. Comments \& documentation](#13-comments--documentation)
  - [14. Performance](#14-performance)
  - [15. Browser support](#15-browser-support)
  - [16. Linting \& tooling](#16-linting--tooling)
  - [17. Git \& change control](#17-git--change-control)
  - [18. Example: component skeleton](#18-example-component-skeleton)
  - [19. Attribution](#19-attribution)
  - [20. References](#20-references)
  - [Appendix A – header block template](#appendix-a--header-block-template)

---

## 1. Principles

- **Clarity over cleverness.** Prefer readable CSS to micro‑optimisations.
- **Accessible by default.** Respect user preferences and contrast needs.
- **Predictable cascade.** Use cascade layers, small components, and low
  specificity.
- **Progressive enhancement.** New features with safe fallbacks.
- **Single source of truth.** Centralise tokens (colour, spacing, type, motion).

---

## 2. File structure

```text
styles/
  core.css          # @layer declarations + resets + tokens
  layout.css        # base page layout and common wrappers
  components.css    # reusable components
  utilities.css     # simple one‑off helpers
  pages/            # page‑specific overrides (last to load)
```

Load order (top → bottom): **core → layout → components → utilities → pages**.

---

## 3. Cascade layers

Declare the stack first. Keep rules inside layers.

```css
/* 1) Declare once, at the very top of core.css */
@layer base, theme, components, utilities, pages;

/* 2) Define inside layers */
@layer theme { /* tokens and colours */ }
@layer base { /* layout and scaffolding */ }
@layer components { /* buttons, cards, etc. */ }
@layer utilities { /* .u-text-center, .u-sr-only */ }
@layer pages { /* page-specific tweaks */ }
```

**Why**: predictable overrides and fewer specificity wars.

---

## 4. Naming

- **Components**: `.c-thing` (e.g. `.c-card`, `.c-modal`).
- **Elements**: `.c-card__header`.
- **Modifiers**: `.c-card--raised`.
- **State**: `.is-open`, `.is-invalid` (added by JS only).
- **Utilities**: `.u-hidden`, `.u-flow-300`.
- **JS hooks**: `[data-js="toggle"]` (never style by `js-` classes).

Keep names **short, specific, lower‑case**, with hyphens.

---

## 5. Selectors & specificity

- One class per rule where possible: `.c-card { … }`.
- Avoid ID selectors for styling. Use IDs for landmarks and ARIA targets only.
- Scope instance variables to a parent to **avoid leaks**:

```css
.c-blobs .d1 { --dx: 30s; }
```

- Avoid `!important` except in **utilities** (document why).

---

## 6. Tokens (custom properties)

Define in `@layer theme` under `:root`.

```css
@layer theme {
  :root {
    /* Colour (HSL preferred for easy theming) */
    --brand-h: 352; --brand-s: 50%; --brand-l: 53%;
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

Use tokens everywhere; avoid raw values in components.

---

## 7. Units & sizing

- **rem** for type and spacing. **px** only for borders/hairlines.
- Use **aspect-ratio** where possible. Avoid magic numbers.
- Prefer **min() / max() / clamp()** for responsive sizing.

```css
.c-hero { font-size: clamp(1rem, 1vw + 1rem, 1.5rem); }
```

---

## 8. Colour & contrast

- Use tokens; derive variants with **HSL** or colour‑mix.
- Minimum contrast: **WCAG AA** for text and UI.
- Reserve pure black/white for ink/background; avoid muddy greys.

```css
.c-button { background: var(--brand); color: white; }
```

---

## 9. Typography

- Define scale in theme. Use logical properties.
- Line length target: **45–85 ch**. Preserve readability.

```css
@layer theme {
  :root { --font-body: system-ui, sans-serif; }
}
body { font-family: var(--font-body); }
```

---

## 10. Layout

- Prefer **Grid** for page and complex layout; **Flexbox** for one‑dimensional.
- Use content‑driven gaps: `gap: var(--space-400);`
- Avoid fixed heights; use min/max and intrinsic sizing.

---

## 11. Motion & animation

- Respect reduced motion.
- Use the **global --speed** multiplier.
- Keep durations in the **200–700ms** range for UI.
- Animate **opacity, transform, filter**. Avoid layout‑thrashing properties.

```css
@media (prefers-reduced-motion: reduce) { * { animation: none; transition: none; } }
```

For SVG geometry animation, document support and provide sensible fallbacks.

---

## 12. Accessibility

- Always include reduced motion and focus‑visible rules.
- Hit area: **44×44px** minimum for touch actions.
- Do not rely on colour alone; add text, icons, or patterns.

```css
:focus-visible { outline: 2px solid currentColor; outline-offset: 2px; }
```

---

## 13. Comments & documentation

Use a **header docblock** per file and **targeted inline comments** only where
they add real value. Follow this template:

```css
/*
 * Component: Card
 * Purpose: Present content in a contained panel.
 * API: .c-card [--elevation], .c-card__header, .c-card__body
 * Accessibility: Focus states, contrast >= AA.
 * Risks: Long titles overflow → text-wrap: balance.
 * Changelog: 2025-11-05 Added compact variant.
 */
```

Inline comments explain **why**, not what:

```css
/* Push above adjacent image to preserve rhythm at small sizes */
margin-block-start: var(--space-300);
```

---

## 14. Performance

- Minimise repaint/reflow. Prefer `transform` over `top/left` in animations.
- Avoid deep descendant selectors.
- Audit unused CSS; set up coverage checks in CI.

---

## 15. Browser support

- Target **last 2 evergreen versions** and **current iOS/Android WebView**.
- Provide fallbacks for features behind flags or limited support.
- Document any known gaps in the component header.

---

## 16. Linting & tooling

- Use **Stylelint** with the standard config. Project overrides below.

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

Add Prettier for formatting. 2‑space indent, trailing newline, LF line endings.

---

## 17. Git & change control

- One change per commit. Imperative mood, short subject.
- Reference issue/PR IDs. Include **scope** when helpful.

```text
feat(card): add raised variant and tokens
```

Include a brief **why** in the body when non‑obvious.

---

## 18. Example: component skeleton

```css
/*
 * Component: Button
 * Purpose: Primary action trigger.
 * API: .c-button [.c-button--danger] [.is-loading]
 * Accessibility: Focus-visible ring; min target size; reduced motion.
 */
@layer components {
  .c-button {
    display: inline-grid; place-items: center;
    min-width: 10ch; min-height: 44px;
    padding-inline: var(--space-400);
    border-radius: 999px;
    background: var(--brand); color: white;
    transition: transform 200ms, box-shadow 200ms;
  }
  .c-button:focus-visible { outline: 2px solid white; outline-offset: 2px; }
  .c-button:is(:hover, :focus-visible) { transform: translateY(-1px); }
  .c-button--danger { background: color-mix(in oklab, var(--brand), red 40%); }
  .c-button.is-loading { pointer-events: none; opacity: 0.7; }
}
@media (prefers-reduced-motion: reduce) {
  .c-button { transition: none; }
}
```

---

## 19. Attribution

Credit any reused animation logic or design patterns in component headers.

---

## 20. References

- Google HTML/CSS Style Guide – structure, naming, and formatting.
- MDN – CSS cascade layers, custom properties, media features.
- WCAG 2.2 – contrast and focus requirements.

---

## Appendix A – header block template

```css
/*
 * File: components.css
 * Purpose: Reusable components styled with low specificity.
 * Owner: Frontend team
 * Changelog: 2025-11-05 initial version
 */
```
