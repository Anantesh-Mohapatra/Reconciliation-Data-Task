# AGENTS.md - Global Rules for This Project

## Core Principles
- Write clean, readable, heavily commented R code.
- Code should favor clarity over cleverness:
  - explicit variable names
  - step-by-step transformations
  - no dense one-liners
- Never make silent judgment calls.
- If something is ambiguous, document it.

## Language Requirement
- Use R only.
- Do not write Python code.
- The primary analysis file is `run_analysis.Rmd`, which must be runnable top-to-bottom from a single entry point.

## Logging and Transparency
- Maintain a curated NOTES.md file:
  - keep only lessons, shortcuts, and preventive notes for future work
  - keep entries specific and actionable
- For any major analytical decisions, always defer to user
- If an ambiguity cannot be resolved cleanly, proceed only with a clearly documented default, or stop

## Data Safety
- Treat raw data files as read-only.
- Never overwrite the original Excel file.
- The final dataset used for analysis must be written to /output.

## Failure Mode
- Fail loudly and early if assumptions are violated:
  - missing required variables
  - unexpected factor levels
  - implausible ranges
  - sample sizes too small to proceed
- Use clear error messages explaining what failed and why.

## Scope Control
- Only analyze variables explicitly described in plan.md.
- Do not introduce new predictors, outcomes, or controls.
- Ignore free-text fields unless explicitly instructed.

## Output Discipline
- Any tables, figures, and text outputs go in /output.
- Produce paste-ready artifacts (tables, captions).

These rules apply to all steps unless explicitly overridden in plan.md.
