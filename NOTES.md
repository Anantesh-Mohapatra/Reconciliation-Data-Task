NOTES (LESSONS AND SHORTCUTS)

- If `readxl` warns about being built under a different R version, it is usually non-fatal but should be noted; re-install the package if it becomes a reproducibility concern.
- PDF rendering requires Pandoc and a TeX engine (TinyTeX is sufficient) on PATH; if missing, render will fail.
- When an `.Rmd` is not in the project root, set `knitr::opts_knit$set(root.dir = "..")` to keep relative paths working.
- `stargazer` LaTeX tables render cleanly when the chunk uses `results = "asis"` and `comment = NA`.
- For `stargazer` robustness tables, pass models as a list and set `object.names = FALSE` to avoid name-parsing errors.
- Avoid wrapping `stargazer` output in `\resizebox{}`; it can trigger LaTeX ?outer par mode? errors. If width is a concern, adjust table content instead.
- If a data-cleaning chunk depends on intermediate objects, recompute masks/counts inside the chunk to avoid object-not-found errors during knit.
- If you enable `knitr` tidy formatting, add `formatR` to required packages; set a width cutoff (e.g., 80) to avoid PDF overflow.
