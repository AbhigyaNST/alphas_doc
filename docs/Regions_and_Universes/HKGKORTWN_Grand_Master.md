# HKG/KOR/TWN [Grand Master]

_Section: Regions and Universes | page id: getting-started-hkgkortwn_

 .summary-card { background: #f7f9fb; border: 1px solid #eaecf0; border-radius: 8px; padding: 16px; width: fit-content; max-width: 760px; } .summary-header { display: flex; align-items: center; gap: 8px; margin-bottom: 8px; } .summary-icon { font-size: 14px; color: #704e9c; } .summary-label { font-size: 13px; font-weight: 600; color: #222733; } .summary-body { font-size: 13px; line-height: 140%; color: #222733; margin: 0; }

 ✨ Summary

 This article explains why Alpha research in Hong Kong, Korea, and Taiwan requires special care because market mechanisms, transaction costs, and short-selling constraints can change how signals behave. It helps users set realistic turnover, margin, and Max Trade expectations while encouraging region-specific datasets beyond general ASI ideas.

- In Korea and Taiwan regions, “(-1) * Alpha” is not the opposite of the alpha due to the way we a trade is simulated and the more common presence of circuit breakers in these regions.
- Due to the generally high trading cost, it is better to have higher margin that is at least 10 bps for Taiwan region.
- In Korea and Hong Kong regions, it is better to control the turnover to be less than 30%. If your alphas do have higher turnover, then the alphas should have higher Sharpe and Returns to cover those higher trading costs.
- You can try alpha ideas that work well in ASI. In addition to your ideas that work in ASI, you can also try other specific ideas or specific datasets which are only available or have higher coverage in a certain country.
- When simulating or submitting Alphas in HKG, KOR or TWN regions, you have to turn on the 'Max Trade' option.
- To get started, besides price volume, we recommend to try out some of the below specific datasets:

- HKG: [model25](https://platform.worldquantbrain.com/data/data-sets/model25?delay=1&instrumentType=EQUITY&limit=20&offset=0&region=HKG&universe=TOP800), [other85](https://platform.worldquantbrain.com/data/data-sets/other85?delay=1&instrumentType=EQUITY&limit=20&offset=0&region=HKG&universe=TOP800)
- KOR: [analyst25](https://platform.worldquantbrain.com/data/data-sets/analyst25?delay=1&instrumentType=EQUITY&limit=20&offset=0&region=KOR&universe=TOP600)
