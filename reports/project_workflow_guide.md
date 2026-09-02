# KORE2 Battery SOH Project — Workflow Guide

This guide walks through the project following the CRISP-DM methodology used in the brief
(`reports/electric_boda_battery_soh_brief.docx`) and shows which file in this repository
supports each phase.

## CRISP-DM phases → project folders

| Phase | What happens | Where it lives in this project |
| --- | --- | --- |
| 1. Business Understanding | Define the problem: tracking State of Health (SOH) of electric boda boda batteries; identify who it matters to (battery-swap and e-boda operators) | `reports/electric_boda_battery_soh_brief.docx` (sections 1–2) |
| 2. Data Understanding | Explore the data: fleet telemetry and individual battery performance logs | `data/ghana_telemetry_data.csv` (real, 1,481 batteries) · `data/kore2_battery_performance.csv` (synthetic) · first pass in `notebooks/kore2_battery_performance_analysis.ipynb` |
| 3. Data Preparation | Clean, reshape, and merge the telemetry into analysis-ready tables | `notebooks/kore2_battery_performance_analysis.ipynb` (EDA + cleaning) |
| 4. Modeling | Compute and model SOH, capacity fade, cycle counts, swap economics | `notebooks/kore2_battery_performance_analysis.ipynb` (metrics + evaluation) |
| 5. Evaluation | Validate findings: which batteries are near end-of-life, which complaints are supported by data | `reports/electric_boda_battery_soh_brief.docx` (sections 5–7) |
| 6. Deployment | Ship the monitoring tool operators use in the field | `dashboard/fleet_ops_dashboard.html` |

## How each piece is used

### `data/`
Input datasets. Keep them raw; do all cleaning in the notebook so the pipeline is reproducible.

- `ghana_telemetry_data.csv` — real operational telemetry (Ghana fleet, 1,481 batteries). Used for fleet-level statistics and dashboard KPIs.
- `kore2_battery_performance.csv` — synthetic battery-level performance logs for the laboratory-style EDA (timestamps, `battery_id`, state, speed, voltage, current, SOC, SOH, temperature).

### `notebooks/`
- `kore2_battery_performance_analysis.ipynb` — cleaning + modeling + evaluation:
  1. Exploratory Data Analysis
  2. Executive Summary
  3. Methodology
  4. Evidence of rapid drain
  5. Evidence of abrupt shutdowns
  6. Recommendations

### `dashboard/`
- `fleet_ops_dashboard.html` — the deployed tool; a self-contained HTML dashboard that operators open in a browser. It visualises fleet status, battery SOH, and swap-station activity from the Ghana telemetry.

### `reports/`
- `electric_boda_battery_soh_brief.docx` — the full industry brief (business context, CRISP-DM roadmap, KOFA/Kore2 case study, dashboard description, recommendations).
- `group_presentation.pptx` — the 9-slide group presentation deck (project summary, findings, recommendations).
- `project_workflow_guide.md` — this file.

## Recommended run order

1. Read the brief (`reports/electric_boda_battery_soh_brief.docx`) to understand business context.
2. Open `notebooks/kore2_battery_performance_analysis.ipynb` for the data cleaning, modeling, and evaluation.
3. Open `dashboard/fleet_ops_dashboard.html` to see the deployed monitoring tool.
4. Use `reports/group_presentation.pptx` to present the results.

## Getting started (code)

```bash
cd kore2-battery-analysis
python -m venv .venv && source .venv/bin/activate   # optional but recommended
pip install -r requirements.txt
jupyter notebook notebooks/kore2_battery_performance_analysis.ipynb
```

For the dashboard, simply open `dashboard/fleet_ops_dashboard.html` in a browser.