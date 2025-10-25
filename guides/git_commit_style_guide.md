# 📝 Git Commit Style Guide

Short, practical rules for **clear, consistent commits**.
Based on [Conventional Commits](https://www.conventionalcommits.org/), with extras for **UX** and **accessibility**.

---

## 📖 Table of Contents

- [📝 Git Commit Style Guide](#-git-commit-style-guide)
  - [📖 Table of Contents](#-table-of-contents)
  - [📖 Overview](#-overview)
  - [✨ Format](#-format)
  - [✅ Types](#-types)
  - [🗂 Scope (Optional)](#-scope-optional)
    - [🔍 Examples](#-examples)
  - [🧠 Summary (Required)](#-summary-required)
    - [✅ Good Examples](#-good-examples)
    - [❌ Avoid](#-avoid)
  - [📝 Body (Optional)](#-body-optional)
  - [🚨 Footer (Optional)](#-footer-optional)
  - [💡 Examples by Type](#-examples-by-type)
    - [`feat`](#feat)
    - [`fix`](#fix)
    - [`docs`](#docs)
    - [`style`](#style)
    - [`refactor`](#refactor)
    - [`test`](#test)
    - [`chore`](#chore)
    - [`ux`](#ux)
    - [`a11y`](#a11y)
  - [📁 Optional Template](#-optional-template)
  - [⚠️ Common Mistakes](#️-common-mistakes)
  - [🔚 Summary](#-summary)
    - [Why this matters](#why-this-matters)
  - [🔧 Maintenance](#-maintenance)
  - [👤 Author](#-author)

---

## 📖 Overview

A good commit message tells **what** changed and **why**.
It helps you trace intent, debug faster, and keep a clean history.

---

## ✨ Format

```text
<type>[optional scope]: <short summary>

[optional body]

[optional footer(s)]
```

Each commit should do **one clear thing**.
Wrap body lines at **~72 chars**.

---

## ✅ Types

| Type       | Purpose | Example |
| ---------- | ------- | ------- |
| `feat`     | Add a new feature | `feat(api): add search by region` |
| `fix`      | Correct a bug | `fix(header): prevent flicker on load` |
| `refactor` | Improve structure or clarity without changing behaviour | `refactor(utils): extract parseDate helper` |
| `docs`     | Update documentation only | `docs: add setup steps to README` |
| `style`    | Change formatting or whitespace only | `style: format files with Prettier` |
| `test`     | Add or modify tests | `test(api): add missing auth tests` |
| `chore`    | Maintenance or tooling updates | `chore: update ESLint config` |
| `build`    | Build system or dependency changes | `build: upgrade Next.js to v15` |
| `ci`       | CI/CD config updates | `ci: fix deploy job on main` |
| `perf`     | Performance improvements | `perf(layout): memoise expensive render` |
| `ux`       | Visual or usability tweaks | `ux(nav): improve focus outline visibility` |
| `a11y`     | Accessibility fixes (ARIA, colour, keyboard) | `a11y(button): add aria-pressed state` |

---

## 🗂 Scope (Optional)

Describe **where** the change happens — a module, file, or feature.

- Use lowercase
- Keep it short (1–2 words)
- Skip if it adds no clarity

### 🔍 Examples

```bash
feat(layout): add hero image support
fix(reading-time): correct logic for empty content
docs(api): update JSDoc for getUserToken
```

---

## 🧠 Summary (Required)

- Use **imperative mood** — “add”, not “added”
- **No punctuation** at the end
- Stay under **50 chars** when possible
- Say **what** changed, not **how**

### ✅ Good Examples

```bash
feat: add reading time calculation
fix(header): show fallback image if missing
refactor: move logic to useEffect hook
```

### ❌ Avoid

```bash
added new layout feature
fixes reading-time bug.
Refactored layout logic
```

---

## 📝 Body (Optional)

Explain the **reasoning** behind the change.

```bash
refactor(layout): move reading time logic to useEffect

Previously, reading time was injected via a <Script> tag,
causing hydration issues. It now runs in a useEffect hook
after render for better React compatibility.
```

---

## 🚨 Footer (Optional)

Use for issue links or breaking changes.

```bash
BREAKING CHANGE: removed deprecated layout prop

Closes #42
```

---

## 💡 Examples by Type

### `feat`

```bash
feat(layout): add sidebar toggle for mobile
feat(a11y): support high contrast mode
```

### `fix`

```bash
fix(header): prevent flicker on page load
fix(api): handle missing query params safely
```

### `docs`

```bash
docs: update README quick start
docs(api): clarify prop defaults
```

### `style`

```bash
style: reformat layout files with Prettier
```

### `refactor`

```bash
refactor(api): rename variables for clarity
```

### `test`

```bash
test(layout): add snapshot test
```

### `chore`

```bash
chore: update Tailwind to v3.4.0
```

### `ux`

```bash
ux(header): improve spacing between title and metadata
```

### `a11y`

```bash
a11y(layout): ensure contrast in dark mode
```

---

## 📁 Optional Template

```bash
# .gitmessage
<type>(<scope>): <summary>

<body>

<footer>
```

Enable it globally:

```bash
git config --global commit.template ~/.gitmessage
```

---

## ⚠️ Common Mistakes

| Mistake | Why it’s a problem | Correct form |
| ------- | ------------------ | ------------ |
| `Added new feature` | Uses past tense | `feat: add new feature` |
| `fix: fixed bug` | Repeats type | `fix: correct error in API call` |
| `chore: misc updates` | Too vague | `chore(deps): bump Next.js` |
| `feat(layout):` *(empty)* | Missing summary | `feat(layout): add sidebar toggle` |

---

## 🔚 Summary

| ✅ Do | ❌ Avoid |
| ---- | -------- |
| Use imperative mood | Past tense |
| Keep one idea per commit | “misc fixes” |
| Add scope for clarity | Over-describing |
| Keep format consistent | Skipping colons or types |

---

### Why this matters

- Makes history searchable
- Clarifies intent
- Reduces mental load in reviews

---

## 🔧 Maintenance

- Treat this guide as **living** — update it when new conventions or tools emerge.
- Review periodically to ensure it matches actual commit practices.
- Add new **types** or **scopes** only when they serve clear value.
- Keep examples **copy-pasteable** and tested.
- Remove or update any conventions that no longer reflect team standards.

---

## 👤 Author

Made with ❤️ by [Karl Horning](https://github.com/Karl-Horning)
