# el-nino-watch-2026

This is the dev/analysis environment behind two pages on my portfolio site,
[velezf.github.io](https://velezf.github.io): a historical coral bleaching risk
notebook and a live 2026 El Niño reef thermal-stress monitoring page. The
deployed, canonical versions of both pages live in the `velezf.github.io` repo
under `projects/`. The `.qmd` in this repo is a working copy and may lag the
deployed one — if there's a discrepancy, the portfolio repo is the source of
truth.

I'm a data scientist learning marine science, not a coral ecologist. Everything
here is derived from NOAA's publicly available monitoring products. The El Niño
monitoring page in particular is a live instrument, not a forecast or a finished
analysis — think of it as the kind of thing a reef manager might bookmark and
check weekly.

## What's here

- `coral_bleaching_dhw_analysis.ipynb` — Project 1 dev notebook: historical
  bleaching risk analysis using NOAA CRW DHW data across five Caribbean/Atlantic
  reef sites.
- `el-nino-watch-2026-dev.ipynb` — Project 2 dev notebook: working scratchpad
  for the live El Niño monitoring page.
- `el-nino-watch-2026.qmd` — Working copy of the Quarto source for the
  monitoring page. See note above about the portfolio repo being the source of
  truth.
- `references.bib` — Bibliography for both projects.
- `pyproject.toml` / `uv.lock` — Fully specified Python environment (see below).

The `data/` directory is not committed. It's created at run time and holds the
raw NOAA cache files and processed figure outputs; they're regenerated on every
render.

## Setup

This project uses [uv](https://docs.astral.sh/uv/). Python 3.11 or later is
required.

```bash
uv sync
```

To register the Jupyter kernel used by the notebooks and the Quarto document:

```bash
uv run python -m ipykernel install --user --name el-nino-2026 --display-name "el-nino-2026"
```

To open the notebooks:

```bash
uv run jupyter lab
```

## Data sources

**NOAA Coral Reef Watch Virtual Stations** — 5 km resolution, v3.1 product
suite. Daily composites of SST, SST Anomaly, HotSpot, and Degree Heating Weeks
(DHW) for each monitored reef site.
<https://coralreefwatch.noaa.gov/product/vs/data.php>

**NOAA CPC Oceanic Niño Index (ONI)** — NOAA's official metric for tracking
El Niño and La Niña events, measuring SST anomalies in the Niño 3.4 region.
<https://www.cpc.ncep.noaa.gov/data/indices/oni.ascii.txt>

Both sources are fetched live at render time and cached under `data/raw/`.

## Live pages

- [Coral Bleaching Risk — Historical Analysis](https://velezf.github.io/projects/bleaching-risk-notebook.html)
- [2026 Super El Niño Watch — Live Monitoring](https://velezf.github.io/projects/el-nino-watch-2026.html)

This is a portfolio learning project. It is not an official NOAA product.
