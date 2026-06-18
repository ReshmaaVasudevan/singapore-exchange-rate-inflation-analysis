# Impact of Exchange Rate Fluctuations on Singapore's Inflation

Econometric study examining how SGD exchange rate movements 
against major currencies (USD, EUR, GBP, INR) transmit to 
Singapore's Consumer Price Index (CPI) and Import Price 
Index (IPI).

## Overview
Singapore's monetary policy is unique — the MAS manages the 
SGD exchange rate directly rather than adjusting interest rates. 
This study quantifies how effective that approach is in 
containing imported inflation, using 10 years of monthly data 
(2014–2024).

## Research Questions
- Do SGD exchange rate movements directly affect consumer inflation?
- Is the transmission channel direct (FX → CPI) or indirect 
  (FX → IPI → CPI)?
- How long does the transmission lag take?

## Key Findings
| Finding | Result |
|---------|--------|
| FX → CPI (direct) | Weak, not statistically significant |
| FX → IPI (import prices) | Statistically significant |
| IPI → CPI (Granger causality) | **p = 0.035** ✓ |
| Transmission lag | **2–4 months** via import prices |
| SGD/GBP → CPI | Significant at 5% level (β = −0.042) |

**Conclusion:** Exchange rate shocks transmit to consumer 
inflation *indirectly* through import prices, with a 2–4 month 
delay — supporting the effectiveness of MAS's exchange-rate-based 
monetary policy.

## Methodology
```
1. Descriptive Analysis    — distribution plots, correlation heatmap
2. Time Series Decomposition — trend, seasonal, residual (additive model)
3. OLS Regression          — FX returns → CPI inflation & IPI inflation  
4. Granger Causality Tests — FX → IPI, FX → CPI, IPI → CPI
5. VAR Modelling           — multivariate dynamic relationships
6. Impulse Response (IRF)  — shock propagation over 12-month horizon
```

## Regression Results Summary

**CPI Inflation on Exchange Rate Returns (OLS)**
| Variable | Coefficient | p-value |
|----------|-------------|---------|
| Intercept | 0.1169 | 0.001*** |
| SGD/USD Return | 0.001 | 0.961 |
| SGD/EUR Return | 0.027 | 0.284 |
| SGD/GBP Return | −0.042 | 0.039* |
| R² | 0.0101 | |

**Granger Causality Tests**
| Hypothesis | F-statistic | p-value |
|------------|-------------|---------|
| FX → IPI Inflation | 0.8753 | 0.456 |
| FX → CPI Inflation | 0.6167 | 0.605 |
| IPI → CPI Inflation | 2.9519 | **0.035*** |

## Data Sources
| Dataset | Source | Frequency |
|---------|--------|-----------|
| SGD/USD, EUR, GBP, INR exchange rates | MAS (mas.gov.sg) | Daily → Monthly avg |
| Consumer Price Index (CPI) | SingStat (singstat.gov.sg) | Monthly |
| Import Price Index (IPI) | SingStat (singstat.gov.sg) | Monthly |
| Sample period | 2014–2024 | 141 observations |

## Tech Stack
- **R** — primary analysis (dplyr, ggplot2, xts, lubridate, 
  vars, readxl)
- **Python** — supporting EDA (Pandas, NumPy, Matplotlib, 
  Seaborn, statsmodels)
- Jupyter Notebook / R Markdown

## How to Run
```bash
# Python EDA
pip install pandas numpy matplotlib seaborn statsmodels
jupyter notebook exchange_rate_inflation_analysis.ipynb

# R analysis
install.packages(c("readr","dplyr","ggplot2","xts",
                   "lubridate","vars","readxl"))
# Run exchange_rate_analysis.R
```

## Project Structure
```
singapore-exchange-rate-inflation-analysis/
│
├── data/
│   └── final_I_hope.xlsx        # Combined MAS + SingStat dataset
├── exchange_rate_inflation.ipynb # Python EDA and visualizations
├── exchange_rate_analysis.R      # R econometric models
└── README.md
```

## Key Visualizations
- SGD/USD exchange rate distribution and trend
- CPI vs IPI comparison (dual-axis time series)
- Correlation heatmap: exchange rates, CPI, IPI
- Time series decomposition (trend, seasonal, residual)
- Impulse response functions (CPI and IPI response to USD shock)

## Policy Implication
Results support MAS's exchange-rate-based monetary framework. 
Import prices serve as the primary transmission channel from 
external shocks to domestic inflation — meaning SGD appreciation 
effectively dampens imported inflation, but with a 2–4 month lag.

## References
- MAS Statistics: https://www.mas.gov.sg/statistics
- SingStat: https://www.singstat.gov.sg
- CONG, D.C.G. (2024). Exchange rate pass-through: Evidence 
  from Singapore. NUS Libraries.
