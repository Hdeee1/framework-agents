---
trigger: glob
globs: "**/*.tsx, **/*.jsx, **/*.html, **/*.css, **/*.scss, **/*.vue, **/*.svelte, **/*.astro"
description: "Web frontend standards: accessibility, performance, component architecture, browser security."
---

# Web Frontend Standards

Applies only if the project renders a web UI. Otherwise ignore this file.

## Semantics & Accessibility (WCAG 2.2 AA)

- Use native elements (`<button>`, `<a>`, `<nav>`, `<main>`, `<label>`, `<dialog>`) before adding ARIA.
- All controls must work by keyboard (`Tab`, `Enter`, `Space`, `Escape`), show a visible `:focus-visible` indicator, and keep text contrast at least `4.5:1`.
- Give every input an explicit `<label>` and programmatic error text (`aria-describedby` / `aria-invalid`). Informative images need meaningful `alt`; decorative images use `alt=""`.
- Respect `prefers-reduced-motion` and `prefers-color-scheme`. Layouts must not scroll horizontally from `320px` width up. Never rely on hover alone for core actions.

## Performance

- Targets: LCP `< 2.5s`, INP `< 200ms`, CLS `< 0.1`.
- Set `width`/`height` or `aspect-ratio` on images and embeds. Use `loading="lazy"` below the fold and `font-display: swap` for WOFF2 fonts.
- Split bundles at route boundaries and lazy-load heavy non-critical views. Import submodules, not whole utility libraries, when tree-shaking is not guaranteed.

## Components & State

- Separate data-fetching/business state from presentational components.
- Every async view or form must render `loading`, `error`, `empty`, and `success` states and block duplicate submission while in flight.
- Use the project's CSS variables or theme tokens, not hardcoded hex/pixel values.

## Browser Security

- Never put unsanitized data into raw HTML sinks (`innerHTML`, `dangerouslySetInnerHTML`, `v-html`). If raw HTML is required, sanitize with a vetted sanitizer first.
- Store session tokens in `HttpOnly; Secure; SameSite` cookies, not `localStorage`. Add `rel="noopener noreferrer"` to links opened in a new tab.
