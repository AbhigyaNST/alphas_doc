# Sentiment1 dataset

_Section: Understanding Data | page id: getting-started-sentiment1-dataset_

 .summary-card { background: #f7f9fb; border: 1px solid #eaecf0; border-radius: 8px; padding: 16px; width: fit-content; max-width: 760px; } .summary-header { display: flex; align-items: center; gap: 8px; margin-bottom: 8px; } .summary-icon { font-size: 14px; color: #704e9c; } .summary-label { font-size: 13px; font-weight: 600; color: #222733; } .summary-body { font-size: 13px; line-height: 140%; color: #222733; margin: 0; }

 ✨ Summary

 This article explains the sentiment1 dataset and why combining fast-moving market sentiment with slower analyst and earnings signals can support different types of Alpha ideas. It shows how users can work with signal speed, decay, lookback windows, and coverage to avoid relying on stale information.

**Getting Started with sentiment1 dataset (Research Sentiment Data)**

- The sentiment1 dataset combines sentiment metrics with earnings estimations and surprises for U.S.-listed companies.
- It provides insights into market mood, analyst consensus, and earnings-based signals.
- Key fields include sentiment scores, ratios of analyst buy/sell recommendations, earnings surprises, and dispersion among analyst estimates.
- Sentiment scores are dynamic with higher turnover in nature, while analyst and earnings metrics are slower-moving signals.
- Use smoothing **decay** operations to manage high-frequency sentiment data and be considerate when using long lookback periods (>63 days) as older events may lose relevance.
- The dataset has coverage of approximately 2000 on TOP3000. Do try your ideas on more liquid universes such as TOP1000 and TOPSP500 but ensure sufficient long & short count to avoid overfitting.

**Example Alpha Ideas**

- Positive sentiment indicates market confidence, while negative sentiment signals potential downside. Go long on stocks with bullish sentiment (**snt1_cored1_score** > 5) and short on stocks with bearish sentiment (**snt1_cored1_score** < -5).
- Positive earnings surprises often lead to upward price movements. Go long on stocks with positive earnings surprises using **snt1_d1_earningssurprise**.
- A strong analyst consensus combined with sufficient analyst coverage reflects market confidence. Go long on stocks with a high ratio of analyst buys over sells using **snt1_d1_buyrecpercent**, filtering out stocks with low analyst coverage with **snt1_d1_analystcoverage**
