# Predoc Data Task

This repository contains the analysis for the UChicago Booth Behavioral Science and Marketing Predoc data task.

## How To Run (Terminal)

1. Open the project root as your working directory.
2. Run the analysis:

```r
rmarkdown::render('run_analysis.Rmd')
```

This will:
- Read the raw Excel file (read-only)
- Perform the data pipeline and checks
- Generate `run_analysis.pdf`
- Write `output/cleaned_analysis_data.csv`
- Write `output/figure_1_conciliation.png`

## Requirements

- R (tested with 4.5.x)
- Pandoc
- A LaTeX engine (TinyTeX is sufficient)

Required R packages are installed automatically by the script:
- `readxl`, `knitr`, `rmarkdown`, `stargazer`, `formatR`, `sandwich`, `lmtest`

## Outputs

- `run_analysis.pdf` (main report)
- `output/cleaned_analysis_data.csv`
- `output/figure_1_conciliation.png`

## Notes

- Raw data (`Data - 2026.xlsx`) is treated as read-only.
- The main analysis file is `run_analysis.Rmd`.
