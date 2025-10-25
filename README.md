# 🧭 Developer Style Guides

[![Lint & Spellcheck](https://github.com/Karl-Horning/karl-style-guides/actions/workflows/lint.yml/badge.svg)](https://github.com/Karl-Horning/karl-style-guides/actions/workflows/lint.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

Concise, practical rules for **readable, consistent, and accessible** documentation and commits.
This repository collects style guides and templates designed to make text-based resources easier to **read, navigate, and maintain**.

---

## 📖 Table of Contents

- [🧭 Developer Style Guides](#-developer-style-guides)
  - [📖 Table of Contents](#-table-of-contents)
  - [🤓 Overview](#-overview)
  - [🚀 Quick Start](#-quick-start)
  - [🧩 Contents](#-contents)
    - [📚 Guides](#-guides)
    - [🧠 Templates](#-templates)
    - [🧪 Examples](#-examples)
  - [🧱 Formatting Rules](#-formatting-rules)
  - [♿ Accessibility \& Tone](#-accessibility--tone)
  - [🔧 Maintenance](#-maintenance)
  - [👤 Author](#-author)

---

## 🤓 Overview

A personal collection of **living documents** defining standards for writing and maintaining:

- Project READMEs
- Git commit messages
- Code comments and JSDoc in JS/TS projects

They follow accessibility and readability principles to reduce cognitive load and improve collaboration.

---

## 🚀 Quick Start

Clone the repository and explore the `guides/` folder:

```bash
git clone https://github.com/Karl-Horning/karl-style-guides.git
cd karl-style-guides/guides
```

Optionally copy templates for your own projects:

```bash
cp -r templates/* ~/your-project/
```

---

## 🧩 Contents

### 📚 Guides

- **README Style Guide** — `guides/readme_style_guide.md`
- **Git Commit Style Guide** — `guides/git_commit_style_guide.md`
- **Comments & Documentation Style (JS/TS)** — `guides/comments_and_documentation_style_js_ts.md`
  *(Adapted in part from [Google’s TypeScript Style Guide](https://google.github.io/styleguide/tsguide.html#comments-documentation))*

### 🧠 Templates

- `templates/README_TEMPLATE.md`
- `templates/.gitmessage`
- `templates/JSDOC_EXAMPLES.md`

### 🧪 Examples

- `examples/before-after-readme.md`
- `examples/commit-messages.md`

---

## 🧱 Formatting Rules

- **Headings:** One H1 per file; clear emoji for quick scanning.
- **Lists:** Use hyphens (`-`) for unordered lists.
- **Code blocks:** Use fenced code with a language tag.
- **Links:** Prefer absolute or repo-relative links.
- **Tables:** Only when data requires grid layout.

---

## ♿ Accessibility & Tone

- Avoid **smart quotes** and **curly apostrophes** — use straight quotes (`"` and `'`) for readability.
  ⚠️ *(Does not apply to code in backticks.)*
- Use **hyphens (`-`)** for bullet points to make lists easier to scan.
- Reserve *italics* for rare cases (e.g. technical terms or examples).
- Include **alt text** for all images — describe what’s shown and why it matters; avoid decorative images without purpose.
- Write **short, direct sentences** and prefer plain English.
- Keep examples **copy-pasteable** and tested.

---

## 🔧 Maintenance

- Treat this repository as **living** — update when new conventions or tools emerge.
- Keep examples accurate and templates usable.
- Align terminology with real project usage.
- Remove or revise outdated rules promptly.

---

## 👤 Author

Made with ❤️ by [Karl Horning](https://github.com/Karl-Horning)
