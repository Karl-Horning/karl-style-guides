# Git commit style guide

This document provides practical rules for writing clear and consistent commit messages. It is based on the Conventional Commits specification, with specific additions for user experience and accessibility.

## Table of Contents

- [Git commit style guide](#git-commit-style-guide)
  - [Table of Contents](#table-of-contents)
  - [Overview](#overview)
  - [Format](#format)
  - [Types](#types)
  - [Scope](#scope)
    - [Scope examples](#scope-examples)
  - [Summary](#summary)
    - [Recommended summaries](#recommended-summaries)
    - [Avoid these patterns](#avoid-these-patterns)
  - [Body](#body)
  - [Footer](#footer)
  - [Examples by type](#examples-by-type)
    - [feat](#feat)
    - [fix](#fix)
    - [docs](#docs)
    - [style](#style)
    - [refactor](#refactor)
    - [test](#test)
    - [chore](#chore)
    - [ux](#ux)
    - [a11y](#a11y)
  - [Configuration template](#configuration-template)
  - [Common mistakes](#common-mistakes)
  - [Maintenance](#maintenance)

## Overview

A documented commit message explains what changed and why it changed. This practice assists in tracing intent, accelerating debugging, and maintaining a legible project history.

## Format

Each commit must encompass one clear objective. Wrap body lines at approximately 72 characters.

```text
<type>[optional scope]: <short summary>

[optional body]

[optional footer(s)]
```

## Types

| Type | Purpose | Example |
| --- | --- | --- |
| `feat` | Add a new feature | `feat(api): add search by region` |
| `fix` | Correct a bug | `fix(header): prevent flicker on load` |
| `refactor` | Improve structure or clarity without changing behavior | `refactor(utils): extract parseDate helper` |
| `docs` | Update documentation only | `docs: add setup steps to README` |
| `style` | Change formatting or whitespace only | `style: format files with Prettier` |
| `test` | Add or modify tests | `test(api): add missing auth tests` |
| `chore` | Maintenance or tooling updates | `chore: update ESLint config` |
| `build` | Build system or dependency changes | `build: upgrade Next.js to v15` |
| `ci` | CI/CD config updates | `ci: fix deploy job on main` |
| `perf` | Performance improvements | `perf(layout): memoize expensive render` |
| `ux` | Visual or usability tweaks | `ux(nav): improve focus outline visibility` |
| `a11y` | Accessibility fixes (ARIA, color, keyboard) | `a11y(button): add aria-pressed state` |

## Scope

Describe where the change happens, such as a module, file, or feature. Skip the scope if it adds no clarity.

- Use lowercase text.
- Keep the description to one or two words.

### Scope examples

```bash
feat(layout): add hero image support
fix(reading-time): correct logic for empty content
docs(api): update JSDoc for getUserToken
```

## Summary

The summary provides a brief explanation of the change. State what changed, not how it was implemented.

- Use the imperative mood (e.g., "add", not "added").
- Do not use punctuation at the end of the line.
- Keep the character count under 50.

### Recommended summaries

```bash
feat: add reading time calculation
fix(header): show fallback image if missing
refactor: move logic to useEffect hook
```

### Avoid these patterns

```bash
added new layout feature
fixes reading-time bug.
Refactored layout logic
```

## Body

Use the body to explain the reasoning behind the code change.

```bash
refactor(layout): move reading time logic to useEffect

Previously, reading time was injected via a <Script> tag,
causing hydration issues. It now runs in a useEffect hook
after render for better React compatibility.
```

## Footer

Use the footer to document issue links or breaking changes.

```bash
BREAKING CHANGE: removed deprecated layout prop

Closes #42
```

## Examples by type

### feat

```bash
feat(layout): add sidebar toggle for mobile
feat(a11y): support high contrast mode
```

### fix

```bash
fix(header): prevent flicker on page load
fix(api): handle missing query params safely
```

### docs

```bash
docs: update README quick start
docs(api): clarify prop defaults
```

### style

```bash
style: reformat layout files with Prettier
```

### refactor

```bash
refactor(api): rename variables for clarity
```

### test

```bash
test(layout): add snapshot test
```

### chore

```bash
chore: update Tailwind to v3.4.0
```

### ux

```bash
ux(header): improve spacing between title and metadata
```

### a11y

```bash
a11y(layout): ensure contrast in dark mode
```

## Configuration template

You can enforce this structure locally using a Git template.

```bash
# .gitmessage
<type>(<scope>): <summary>

<body>

<footer>
```

Enable the template globally using the following command:

```bash
git config --global commit.template ~/.gitmessage
```

## Common mistakes

| Mistake | Issue | Correct form |
| --- | --- | --- |
| `Added new feature` | Uses past tense | `feat: add new feature` |
| `fix: fixed bug` | Repeats type | `fix: correct error in API call` |
| `chore: misc updates` | Too vague | `chore(deps): bump Next.js` |
| `feat(layout):` | Missing summary | `feat(layout): add sidebar toggle` |

## Maintenance

- Treat this guide as a living document and update it when new conventions emerge.
- Review the document periodically to ensure it matches actual commit practices.
- Add new types or scopes only when they serve clear structural value.
- Keep all examples functional and copy-pasteable.
- Remove conventions that no longer reflect active team standards.
