# P&G Stock Risk Analysis — CAPM & Fama-French Three-Factor Model

**Team Project — NYU Tandon, Financial Analysis**
Shubh Patel, Domenico Nigro, Divya Mudliar, Ziang Lu

A quantitative asset pricing analysis of Procter & Gamble (NYSE: PG) using the Capital Asset Pricing Model (CAPM) and the Fama-French Three-Factor Model, built on 144 months of return data and tested through formal statistical hypothesis testing.

---

## Project Overview

This project asks a simple question with a rigorous answer: **does P&G generate returns beyond what its risk exposure predicts, and how risky is it relative to the market?**

Using monthly return data from November 2012 to October 2024, we estimate P&G's market beta, test it against formal hypotheses, then extend the analysis with the Fama-French Three-Factor Model to isolate size and value effects from pure market risk.

---

## Data Sources

| Source | Data | Period |
|--------|------|--------|
| Yahoo Finance | PG daily adjusted close prices | Nov 2022 – Nov 2024 (506 obs) |
| Yahoo Finance | PG monthly adjusted close prices | Oct 2012 – Oct 2024 (144 months) |
| Kenneth French Data Library | Mkt-RF, SMB, HML, RF factors | Nov 2012 – Oct 2024 (144 months) |

---

## Methodology

### Model 1 — CAPM
```
(R_PG − RF) = α + β(Mkt-RF) + ε
```
Single-factor model isolating P&G's sensitivity to overall market risk.

### Model 2 — Fama-French Three-Factor
```
(R_PG − RF) = α + β_MKT(MKT) + β_SMB(SMB) + β_HML(HML) + ε
```
Extends CAPM by adding size (SMB) and value (HML) factors to isolate pure market risk from size and value premiums.

---

## Key Findings

### 1. No Significant Trend in Daily Returns
R² of linear trendline = 0.04% — daily returns behave as random noise, consistent with weak-form market efficiency.

### 2. Risk-Return Trade-off
| Metric | PG | Market |
|--------|-----|--------|
| Avg monthly excess return | 0.59% | 1.10% |
| Monthly std deviation | 4.44% | 4.29% |

PG underperformed the market on average return while carrying comparable risk — a less favorable risk-return trade-off over this period.

### 3. CAPM Regression Results
| Coefficient | Estimate | Std Error | t-Stat | p-value |
|-------------|----------|-----------|--------|---------|
| α (Intercept) | 0.00177 | 0.00357 | 0.495 | 0.621 (not significant) |
| β (Market) | 0.377 | 0.0808 | 4.658 | 0.0000073 (significant) |

**R² = 13.25%** — β confirms PG as a **defensive stock**: for every 1% market move, PG moves only ~0.38%.

### 4. Hypothesis Testing
- **H₀: β = 0** → REJECTED (t = 4.658, p < 0.05) — market exposure is real
- **H₀: β ≤ 1** → FAILED TO REJECT (t = −7.711) — PG is not riskier than the market
- **H₀: α ≤ 0** → FAILED TO REJECT (FF3 model) — no evidence of positive risk-adjusted alpha

### 5. Fama-French Three-Factor Results
| Coefficient | Estimate | t-Stat | p-value |
|-------------|----------|--------|---------|
| α | −0.00022 | −0.067 | 0.947 (not significant) |
| β_MKT | 0.495 | 6.424 | < 0.001 (significant) |
| β_SMB | −0.681 | −5.481 | < 0.001 (significant) |
| β_HML | 0.068 | 0.749 | 0.455 (not significant) |

**R² jumps from 13.25% (CAPM) to 28.61% (FF3)** — adding SMB and HML nearly doubles explanatory power. The negative SMB beta confirms PG trades like a large-cap stock, underperforming when small caps rally.

### 6. Collinearity Check
All pairwise correlations between MKT, SMB, and HML were below 0.30 — no problematic multicollinearity, supporting inclusion of all three factors in the model.

---

## Model Comparison

| Metric | CAPM | FF3 |
|--------|------|-----|
| R² | 13.25% | 28.61% |
| Adjusted R² | 12.64% | 27.08% |
| Residual Std Error | 0.04146 | 0.03788 |
| Significant Factors | Market only | Market + SMB |

---

## Conclusions

1. **P&G is a defensive, large-cap stock** — low market beta (0.377–0.495), significantly negative SMB exposure
2. **No evidence of positive alpha** — consistent with market efficiency; PG's price reflects available information
3. **No value/growth tilt** — HML coefficient is not statistically significant
4. **Size factor materially improves the model** — SMB alone explains a meaningful share of PG's return variation beyond pure market risk

---

## Repository Contents

| File | Description |
|------|-------------|
| `PG_Project_Group_4.xlsx` | Full workbook — daily/monthly data, factor data, CAPM and FF3 regression outputs |

**Sheets included:**
- `PG DAILY DATA` — daily price and return data
- `PG MONTHLY DATA` — monthly returns used in regression
- `QUESTIONS 8-10` — Fama-French factor analysis and collinearity checks
- `CAPM Regression Output` — full OLS regression output (Excel Data Analysis ToolPak)
- `FF3 Regression Output` — full three-factor OLS regression output

---

## Tools Used

- **Excel** — Data Analysis ToolPak (OLS regression), CORREL, STDEV, AVERAGE functions
- **Statistical methods** — OLS regression, two-tailed and one-tailed hypothesis testing, collinearity diagnostics

---

## About

Completed as a team project for the Financial Analysis course at NYU Tandon School of Engineering.

**Shubh Patel**
MS Management of Technology — NYU Tandon
[GitHub](https://github.com/shubh-patel-nyu) | [LinkedIn](https://linkedin.com/in/shubhpatel18)