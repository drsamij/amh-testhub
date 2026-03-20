# CLAUDE.md — AMH Patient App Test Hub

## Project Overview

**AMH TestHub v3.0** is a single-file, mobile-first testing platform for the AMH patient application. It follows IEEE 829 Test Execution Log and ISTQB Foundation Best Practices. The entire application lives in `index.html` (~1,565 lines).

**Domain:** Healthcare (Saudi Arabia context) — patient app QA testing
**Stack:** Pure HTML5/CSS3/JavaScript, Chart.js 4.4.1 (CDN), no build system

## Architecture

### Single-File Structure

All code is in `index.html`, organized in sections marked with `/* === SECTION NAME === */`:

1. **CSS styles** — inline `<style>` block with responsive design and RTL support
2. **HTML markup** — three-tab layout (Tester, Admin, Expert) plus onboarding modal
3. **JavaScript** — organized as DATA → STATE → UTILS → FEATURES → INIT

### Three Tabs / User Roles

| Tab | Purpose | Access |
|-----|---------|--------|
| **Tester** | Execute 42 test scenarios across 10 modules, record pass/fail/blocked/N/A with severity and bug classification | Open |
| **Admin** | Aggregate multi-tester results via JSON import, export HTML/CSV reports | Password-protected (`admin2026`) |
| **Expert** | Go-Live Readiness scoring (0-100), risk-based module health, radar/bar/doughnut charts | Requires admin data |

### Data Persistence

All state is stored in `localStorage`:

| Key | Contents |
|-----|----------|
| `amh_tester_info` | Current tester metadata (name, OS, device, version, network) |
| `amh_tester_results` | Test results per scenario (status, severity, bugType, notes, timestamp, history) |
| `amh_admin_data` | Aggregated multi-tester data |
| `amh_expert_data` | Expert assessment data |
| `amh_collapsed` | Module collapse state |
| `amh_saved_sessions` | Resumable sessions keyed by tester name |

### Test Modules

10 modules, 42 scenarios total. Some modules are optional (Payments, Telehealth, Notifications, Patient Education). Each scenario has: ID, English text, Arabic text, expected result, priority (High/Medium/Low), and default N/A flag.

## Development Conventions

### Code Style

- **Functions/variables:** camelCase (`renderScenarios`, `saveResults`)
- **CSS ID prefixes:** `ob-` (onboarding), `sc-` (scenario), `si-` (session info), `chart-` (charts)
- **DOM data attributes:** `data-tab`, `data-mod` for UI state
- **Comment blocks:** `/* === SECTION === */` to separate major sections

### Key Functions

- `checkOnboarding()` — entry point on DOMContentLoaded
- `switchTab(tab)` — tab navigation with admin password gating
- `renderScenarios()` — renders the tester test list with search/filter
- `saveResults()` — exports session as JSON
- `renderAdmin()` — builds the multi-tester aggregation view
- `renderExpert()` — computes readiness score and renders charts
- `exportTesterJSON()` / `exportAdminHTML()` / `generateExpertReport()` — report exports

### UI Patterns

- **Toast notifications:** auto-dismiss in 3.2s via `showToast(msg, type)`
- **Modals:** overlay-based with close handlers
- **Status colors:** success=#28a745, error=#dc3545, warning=#f0850e, info=#0d6efd
- **Primary palette:** teal #0d7c5f with dark/light variants
- **Fonts:** DM Sans (EN) + Noto Kufi Arabic (AR), both from Google Fonts CDN

### Bilingual Support

The app supports English and Arabic (RTL). Test scenario data includes both `en` and `ar` text fields. The UI detects language preference and applies `direction: rtl` when needed.

### Mobile Features

- iOS webapp capable (`apple-mobile-web-app-capable`)
- Triple-tap unlock for admin on mobile (screen width > 768px check)
- Web Share API integration with clipboard fallback
- Device detection with Saudi Arabia device defaults

## Build & Deployment

- **No build step** — the app is a single static HTML file
- **No package manager** — only external dependency is Chart.js via CDN
- **Deploy:** serve `index.html` from any static host
- **No tests or linters configured** — manual QA via the app itself

## Making Changes

When modifying this codebase:

1. All changes go into `index.html` — respect the section comment markers
2. Keep the DATA section (scenario definitions) separate from rendering logic
3. Maintain bilingual (EN/AR) text for any new scenarios
4. Test on mobile viewports — the app is mobile-first
5. Preserve localStorage key naming (`amh_` prefix) for backward compatibility
6. Chart.js is loaded from CDN — do not add local copies without reason
7. Keep export formats stable (JSON structure) so existing saved sessions remain loadable
