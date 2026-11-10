# Power Pool Alphas

_Section: Consultant Information | page id: getting-started-power-pool-alphas_

 .summary-card { background: #f7f9fb; border: 1px solid #eaecf0; border-radius: 8px; padding: 16px; width: fit-content; max-width: 760px; } .summary-header { display: flex; align-items: center; gap: 8px; margin-bottom: 8px; } .summary-icon { font-size: 14px; color: #704e9c; } .summary-label { font-size: 13px; font-weight: 600; color: #222733; } .summary-body { font-size: 13px; line-height: 140%; color: #222733; margin: 0; }

 ✨ Summary

 This article explains Power Pool Alphas and why this Alpha type rewards simple, clean, and high-quality ideas rather than unnecessary complexity. It helps consultants understand eligibility rules, submission limits, required explanations, tagging, and how to build a diverse set of low-correlation Power Pool signals.

Power Pool Alphas are simpler, smaller, higher quality Alphas that can help you do well across Genius, competitions and themes.

# Eligibility Criteria for Power Pool Alphas

Following are the list of criteria for an Alpha to be considered eligible for Power Pool Alphas:

- Sharpe >= 1.0
- Number of total operators, including repeat operators <= 8 (ts_backfill and group_backfill are not counted)
- Number of unique data fields (excluding grouping fields) <= 3, grouping fields: country, industry, subindustry, currency, market, sector, exchange
- Power Pool Correlation < 0.5.
- Turnover tests PASS
- Sub-universe test PASS
- Robust-universe test (where applicable) PASS
- Eligible region, delay, universe and other conditions (risk neutralization, datasets, turnover ranges, etc) are defined by the active Power Pool theme (e.g. GLB/D1, All regions/D0, EUR/D1 Fast Factors)

Note: If the Power Pool correlation is > 0.5, the Alpha must have a Sharpe at least 10% higher than the most correlated Alpha to be considered eligible for submission.

If in addition Alpha passes all other performance related tests it is [Power Pool + Regular] - meaning both - Power Pool and Regular alpha.

If Power Pool alpha uses data from only one dataset and passes all tests except IS Ladder - [Power Pool + ATOM] - meaning that this alpha is simultaneously Power Pool and ATOM alpha.

If [Power Pool + ATOM] alpha passes all performance related tests then it is [Power Pool + ATOM + Regular].

# Power Pool Thematic Competition

- To submit Power Pool Alpha that does not PASS regular Alpha tests (pure Power Pool Alpha) – this Alpha must match Power Pool Theme
- At least 5 tagged Power Pool Alphas are required per Power Pool Thematic leaderboard to be eligible for Power Pool Thematic Competition award.
- For more details – refer to here - [Which Alphas are eligible for Power Pool Alphas Thematic Competition? – WorldQuant BRAIN](https://support.worldquantbrain.com/hc/en-us/articles/37443810800535-Which-Alphas-are-eligible-for-Power-Pool-Alphas-Thematic-Competition)

# Submission Quotas After First Power Pool Alpha

Effective from the Power Pool quota update (22 September 2026). The submission limits for pure Power Pool Alphas are based on the time elapsed since your first Power Pool Alpha submission:

```json
{
  "type": "TABLE",
  "value": {
    "data": [
      [
        "Time since first Power Pool Alpha submission",
        "Daily limit (pure Power Pool Alphas)",
        "Monthly limit"
      ],
      [
        "Weeks 1-2",
        "4 per day",
        "No monthly quota"
      ],
      [
        "Weeks 3-4",
        "2 per day",
        "No monthly quota"
      ],
      [
        "Weeks 5-6",
        "1 per day",
        "No monthly quota"
      ],
      [
        "After 6 weeks",
        "1 per day (must match an active Power Pool Theme)",
        "10 pure Power Pool Alphas per calendar month, per scope"
      ]
    ],
    "firstRowIsTableHeader": true,
    "firstColIsHeader": false
  },
  "id": "41939c0b-6648-4a11-872e-a20d197ba341"
}
```

- Pure Power Pool Alphas are those that do not meet submission criteria of either Atom or Regular Alphas.
- The monthly scope is a single scope: USA D0 and D1, EUR D0 and D1, ASI D1, GLB D1 and OTHER (JPN, CHN, HKG, TWN, KOR, AMR, IND) D0 and D1.
- After 6 weeks since your first Power Pool Alpha submission, pure Power Pool Alpha submissions must match an active Power Pool Theme. Submissions that do not match any Power Pool Theme will be rejected with the message: "Pure Power Pool submission does not match any Power Pool Theme".
- Alpha classified as [Power Pool + ATOM] or [Power Pool + Regular] or [Power Pool + ATOM + Regular] is excluded from these limits.
- Example of daily submissions:
- **1** Pure Power Pool Alpha (matching an active theme)
- 1 [Power Pool + ATOM] Alpha
- Total: 2 Power Pool-related submissions

Note for consultants who submitted their first Power Pool Alpha before this update went live:

- If your first Power Pool Alpha was submitted more than 90 days before the update, the graduated schedule does not apply to you. The standard quotas apply: 1 pure Power Pool Alpha per day, 10 pure Power Pool Alphas per calendar month per scope, and pure Power Pool submissions must match an active Power Pool Theme.
- If your first Power Pool Alpha was submitted within 90 days before the update, your first-submission date is adjusted so that you still receive part of the graduated schedule — at least 2 weeks at 2 pure Power Pool Alphas/day and 2 weeks at 1 pure Power Pool Alpha/day — before the thematic and monthly quotas apply.

# Description of the Power Pool Alpha

To submit a Power Pool Alpha, it is mandatory to describe the idea in at least 100 characters. In the PROPERTIES section at the bottom of the Simulation results. Using the template of Idea and Rationale. Otherwise the Alpha will not be eligible for Power Pool.

Here is an example description:

- **Idea**: In normal market conditions, if a stock is shorted more, its likelihood of bouncing back may also increase (reversion). However, in extreme cases where the consensus in the market is high reflecting in extremely high/low level of short interest, it may potentially be better to follow that trend
- **Rationale for data used:** shrt3_bar field is a vector data field representing the demand to borrow stock, with higher values indicating higher demand
- **Rationale for operators used:**

- vec_avg(): Calculates the average value of shrt3_bar for a given day
- Conditional operator: Separates normal cases from extreme ones
- ts_backfill: Handles NaN values in the data field, detected by checking the coverage with a visualization tool

# How do I add or remove Alphas from the Power Pool?

You can view the list of your Power Pool Alphas on the Alphas Page under the [Submitted](https://platform.qa.worldquantbrain.com/alphas/submitted) tab. To remove a submitted Alpha from the Power Pool, go to the Submitted tab, open the Alpha description, and click the cross next to the "PowerPoolSelected" tag in the Properties section.

**Please note that even after removing the tag, this Alpha will still be part of the self-correlation pool, so new Power Pool Alphas will still be checked for correlation against it.**

To retag a submitted Alpha later to the Power Pool, in the Properties section of the Alpha, click on the Tags dropdown and retag the alpha as "PowerPoolSelected"

# Tips to create Power Pool Alphas

- Review Merged Performance before tagging the Alpha
- Explore Low turnover Alphas and liquid (small) universes, which can help improve [After Cost performance](https://support.worldquantbrain.com/hc/en-us/community/posts/29647491881623-How-to-Improve-After-Cost-Performance)
- Explore your existing Alpha pool for eligible signals
- Make use of the newly released [Investability Constrained PNL](https://support.worldquantbrain.com/hc/en-us/articles/30816357468183-How-can-I-make-use-of-Investability-Constrained-PnL-for-excelling-in-Power-Pool-Alphas-Competition)
- Your pool should have diverse signals to ensure robust performance of your pool in OS. Diversify your pool across datasets, ideas, operators, universes and even turnover (to some extent)
- After creating a sizable pool of Power Pool Alphas, consider removing Alphas which have high correlation with other Alphas in your Power Pool. This may potentially improve combo performance while reducing the Alpha count penalty
- Reach out to your research advisor for specific tips on creating good Power Pool Alphas
