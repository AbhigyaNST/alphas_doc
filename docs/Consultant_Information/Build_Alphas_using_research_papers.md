# Build Alphas using research papers

_Section: Consultant Information | page id: respapers_

The first and foremost step of building an alpha is coming up with an alpha idea. While there are multiple sources for finding ideas, research papers stand out as one of the most useful. In the beginning, the learn section of the platform is a good resource for sourcing ideas. For instance, the “Example” tab and Alpha concepts page are very useful. Although, for building low correlation alphas, it is important to use some unique or lesser utilized ideas. Research papers can assist you in finding different ideas.

Here are some general guidelines to build alphas using research papers:

**Know your Operators**: The second step of the research process is to implement your alpha idea using operator. Hence, it is important to understand the concept of operators well. We recommend you go through the detailed operator descriptions before reading the research papers.

**Reading the paper**: Visit any online journal and go through a few abstracts of the research papers. Choose a paper with an interesting idea to work with amongst all of the options. You can read the introduction, abstract, and main body. The aim is to gain a decent understanding of the research paper so that you know the methodology and data used by the authors.

**Formulating your alpha**: The final step is to formulate your alpha. This is where your understanding of the operators comes in. Try to replicate the idea suggested in the paper and assess its performance, then think of any improvements that can be made on this version using any additional operators / data.

We will take you through an example [research paper](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=247435) to show you how you can come up with an idea and refine it to create an alpha. This research paper talks about meeting or beating earnings estimate. Stocks that are better or equal to their earnings estimate are likely to show an outperformance as compared to other firms.

**Iteration 1**

Since the research paper is talking about an event (earnings release), we can use trade_when operator. A simple implementation of this idea could be to enter your positions when earnings estimate are beaten and amongst those stocks take positions according to the rank of ratio of actual earnings and estimated earnings and maintainyour position for the remainder of the quarter.

We have used the days_from_last_change operator to check if the earnings announcement was recent or not. The alpha below is in the US region, decay 4 and on subindustry neutralization, you can feel free to play around with the settings.

**Alpha example**

```
event=days_from_last_change(eps)<=5 && ts_delay(est_eps,10) <eps ;
trade_when(event,rank(eps/est_eps),-1)
```

Settings: `{"instrumentType": "EQUITY", "region": "USA", "universe": "TOP3000", "delay": 1, "decay": 3, "neutralization": "INDUSTRY", "truncation": 5.0, "pasteurization": "ON", "unitHandling": "VERIFY", "nanHandling": "OFF", "language": "FASTEXPR", "maxTrade": "OFF"}`

Here are the results

![image]({"title": "is_summary.png", "width": 871, "height": 109, "fileSize": 16174, "url": "https://api.worldquantbrain.com/content/images/W3F03AjtpctsJ2VwKlUHwEv9smQ=/170/original/is_summary.png"})

![image]({"title": "Finding Consultant Alphas: Iteration 1 Graph", "width": 735, "height": 600, "fileSize": 47533, "url": "https://api.worldquantbrain.com/content/images/aEonuFZ7RGOSb7ZX1VdPlBnm87k=/138/original/Finding_Consultant_Alphas_Iteration_1_Graph.png"})

The alpha isn’t submittable but the results aren’t too bad either. This is a good sign for us and increases our confidence in the idea since our first implementation has shown decent results. Performance metrics give us a direction that we need to focus on increasing the turnover.

**Iteration 2**

In our first iteration, we only focused on stocks that were meeting or beating the earnings estimate and hence we took positions in a small subset of stocks. We can try another implementation of our idea where we take positions in all stocks but take positive weight in those stocks that beat expectations.

![image]({"title": "4.png", "width": 549, "height": 59, "fileSize": 5960, "url": "https://api.worldquantbrain.com/content/images/KX4na4dk2YzHGv2P5sRwzE98b2I=/139/original/4.png"})

The 0.5 + rank(sales/assets) ensures that we up weight stocks that meet or beat earnings estimate. The asset turnover ratio was used to get an idea of how efficiently the firm uses its resources, you can obviously try out different ratios or data fields as a proxy for financial health of the firm /as a default fundamental signal.

![image]({"title": "5.png", "width": 879, "height": 129, "fileSize": 16335, "url": "https://api.worldquantbrain.com/content/images/SJARGBfkiMIEV-3rAAcUGg9jyW8=/140/original/5.png"})

![image]({"title": "6.png", "width": 888, "height": 720, "fileSize": 40737, "url": "https://api.worldquantbrain.com/content/images/t7O6wXsjXZ9dPVCYedpjp6wSBvU=/141/original/6.png"})

Our turnover has increased since we have now moved from trade_when to if_else operator and take positions in all the stocks. We have taken a hit on our fitness due to this.

**Iteration 3**

Working on a new idea doesn’t mean you can’t use your previous knowledge or ideas to aid your research. In fact, a responsible use of your past knowledge with your new ideas can help you build a great number of alphas from a single research paper.

Our paper here talks about the outperformance of stocks that beat earnings estimate. So, deciding to go long on these stocks for the complete quarter sounds plausible. For the other stocks, it would make sense to use an idea which is irrespective of meeting or beating the earnings estimate. This will make sure we are not taking positions solely on the basis of information added at an interval of 3 months. From our past knowledge, we can bet on the mean reverting nature for these other stocks in our portfolio.

![image]({"title": "7.png", "width": 578, "height": 90, "fileSize": 6855, "url": "https://api.worldquantbrain.com/content/images/q1ksUMnw9AWVYr2Vs7K9yPDreng=/142/original/7.png"})

Alpha =1 makes sure we are long on the stocks that beat earnings estimate since 1 is the max possible value of our alt_alpha hence even after neutralization it is likely that these stocks will have positive weight.

![image]({"title": "8.png", "width": 887, "height": 129, "fileSize": 15781, "url": "https://api.worldquantbrain.com/content/images/yImTywQUTKZB-f9uKjJBLzlJLMM=/143/original/8.png"})

![image]({"title": "9.png", "width": 882, "height": 721, "fileSize": 33584, "url": "https://api.worldquantbrain.com/content/images/50qIxwnV6awayEZ5TCtQyJQSzMw=/144/original/9.png"})

We see a significant improvement in all of our performance metrics. You may notice we have used the same event across all three implementations and despite that, achieved very different results. This shows how we can use a single framework and a responsible combination of different ideas to build multiple alphas.

**Iteration 4**

Similar to the previous iteration here we have scaled the alpha by sales_ps in order to adjust for different eps scales of different firms

![image]({"title": "10.png", "width": 526, "height": 68, "fileSize": 7455, "url": "https://api.worldquantbrain.com/content/images/2ylOLtBHkKaROEG1zOjYz6GzZFM=/145/original/10.png"})

![image]({"title": "11.png", "width": 881, "height": 121, "fileSize": 15902, "url": "https://api.worldquantbrain.com/content/images/TI5j92ysrWCn8LuqBFBQTRU8jZw=/146/original/11.png"})

![image]({"title": "12.png", "width": 891, "height": 725, "fileSize": 32433, "url": "https://api.worldquantbrain.com/content/images/GKdsncoy3eB6Zzh9_SEQJ_FODUk=/147/original/12.png"})

You can use different implementations for the same idea on the brain platform or use any of the numerous data fields at your disposal to improve an idea or come up with an alpha that is not correlated to our existing production pool. So, reading new ideas/papers will not only help you build high-sharpe alphas but also in bringing down your correlation, which should be an equally important goal of your research. Further, the target is never to make an alpha “just good enough to be submittable” you may carry forward improvements even after passing all tests and submit the best version that you deem fit since the OS results hold the highest importance.

**Some Additional Tips**

Reading helps. Almost none of the ideas given in the research papers would work as they are presented (in some cases, opposite works). They are helpful in guiding you to think in a certain direction which you might otherwise miss completely.

Before reading, also make sure that the dataset given in the research paper exists in Brain. This will save you a lot of time in case you read a research paper only to realize the dataset isn’t available.
