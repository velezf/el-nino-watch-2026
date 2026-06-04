# Monitoring 2026 Super El Niño Reef Thermal Stress

A reproducible Python/Jupyter live-monitoring analysis of satellite-derived coral thermal stress metrics across seven reef systems, using live NOAA Coral Reef Watch (CRW) Degree Heating Weeks (DHW) data and NOAA CPC Oceanic Niño Index (ONI) context.

**Portfolio project page:** [velezf.github.io/projects/el-nino-watch-2026.html](https://velezf.github.io/projects/el-nino-watch-2026.html)

---

## Study Sites

| Site | Ocean |
|------|-------|
| Florida Keys, USA | Caribbean/Atlantic |
| Grand Cayman | Caribbean |
| Roatán, Honduras | Caribbean (Mesoamerican Reef) |
| ABC Islands (Bonaire/Aruba/Curaçao) | Southern Caribbean |
| Great Barrier Reef (Central sector) | Indo-Pacific |
| Palau | Western Pacific |
| West Papua | Coral Triangle |

## Key Metrics Analyzed

- **DHW (Degree Heating Weeks)** — accumulated coral thermal stress (°C-weeks)
- **SST Anomaly** — departure from daily climatological SST
- **HotSpot** — SST departure above the Maximum Monthly Mean (bleaching threshold baseline)
- **Bleaching Alert Levels** — NOAA CRW 5-level alert classification
- **ONI (Oceanic Niño Index)** — SST anomaly in the Niño 3.4 region; El Niño/La Niña tracking metric

## Data Sources

NOAA Coral Reef Watch Version 3.1 Daily 5km Satellite Coral Bleaching Heat Stress Product Suite (CoralTemp). Updated daily. Available at: https://coralreefwatch.noaa.gov/

NOAA Climate Prediction Center Oceanic Niño Index (ONI). Available at: https://www.cpc.ncep.noaa.gov/

Both sources are fetched live via the CRW Virtual Station feed (space-delimited `.txt` files) and cached locally in `data/raw/` on first run.

---

## Quickstart

**Prerequisites:** [uv](https://docs.astral.sh/uv/) and Python 3.11.

### 1. Clone the repo

```bash
git clone https://github.com/velezf/el-nino-watch-2026.git
cd el-nino-watch-2026
```

### 2. Set up the environment

```bash
uv sync
```

### 3. Register the Jupyter kernel

```bash
uv run python -m ipykernel install --user --name el-nino-2026
```

### 4. Open the dev notebooks

```bash
uv run jupyter lab
```

On first run, the notebooks fetch live data from NOAA CRW and NOAA CPC and cache the raw `.txt` files to `data/raw/`. Subsequent runs use the cache. To force a fresh download: set `force_refresh=True` in the fetch call.

### 5. View the Quarto portfolio page (optional)

The narrative Quarto page (`el-nino-watch-2026.qmd`) lives in the [velezf.github.io](https://github.com/velezf/velezf.github.io) site repo under `projects/`, where it is rendered and deployed. It is intentionally not tracked here — this repo holds the analysis notebooks. The rendered page is published at the portfolio link above.

---

## Repository Structure

```
el-nino-watch-2026/
├── README.md
├── LICENSE
├── .gitignore
├── .python-version                            # Python 3.11 pin
├── pyproject.toml                             # uv project config and dependencies
├── uv.lock                                    # Pinned dependency lock file
├── coral_bleaching_dhw_analysis.ipynb         # Dev notebook — historical bleaching risk (Project 1)
├── el-nino-watch-2026-dev.ipynb               # Dev notebook — live El Niño monitoring (Project 2)
├── references.bib                             # BibTeX citations for both projects
│
└── data/                                      # Generated at run time — not committed
    ├── raw/                                   # NOAA CRW & ONI .txt files — fetched on first run
    └── processed/                             # Figure outputs — regenerated on every render
```

> The Quarto page (`el-nino-watch-2026.qmd`, `_quarto.yml`) and rendered outputs are
> gitignored; they live in the site repo or local working directory only.

---

## Key References

1. Skirving, W., et al. (2020). CoralTemp and the Coral Reef Watch Coral Bleaching Heat Stress Product Suite Version 3.1. *Remote Sensing, 12*(23), 3856. https://doi.org/10.3390/rs12233856

2. NOAA Climate Prediction Center. (2026). Oceanic Niño Index (ONI). https://www.cpc.ncep.noaa.gov/data/indices/oni.ascii.txt

3. Hughes, T.P., et al. (2017). Global warming and recurrent mass bleaching of corals. *Nature, 543*, 373–377.

---

## License

Code: MIT License  
Data: NOAA CRW and NOAA CPC data are public domain per NOAA's open data policy.

---

*Part of a marine science and environmental data science portfolio.*  
*Built with Python · Jupyter · Quarto · NOAA Open Data*
