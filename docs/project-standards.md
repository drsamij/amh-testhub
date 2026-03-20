# Project Standards

## Code Style

- **No framework** — vanilla HTML, CSS, JavaScript only
- Use CSS custom properties from `:root` for all colors, spacing, and radii
- Follow existing naming: `camelCase` for JS functions/variables, `kebab-case` for CSS classes
- Keep all code in `index.html` unless a compelling reason exists to split
- Bilingual: every user-facing string must have both English and Arabic variants

## CSS

- Use existing CSS variables (`--pri`, `--bg`, `--card`, `--text`, `--border`, etc.)
- Mobile-first responsive design; breakpoints at 768px and 480px
- Minimum touch target: 44px height for interactive elements
- RTL support via `.ar` class on `<body>`

## JavaScript

- Global scope functions (no module system)
- Debounce auto-save at 800ms
- Use `esc()` helper for any user-generated content rendered as HTML
- Use `toast()` for user feedback messages
- Store data via `localStorage` with `amh_` prefix

## Commit Standards

- Short imperative subject line (<72 chars)
- Reference the affected module (e.g., "Fix appointment cancel flow in Tester tab")
- One logical change per commit

## Security

- Never log or expose patient data
- Sanitize all rendered user input via `esc()`
- Admin password changes require explicit approval
- No inline `eval()` or dynamic script injection
