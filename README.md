# CMO/CEO Marketing Dashboard

Interactive, single-file HTML dashboard for tracking marketing performance metrics. Built with Chart.js and designed for drag-and-drop data refresh from Excel files.

## Quick Start

1. Download `dashboard.html`
2. Open it in any modern browser (Chrome, Edge, Firefox)
3. Drag and drop your `.xlsx` data file onto the drop zone in the header

No server, no install, no dependencies to manage — everything runs in the browser.

## Features

- **5 KPI summary cards** with color-coded attainment (green/amber/red)
- **6 interactive charts**: Influenced ARR, Pipeline, Leads, BDR Performance, Connections, Marketing-Attributed Pipeline
- **Marketing Investment trend** (quarterly line chart)
- **Quarterly Benchmarks table** with conditional formatting
- **Filters**: month range, monthly/cumulative toggle, category tabs
- **Drag-and-drop Excel upload** to refresh all data instantly
- Dark theme, responsive layout

## Excel File Format

Your `.xlsx` file must follow this sheet and row structure. In every sheet, **column B = January** (or Q1), **column C = February**, etc. Column A contains row labels.

### Required Sheets

| Sheet Name | Row | Contents |
|---|---|---|
| **Influenced ARR** | 2 | Monthly targets |
| | 3 | Monthly actuals |
| | 4 | Monthly attainment (%) |
| | 8 | Cumulative targets |
| | 9 | Cumulative actuals |
| **Pipeline** | 2 | Monthly targets |
| | 3 | Monthly actuals |
| | 4 | Monthly attainment (%) |
| **Leads** | 2 | Prior year average (used as baseline) |
| | 3 | Monthly actuals |
| | 4 | Monthly attainment (%) |
| **BDR Data** | 2-3 | Meetings target & actuals |
| | 8-9 | Opps target & actuals |
| | 14-15 | Pipeline Created target & actuals |
| | 19-20 | Bookings target & actuals |
| **Connections Data** | 6-7 | Monthly target & actuals |
| | 14-15 | Cumulative target & actuals |
| **CORP Pipe & Bookings w PWR** | 2 | Total pipeline (quarterly) |
| | 3 | Marketing-sourced pipeline |
| | 4 | Sales-sourced pipeline |
| | 5 | Marketing % of total |
| | 14-17 | Total bookings (same structure) |
| | 28 | Investment — fully loaded |
| | 29 | Investment — staff only |
| | 30 | Investment — programs only |
| **Quarterly Performance Benchmark** | 2-4 | Metric name (col A), High Performers (col B), Median (col C), Your Company (col E) |

### Example Row Layout

```
     |  A (label)  |  B (Jan)  |  C (Feb)  |  D (Mar)  | ...
  2  |  Target     | $142,000  | $142,000  | $142,000  |
  3  |  Actuals    | $143,041  | $156,055  | $144,193  |
  4  |  Attainment |   101%    |   110%    |   102%    |
```

## Customization

The dashboard is a single HTML file with inline CSS and JavaScript. To customize:

- **Default data**: Edit the `DATA` object near line 156
- **Colors/theme**: Modify CSS variables in the `:root` block (line 13)
- **Chart behavior**: Each chart is configured in the `renderCharts()` function (line 307)
- **Excel parsing**: The `parseWorkbook()` function (line 479) maps sheet rows to data — adjust row numbers here if your layout differs

## Tech Stack

All loaded from CDN — no build step required:

- [Chart.js 4.4.1](https://www.chartjs.org/) — charts
- [chartjs-plugin-datalabels 2.2.0](https://chartjs-plugin-datalabels.netlify.app/) — value labels on bars
- [SheetJS (xlsx) 0.20.0](https://sheetjs.com/) — Excel file parsing
- [Inter font](https://rsms.me/inter/) — typography
