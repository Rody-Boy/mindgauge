# PsycheMetrics

A privacy-first, browser-based psychometric assessment suite for HR and psychologist workflows.

PsycheMetrics runs fully client-side (no backend required) and includes:
- Public assessment pages with validated scoring logic.
- An admin portal for link/battery generation.
- A local admin inbox for review workflows.
- Guided battery flows across multiple assessments.
- Printable/copyable results and optional email-draft routing.

---

## Table of Contents
- [Overview](#overview)
- [Key Features](#key-features)
- [Project Structure](#project-structure)
- [Assessments Included](#assessments-included)
- [Quick Start](#quick-start)
- [Admin & Battery Workflow](#admin--battery-workflow)
- [Local Storage Keys](#local-storage-keys)
- [Standalone Package](#standalone-package)
- [Customization Notes](#customization-notes)
- [Troubleshooting](#troubleshooting)
- [Privacy & Data Handling](#privacy--data-handling)
- [Contributing](#contributing)
- [License / Usage](#license--usage)

---

## Overview

PsycheMetrics is designed for low-infrastructure deployments where teams need guided assessments and admin review without standing up a server stack.

The app uses static HTML/CSS/JS pages plus browser storage (`localStorage` and `sessionStorage`) to:
- Capture participant details,
- Compute assessment outcomes,
- Route results to an admin inbox,
- Support battery progress tracking.

---

## Key Features

- **Admin-managed flow** via `portal.html` and `admin.html`.
- **Guided batteries** via `battery.html` with per-test completion tracking.
- **Client-side result routing** to admin inbox using local storage.
- **Optional `mailto:` delivery** of result summaries to configured admin email.
- **Printable results** and **copy summary** actions across assessments.
- **Report preview assets** for demos and collateral.
- **Standalone wrapper package** under `standalone-system/`.

---

## Project Structure

```text
.
├── index.html                          # Main landing page
├── portal.html                         # Admin portal (link + battery builder)
├── admin.html                          # Admin inbox/review page
├── battery.html                        # Guided battery runner
├── client-demo.html                    # Interactive demo page
├── pricing.html                        # Pricing page
├── ipip-neo-120-assessment.html        # IPIP NEO-120 assessment
├── big5-ipip50-assessment.html         # Big Five IPIP-50 assessment
├── gse-assessment.html                 # General Self-Efficacy assessment
├── grit-s-assessment.html              # Grit-S assessment
├── uwes9-assessment.html               # UWES-9 assessment
├── assets/
│   └── report-previews/                # Report preview SVGs
├── documents/
│   ├── quotation-one-time-installation.html
│   └── quotation-one-time-installation.pdf
└── standalone-system/
    ├── README.md
    ├── index.html
    ├── portal.html
    └── admin.html
```

---

## Assessments Included

- IPIP NEO-120
- Big Five IPIP-50
- General Self-Efficacy (GSE)
- Grit-S
- Utrecht Work Engagement Scale (UWES-9)

Each assessment page includes:
- Participant detail capture,
- Score computation and visualization,
- Result summary copy/print actions,
- Admin submission integration.

---

## Quick Start

### 1) Clone / open the repository

```bash
git clone <your-repo-url>
cd mindgauge
```

### 2) Run a local static server

Any static server works. Example with Python:

```bash
python3 -m http.server 7044 --directory .
```

Then open:
- `http://localhost:7044/index.html`

### 3) Primary pages

- Landing: `index.html`
- Admin portal: `portal.html`
- Admin inbox: `admin.html`
- Guided battery: `battery.html` (normally opened from portal-generated links)

---

## Admin & Battery Workflow

1. Open `portal.html`.
2. Set/save **administrator email** (used for optional `mailto:` drafts).
3. Generate individual assessment links or a multi-test battery link.
4. Participant completes tests.
5. Results are stored in local admin submission storage.
6. Admin reviews submissions in `admin.html`.

Battery flow notes:
- Battery links include `batteryId`, role metadata, and test list.
- Completed tests are marked in battery state storage and reflected in progress.

---

## Local Storage Keys

Common keys used by the app:

- `psychemetrics_hr_submissions_v1`
  - Admin inbox submissions queue.
- `psychemetrics_test_attempts_v1`
  - Completed assessment attempt history.
- `psychemetrics_active_participant_v1`
  - Current participant metadata in session.
- `psychemetrics_admin_notification_email`
  - Admin email used for optional result draft routing.
- `psychemetrics_battery_templates_v1`
  - Saved battery template definitions from portal.
- `psychemetrics_battery_state_<batteryId>`
  - Per-battery completion/progress state.

> Tip: Use browser DevTools > Application > Local Storage/Session Storage to inspect or clear data while testing.

---

## Standalone Package

The `standalone-system/` folder contains wrapper pages and a dedicated README for local/offline-style demonstrations.

See:
- `standalone-system/README.md`

---

## Customization Notes

- **Branding/content**: update labels, copy, and logos directly in HTML files.
- **Assessment UX**: adjust question text/scales in each assessment file.
- **Scoring logic**: scoring code is embedded per assessment page.
- **Email routing**: adjust `mailto:` subject/body templates in submission helpers.
- **Pricing/docs**: update `pricing.html` and `documents/` collateral.

---

## Troubleshooting

### Results not appearing in admin inbox
- Ensure the assessment reached the results state.
- Check browser storage for `psychemetrics_hr_submissions_v1`.
- Confirm no browser restrictions are blocking storage access.

### Battery opens but appears empty
- Ensure battery links include a non-empty `tests` query parameter.
- Regenerate links from `portal.html` if needed.

### Email draft does not open
- `mailto:` behavior depends on local OS/browser mail client configuration.
- Results are still stored locally even without email-client integration.

---

## Privacy & Data Handling

- No backend is required for core workflows.
- Data is stored in-browser on the local machine/profile.
- Clearing browser data removes stored submissions/attempts unless exported manually.

For production deployment in regulated environments, consider adding:
- Secure authentication,
- Server-side encrypted persistence,
- Access controls/audit logs,
- Data retention policies.

---

## Contributing

1. Create a feature branch.
2. Make targeted changes.
3. Run local smoke checks using a static server.
4. Commit with clear messages.
5. Open PR with:
   - Summary of changes,
   - Screenshots for visual updates,
   - Validation steps.

---

## License / Usage

No explicit repository license file is currently included.

If you intend external distribution, add a `LICENSE` file and update this section accordingly.
