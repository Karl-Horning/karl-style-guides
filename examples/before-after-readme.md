# README Examples — Before / After

Short examples showing how the README Style Guide improves clarity and accessibility.

---

## Before

- Long paragraphs without structure.
- No Quick Start or Usage section.
- Inconsistent headings and no licence info.

> our project lets you do a bunch of stuff. install it however you want.
> we might add docs later. it probably works on windows.

---

## After

### Overview

A small tool for converting CSV files to JSON.

### Quick Start

`npm install`
`npm run convert input.csv > output.json`

### Usage / Scripts

- `npm run convert <file>` — convert CSV to JSON.

### Project Structure

```text

src/
├─ cli/        # command-line entry points
└─ lib/        # pure helpers

```

### License

[MIT](../LICENSE)
