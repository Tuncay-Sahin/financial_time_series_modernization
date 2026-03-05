# Financial Time Series Analysis of Consumer Confidence (VAR Model)

🇹🇷 Turkish project report is available in `docs/project_report.md`.

![Python](https://img.shields.io/badge/Python-3.12-blue)
![Econometrics](https://img.shields.io/badge/Model-VAR-green)
![TimeSeries](https://img.shields.io/badge/Analysis-Time%20Series-orange)

This repository presents an econometric analysis of the dynamic relationships between **consumer confidence and macroeconomic variables** using a **Vector Autoregression (VAR)** framework.

The project investigates how macroeconomic shocks propagate through the system and how consumer confidence reacts to changes in key economic indicators.

---

## Navigation

- [Project Overview](#project-overview)
- [Methodology](#methodology)
- [Model Pipeline](#model-pipeline)
- [Analysis Workflow](#analysis-workflow)
- [Key Findings](#key-findings)
- [Repository Structure](#repository-structure)
- [Future Work](#future-work)

---

# Project Overview

Consumer confidence is an important indicator reflecting households’ expectations about economic conditions. Understanding the drivers of consumer confidence provides valuable insights into economic sentiment and potential future consumption behavior.

This project analyzes the dynamic interactions between:

- Consumer Confidence Index (CCI / TGE)
- USD Exchange Rate
- Real Effective Exchange Rate
- Stock Market Index (BIST)
- Industrial Production Indicators
- Inflation
- Economic Confidence Indicators

The analysis focuses on identifying:

- how macroeconomic shocks influence consumer confidence
- how long these shocks persist
- the relative importance of different economic variables

To address these questions, a **Vector Autoregression (VAR)** model is estimated and evaluated using standard econometric diagnostics.

---

# Methodology

The analysis follows a standard econometric workflow used in **macroeconomic time series modeling**.

### 1. Data Preparation

- Import and structure macroeconomic time series data
- Handle missing values
- Apply log transformations where appropriate

### 2. Stationarity Testing

- Augmented Dickey-Fuller (ADF) tests
- Transformation using **log-differences** to ensure stationarity

### 3. VAR Model Estimation

- Lag length selection using information criteria
- Estimation of a **Vector Autoregression (VAR)** model
- Stability diagnostics

### 4. Granger Causality Analysis

- Testing directional relationships between variables
- Identification of predictive relationships in the system

### 5. Impulse Response Analysis (IRF)

- Evaluating how shocks propagate through the system
- Measuring dynamic responses of consumer confidence to macroeconomic shocks

### 6. Forecast Error Variance Decomposition (FEVD)

- Quantifying the contribution of each variable to forecast error variance
- Understanding the relative importance of different macroeconomic drivers

### 7. Residual Diagnostics

Model adequacy is evaluated using:

- Portmanteau (Whiteness) test for serial correlation
- Normality test of residuals
- Residual ACF inspection
- Q-Q plot analysis

These diagnostics help ensure that the model specification is statistically appropriate.

---

# Model Pipeline

The econometric analysis follows a structured pipeline from raw macroeconomic data to economic interpretation.

Raw Macroeconomic Data  
↓  
Data Cleaning & Preparation  
↓  
Stationarity Testing (ADF)  
↓  
Log-Difference Transformation  
↓  
VAR Model Estimation  
↓  
Lag Selection & Stability Check  
↓  
Granger Causality Analysis  
↓  
Impulse Response Functions (IRF)  
↓  
Forecast Error Variance Decomposition (FEVD)  
↓  
Residual Diagnostics  
↓  
Economic Interpretation

---

# Analysis Workflow

The analytical workflow implemented in this repository follows a standard empirical macroeconometric research pipeline.

Data Collection  
↓  
Exploratory Data Analysis  
↓  
Stationarity Tests  
↓  
Model Specification  
↓  
VAR Estimation  
↓  
Dynamic Analysis (IRF & FEVD)  
↓  
Model Diagnostics  
↓  
Economic Interpretation

This workflow reflects a typical structure used in **macroeconomic time series analysis and applied econometrics research**.

---

# Key Findings

The empirical results reveal several important insights:

- **Consumer confidence is primarily driven by its own shocks**, explaining roughly **80% of the forecast error variance**.

- **Exchange rate shocks contribute moderately**, accounting for approximately **13% of consumer confidence variability**.

- **Macroeconomic shocks dissipate relatively quickly**, with impulse responses typically fading within **6–8 periods**.

- Residual diagnostic tests indicate that the **VAR model provides a stable and statistically adequate representation** of the system.

Overall, the findings suggest that consumer confidence is influenced by macroeconomic conditions but remains largely shaped by **internal expectation dynamics**.

---

# Repository Structure

financial_time_series_modernization/

data/  
&nbsp;&nbsp;&nbsp;&nbsp;raw/ — original dataset  
&nbsp;&nbsp;&nbsp;&nbsp;interim/ — intermediate processing  
&nbsp;&nbsp;&nbsp;&nbsp;processed/ — cleaned or transformed data  

notebooks/  
&nbsp;&nbsp;&nbsp;&nbsp;01_var_analysis.ipynb — main econometric analysis notebook  

docs/  
&nbsp;&nbsp;&nbsp;&nbsp;project_report.md — detailed project report  

requirements.txt — Python dependencies  
.gitignore — excluded files  
README.md — project documentation

---

# Future Work

Several extensions could further enhance the analysis.

### Dataset Expansion

Extending the dataset to include more recent observations would allow capturing **new economic cycles and structural shifts**.

### Cointegration Analysis

Future work could test for **long-run equilibrium relationships** between variables using the **Johansen cointegration test**.

If cointegration is detected, the analysis could be extended using a **Vector Error Correction Model (VECM)**.

### Structural Models

Additional econometric approaches could be explored:

- Structural VAR (SVAR)
- Nonlinear time series models
- Regime-switching models

### Forecasting Applications

The VAR framework could be extended to perform **out-of-sample forecasting** of consumer confidence dynamics.

---

# Author

This project was developed as part of a learning and research effort in:

- Financial Time Series Analysis  
- Econometrics  
- Applied Data Science with Python
