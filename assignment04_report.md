# Assignment 04 Interpretation Memo

**Student Name:** Ashlynn Comstock
**Date:** 2/15/2026
**Assignment:** REIT Annual Returns and Predictors (Simple Linear Regression)

---

## 1. Regression Overview

You estimated **three** simple OLS regressions of REIT *annual* returns on different predictors:

| Model | Y Variable   | X Variable  | Interpretation Focus                    |
| ----- | ------------ | ----------- | --------------------------------------- |
| 1     | ret (annual) | div12m_me   | Dividend yield                          |
| 2     | ret (annual) | prime_rate  | Interest rate sensitivity               |
| 3     | ret (annual) | ffo_at_reit | FFO to assets (fundamental performance) |

For each model, summarize the key results in the sections below.

---

## 2. Coefficient Comparison (All Three Regressions)

**Model 1: ret ~ div12m_me**

- Intercept (β₀): 0.108196 (SE: 0.005987, p-value: 0.0000)
- Slope (β₁): -0.068682 (SE: 0.032495, p-value: 0.0346)
- R²: 0.0018 | N: 2527

**Model 2: ret ~ prime_rate**

- Intercept (β₀): 0.199799 (SE: 0.015764, p-value: 0.0000)
- Slope (β₁): -0.019449 (SE: 0.002998, p-value: 0.0000)
- R²: 0.0164 | N: 2527

**Model 3: ret ~ ffo_at_reit**

- Intercept (β₀): 0.097273 (SE: 0.009194, p-value: 0.0000)
- Slope (β₁): 0.577042 (SE: 0.567462, p-value: 0.3093)
- R²: 0.0004 | N: 2518

*Note: Model 3 may have fewer observations if ffo_at_reit has missing values; statsmodels drops those rows.*

---

## 3. Slope Interpretation (Economic Units)

**Dividend Yield (div12m_me):**

- A 1 percentage point increase in dividend yield (12-month dividends / market equity) is associated with a -0.0687 change in annual return.
- Higher dividend yield is associated with lower annual returns, which may reflect that high yield signals lower growth prospects or elevated risk.

**Prime Loan Rate (prime_rate):**

- A 1 percentage point increase in the year-end prime rate is associated with a -0.0194 change in annual return.
- The evidence suggests REIT returns are negatively sensitive to interest rates, consistent with higher borrowing costs reducing valuations.

**FFO to Assets (ffo_at_reit):**

- A 1 unit increase in FFO/Assets (fundamental performance) is associated with a 0.5770 change in annual return.
- The positive sign suggests more profitable REITs may earn higher returns, but the estimate is imprecise and not statistically significant.

---

## 4. Statistical Significance

For each slope, at the 5% significance level:

- **div12m_me:** [Significant / Not significant] — [one sentence conclusion]
- **prime_rate:** [Significant / Not significant] — [one sentence conclusion]
- **ffo_at_reit:** [Significant / Not significant] — [one sentence conclusion]
- **div12m_me:** Significant — dividend yield has a small negative but statistically significant relationship with annual returns.
- **prime_rate:** Significant — higher prime rates are associated with lower annual returns, with strong statistical evidence.
- **ffo_at_reit:** Not significant — the positive estimate is not distinguishable from zero at 5%.

**Which predictor has the strongest statistical evidence of a relationship with annual returns?** Prime rate (largest t-statistic and lowest p-value).

---

## 5. Model Fit (R-squared)

Compare R² across the three models:

- [Your interpretation: Which predictor explains the most variation in annual returns? Is R² high or low in general? What does this suggest about other factors driving REIT returns?]
- Prime rate explains the most variation (highest R²), but all R² values are very low, suggesting most variation in annual returns is driven by other factors not captured by these single-predictor models.

---

## 6. Omitted Variables

By using only one predictor at a time, we might be omitting:

- [Variable 1]: [Why it might matter]
- [Variable 2]: [Why it might matter]
- [Variable 3]: [Why it might matter]
- Market beta: captures systematic risk that affects returns and may correlate with yield or profitability.
- Size (lnmcap or market_equity): larger REITs may have different return dynamics and may correlate with dividend policy.
- Value (btm or be_me): valuation ratios may correlate with yields and expected returns.

**Potential bias:** If yield or prime rate correlates with these omitted risk/valuation characteristics, slope estimates could be biased; for example, high dividend yield may proxy for value or distress risk, exaggerating a negative slope.

---

## 7. Summary and Next Steps

**Key Takeaway:**
Prime rate has the strongest and most statistically robust relationship with REIT annual returns, and the negative sign aligns with higher financing costs reducing REIT performance. Dividend yield also shows a small negative relationship, while FFO/Assets is not statistically significant. Overall, these single-factor models explain very little of the variation in returns.

**What we would do next:**

- Extend to multiple regression (include two or more predictors)
- Test for heteroskedasticity and other OLS assumption violations
- Examine whether relationships vary by time period or REIT sector

---

## Reproducibility Checklist

- [X] Script runs end-to-end without errors
- [X] Regression output saved to `Results/regression_div12m_me.txt`, `regression_prime_rate.txt`, `regression_ffo_at_reit.txt`
- [X] Scatter plots saved to `Results/scatter_div12m_me.png`, `scatter_prime_rate.png`, `scatter_ffo_at_reit.png`
- [X] Report accurately reflects regression results
- [X] All interpretations are in economic units (not just statistical jargon)
- [X] Script runs end-to-end without errors
- [X] Regression output saved to `Results/regression_div12m_me.txt`, `regression_prime_rate.txt`, `regression_ffo_at_reit.txt`
- [X] Scatter plots saved to `Results/scatter_div12m_me.png`, `scatter_prime_rate.png`, `scatter_ffo_at_reit.png`
- [X] Report accurately reflects regression results
- [X] All interpretations are in economic units (not just statistical jargon)
