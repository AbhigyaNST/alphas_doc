# China Alphas: Understand the market 🥈

_Section: Regions and Universes | page id: china-region_

## REGION SPECIFICS – Things to consider

With BRAIN you can create alphas on China’s Stock market - the second largest in the world by capitalization. There are two primary exchanges:

- Shanghai Stock Exchange (SSE): >2000 listed companies, market cap >7 trillion USD
- Shenzhen Stock Exchange (SZSE): >2000 listed companies, market cap >5 trillion USD

## Universes on the CHN region TOP2000U

### What are the notable characteristics of this universe?

This CHN universe covers 2,000 instruments, most of which are the same as the ones in the previous TOP2000 universe; the rest are replaced with instruments that are more market index oriented, so that CHN alphas can have a better risk profile in the real market environment.

### Tips for Success

- Re-simulate past CHN TOP3000 alphas with good sub-universe Sharpe on TOP2000U.
- Re-simulate past TOP2000 alphas on TOP2000U — the performances are expected to be similar.
- Model (model14, model25, model26, model31, model53, model122), Fundamental (fundamental5, fundamental17, fundamental27), and Analyst (analyst14, analyst17) datasets are good resources to research on.
- Read more academic and research papers to develop alphas with deeper CHN market insight.
- Risk-handled neutralization is a useful tool to evaluate the effectiveness and uniqueness of CHN alphas.
- Try to keep a high retaining rate in Robust universe Sharpe and Return.

## Different submission criteria

The China market has a high cost of trading, thus requiring higher returns than other regions.

- D1 criteria: Sharpe >= 2.07 ; Returns >= 8% ; Fitness >= 1.0
- D0 criteria: Sharpe >= 3.49 ; Returns >= 12% ; Fitness >= 1.5

[**Daily trading limit**](https://www.investopedia.com/terms/d/daily_trading_limit.asp#:~:text=A%20daily%20trading%20limit%20is,occurring%20over%20one%20trading%20day.)**:** price can change in 5-10% range based on stock type. The daily price limit does not apply on the first five trading days after an IPO.[1]

[**Short-selling Restriction:**](https://www.investopedia.com/ask/answers/09/short-selling-china.asp) both short selling and margin buying is allowed only for eligible "blue chip" stocks with good earnings performance and is only permitted for locally licensed investors.

This implies that the opposite alphas will not flip the performance. Check alpha example with same simulation setting below:

![image]({"title": "CHN_1", "width": 1077, "height": 506, "fileSize": 78053, "url": "https://api.worldquantbrain.com/content/images/IXeVl9KLtAFM9AT65sjUe4oLiOs=/267/original/chn1.png"})

## CHN region simulation settings

China [alphas](https://support.worldquantbrain.com/hc/en-us/articles/4902349883927-Click-here-for-a-list-of-terms-and-their-definitions#:~:text=A-,Alpha,-An) are created and simulated on the “Simulate” page. To run your first [simulation](https://support.worldquantbrain.com/hc/en-us/articles/4902349883927-Click-here-for-a-list-of-terms-and-their-definitions#:~:text=definition.-,Simulation,-Simulation) on China region:

- Click on the gear icon under your simulation tab to open the settings panel.
- Select “CHN” in Region drop down menu and click “Apply”

![image]({"title": "image (22)", "width": 798, "height": 679, "fileSize": 53956, "url": "https://api.worldquantbrain.com/content/images/5ncxEdMJcsGDW8d3HKyIyh9JQEI=/465/original/image_22.png"})

## The replicate of China Stock Index 1000 on BRAIN

The CSI 1000 Index is composed of 1,000 small-scale and well-liquid stocks after excluding the constituent stocks of the CSI 800 Index from all A-shares. It comprehensively reflects the stock price performance of small and medium-sized companies in China's A-share market. You can replicate this index on BRAIN platform:

![image]({"title": "chn3.png", "width": 731, "height": 736, "fileSize": 57846, "url": "https://api.worldquantbrain.com/content/images/c9dffleUllw_8WD5KN787R1UCvE=/269/original/chn3.png"})

### Formula

**Alpha example**

```
rank(cap) < 0.6 ? rank(cap) > 0.1 ? cap : 0 : 0
```

Settings: `{"instrumentType": "EQUITY", "region": "CHN", "universe": "TOP2000", "delay": 0, "decay": 0, "neutralization": "NONE", "truncation": 0.0, "pasteurization": "ON", "unitHandling": "VERIFY", "nanHandling": "OFF", "language": "FASTEXPR", "maxTrade": "OFF"}`

Since CSI1000 takes 1000 stocks based on the market cap ranking from 800 to 1800, so we have this range from 0.1 to 0.6.

Don’t miss your chance to make unique alphas for the China region and boost performance of your BRAIN alpha portfolio!

[1]: [The impact of price limit system on the comprehensive quality of the stock market: Research on long-term and short-term effects based on submarkets](https://www.tandfonline.com/doi/full/10.1080/23322039.2022.2106635)
