# Research Design Group Project

Z-curve analysis on a set of FFA (fusiform face area) fMRI studies, estimating observed/expected discovery rates, replicability, and Soric FDR.

## Project structure

```
.
├── README.md
├── Z-curve-analysis.Rmd   # main analysis (R Markdown)
├── Z-curve-analysis.html  # pre-built report (open in browser)
└── clean_dataset_apr_13.csv  # literature extraction sheet (reference)
```

- **`Z-curve-analysis.Rmd`** — defines a `raw_dat` tibble of 30 studies with hand-entered two-sided *p*-values, converts *p* → |*z*|, fits a z-curve via the `zcurve` package, and renders a summary + plot.
- **`clean_dataset_apr_13.csv`** — the source extraction spreadsheet (study metadata, statistics, effect sizes). The Rmd uses manually copied *p*-values from this sheet, not a direct `read_csv()` call.
- **`Z-curve-analysis.html`** — the rendered output; open directly in a browser to view results without re-running R.

## Reproducing the analysis

### Requirements

R with the following packages:

```r
install.packages(c("zcurve", "dplyr", "stringr", "readr", "tibble",
                   "knitr", "rmarkdown", "mice"))
```

### Render the report

In R (or RStudio → Knit):

```r
rmarkdown::render("Z-curve-analysis.Rmd")
```

This produces a new `Z-curve-analysis.html` with the z-curve plot and summary statistics (ODR, EDR, ERR, EFDR).
