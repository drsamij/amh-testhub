# Skill: Bug Investigator

## Purpose

Diagnose and fix bugs reported in the AMH Test Hub application.

## Process

1. **Reproduce**: Understand the reported behavior and identify the affected tab/module
2. **Locate**: Search `index.html` for the relevant function(s) — use scenario IDs, function names, or UI text as search anchors
3. **Diagnose**: Trace the data flow from user action → JS handler → localStorage → UI render
4. **Fix**: Apply the minimal change that resolves the issue
5. **Verify**: Confirm the fix in both English and Arabic modes
6. **Regression Check**: Ensure adjacent features in the same tab still work

## Common Bug Categories

| Category | Where to Look |
|----------|--------------|
| Scenario not saving | `saveTesterResults()`, auto-save debounce logic |
| Chart not rendering | Chart.js initialization in `renderExpertCharts()` |
| Admin import failing | JSON parse logic in admin tab event handlers |
| RTL layout broken | CSS `.ar` rules, `direction:rtl` overrides |
| Export format wrong | `exportDevCSV()`, `generateExpertReport()`, JSON export |
| Session resume failing | `resumeSession()`, `amh_saved_sessions` key |
| Toast not showing | `toast()` function, `#toast-container` element |

## Constraints

- Do not change the fix scope beyond what the bug requires
- If the bug is in an approval-required area, flag it and request sign-off
- Preserve all existing localStorage data — never clear or restructure without migration
- Test both languages after every fix

## Output

- Root cause explanation (1–2 sentences)
- Fix applied in `index.html`
- Commit with "Fix: [description]" format
