# Copilot Instructions

## Architecture

This is a static personal portfolio site with no build step. There are four files that work together:

- **`data.js`** — Single source of truth. Exports a `const main` object containing all site content (name, email, avatar URL, social links, internal links).
- **`script.js`** — Reads from `main` and populates DOM elements by ID. Uses a lazy `getDOM(selector)` factory that returns a function, so DOM nodes are queried at call time (e.g., `dom.main.name()` not `dom.main.name`).
- **`index.html`** — Bare shell with empty elements (IDs: `#name`, `#role`, `#mail`, `#img`, `#connects`, `#links`). Script fills them at runtime.
- **`index.css`** — Desktop-only overrides (`lg:` breakpoint) for vertical centering; Tailwind handles everything else.

## Key Conventions

**All content changes go in `data.js` only.** The HTML and JS are structural and should not need editing for content updates.

**Social/connect icons use [Ionicons](https://ionicons.com/).** Each entry in `main.connects` requires a `name`, `iconName` (from Ionicons), and `link`. Icons render as `<ion-icon name="...">` via the Ionicons CDN script in `index.html`.

**Dependencies are CDN-only** (Tailwind CSS `^2` and Ionicons `5.0.0` via unpkg). There is no `package.json`, no bundler, and no install step.

**Layout is mobile-first Tailwind + desktop CSS.** Tailwind utility classes handle mobile layout; `index.css` adds the vertical-centering logic for `lg:` (1024px+) screens only.

## Running Locally

Open `index.html` directly in a browser, or serve with any static server:

```sh
npx serve .
# or
python3 -m http.server
```
