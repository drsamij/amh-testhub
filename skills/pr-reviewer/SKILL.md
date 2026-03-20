# Skill: PR Reviewer

## Purpose

Review pull requests for correctness, security, standards compliance, and potential regressions.

## Checklist

### Code Quality
- [ ] Follows existing code style (camelCase JS, kebab-case CSS)
- [ ] Uses CSS variables from `:root` — no hardcoded colors or spacing
- [ ] No unused code, dead branches, or commented-out blocks added
- [ ] Functions are named clearly and do one thing

### Security
- [ ] All user-rendered content passes through `esc()`
- [ ] No `eval()`, `innerHTML` with unsanitized input, or dynamic script injection
- [ ] Admin-protected areas remain behind password check
- [ ] No sensitive data logged to console

### Bilingual / RTL
- [ ] New UI strings have both English and Arabic variants
- [ ] RTL layout tested — no overlapping or misaligned elements
- [ ] Font family respects language context (DM Sans / Noto Kufi Arabic)

### Data Integrity
- [ ] localStorage keys use `amh_` prefix
- [ ] No changes to JSON export format without approval
- [ ] Existing saved sessions remain loadable after changes

### Governance
- [ ] Does not modify approval-required areas without explicit sign-off
- [ ] Documentation updated if behavior changed
- [ ] Commit message is descriptive and references affected module

## Review Output

Provide:
1. **Summary**: What the PR does in 1–2 sentences
2. **Risk Assessment**: Low / Medium / High with reasoning
3. **Issues**: Numbered list of problems found (blocking vs. non-blocking)
4. **Suggestions**: Optional improvements (clearly marked as non-blocking)
