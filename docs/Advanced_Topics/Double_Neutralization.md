# Double Neutralization

_Section: Advanced Topics | page id: neut-users_

 .summary-card { background: #f7f9fb; border: 1px solid #eaecf0; border-radius: 8px; padding: 16px; width: fit-content; max-width: 760px; } .summary-header { display: flex; align-items: center; gap: 8px; margin-bottom: 8px; } .summary-icon { font-size: 14px; color: #704e9c; } .summary-label { font-size: 13px; font-weight: 600; color: #222733; } .summary-body { font-size: 13px; line-height: 140%; color: #222733; margin: 0; }

 ✨ Summary

 This article explains double neutralization and why multi-country regions often require controlling for two group dimensions at once, such as country and industry. It shows why sequential neutralization can undo earlier adjustments and how group_cartesian_product creates cleaner combined peer groups.

You can apply simultaneous neutralizations by two different groups, such as country and industry with the help of "group_cartesian_product", in regions with many countries like EUR, ASI, and GLB. Double neutralization neutralizes Alphas within a group of stocks that share the same 'country' and 'industry' identifiers. In the USA, we can use other pairs, such as combinations from industry/subindustry/sector and another group (for example, sector, sta1_top1000c50).

If you use two "group_neutralize" operators sequentially, such as **group_neutralize(group_neutralize(Alpha, industry), country)**, the second neutralization partially negates the first one. The double neutralization approach differs from using two group_neutralize operators.

## ASI Example: Double neutralization by industry and country

**Original Alpha:** ts_rank(eps, 252)

*Set Neutralization=Sector:* In settings, set Universe=MINVOL1M

**Double Neutralization Alpha:**

alpha = ts_rank(eps, 252) group = densify(group_cartesian_product(industry, country)) group_neutralize(alpha, group)

Line 2 uses group_cartesian_product to merge industry and country into a new group. This ensures unique values for each pair of industry and country

## USA Example: Double neutralization by sector and other grouping

**Original Alpha:** group_rank(ts_rank(eps, 252), sector)

*Set Neutralization=Sector:* In settings, set Universe=TOP1000

**Double Neutralization Alpha:**

group = group_cartesian_product(sector, sta1_top1000c50) alpha = group_rank(ts_rank(eps, 252), group) group_neutralize(alpha, group)

Line 1 uses group_cartesian_product to merge sta1_top1000c50 with the sector grouping. This ensures that all group operators in the Alpha consider both sector and statistical grouping.

## Tips for Success

- Using basic grouping fields in 'double neutralization' for the multi-country region can improve an Alpha’s simulated performance.
- Try using other grouping datasets for 'double neutralization' in the USA/EUR/ASI regions to improve an Alpha’s simulated performance
