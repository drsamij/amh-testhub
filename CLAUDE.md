# AMH Patient App — Test Hub v3.0

## Overview

A single-page HTML application for QA testing the AMH (Al Moosa Hospital) Patient mobile app. Testers use this tool to systematically test app scenarios, log bugs, and generate reports. The entire application lives in one file: `index.html`.

## Tech Stack

- **Frontend**: Vanilla HTML/CSS/JavaScript (no build system, no bundler)
- **Charting**: Chart.js 4.4.1 (CDN)
- **Fonts**: Google Fonts — DM Sans + Noto Kufi Arabic
- **Storage**: Browser localStorage (no backend)
- **Bilingual**: English + Arabic (RTL support)

## Architecture

Everything is in `index.html` — styles, markup, and JavaScript. There is no build step, no package.json, no tests, and no CI pipeline.

### Key Sections

- **Modules & Scenarios**: 10 test modules (Login, Dashboard, Appointments, Medical Records, Payments, Telehealth, Notifications, Profile, Patient Education, General UI) with ~45 total test scenarios defined in the `MODULES` constant
- **Tester Tab**: Testers fill in device info, execute scenarios (Pass/Fail/N/A), attach bug details with severity levels
- **Admin Tab**: Password-protected (`amh2026`), aggregates results across testers, provides export/reporting
- **Expert Analysis Tab**: Aggregated statistics, charts, and exportable reports
- **Developer Summary Tab**: Bug-focused view with email/WhatsApp/Telegram sharing

### Data Model

- `testerResults` — per-scenario test results with status, bugs, timestamps
- `testerInfo` — device/OS/tester metadata
- `adminData` — imported results from multiple testers
- `expertData` — imported aggregate data for expert analysis
- All persisted via `localStorage` with keys prefixed `amh_`

## Development Notes

- No linting, formatting, or type checking configured
- To preview: open `index.html` in a browser (no server required)
- The file is large (~2500 lines). When editing, use line-number references to navigate
- CSS variables are defined in `:root` (line ~16) — use them for consistent theming
- All functions are in the global scope within a single `<script>` block starting at line ~493
