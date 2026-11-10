# Global Alphas [Gold]

_Section: Regions and Universes | page id: global-region_

 .summary-card { background: #f7f9fb; border: 1px solid #eaecf0; border-radius: 8px; padding: 16px; width: fit-content; max-width: 760px; } .summary-header { display: flex; align-items: center; gap: 8px; margin-bottom: 8px; } .summary-icon { font-size: 14px; color: #704e9c; } .summary-label { font-size: 13px; font-weight: 600; color: #222733; } .summary-body { font-size: 13px; line-height: 140%; color: #222733; margin: 0; }

 ✨ Summary

 This article explains the Global region and why testing an Alpha across thousands of stocks in many countries can provide stronger evidence that an idea is broadly robust. It helps users manage country risk, apply double neutralization, evaluate sub-region consistency, and improve regional PnL balance.

Global simulations aggregate all the stocks in various regions into a single simulation.

Due to the time differences across the globe, these simulations are currently available in delay-1 mode only.

**Alphas**

- Since ASI is a region, which has multiple countries too, you can try alpha ideas that work well in ASI. In addition to your ideas that work in ASI, you can also try other specific ideas or specific datasets which are only available or have higher coverage in a certain country.
- Rather than thinking about alphas that work in specific countries or exchanges, it might be more advantageous to think of ideas that work generally for equities.
- The advantage of a large universe is that you will have greater confidence in the robustness of the alpha if you can pass the submission criteria, as you can see that historically, your idea worked across the globe in all liquid equities!

**Global Universe**

- The Global Region universe is about 9000 stocks in total, spanning several countries.

**Neutralization**

Right now, neutralization by market will neutralize all stocks by the global mean values, likewise for sector, subindustry and industry neutralization settings.

- It might be more meaningful to instead neutralize by country first before neutralizing by any other grouping (concept of double neutralization will be useful here). This is a new neutralization setting that we have added for Global region. This will neutralize all stocks by their country mean values, hence removing country specific risk from your alpha.
- You can also neutralize your GLB alphas against a group of risk factors. Read this page on [risk neutralization](https://platform.worldquantbrain.com/learn/documentation/advanced-topics/getting-started-risk-neutralized-alphas) for more details. If you select one of SLOW/FAST/SLOW_AND_FAST as the neutralization setting, the group neutralization setting defaults to market. Hence, it is a good practice to check your risk-neutralized GLB alpha's performance with the group_neutralize operator and country grouping

**Sub-Geography Sharpe Cutoff for GLB Alphas**

```json
{
  "type": "TABLE",
  "value": {
    "data": [
      [
        "Submission Criteria",
        "Threshold"
      ],
      [
        "AMER Sharpe ",
        "≥ 1"
      ],
      [
        "APAC Sharpe",
        "≥ 1"
      ],
      [
        "EMEA Sharpe ",
        "≥ 1"
      ]
    ],
    "firstRowIsTableHeader": false,
    "firstColIsHeader": true
  },
  "id": "fc15f51b-71a7-4568-bca9-d8eda5b918dd"
}
```

GLB Alphas are subject to additional sub-geography Sharpe cutoff criteria. These criteria ensure that your Alpha isn’t just performing well globally but is also delivering consistent returns across all three geographies. The goal is to avoid over-reliance on a single geography and encourage a more balanced contribution to your overall PnL.

**Tips to Improve Sharpe Across Geographies**

- **AMER**: Focus on high-liquidity equities and consider incorporating earnings-related signals, as the stocks in these markets are highly responsive to earnings announcements.
- **APAC**: Pay attention to market microstructure data, as price-volume patterns in APAC markets often differ due to shorter market hours and unique market regulations.
- **EMEA**: Explore macroeconomic indicators, as EMEA stocks are often influenced by geopolitical events and currency fluctuations.
- GLB Alphas also include a breakdown of global PnL by geography in their PnL chart, making it easy to see how much each geography is contributing. This helps you identify imbalances and determine areas for improvement.

![image]({"title": "Picture1.png", "width": 624, "height": 442, "fileSize": 84498, "url": "https://api.worldquantbrain.com/content/images/XRKUfH1WF2_5hHtfWieOJ37eCIY=/422/original/Picture1.png"})

**Increasing robustness**

Try exploring [Derived](https://platform.worldquantbrain.com/data/data-sets/pv29?delay=1&instrumentType=EQUITY&limit=20&offset=0&region=GLB&universe=TOP3000) and [Alternate](https://platform.worldquantbrain.com/data/data-sets/pv30?delay=1&instrumentType=EQUITY&limit=20&offset=0&region=GLB&universe=TOP3000) Industry Classification datasets. Using group operators using these grouping fields can help make your alpha signals robust
