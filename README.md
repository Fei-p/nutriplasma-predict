# NutriPlasmaPredict: Modeling Plasma Beta-Carotene & Retinol from Diet and Demographics

## Overview
This project models **plasma beta-carotene (BETAPLASMA)** and **retinol (RETPLASMA)** levels using dietary intake and participant characteristics. We compare first-order and interaction models, apply log-transformations where appropriate, and evaluate fit and generalization with diagnostics and a train/validation split. 

## Key findings (brief)
- **Beta-carotene (log scale):** Higher **fiber** and **vitamin use** associate with higher levels; **Quetelet index (adiposity)** and **fat intake** associate with lower levels; **age** shows a positive effect in some models. 
- **Retinol (log scale):** **Sex (male)**, **calories**, and **age** are the most consistent predictors; interaction terms offer limited incremental gain. 
- Model selection used **AIC/BIC**, **Mallows’ Cp**, **PRESS**, and test-set error; the simpler log-linear models performed competitively vs. larger interaction sets. 

> See the report for full coefficients, diagnostics (Box-Cox, residuals, leverage), and validation summaries. 

## Repository contents
- **`NutriPLasmaPredict_Proj.pdf`** — Report with EDA, model building, diagnostics, and validation results. 
- **`RMD_scripts.rmd`** — R Markdown code used to produce the analysis and figures.  
- **`README.md`** — This file.

## Data
The analysis uses the **Plasma** dataset (course dataset). The response variables are **BETAPLASMA** (beta-carotene) and **RETPLASMA** (retinol). Predictors include demographics (e.g., **AGE**, **SEX**, **SMOKSTAT**), diet (e.g., **CALORIES**, **FAT**, **FIBER**, **ALCOHOL**, **CHOLESTEROL**, **BETADIET**, **RETDIET**), and indices such as **QUETELET**. Categorical variables (**SEX**, **SMOKSTAT**, **VITUSE**) are treated as factors. 

## Methods
- **EDA:** type checks, distributions, pairwise plots, ANOVA/Tukey HSD for group differences. 
- **Modeling:** multiple linear regression for **log(BETAPLASMA)** and **log(RETPLASMA)**; first-order and selected **interaction** terms via stepwise AIC. 
- **Diagnostics:** residual plots, normality checks, **Box-Cox**, leverage/influence; proportional comparison of alternative specifications. 
- **Selection/Validation:** **AIC, BIC, Cp, PRESS**, and **hold-out validation** (80/20 split) with MSPE comparison.

## How to reproduce
1. Open **`RMD_scripts.rmd`** in RStudio.  
2. Install packages (first run only):
   ```r
   install.packages(c(
     "dplyr","MASS","broom","tibble","knitr","psych"
   ))
