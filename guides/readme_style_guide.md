# README Style Guide

Short, practical rules for **clear, consistent, and accessible READMEs**. This guide is designed to make documents easier to **read, navigate, and maintain**, improving accessibility for all contributors and users.

---

## Table of Contents

- [README Style Guide](#readme-style-guide)
  - [Table of Contents](#table-of-contents)
  - [Required Sections](#required-sections)
    - [1) Title](#1-title)
    - [2) Overview](#2-overview)
    - [3) Quick Start](#3-quick-start)
    - [4) Usage / Scripts](#4-usage--scripts)
    - [5) Project Structure](#5-project-structure)
    - [6) License](#6-license)
  - [Optional Sections](#optional-sections)
    - [Badges](#badges)
    - [Live / Demo](#live--demo)
    - [Tech Stack](#tech-stack)
    - [Configuration](#configuration)
    - [Contributing](#contributing)
    - [Testing](#testing)
    - [Roadmap](#roadmap)
    - [🙋FAQ / Known Issues](#faq--known-issues)
  - [Formatting Rules](#formatting-rules)
  - [♿ Accessibility \& Tone](#-accessibility--tone)
  - [Maintenance](#maintenance)
  - [Author](#author)

---

## Required Sections

### 1) Title

One H1, clear and complete.

- **Use:** Project name + short tagline.
- **Example:** `# GetOneLiner — Tiny JSON jokes API`

### 2) Overview

1–3 sentences answering **what**, **why**, **who for**.

- **Use:** State purpose and scope; link to docs if they exist.

### 3) Quick Start

Minimal steps to run in dev.

- **Use:** Shell fenced block; prefer copy-paste commands.
- **Example:**

  ```bash
  npm install
  npm run dev
  ```

### 4) Usage / Scripts

How to use or run scripts.

- **Use:** Table or hyphen lists with short, action-led descriptions.

### 5) Project Structure

Show key folders only.

- **Use:** Tree with comments; avoid noise.

  ```text
  src/
  ├─ controllers/   # HTTP handlers
  ├─ routes/        # Express routers
  └─ utils/         # Pure helpers
  ```

### 6) License

Name the licence (e.g. MIT) or say "All rights reserved".

- **Use:** Link to `LICENSE`.

---

## Optional Sections

### Badges

High-value only (build, coverage, version).

### Live / Demo

One link and/or one screenshot.

### Tech Stack

- Bullets with versions if important.

### Configuration

- List required env vars and defaults.

### Contributing

- How to propose changes; link to `CONTRIBUTING.md` if present.

### Testing

- How to run tests; note frameworks.

### Roadmap

- Only if actively maintained; use short checklists.

### 🙋FAQ / Known Issues

- Small, focused lists.

---

## Formatting Rules

- **Headings:** ATX `#` style; **one H1 per file**. Space before/after headings.
- **Lists:** Use **hyphens (`-`)** for unordered lists.
  Use lazy numbering for long ordered lists.
- **Code blocks:** **Fence** with language (e.g. `bash`, `js`). Prefer fenced over indented.
- **Links:** Prefer explicit repo-relative paths; avoid deep `../..` hops.
- **Tables:** Only for real tabular data; otherwise use lists.
- **Markdown over HTML:** Prefer plain Markdown for portability.

---

## ♿ Accessibility & Tone

- Use **emojis** in H1 and H2 headings to improve scanning and recognition.
- Avoid **smart quotes** and **curly apostrophes** — use straight quotes (`"` and `'`) for better readability and consistency.
  ⚠️ **(This rule doesn’t apply to code enclosed in backticks.)**
- Use **hyphens (`-`)** for bullet points to make lists easier to scan, especially when they include bold or italicised text.
- Reserve *italics* for rare cases (e.g., technical terms or examples). Overuse can reduce readability and increase visual strain; prefer **bold** for emphasis.
- Add **horizontal rules (`---`)** between major H2 sections for visual separation.
- Include **alt text** for all images — describe what’s shown and why it matters. Avoid decorative images without a clear purpose.
- Write **short, direct sentences** and avoid jargon where possible.
- Ensure **copy-pasteable examples** — no placeholder text or truncated code.

---

## Maintenance

- Treat README as **living**: update with meaningful changes.
- Remove stale sections quickly ("better over best").
- Keep examples **copy-pasteable** and tested.

---

## Author

Made with ❤️ by [Karl Horning](https://github.com/Karl-Horning)
