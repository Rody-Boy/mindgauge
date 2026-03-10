# PsycheMetrics Standalone System

This folder provides a **ready-to-install standalone launcher** for:

1. **Battery options** (role-based multi-test links)
2. **All 5 assessments** (individual launch)
3. **Response dashboard** (reads local browser data and opens detailed results)

## Files

- `index.html` — standalone control center UI

## How to run

From the repo root:

```bash
python3 -m http.server 7000 --directory /workspace/mindgauge
```

Open:

- `http://127.0.0.1:7000/standalone-system/index.html`

## Data sources used

- Submissions: `localStorage['psychemetrics_hr_submissions_v1']`
- Attempts: `localStorage['psychemetrics_test_attempts_v1']`

## Notes

- "Open Result" jumps to `admin.html?submission=<id>`.
- Battery links open the guided runner in `battery.html`.
- Assessment links open the individual assessment pages directly.
