# OLS_regression_wages
OLS regression models of hourly wages on a variety of explanatory variables with a focus on education and work experience, using data collected from the 1976 US current population survey. 

# README

## Explaining Wage Variability in the US Using OLS Models

## Project Overview

The project investigates the relationship between hourly wages and socioeconomic characteristics using Ordinary Least Squares (OLS) regressions. This is conducted under 3 different OLS regressions. Model 1 is a regression of wage on education and a constant, model 2 a regression of wage on education, work experience and a constant, and model 3 is a regression of wage on education, work experience, tenure, gender, marital status, number of dependents and a constant. By estimating the models sequentially, the relationship between education and wages changes with the introduction of additional controls across the models and can therefore be examined. Coefficients and statistical significance are compared across the models. A full research report including a literature review, reproducible Python notebook, and supporting documentation are included in this repository.

## Dataset

The dataset 'wage1' is from Wooldridge's assessment of the 1976 US current population survey, although it is accessed through the RDatasets repository maintained by Vincent Arel-Bundock linked below: <https://vincentarelbundock.github.io/Rdatasets/csv/wooldridge/wage1.csv>.

The dataset contains 526 observations and 23 explanatory variables, of which 6 are used in the models presented in the report and listed in the table below.

| Variable | Code name | Variable type | Definition |
|---|---|---|---|
| Wage | wage | Integer | Hourly wage ($) |
| Education | educ | Integer | Years of education |
| Experience | exper | Integer | Years of potential work experience |
| Tenure | tenure | Integer | Years with current employer |
| Gender | female | Categorical | Dummy variable (1 if female, 0 if male) |
| Marital Status | married | Categorical | Dummy variable (1 if married, 0 if not married) |
| Number of dependents | numdep | Integer | Number of dependents in the household |

## Methodology

The 3 OLS models are estimated as follows and compared using coefficient estimates, statistical significance, and R-squared.

**Model 1:**

$${wage}_{i} = \beta_{0} + \beta_{1}{educ}_{i} + \varepsilon_{i}$$

**Model 2:**

$${wage}_{i} = \alpha_{0} + \alpha_{1}{educ}_{i} + \alpha_{2}{exper}_{i} + \mu_{i}$$

**Model 3:**

$${wage}_{i} = \pi_{0} + \pi_{1}{educ}_{i} + \pi_{2}{exper}_{i} + \pi_{3}{tenure}_{i} + \pi_{4}{female}_{i} + \pi_{5}{married}_{i} + \pi_{6}{numdep}_{i} + \gamma_{i}$$

The following diagnostic procedures are also performed prior to conducting each regression:

- Breusch-Pagan test for heteroskedasticity
- Heteroskedasticity-robust (HC1) standard errors
- Variance Inflation Factor (VIF) analysis
- Residuals versus fitted values analysis

## Main Findings

- The explanatory power of the models increases as additional variables are introduced (table below).

| Model | R-squared |
|---|---|
| Regression 1 | 0.165 |
| Regression 2 | 0.225 |
| Regression 3 | 0.370 |

- Education and experience have positive and statistically significant coefficients.
- In the full model, the estimated coefficient for the 'female' variable is -1.76. This is evidence of the gender pay gap as females have an estimated hourly wage approximately $1.76 lower than males, conditional on the other variables included in the model.
- Results should be interpreted as conditional associations rather than causal effects because the data are observational, and OVB and endogeneity remain.

## Limitations

The main limitations of the analysis are:

- The dataset is from 1976 and has limited relevance to current labour markets
- The dataset only has 526 observations from observational data which shouldn't be interpreted causally
- OVB and measurement error may affect estimates
- 'exper' represents potential work experience rather than actual labour market experience
- The models don't include experience as a quadratic term and may fail to fully capture nonlinear returns to experience

## Repository Structure

| File | Description |
|---|---|
| README_applied.md | Project overview, setup instructions, methodology and key findings |
| Applied_report.pdf | Full research report with literature review, methodology, results and discussion |
| OLS_wage.ipynb | Code following the 3 OLS regressions and diagnostic tests |
| Requirements_applied.txt | Required Python packages |
| LICENSE | MIT License |
| .gitignore | Specifies files ignored by Git |

## Requirements

- Python 3.12
- matplotlib
- pandas
- seaborn
- statsmodels

## How to Run

1. Clone the repository
2. Install the required Python packages
3. Open the notebook: OLS_wage.ipynb
4. Run all the cells from top to bottom

## References

Arel-Bundock, V. (n.d.). *wage1.csv*. RDatasets, Wooldridge dataset. [online] Available at: <https://vincentarelbundock.github.io/Rdatasets/csv/wooldridge/wage1.csv>.

Blau, F. and Kahn, L. (2016). The Gender Wage Gap: Extent, Trends, and Explanations. [online] doi:10.3386/w21913.

Blundell, R., Dearden, L., Meghir, C. and Sianesi, B. (1999). Human Capital Investment: The Returns from Education and Training to the Individual, the Firm and the Economy. *Fiscal Studies*, [online] 20(1), pp.1-23. doi:10.1111/j.1475-5890.1999.tb00001.x.

Card, D. (1999). The Causal Effect of Education on Earnings. *Handbook of Labor Economics*, [online] pp.1801-1863. doi:10.1016/s1573-4463(99)03011-4.

Hanson, M. (2020). *U.S. Public Education Spending Statistics*. [online] Education Data Initiative. Available at: <https://educationdata.org/public-education-spending-statistics> [Accessed 10 Sept. 2026].
