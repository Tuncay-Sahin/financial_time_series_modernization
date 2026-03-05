# Financial Time Series Analysis of Consumer Confidence (VAR Model)
🇹🇷 Turkish project report is available in `docs/project_report.md`.

This repository presents an econometric analysis of the dynamic relationships between **consumer confidence and macroeconomic variables** using a **Vector Autoregression (VAR)** framework.

The project investigates how macroeconomic shocks propagate through the system and how consumer confidence reacts to changes in key economic indicators.

---

## Navigation

- [Project Overview](#project-overview)
- [Methodology](#methodology)
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

# Key Findings

The empirical results reveal several important insights:

- **Consumer confidence is primarily driven by its own shocks**, explaining roughly **80% of the forecast error variance**.

- **Exchange rate shocks contribute moderately**, accounting for approximately **13% of consumer confidence variability**.

- **Macroeconomic shocks dissipate relatively quickly**, with impulse responses typically fading within **6–8 periods**.

- Residual diagnostic tests indicate that the **VAR model provides a stable and statistically adequate representation** of the system.

Overall, the findings suggest that consumer confidence is influenced by macroeconomic conditions but remains largely shaped by **internal expectation dynamics**.

---

# Repository Structure

```text
financial_time_series_modernization/
│
├── data/
│   ├── raw/            # Original dataset
│   ├── interim/        # Intermediate processing (optional)
│   └── processed/      # Cleaned or transformed data
│
├── notebooks/
│   └── 01_var_analysis.ipynb   # Main econometric analysis notebook
│
├── docs/
│   └── project_report.md       # Detailed methodological and analytical report
│
├── requirements.txt            # Python dependencies
├── .gitignore                  # Files excluded from version control
└── README.md                   # Project documentation