# PsycheMetrics System Package

This folder provides a local install package with 3 locked-navigation pages:

1. `index.html` — Launcher (batteries, all assessments, response dashboard)
2. `portal.html` — Portal page
3. `admin.html` — Submission inbox page

## How to run

From the repo root:

```bash
python3 -m http.server 7000 --directory /workspace/mindgauge
```

Open:

- `http://127.0.0.1:7000/standalone-system/index.html`
- `http://127.0.0.1:7000/standalone-system/portal.html`
- `http://127.0.0.1:7000/standalone-system/admin.html`

## Data sources used

- Submissions: `localStorage['psychemetrics_hr_submissions_v1']`
- Attempts: `localStorage['psychemetrics_test_attempts_v1']`

## Notes

- "Open Result" opens the inbox view with the submission context.
- Battery links open the guided runner in `battery.html`.
- Assessment links support open + copy actions.
