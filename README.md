 HEAD
# KORE2 Battery SOH Analysis — Project Map

Tracking the State of Health (SOH) of electric boda boda batteries (KOFA's Kore2 network), using the CRISP-DM methodology.

## Project structure (phase-to-folder map)

```
kore2-battery-analysis/
├── README.md                                    ← phase-to-folder map + how to use each piece
├── .gitignore
├── data/
│   ├── kore2_battery_performance.csv            (synthetic, illustrative)
│   └── ghana_telemetry_data.csv                 (real, 1,481 batteries)
├── notebooks/
│   └── kore2_battery_performance_analysis.ipynb (cleaning + modeling + evaluation)
├── dashboard/
│   └── fleet_ops_dashboard.html                 (the deployed tool)
└── reports/
    ├── electric_boda_battery_soh_brief.docx
    ├── group_presentation.pptx
    └── project_workflow_guide.md
```

## How each piece is used

| Piece | Role |
| --- | --- |
| `data/kore2_battery_performance.csv` | Synthetic battery performance logs used for the EDA notebook |
| `data/ghana_telemetry_data.csv` | Real fleet telemetry (Ghana, 1,481 batteries) used for fleet stats and the dashboard |
| `notebooks/kore2_battery_performance_analysis.ipynb` | Cleans the data, builds SOH metrics, evaluates findings (rapid drain, abrupt shutdowns) |
| `dashboard/fleet_ops_dashboard.html` | The deployed fleet operations tool; open directly in a browser |
| `reports/electric_boda_battery_soh_brief.docx` | Full CRISP-DM industry brief |
| `reports/group_presentation.pptx` | 9-slide group presentation deck |
| `reports/project_workflow_guide.md` | Detailed phase-to-folder workflow guide |

## Setup

```bash
cd kore2-battery-analysis
python -m venv .venv && source .venv/bin/activate   # optional but recommended
pip install -r requirements.txt
jupyter notebook notebooks/kore2_battery_performance_analysis.ipynb
```

Open `dashboard/fleet_ops_dashboard.html` in any browser to use the deployed tool.

# E-Boda-Battery-Passport
 fec706eb16d7686c10e74ab8a4428706f7c2980b
