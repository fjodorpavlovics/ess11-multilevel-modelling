# Multilevel Modelling of Trust in Parliament

An R project demonstrating least-squares estimation and multilevel modelling using European Social Survey Round 11 data.

The emphasis is on explaining the statistical methods, connecting equations to R code, and interpreting model outputs. Trust in parliament provides the empirical application.

## View the project

- [Analysis source: R Markdown](mlm_ess11.Rmd)
- [HTML report with explanations, outputs and figures](mlm_ess11.html)

To read the rendered report, download the HTML file and open it in a web browser.

## Data and variables

The analysis includes respondents from 30 countries and 328 regions. Models containing all predictors use 47,217 respondents.

- **Outcome:** trust in parliament.
- **Religiosity predictors:** self-rated religiosity, religious attendance and prayer frequency.
- **Controls:** age, gender, educational level and political interest.

Numeric scores are standardised using unweighted sample means and standard deviations. Gender is coded as a binary indicator. ESS analysis weights are supplied during model estimation.

## Methods covered

- Weighted least squares: coefficient estimation, matrix notation and residual sums of squares.
- Regression fit: variance estimation, F-tests, R² and adjusted R².
- Regional null and random-intercept models.
- Regional random slopes for self-rated religiosity.
- Three-level models with respondents nested within regions and countries.
- Model comparison using maximum-likelihood fits, AIC, BIC and likelihood-ratio tests.
- Visualisation of regional random effects and residual diagnostics.

Multilevel variance components are estimated using REML for the reported models. Fixed-effect estimation connects to generalised least squares under the estimated covariance structure; `lme4` uses penalised least-squares computations within the fitting procedure.

## Main findings

Among the three compared predictor models, the specification combining regional random intercepts, regional religiosity slopes and country random intercepts has the lowest AIC and BIC.

The estimated religiosity association varies across regions, while country intercepts account for substantial differences in baseline trust. Residual diagnostics indicate limitations in the assumed error distribution and variance structure.

These results describe conditional associations and do not establish causal effects.

## Reproducing the analysis

1. Obtain the ESS Round 11 integrated dataset, edition 4.1, from the [ESS Data Portal](https://ess.sikt.no/).
2. Install the required R packages:
   ```r
   install.packages(c(
     "dplyr", "tidyr", "lme4", "ggplot2",
     "performance", "rmarkdown", "knitr"
   ))
