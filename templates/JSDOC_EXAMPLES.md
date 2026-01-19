# JSDoc Examples (JS/TS)

Examples of clear, copy-pasteable JSDoc for JavaScript and TypeScript projects.

---

## JavaScript

```js
/**
 * Returns a random item from an array.
 * @template T
 * @param {T[]} items - The items to choose from.
 * @returns {T} A randomly selected item.
 */
export function getRandom(items) {
  return items[Math.floor(Math.random() * items.length)];
}
```

---

## TypeScript

```ts
/**
 * Returns unique authors (order preserved).
 * @param jokes - Array of joke objects containing an author property.
 * @returns Array of unique author names.
 */
export function getAuthors(jokes: { author: string }[]): string[] {
  const seen = new Set<string>();
  return jokes.map(j => j.author).filter(a => !seen.has(a) && seen.add(a));
}
```
