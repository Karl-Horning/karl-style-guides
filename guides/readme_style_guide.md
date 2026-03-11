# Project documentation standard

Short, practical rules for clear, consistent, and accessible documentation. This guide aligns with Google's developer documentation style to ensure objective and maintainable repositories.

## Required sections

### Title

Create one H1 header containing the project name and a brief tagline.

- **Example:** `# GetOneLiner — Tiny JSON jokes API`

### Overview

Write one to three sentences defining the purpose and scope. Link to external documentation where applicable.

### Quick start

Document the minimal steps required to run the project in a development environment.

- **Use:** Fenced code blocks with the language specified.
- **Example:**

```bash
  npm install
  npm run dev
```

### Usage and scripts

Describe interactions using tables or hyphenated lists with short, action-led descriptions.

### Project structure

Display key directories using a text-based tree structure. Avoid listing every file to reduce noise.

**Example:**

```text
src/
├─ controllers/   # HTTP handlers
├─ routes/        # Express routers
└─ utils/         # Pure helpers
```

### License

State the license type or specify if all rights are reserved. Link directly to the license file.

## Optional sections

- **Badges:** Include only high-value badges such as build status, coverage, or version.
- **Live demo:** Provide one descriptive link or one screenshot.
- **Tech stack:** Detail the stack using bullet points with version numbers if necessary.
- **Configuration:** List required environment variables and their default values.
- **Contributing:** Explain how to propose changes and link to the contributing document.
- **Testing:** Explain how to run tests and specify the frameworks used.
- **Roadmap:** Include short checklists only if the project is actively maintained.
- **FAQ and known issues:** Keep lists small and focused.

## Formatting rules

- **Headings:** Use sentence case for all headings and ensure there is only one H1 per file. Include space before and after headings.
- **Lists:** Use hyphens (`-`) for unordered lists and lazy numbering for long ordered lists.
- **Code blocks:** Always use fenced blocks with language identifiers and prefer them over indented blocks.
- **Links:** Prefer explicit repository-relative paths instead of deep directory hops.
- **Tables:** Use tables only for strictly tabular data; otherwise, use lists.
- **Markup:** Prefer plain Markdown over HTML to maintain portability.

## Accessibility and tone

- **Emojis:** Avoid emojis in headings to ensure compatibility with screen readers and maintain professional neutrality.
- **Punctuation:** Use straight quotes (`"` and `'`) instead of smart quotes to improve readability and consistency.
- **Visual separation:** Avoid manual horizontal rules (`---`) between major sections. Allow the platform's native heading styles (e.g., GitHub's H2 borders) to provide natural structural breaks.
- **Alt text:** Provide descriptive alt text for all images explaining their purpose. Avoid decorative images without clear value.
- **Tone:** Write short, direct sentences, avoid jargon, and ensure all examples are completely copy-pasteable without placeholder text.
- **Emphasis:** Use bold text for emphasis. Reserve italics for technical terms to reduce visual strain.

## Maintenance

- Treat the documentation as a living document and update it alongside meaningful code changes.
- Remove stale sections quickly to prioritise accuracy.
- Ensure all code examples remain fully functional and tested.
