# Analysis Plan - Predoc Data Task

This file defines the full analytical plan Codex must follow.
Do not deviate from this plan unless explicitly instructed.
All judgment calls must be logged.
All analysis must be implemented in R.

---

## 1. Research Question

Primary question:
- Are respondents of different sexes more or less likely to report choosing an apologetic or conciliatory response in the survey's conflict scenarios?

Secondary considerations:
- Does this relationship persist after controlling for respondent age?
- Does including or excluding real/imaginary conflict framing affect results?
- Does including or excluding blame affect results?

Context:
- The analysis concerns patterns in survey responses to conflict scenarios.
- Sex is the primary explanatory variable.
- Age is a control only.
- Real/imaginary framing and blame are not the main focus and should be treated as controls or handled via sample restriction.

---

## 2. Data Sources

- One Excel file containing:
  - survey responses
  - a key/metadata sheet describing variables
- Treat the Excel file as read-only.

---

## 3. Variables and Roles

### Primary Explanatory Variable
- `sex`
  - Use as the main predictor.
  - If missing sex is present after cleaning, exclude those observations from the main analysis.

### Control Variable
- `age`
  - Numeric control only.
  - Do not use as a moderator.

### Additional Control (Robustness)
- `blame_1`
  - Use only as an additional control in robustness checks.
  - Do not treat as a primary explanatory variable.

### Additional Control / Sample Dimension
- `real_imaginary`
  - Indicates whether respondent recalled a real or imagined conflict.
  - Use only as a control or for robustness checks.
  - Do not treat as a primary explanatory variable.

### Outcomes
- Binary indicators capturing apologetic or conciliatory responses.
- Carefully map survey response options to 0/1 outcomes.
- Document all recoding decisions.

### Filtering Variables
- `Finished`
- `passedattn`

These are used only for sample construction.

### Explicit Exclusions
- Free-text conflict descriptions
- Location variables (latitude/longitude)
- Captcha-related fields
- System metadata fields

---

## 4. Sample Construction

Steps:
1. Load raw data and record raw N.
2. Apply eligibility filters; exclude respondents who:
   - did not finish the survey
   - failed the attention check (`passedattn`)
   - explicitly indicated their responses should not be used
3. Perform data-quality checks (ranges, missingness, observed levels) on the eligible sample.
4. Review extreme values (e.g., ages > 100), print flagged rows, and defer to user on how to handle flagged rows.
5. Apply any explicit data-quality exclusions (e.g., drop the extreme-age row).
6. Recode outcomes and controls with strict allowed-values checks (fail loudly on unexpected values).
7. Summarize post-recode missingness for core variables.
8. Construct the final analysis sample (exclude missing sex only if present).
9. Save a cleaned analysis dataset to /output.

Log:
- Counts at each exclusion step.
- Final analysis sample size.

---

## 5. Preliminary Checks

Before analysis:
- Inventory all variables used.
- Verify ranges and missingness.
- List observed levels of categorical variables.
- Confirm each respondent appears once.
- Confirm key variables vary between respondents, not within.

---

## 6. Descriptive Statistics

Produce:
- Descriptive statistics for outcomes, sex, age, blame, and real/imaginary framing.

---

## 7. Main Analysis

### 7.1 Difference-in-Means (T-test)
- Compare outcome proportions across sex.
- Report group means, differences, confidence intervals, and p-values.

### 7.2 Regression Analysis
- Estimate linear probability models:
  - outcome ~ sex + age
  - optionally include real_imaginary as a control
- Clearly label the main specification.

Report:
- Regression tables.
- Effect sizes interpreted as changes in probability.

---

## 8. Robustness Checks

Conduct and document:

1. Control robustness:
   - Re-estimate models with and without real_imaginary included.
   - Re-estimate models with and without blame_1 included.

2. Sample robustness:
   - Only if missing sex is present after cleaning, consider alternative handling.

3. Estimator robustness:
   - Compare linear probability models across specifications only.

Each robustness check must include:
- A short statement of purpose after discussion with user.
- A clear comparison to the main results.

---

## 9. Outputs for Final Report

Produce:
- Main tables
- Robustness tables
- Appendix sections addressing:
  - ranges and missingness
  - data structure
  - variable levels
  - missing data handling
- A cleaned analysis dataset saved to /output.

---

## 10. Logging Requirements

Throughout execution:
- Keep NOTES.md as a curated lessons/shortcuts document (not an activity log).
- Log unexpected issues and fixes only if they yield a reusable lesson.
- If an ambiguity arises:
  - document it
  - propose options
  - choose a default only with justification

Do not proceed silently past ambiguities.

---

End of plan.
