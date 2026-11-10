# EUR TOP2500 Universe

_Section: Regions and Universes | page id: getting-started-eur-top2500-universe_

 .summary-card { background: #f7f9fb; border: 1px solid #eaecf0; border-radius: 8px; padding: 16px; width: fit-content; max-width: 760px; } .summary-header { display: flex; align-items: center; gap: 8px; margin-bottom: 8px; } .summary-icon { font-size: 14px; color: #704e9c; } .summary-label { font-size: 13px; font-weight: 600; color: #222733; } .summary-body { font-size: 13px; line-height: 140%; color: #222733; margin: 0; }

 ✨ Summary

 This article introduces the EUR TOP2500 universe and explains why expanding beyond TOP1200 can improve coverage, peer comparisons, and neutralization stability. It helps users retest existing European Alphas, check performance in more liquid subsets, and apply stronger neutralization methods for broader European research.

# Characteristics of the EUR TOP2500 Universe

The EUR TOP2500 universe expands from the TOP1200, covering around 2500 instruments. This offers a broader area for analysis.

# Tips for Success

- Resimulate your TOP1200 Alphas on the new TOP2500 universe.
- Adapt GLB region Alphas to the EUR TOP2500 universe.
- Start with datasets in price volume, analyst, fundamental, option, and short interest categories.
- In addition to sub-universe test, check Alpha's performance on the TOP800 universe to evaluate performance on liquid instruments.
- **Apply Double Neutralization**:

- With the expanded EUR TOP2500 universe, more instruments are available within each group. This increased number of instruments per group enhances the reliability and robustness of your Alphas.
- **Country Neutralization**: Remove country-specific risk by neutralizing by country mean values.
- **Sector/Industry Neutralization**: Further refine by neutralizing by sector or industry.
- **Example**: new_group = group_cartesian_product(country, industry), or new_group = densify(country) + densify(industry)*100

- Neutralize EUR Alphas against a group of risk factors using group neutralize operators or use SLOW, FAST, SLOW_AND_FAST, CROWDING, STATISTICAL neutralization in settings.

Take advantage of the expanded EUR TOP2500 universe for more reliable and robust Alphas.

Happy simulating!
