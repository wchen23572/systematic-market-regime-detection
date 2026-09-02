# systematic-market-regime-detection
Unsupervised market regime detection using PCA, K-Means, macroeconomic indicators, and cross-asset data.
# Systematic Market Regime Detection & Cross-Asset Analysis

Unsupervised market-regime detection using **PCA, K-Means clustering, macroeconomic indicators, and cross-asset market data**.

## Overview

This project investigates whether unsupervised machine learning can identify economically meaningful market regimes from macroeconomic and financial-market data.

Using **4,681 daily observations** and **13 market and macroeconomic features**, the analysis applies:

- Standardization
- Principal Component Analysis (PCA)
- K-Means clustering
- Silhouette analysis
- Historical regime validation
- Cross-asset performance analysis
- Regime-transition analysis
- Clustering-stability testing

The final model identifies three interpretable market regimes:

1. **Low-Volatility / Risk-On**
2. **Inflationary / Tight Monetary**
3. **Crisis / Severe Risk-Off**

## Key Results

- PCA reduces **13 features to 7 principal components** while retaining **92.21% of total variance**.
- Silhouette analysis selects **3 clusters** as the preferred K-Means solution.
- The model classifies:
  - Lehman Brothers bankruptcy as **Crisis / Severe Risk-Off**
  - The 2011 U.S. credit downgrade as **Crisis / Severe Risk-Off**
  - The March 2020 COVID crash as **Crisis / Severe Risk-Off**
  - The June 2022 inflation/rate-hike environment as **Inflationary / Tight Monetary**
- Cross-asset behavior differs materially across regimes:
  - **SPY** performs strongest during Risk-On conditions
  - **GLD** performs particularly well during Inflationary / Tight Monetary conditions
  - **TLT** performs strongly during Crisis conditions
- K-Means clustering is stable across tested random initializations, with **ARI = 1.00** across all tested seeds.

## Data

### Market Data

Market data are sourced from Yahoo Finance.

| Ticker | Representation |
|---|---|
| SPY | U.S. equities / S&P 500 |
| TLT | Long-term U.S. Treasuries |
| GLD | Gold |
| DBC | Broad commodities |
| UUP | U.S. dollar |
| ^VIX | Expected S&P 500 volatility |

### Macroeconomic Data

Macroeconomic data are sourced from Federal Reserve Economic Data (FRED).

Features include:

- Year-over-year inflation
- Unemployment rate
- Federal Funds Rate
- 10-Year Treasury yield
- 2-Year Treasury yield
- 10Y–2Y yield-curve spread

Monthly macroeconomic variables are lagged by one monthly observation as a conservative approximation of information availability.

## Feature Set

The final model uses 13 features:

### Market Features

- SPY 60-day momentum
- SPY 30-day realized volatility
- VIX level
- TLT 60-day momentum
- GLD 60-day momentum
- DBC 60-day momentum
- UUP 60-day momentum

### Macroeconomic / Rate Features

- Inflation YoY
- Unemployment
- Federal Funds Rate
- 10-Year Treasury yield
- 2-Year Treasury yield
- Yield-curve spread

## Methodology

```text
Market & Macro Data
        ↓
Feature Engineering
        ↓
Data Alignment
        ↓
Standardization
        ↓
PCA
        ↓
Cluster Selection
        ↓
K-Means
        ↓
Regime Interpretation
        ↓
Historical Validation
        ↓
Cross-Asset Performance Analysis
