# Claude Instructions

Always follow:
- docs/project-standards.md
- docs/architecture.md
- docs/domain-context.md
- docs/workflows.md

Before making changes:
- Understand the affected module
- Check whether approval is required
- Avoid changing production-critical areas without explicit confirmation
- Add or update tests for all new logic
- Update documentation if behavior changes

Never change without approval:
- Core business rules
- Approval logic
- Permissions and roles
- Financial calculations (payments, invoices)
- Production integrations
- Security controls (admin password, data export)

## Project Quick Reference

- **App**: AMH Patient App — Test Hub v3.0
- **Stack**: Single-file vanilla HTML/CSS/JS (`index.html`, ~2500 lines)
- **Dependencies**: Chart.js 4.4.1 (CDN), Google Fonts (DM Sans, Noto Kufi Arabic)
- **Storage**: Browser localStorage (keys prefixed `amh_`)
- **Bilingual**: English + Arabic (RTL)
- **Preview**: Open `index.html` in browser — no build step required

## Code Layout

- CSS variables: `:root` block (line ~16)
- HTML markup: lines ~1–492
- JavaScript: `<script>` block starting at line ~493
- Module/scenario definitions: `MODULES` constant (line ~502)
- All functions in global scope
