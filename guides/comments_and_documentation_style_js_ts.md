# Comments & Documentation Style (JS/TS)

Simple rules for **clear, accessible, tool-friendly** docs. Adapted in part from [Google’s TypeScript Style Guide](https://google.github.io/styleguide/tsguide.html#comments-documentation).

---

## Table of Contents

- [Comments \& Documentation Style (JS/TS)](#comments--documentation-style-jsts)
  - [Table of Contents](#table-of-contents)
  - [Scope \& Intent](#scope--intent)
  - [JSDoc: General Rules](#jsdoc-general-rules)
    - [Bad list in prose](#bad-list-in-prose)
    - [Good Markdown list](#good-markdown-list)
  - [JSDoc in TypeScript vs JavaScript](#jsdoc-in-typescript-vs-javascript)
    - [TS example](#ts-example)
    - [JS example](#js-example)
  - [Functions \& Methods](#functions--methods)
  - [Classes \& Parameter Properties (TS)](#classes--parameter-properties-ts)
  - [Module (File) Docs](#module-file-docs)
  - [Line Comments (`//`)](#line-comments-)
  - [Call-site "parameter name" comments](#call-site-parameter-name-comments)
  - [Decorators (TS/Frameworks)](#decorators-tsframeworks)
  - [Accessibility Guidelines](#accessibility-guidelines)
  - [Do / Don't](#do--dont)
  - [Quick Examples](#quick-examples)
    - [Good single-line](#good-single-line)
    - [Good multi-line with tags](#good-multi-line-with-tags)
  - [Maintenance](#maintenance)
  - [Author](#author)

---

## Scope & Intent

- **JSDoc (`/** … */`)** → **API docs** users of the code should read.
- **Line comments (`// …`)** → **implementation notes** for maintainers.
- **Multi-line** remarks use **stacked `//`**, not `/* … */`.

---

## JSDoc: General Rules

- First line is a **complete sentence in third person**, ending with a **period**.
- Prefer **imperative voice** ("Return…" instead of "Returns…").
- Place JSDoc **immediately above** the symbol, with one space before the code.
- Use **Markdown** (lists, code fences). No decorative boxes.
- **One tag per line**, in this canonical order:
  1. `@param`
  1. `@returns`
  1. `@throws`
  1. `@deprecated`
  1. `@example`
- **Wrap ~80 chars** for readability.
- **Document all top-level exports** and any non-obvious symbols.
- **Avoid redundancy** — do not restate variable names or trivial logic.

### Bad list in prose

```js
/**
 * Compute weight from: items sent, items received, last timestamp
 */
```

### Good Markdown list

```js
/**
 * Compute weight based on:
 * - items sent
 * - items received
 * - last timestamp
 */
```

---

## JSDoc in TypeScript vs JavaScript

- **TypeScript:** **do not duplicate types** in JSDoc. No `@param {Type}`.
- **JavaScript:** JSDoc **may include types** to aid tooling.

### TS example

```ts
/** Return unique authors (order preserved). */
export function getAuthors(jokes: { author: string }[]): string[] { /* … */ }
```

### JS example

```js
/** @param {{author:string}[]} jokes @returns {string[]} */
export function getAuthors(jokes) { /* … */ }
```

---

## Functions & Methods

- Method descriptions **start with a verb phrase** ("Return…", "Filter…").
- Omit `@param/@returns` **if the name/signature is obvious**; include when it adds meaning.

```js
/** Filter jokes by optional author/category/nsfw flags.
 *
 * - Case-insensitive string matching.
 * - Returns a new array (no mutation).
 *
 * @param {Object[]} jokes
 * @param {{author?:string, category?:string, nsfw?:boolean}} opts
 * @returns {Object[]}
 */
export function filterJokes(jokes, opts) { /* … */ }
```

---

## Classes & Parameter Properties (TS)

- Class JSDoc explains **how/when** to use it.
- For **parameter properties**, document with `@param`.

```ts
/** Cache jokes for fast lookup by id. */
export class JokeCache {
  /** @param store In-memory map used for storage. */
  constructor(private readonly store: Map<string, unknown>) {}
}
```

---

## Module (File) Docs

- Every file that exports symbols should start with a `@file` or `@fileoverview` JSDoc.
- The first line must be a **short, complete sentence** ending with a **period**.
- Summarise **the file’s purpose**; include an example if useful.

```js
/**
 * @fileoverview Helpers for list pagination and sorting.
 *
 * @example
 * paginate([1,2,3,4], {page:2, limit:2}) // → [3,4]
 */
```

---

## Line Comments (`//`)

- Explain **why**, not the obvious **what**.
- Avoid restating logic or variable names; focus on reasoning or constraints.
- Keep near the code; prefer short sentences.

```js
// Clamp to avoid huge responses and memory spikes.
const limit = Math.min(100, Math.max(10, Number(q.limit) || 20));
```

---

## Call-site "parameter name" comments

Use when the value's intent isn't obvious.

```js
renderList(items, /* shouldRender= */ true, /* name= */ "popular");
```

Prefer redesigning the API to accept an object if this appears often.

---

## Decorators (TS/Frameworks)

Place JSDoc **before** decorators; never between decorator and declaration.

```ts
/** Component that prints "bar". */
@Component({ selector: "foo", template: "bar" })
export class FooComponent {}
```

---

## Accessibility Guidelines

- Write **short, concrete** sentences; avoid jargon.
- Prefer **descriptive lists** over dense prose.
- Keep examples **copy-pasteable**.
- Use **consistent terms**; avoid synonym switching.
- Keep line length ~**80 chars** for screen readers and diffs.

---

## Do / Don't

Do:

- Document exports; explain intent and constraints.
- Use Markdown lists in JSDoc.
- Stack `//` for multi-line implementation notes.

Don't:

- Don't restate names/types in TS JSDoc.
- Don't use ASCII art boxes.
- Don't narrate trivial code.

---

## Quick Examples

### Good single-line

```js
/** Return a random joke from the dataset. */
export function getRandom(jokes) { /* … */ }
```

### Good multi-line with tags

```js
/** Send a standardised JSON response.
 *
 * - Sets Content-Type and Cache-Control headers.
 *
 * @param {import('express').Response} res
 * @param {*} data
 * @param {number} [status=200]
 * @returns {import('express').Response}
 */
export function sendJson(res, data, status = 200) { /* … */ }
```

---

## Maintenance

- Treat this guide as **living** — update it when new conventions or tools emerge.
- Keep examples **accurate and copy-pasteable**.
- Align terminology with real project usage.
- Remove outdated or redundant rules promptly to avoid confusion.
- Use ESLint with `eslint-plugin-jsdoc` to validate tag order, punctuation, and spacing.

---

## Author

Made with ❤️ by [Karl Horning](https://github.com/Karl-Horning)
