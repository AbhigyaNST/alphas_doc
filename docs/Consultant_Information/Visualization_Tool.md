# Visualization Tool

_Section: Consultant Information | page id: visualization-tool_

 .summary-card { background: #f7f9fb; border: 1px solid #eaecf0; border-radius: 8px; padding: 16px; width: fit-content; max-width: 760px; } .summary-header { display: flex; align-items: center; gap: 8px; margin-bottom: 8px; } .summary-icon { font-size: 14px; color: #704e9c; } .summary-label { font-size: 13px; font-weight: 600; color: #222733; } .summary-body { font-size: 13px; line-height: 140%; color: #222733; margin: 0; }

 ✨ Summary

 This article explains the visualization tool and why seeing Alpha performance by sector, industry, and market-cap group can reveal hidden concentration risks. It helps consultants judge whether returns are broad and stable or overly dependent on a narrow group of stocks before resimulation or submission.

# Visualization Tool

The visualization feature allows users to plot graphs of Alpha values and statistics, in addition to the PnL graph. It enables users to analyze the visualized output and fine tune Alphas before re-simulating or submitting.

Running the visualization has an impact on simulation speed, so be judicious in utilizing this feature. By default this feature is turned off but can be turned on in simulation settings. Visualization data for older Alphas is only available for a week after simulation date.

```json
{
  "type": "TABLE",
  "value": {
    "data": [
      [
        "Term",
        "Usage"
      ],
      [
        "Coverage",
        "Number or percentage of instruments with non-NAN Alpha values"
      ],
      [
        "Size",
        "Amount of money allocated as percentage of booksize"
      ],
      [
        "PNL",
        "PNL attributed to the relevant set of instruments"
      ],
      [
        "Sharpe",
        "Sharpe value of associated PNL stream"
      ],
      [
        "Capitalization",
        "Quintile of market capitalization of underlying stock"
      ],
      [
        "Industry / Sector",
        "Market grouping (scroll down to the bottom of the page for the full list of sectors and industries)"
      ]
    ],
    "firstRowIsTableHeader": true,
    "firstColIsHeader": false
  },
  "id": "b74b4c0f-a7e6-41ab-88fc-8cb3d95c2968"
}
```

# Available Graphs by Category

**Coverage**

- Alpha Coverage
- Coverage by Industry
- Coverage by Sector

*‘Coverage’ denotes the average number of stocks whose value change each day.*

**Size**

- Average Size by Capitalization
- Average Size by Industry
- Average Size by Sector

**PNL**

- PNL by Capitalization
- PNL by Industry
- PNL by Sector

**Sharpe**

- Sharpe by Capitalization
- Sharpe by Industry
- Sharpe by Sector

**Others**

- Turnover with Time
- Industry Average value with Time
- Sector Average value with Time

# Tips to Analyze the Graphs

- Highly varying turnover or average Alpha value with time should be avoided.
- Very large booksize concentrated on low cap or one sector or industry is not good, as it potentially entails low liquidity or diversification.
- Filtering out a lot of stocks in your simulation leading to less diversification across caps, sector or industry is not a good practice. This could be checked using the coverage plots.
- Sharpe contribution from different industries and sectors towards the overall Sharpe indicates diversification.
- Good Sharpe in high cap stocks along with low caps makes a good Alpha.

# Full List of Sectors & Industries

**Sector**

- Distribution Services
- Communications
- Transportation
- Utilities
- Retail Trade
- Miscellaneous
- Consumer Durables
- Industrial Services
- Commercial Services
- Consumer Non-Durables
- Process Industries
- Consumer Services
- Technology Services
- Producer Manufacturing
- Health Technology
- Energy Minerals
- Electronic Technology
- Non-Energy Minerals
- Finance
- -99999 (Uncategorized)

**Industry**

- All Unclassified Establishments
- Public Administration
- Other Services (except Public Administration)
- Educational Services
- Arts Entertainment and Recreation
- Agriculture Forestry Fishing and Hunting
- Health Care and Social Assistance
- Accommodation and Food Services
- Administrative and Support and Waste Management and Remediation Services
- Transportation and Warehousing
- Construction
- Wholesale Trade
- Utilities
- Retail Trade
- Real Estate and Rental and Leasing
- Management of Companies and Enterprises
- Professional Scientific and Technical Services
- Information
- Finance and Insurance
- Mining Quarrying and Oil and Gas Extraction
- Manufacturing
- -99999 (Uncategorized)
