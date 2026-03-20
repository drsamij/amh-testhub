# Architecture

## Overview

Single-page application in one `index.html` file. No backend, no build system, no bundler. All state lives in browser localStorage.

## File Structure

```
index.html          — Entire application (HTML + CSS + JS)
CLAUDE.md           — AI assistant governance rules
docs/               — Project documentation
skills/             — Claude skill definitions
```

## Application Layers

```
┌─────────────────────────────────────────┐
│  UI Layer (HTML + CSS)                  │
│  - Tab-based navigation                 │
│  - Modal overlays                       │
│  - Responsive/RTL layout                │
├─────────────────────────────────────────┤
│  Logic Layer (JavaScript)               │
│  - Tab switching & routing              │
│  - Test scenario state machine          │
│  - Report generation & export           │
│  - Chart rendering (Chart.js)           │
├─────────────────────────────────────────┤
│  Data Layer (localStorage)              │
│  - amh_tester_info                      │
│  - amh_tester_results                   │
│  - amh_admin_data                       │
│  - amh_expert_data                      │
│  - amh_saved_sessions                   │
│  - amh_collapsed                        │
└─────────────────────────────────────────┘
```

## Tabs / Views

| Tab | Purpose | Access |
|-----|---------|--------|
| Tester | Execute test scenarios, log bugs | Public |
| Admin | Aggregate multi-tester results, export reports | Password-protected |
| Expert Analysis | KPIs, charts, readiness scoring | Via admin data import |
| Developer Summary | Bug-focused view, sharing to dev channels | Via admin data |

## Test Module Structure

10 modules, ~48 scenarios. Each scenario object:
```js
{ id, en, ar, expected, defaultNA }
```

Modules are defined in the `MODULES` constant. Adding a module means appending to this array — the UI renders dynamically from it.

## Data Flow

1. Tester fills onboarding → saved to `amh_tester_info`
2. Tester marks scenarios → saved to `amh_tester_results` (auto-save 800ms debounce)
3. Tester exports JSON → admin imports via file upload
4. Admin tab aggregates → populates charts and tables
5. Expert/Developer tabs consume aggregated admin data

## External Dependencies

| Dependency | Version | Loaded Via |
|------------|---------|------------|
| Chart.js | 4.4.1 | CDN (`cdn.jsdelivr.net`) |
| DM Sans font | latest | Google Fonts |
| Noto Kufi Arabic font | latest | Google Fonts |

No npm packages. No local dependencies.
