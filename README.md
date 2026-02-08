# USD-INR Exchange Rate Forecasting using SARIMAX

This project implements a sophisticated time-series forecasting model to predict the **USD-INR exchange rate**. It integrates traditional econometric tests with modern machine learning preprocessing to determine how macroeconomic factors—such as interest rates, crude oil, and trade balances—influence currency valuation.

## 📊 Project Overview

The objective is to move beyond simple linear regression to a statistically robust **SARIMAX (Seasonal AutoRegressive Integrated Moving Average with Exogenous Regressors)** model. The project demonstrates the full data science lifecycle, from multi-source web scraping to advanced model diagnostics.

### Key Features

* 
**Multi-Source Data Integration:** Automated data extraction from the **FRED Database**, **RBI historical archives** (via HTML scraping), and local datasets.


* 
**Statistical Rigor:** Implements **Augmented Dickey-Fuller (ADF)** tests to ensure stationarity, a prerequisite for reliable time-series modeling.


* 
**Multicollinearity Detection:** Utilizes **Variance Inflation Factor (VIF)** to identify redundant features, finding high correlation between Trade Balance and Total Reserves.


* 
**Comparative Modeling:** Compares **Ordinary Least Squares (OLS)** results against **SARIMAX** to highlight why accounting for autocorrelation is vital in economic data.



---

## 🛠️ Technical Workflow

### 1. Data Collection & Preprocessing

* 
**Indicators:** USD/INR Spot Rate, US CPI, WTI Crude Oil, India Trade Balance, US Federal Funds Rate (EFFR), RBI Repo Rate, and India Foreign Exchange Reserves.


* 
**Cleaning:** Handled missing data via linear interpolation and forward filling.


* 
**Stationarity:** Initial data showed a p-value of **0.947** (non-stationary). After applying **First Differencing** (Month-over-Month change), the p-value dropped to **2.01e-25**, confirming stationarity.



### 2. Feature Engineering

* Used **StandardScaler** to normalize features with vastly different scales (e.g., interest rate percentages vs. billions in reserves).


* Targeted the **Month-over-Month (MoM) change** to isolate the immediate impact of economic shifts.



### 3. The SARIMAX Model

* 
**Order:** (1, 1, 0).


* 
**Key Findings:** The **ar.L1** coefficient (-0.5459) is highly significant (p < 0.000), indicating a strong "mean-reverting" tendency where sharp jumps in the exchange rate often experience a pullback the following month.


* 
**Drivers:** Total Reserves (USD) emerged as one of the most important factors for exchange rate stability.



---

## 📈 Results & Forecast

The model provides a 6-month forecast of the USD-INR level.

* 
**Validation:** Residual analysis (Jarque-Bera p=0.10) confirms the errors are normally distributed.


* 
**Forecast Output:** The model projects the USD/INR level to hover around **88.48 by June 2026** based on current macroeconomic trajectories.
