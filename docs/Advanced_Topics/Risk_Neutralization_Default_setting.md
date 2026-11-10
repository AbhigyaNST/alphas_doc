# Risk Neutralization: Default setting

_Section: Advanced Topics | page id: getting-started-risk-neutralized-metrics_

 .summary-card { background: #f7f9fb; border: 1px solid #eaecf0; border-radius: 8px; padding: 16px; width: fit-content; max-width: 760px; } .summary-header { display: flex; align-items: center; gap: 8px; margin-bottom: 8px; } .summary-icon { font-size: 14px; color: #704e9c; } .summary-label { font-size: 13px; font-weight: 600; color: #222733; } .summary-body { font-size: 13px; line-height: 140%; color: #222733; margin: 0; }

 ✨ Summary

 This article explains risk-neutralized metrics and why they are useful for judging how much of an Alpha’s performance comes from genuine signal rather than known factor exposure. It shows how comparing original and risk-neutralized results can help users rank, improve, and select Alphas for submission.

## Introduction

From now on when you simulate non–Risk Neutralized Alphas, you will see another set of PnLs and performance metrics. These new calculated statistics comes from the hypothesis case what if your Alpha is Risk Neutralized (using various Risk setting in Neutralization for Alphas for example “Slow Factors”, “Fast Factors”, “Slow + Fast Factors”).

These metrics won’t be calculated for Alpha already simulate with Risk Neutralization in setting.

If you don’t understand Risk-Neutralized Alpha concept, please check out this [documentation](https://platform.worldquantbrain.com/learn/documentation/advanced-topics/getting-started-risk-neutralized-alphas).

## Where to find the metrics

The new UI on simulation results page looks like this:

![image]({"title": "risk_neu_metric.png", "width": 624, "height": 329, "fileSize": 36429, "url": "https://api.worldquantbrain.com/content/images/D_kBxd1IRG8yhWWpaUIqnJpt7oQ=/324/original/risk_neu_metric.png"})

The IS Summary also has new aggregate data:

![image]({"title": "risk_neu_metric2.png", "width": 624, "height": 421, "fileSize": 89825, "url": "https://api.worldquantbrain.com/content/images/HViQLkaXGpDjpE16dlcR3_AbykE=/325/original/risk_neu_metric2.png"})

## How to use the metrics in your Alpha research

From these stats, you can examine how good does your Alphas capture market anomalies that's not in the risk factor databases.

Because the calculation isn’t exactly the same with Risk Neutralization in setting, the platform uses new technique to speed up the computation. So you will see a bit different performance between Risk Neutralized metrics and actual Risk Neutralization settings (in particular turnover won’t change in the Risk Neutralized metrics but normal Risk Neutralization settings can affect it).

In your Alphas optimization process or Alpha submission selections, you should rank Alphas by the ratio between Risk Neutralized Metrics' sharpe and original Alpha sharpe or between Risk Neutralized Metrics' returns and original Alpha returns and choose the one with higher ratio. An Alpha that retains more of its performance after Risk Neutralization means it's less susceptible to risk factors’ drawdown & volatility and maybe less correlated too.
