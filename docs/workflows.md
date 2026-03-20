# Workflows

## Development Workflow

1. **Open** `index.html` in a browser to preview
2. **Edit** `index.html` directly — all code lives there
3. **Test** changes by refreshing the browser
4. **Commit** with a descriptive message referencing the affected module/tab

No build, lint, or CI steps exist. Manual browser testing is the verification method.

## Adding a New Test Module

1. Add a new object to the `MODULES` array (line ~502):
   ```js
   { id:'M11', name:'New Module', nameAr:'الوحدة الجديدة', priority:'medium', scenarios:[
     {id:'NM-01', en:'Description', ar:'الوصف', expected:'Expected result', defaultNA:false}
   ]}
   ```
2. The UI renders dynamically — no additional HTML changes needed
3. Update `docs/domain-context.md` with the new module

## Adding a New Test Scenario

1. Append a scenario object to the relevant module's `scenarios` array
2. Use the module prefix for the ID (e.g., `AP-06` for Appointments)
3. Include both `en` and `ar` descriptions and an `expected` result

## Modifying the Admin Tab

**Requires approval** — the admin tab controls data aggregation and reporting.

1. Identify the function(s) affected (search for `admin` or `Admin` in the JS)
2. Confirm the change does not alter report output formats
3. Test with sample imported JSON data

## Modifying Report Generation

**Requires approval** — reports are shared externally with developers and stakeholders.

1. Functions: `generateExpertReport()`, `buildDevSummaryText()`, `exportDevCSV()`
2. Verify output format compatibility with existing consumers
3. Test all 6 sharing channels (Email, WhatsApp, Teams, HTML, CSV, Telegram)

## Bug Fix Workflow

1. Reproduce the issue in browser
2. Locate the relevant function in `index.html`
3. Fix and verify — check both English and Arabic modes
4. Confirm no regressions in related module rendering
5. Commit with "Fix: [description]" format

## Data Migration

If localStorage schema changes:
1. Write a migration function that runs on page load
2. Check for old key format, transform to new format
3. Preserve all existing tester data — data loss is unacceptable
