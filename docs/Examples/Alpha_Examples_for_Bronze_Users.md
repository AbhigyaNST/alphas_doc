# ⭐ Alpha Examples for Bronze Users 🥉

_Section: Examples | page id: sample-alpha-concepts_

 .summary-card { background: #f7f9fb; border: 1px solid #eaecf0; border-radius: 8px; padding: 16px; width: fit-content; max-width: 760px; } .summary-header { display: flex; align-items: center; gap: 8px; margin-bottom: 8px; } .summary-icon { font-size: 14px; color: #704e9c; } .summary-label { font-size: 13px; font-weight: 600; color: #222733; } .summary-body { font-size: 13px; line-height: 140%; color: #222733; margin: 0; }

 ✨ Summary

 This article covers Bronze-level Alpha examples that help users move from basic valuation or volatility concepts to testable expressions. It explains the hypothesis behind each idea, how it can be implemented, and how users can improve the signal using fundamental, analyst estimate, and options data.

# Valuation based on cash flow

**Hypothesis**

A lower EV/CF usually suggests the company is becoming cheaper relative to its cash-generating ability; a higher multiple suggests it’s getting more expensive.

**Implementation**

Use ts_zscore to standardize the chang of the ratio and group_rank to control the turnover.

**Hint to Improve Alpha**

There are various types of cash flow, and switching the type used in the metric may improve its performance.

**Alpha example**

```
group_rank(-ts_zscore(enterprise_value/cashflow, 63),industry)
```

Settings: `{"instrumentType": "EQUITY", "region": "USA", "universe": "TOP3000", "delay": 1, "decay": 0, "neutralization": "INDUSTRY", "truncation": 0.08, "pasteurization": "ON", "unitHandling": "VERIFY", "nanHandling": "OFF", "language": "FASTEXPR", "maxTrade": "OFF"}`

# Overpriced stocks

**Hypothesis**

When analyst price target estimates (est_ptp) and free cashflow estimates (est_fcf) move highly in sync over the past month (high positive correlation), it may signal that the market has already fully priced in the cash flow expectations into price targets — leaving little room for further upside.

**Implementation**

Using est_ptp to capture price estimate and est_fcf to capture free cash flow and calculate the dynamics between them with ts_corr.

**Hint to Improve Alpha**

The window of 1 year might be too long to react on the price correction. Try shorter window.

**Alpha example**

```
-ts_corr(est_ptp,est_fcf,252)
```

Settings: `{"instrumentType": "EQUITY", "region": "USA", "universe": "TOP3000", "delay": 1, "decay": 0, "neutralization": "MARKET", "truncation": 0.08, "pasteurization": "ON", "unitHandling": "VERIFY", "nanHandling": "OFF", "language": "FASTEXPR", "maxTrade": "OFF"}`

# Volatility arbitrage

**Hypothesis**

Higher volatility is often observed during bearish markets, while lower volatility is typically seen during bullish markets. A lower Parkinson's volatility coupled with a higher implied volatility may suggest that there could be a stronger bullish sentiment for the stock in the future.

**Implementation**

Long the stock if its implied volatility significantly exceeds its historical volatility and short the opposite

**Hint to Improve Alpha**

Can you use ts_backfill to avoid missing data on certain days?

**Alpha example**

```
implied_volatility_call_120/parkinson_volatility_120
```

Settings: `{"instrumentType": "EQUITY", "region": "USA", "universe": "TOP200", "delay": 1, "decay": 0, "neutralization": "SECTOR", "truncation": 0.08, "pasteurization": "ON", "unitHandling": "VERIFY", "nanHandling": "OFF", "language": "FASTEXPR", "maxTrade": "OFF"}`
