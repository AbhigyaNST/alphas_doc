# India Alphas

_Section: Regions and Universes | page id: getting-started-india-alphas_

 .summary-card { background: #f7f9fb; border: 1px solid #eaecf0; border-radius: 8px; padding: 16px; width: fit-content; max-width: 760px; } .summary-header { display: flex; align-items: center; gap: 8px; margin-bottom: 8px; } .summary-icon { font-size: 14px; color: #704e9c; } .summary-label { font-size: 13px; font-weight: 600; color: #222733; } .summary-body { font-size: 13px; line-height: 140%; color: #222733; margin: 0; }

 ✨ Summary

 This article explains what makes Alpha research in India different, including its separate universe, turnover limits, robust universe tests, and optional Max Trade controls. It helps users adapt ideas from ASI while focusing on liquidity, margin, investability, and diverse data categories suited to the IND market.

## Introduction

India universe on BRAIN consists of the top 500 stocks by liquidity.

Normal Alpha tests are applied, including Sharpe, fitness, sub-universe Sharpe, IS ladder etc.

Max Trade is not mandatory in IND, and maximum turnover cap is 40%.

IND need to pass an additional **robust universe Sharpe test**: IND Alpha should have minimum Sharpe of 1, in liquid stocks selected by BRAIN.

## Tips for Success

**IND stocks are not included in ASI universes**, also **many data appear in both ASI and IND**, so we encourage **retrying your ASI Alphas in IND**. Alphas that do well in both universes, may be strong candidates.

Try **diverse data categories**, while it can lead to better combined performance.

Though maxtrade is optional, we still encourage **keeping the investability constrained PnL to have a reasonable performance**.

Though max turnover is 40%, however we still encourage to **lower the turnover** if possible. Having **high margin**, with turnover lower than 20% is a good practice.
