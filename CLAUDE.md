# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a static data analysis report for **AMDA Sonora** (Asociación Mexicana de Distribuidores de Automotores), covering automotive dealership sales data from the Hermosillo, Sonora survey for 2024. It is a portfolio project by Ángel Ramos in data science and business intelligence.

## Repository Contents

| File | Description |
|---|---|
| `AMDA-SEP.xlsx` | Raw data source — monthly dealership sales survey from AMDA Sonora |
| `index.html` | Static HTML report page that embeds the chart images |
| `grafico_ventas_agosto.png` | Top 10 agencies by sales in August 2024 |
| `grafico_comparativa_anual.png` | Year-over-year comparison: August 2023 vs. August 2024 |
| `grafico_top_crecimiento.png` | Top 5 agencies with highest growth |
| `grafico_top_decrecimiento.png` | Top 5 agencies with highest decline |
| `grafico_tendencia_mensual.png` | Monthly total sales trend across all agencies |

## Architecture

This is a **fully static project** — no build tool, no server, no package manager. The workflow is:

1. Data lives in `AMDA-SEP.xlsx` (the source of truth).
2. Charts are generated externally (e.g., Python with pandas/matplotlib) and saved as PNG files.
3. `index.html` references those PNGs by filename via `<img src="...">` tags.
4. The report is viewed by opening `index.html` directly in a browser.

When updating the analysis, regenerate the relevant PNGs from the Excel data and replace the corresponding files in the repository. The HTML report only needs editing if section titles, captions, or written interpretations change.

## Viewing the Report

Open `index.html` in a browser directly (no server required):

```bash
xdg-open index.html       # Linux
open index.html           # macOS
```

Or serve locally if relative paths need a server context:

```bash
python3 -m http.server 8000
# Then visit http://localhost:8000
```

## Data Context

- **Source:** AMDA Sonora dealership survey (sondeo Hermosillo)
- **Report date:** April 11, 2024
- **Key finding:** Nissan-group dealerships (Nissauto, Gran Auto) dominate August 2024 sales; Agrícola SEAT shows >100% YoY growth; BMW MINI and Chirey show significant declines.
- The `index.html` text is in Spanish.
