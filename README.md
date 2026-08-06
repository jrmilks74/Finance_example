# Reusable Church Finance Dashboard

This Shiny app accepts monthly church financial data from a CSV or Excel file and produces board-level summaries, historical comparisons, attention flags, and forecasts.

## Required columns

The uploaded file must contain one row per month and four columns:

| Date | Tithe | Income | Expenses |
|---|---:|---:|---:|
| 2023-01-01 | 48500 | 74200 | 71800 |

- At least 24 monthly rows are required.
- Text and CSV dates must use `yyyy-mm-dd`, such as `2026-07-01`.
- Excel cells stored as true date values are also accepted, regardless of their displayed style.
- Column capitalization and surrounding spaces are ignored.
- Dollar signs, commas, and accounting-style negative values in parentheses are accepted.
- Each month may appear only once.
- CSV, XLSX, and XLS files are supported.
- For Google Sheets, download the sheet as Microsoft Excel or CSV before uploading.
- If an Excel workbook has multiple worksheets, the app displays a worksheet selector.

`sample-data.csv` contains fictional data from January 2023 through July 2026. It models a highly seasonal organization that receives about 55% of its full-year income in November and December, runs deficits during the other ten months, and finishes with a small positive rolling 12-month operating result. Every monthly value varies. Expenses include illustrative seasonal increases in April for Easter music, July for Vacation Bible School, and December for Christmas programming and decorating. The app also provides a downloadable blank 36-month template.

## Run locally

```r
shiny::runApp()
```

## Required R packages

```r
install.packages(c(
  "shiny", "dplyr", "tidyr", "purrr", "readr", "stringr",
  "tibble", "ggplot2", "plotly", "scales", "fpp3", "lubridate",
  "kableExtra", "htmltools", "readxl"
))
```

The uploaded file is held in the Shiny session's temporary upload location. This app contains no code that saves uploaded financial data to permanent storage.
