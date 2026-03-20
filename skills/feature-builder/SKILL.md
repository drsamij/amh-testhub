# Skill: Feature Builder

## Purpose

Implement new features or enhance existing functionality in the AMH Test Hub.

## Before Starting

1. Read `CLAUDE.md` and `docs/architecture.md`
2. Identify which tab/module is affected
3. Check if the change touches any approval-required area (see `CLAUDE.md`)
4. If it does — ask for explicit confirmation before proceeding

## Process

1. **Understand**: Read the relevant section of `index.html` to understand current behavior
2. **Plan**: Identify the CSS, HTML, and JS changes needed
3. **Implement**:
   - Add CSS using existing variables from `:root`
   - Add HTML in the correct tab section
   - Add JS functions in the `<script>` block, following existing patterns
   - Support both English and Arabic (RTL)
4. **Verify**: Confirm the feature renders correctly and doesn't break adjacent modules
5. **Document**: Update `docs/` if the feature introduces new concepts or changes workflows

## Constraints

- All code stays in `index.html` unless splitting is explicitly requested
- Use `esc()` for any user-generated content rendered as HTML
- Use `toast()` for success/error feedback
- Use `localStorage` with `amh_` prefix for persistence
- Maintain mobile-first responsive design (44px min touch targets)
- Never add new CDN dependencies without approval

## Output

- Working feature in `index.html`
- Updated documentation if applicable
- Commit with clear description of what was added
