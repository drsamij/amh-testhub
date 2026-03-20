# Domain Context

## What This Is

A QA Test Hub for the **AMH (Al Moosa Hospital) Patient mobile application**. It is used by QA testers to systematically verify that the patient-facing app works correctly across devices, languages, and scenarios.

## Who Uses It

| Role | What They Do |
|------|-------------|
| **QA Tester** | Runs test scenarios on a real device, marks pass/fail, logs bugs |
| **QA Admin** | Imports results from multiple testers, reviews aggregate data |
| **QA Expert** | Analyzes readiness, generates go/no-go recommendations |
| **Developer** | Receives bug reports via email, WhatsApp, Teams, or Telegram |

## Key Domain Concepts

- **Module**: A functional area of the patient app (e.g., Login, Appointments, Payments)
- **Scenario**: A specific test case within a module (e.g., "Login with valid credentials")
- **Expected Result**: The acceptance criteria for a scenario
- **Severity**: Bug impact level — Critical, Major, Minor, Cosmetic
- **Bug Type**: Classification — Functional, UI/Layout, Performance, Crash, Data, Security, Accessibility, Localization, Other
- **Readiness Score**: 0–100 scale; determines GO / CONDITIONAL GO / NO-GO verdict
- **Session**: A named test run tied to a tester, device, and timestamp

## Modules Under Test

| ID | Module | Priority |
|----|--------|----------|
| M1 | Login & Authentication | High |
| M2 | Dashboard & Home | High |
| M3 | Appointments | High |
| M4 | Medical Records | High |
| M5 | Payments | Medium |
| M6 | Telehealth | Medium |
| M7 | Notifications | Medium |
| M8 | Profile & Settings | Medium |
| M9 | Patient Education | Low |
| M10 | General & UI | High |

## Healthcare Context

- Hospital setting: supports Arabic (RTL) and English
- Patient-facing: data sensitivity is paramount — no real patient data in this tool
- Aligns with **IEEE 829** test documentation standards and **ISTQB** best practices
- Saudi Arabia device market: preloaded device model dropdown includes common local devices

## Critical Business Rules (Do Not Change Without Approval)

- Severity classification definitions and their mapping to readiness scores
- Admin password and access control logic
- Report generation formulas (pass rate, defect density, readiness verdict thresholds)
- Data export formats (JSON structure consumed by admin import)
- Module and scenario IDs (external references may depend on them)
