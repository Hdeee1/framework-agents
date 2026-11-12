---
trigger: glob
globs: "**/*.tsx, **/*.jsx, **/*.html, **/*.css, **/*.scss, **/*.vue, **/*.svelte, **/*.astro"
description: "Web frontend standards for accessibility, performance, component architecture, and browser security."
---

# Web Frontend Standards

## Semantics & Accessibility (WCAG 2.2 AA)

- **Semantic HTML First:** Use native interactive elements (`<button>`, `<a>`, `<nav>`, `<main>`, `<label>`, `<dialog>`) before adding ARIA attributes.
- **Keyboard & Focus:** Ensure all interactive controls are operable via keyboard alone (`Tab`, `Enter`, `Space`, `Escape`) with a visible `:focus-visible` indicator and a minimum contrast ratio of `4.5:1` for normal text.
- **Forms & Media:** Associate every form input with an explicit `<label>` and programmatic error description (`aria-describedby` / `aria-invalid`). Provide meaningful `alt` text for informative images and `alt=""` for decorative images.
- **User Preferences & Viewport:** Respect `prefers-reduced-motion` and `prefers-color-scheme`. Build responsive layouts that render without unintended horizontal scrolling from `320px` width upward; never rely solely on hover for core actions.

## Performance & Asset Loading

- **Core Web Vitals Targets:** LCP `< 2.5s`, INP `< 200ms`, CLS `< 0.1`.
- **Media & Fonts:** Specify explicit `width` and `height` (or `aspect-ratio`) on images and embeds to prevent layout shift. Use `loading="lazy"` for below-the-fold media and `font-display: swap` for WOFF2 web fonts.
- **Bundle Discipline:** Split bundles at route boundaries and lazy-load heavy non-critical views. Import specific submodules rather than entire utility libraries when tree-shaking is not guaranteed.

## Component & State Architecture

- **Single Responsibility:** Separate data-fetching/business state hooks or stores from presentational UI components.
- **Explicit UI States:** Every asynchronous view or form submission must explicitly handle and render four states: `loading`, `error`, `empty`, and `success` (preventing duplicate submissions while in flight).
- **Design Tokens:** Use project CSS variables or theme tokens for colors, spacing, and typography instead of arbitrary hardcoded pixel/hex values.

## Browser Security

- **XSS Prevention:** Never inject unsanitized data into raw HTML sinks (`innerHTML`, `dangerouslySetInnerHTML`, `v-html`). If rich HTML rendering is strictly required, sanitize with a vetted HTML sanitizer first.
- **Auth & Links:** Prefer `HttpOnly; Secure; SameSite` cookies over `localStorage` for sensitive session tokens. Add `rel="noopener noreferrer"` to external links opening in a new tab.
