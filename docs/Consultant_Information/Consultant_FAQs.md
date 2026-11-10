# Consultant FAQs

_Section: Consultant Information | page id: consultant-faqs_

# Does my Alpha need to pass all the OSTESTS in order to get PROD status?

Answer: The Alphas you submit in BRAIN platform have to pass a set of tests in order to qualify for PROD status. These tests include mandatory and non-mandatory tests. An Alpha needs to pass all the mandatory tests to be eligible to get PROD status. If an Alpha is failing some non-mandatory tests, it can still make it to PROD.

Also note that, we mark an Alpha as OSTEST-FAIL if it fails ‘one or more tests’ (mandatory or non mandatory). For example, even if an Alpha fails a non mandatory test, it will be marked as OSTEST-FAIL, and if you check the Alpha details of this Alpha you might see the status of OTHER as FAIL. However this does not imply that such an Alpha cannot go to PROD.

To summarize, it’s possible that an Alpha that had a status of OSTEST-FAIL initially, can eventually move to OSTEST2-PENDING and finally to PROD.

Few mandatory tests include:

- For Delay 1 Alphas:SubUnivSharpe> sqrt(252) * max(0.065, sqrt(subuniverse_size / largest_universe_size) * 0.15)
- For Delay 0 Alphas: SubUnivSharpe> sqrt(252) * max(0.10, sqrt(subuniverse_size / largest_universe_size) * 0.25)

Following are the sharpe threshold to avoid sub universe warning:

```json
{
  "type": "TABLE",
  "value": {
    "data": [
      [
        "Universe",
        "Required Sharpe"
      ],
      [
        "TOP 2000",
        "1.944"
      ],
      [
        "TOP 1000",
        "1.37"
      ],
      [
        "TOP500",
        "1.03"
      ],
      [
        "TOP 200",
        "-"
      ]
    ],
    "firstRowIsTableHeader": true,
    "firstColIsHeader": false
  },
  "id": "652e68f5-1f3b-4557-8a42-3df9c30eef5b"
}
```

Note: This test is just an approximation of the real test that gets run in OS TEST. If you encounter a warning, then verify if the signal is over-concentrated in the less liquid part of the universe and only submit Alphas once verified.

Earlier, check Weight test was a part of the OSTESTS but now it has been included as a part of submission process.

# Could you please throw some light on the relevance of OS tab and production tab in BRAIN platform?

Answer: Alphas undergo various evaluation tests and based on their performance in these tests, they qualify for further testing and eventually move to production.
During the first round of out sample testing, the submitted Alphas are evaluated for various base tests (such as SubUniv, SuperUniv, CheckCorr, RankSharpe, CheckMemory etc.) in OS Tab.
Alphas that pass most of the base tests move to the Production tab. Here, the Alphas are evaluated based on the performance tests (which include OSSharpe, New High, etc.). An Alpha usually takes longer to pass the performance tests as compared to the base tests.
An overview of the Alpha life cycle:

![image]({"title": "consultant_FAQs_2", "width": 632, "height": 80, "fileSize": 49062, "url": "https://api.worldquantbrain.com/content/images/5_lD0CIpRj-RZWvLMedsmUoe3uw=/37/original/consultant_FAQs.PNG"})

# Why is it that the Alphas tend to perform poorly for 5 year back testing period as compared to 2 year back testing period? Is there a generic solution to this problem?

Answer: Overfitting is one of the reasons why an Alpha tends to perform well in 2 years simulation duration but may not work for 5 years simulation duration. We normally have more confidence on the Alpha which is simulated for 5 years as compared to the one simulated for 2 years.
Consider an Alpha based on quarterly fundamental data. On an average, you would have 4 data points a year for fundamental data. In a 2 year simulation you would end up fitting your Alpha, on the basis of just 8 data points – in which case there’s a good chance that you have overfitted your Alpha. With a 5 year simulation, you have 20 data points, and therefore more confidence in your Alpha. At the same time, it would be difficult to fit your Alpha for all the 5 years, effectively reducing your chances for overfitting.
Therefore, in order to reduce overfitting risk, we have now removed the 2 year simulation option in favour of the 5 year option. So, now the simulation duration is fixed at 5 years.

# Why is it that the Alphas tend to perform poorly for 5 year back testing period as compared to 2 year back testing period? Is there a generic solution to this problem?

Answer: Overfitting is one of the reasons why an Alpha tends to perform well in 2 years simulation duration but may not work for 5 years simulation duration. We normally have more confidence on the Alpha which is simulated for 5 years as compared to the one simulated for 2 years.
Consider an Alpha based on quarterly fundamental data. On an average, you would have 4 data points a year for fundamental data. In a 2 year simulation you would end up fitting your Alpha, on the basis of just 8 data points – in which case there’s a good chance that you have overfitted your Alpha. With a 5 year simulation, you have 20 data points, and therefore more confidence in your Alpha. At the same time, it would be difficult to fit your Alpha for all the 5 years, effectively reducing your chances for overfitting.
Therefore, in order to reduce overfitting risk, we have now removed the 2 year simulation option in favour of the 5 year option. So, now the simulation duration is fixed at 5 years.

# What are the factors that contribute to change in the values of actual weight of an Alpha?

Answer: Actual weight is the actual usage (weight) of Alpha in a production strategy. It gets calculated and updated on a daily basis.
If an Alpha is not performing well in past days, then there are chances that the actual weight may decrease. The current market scenario also might affect your actual weight. For example: if in the past few months markets have been volatile, then good chances that reversion Alphas would work better and therefore receive more weight.
Therefore, it would be a good practice to keep track of market trends and accordingly tune your research. Note that the weight balance criteria are decided by PM’s and some minor fluctuations are expected in the short term. If you have a diversified set of Alphas in your inventory, the chances that some of them always have weight is higher. So try to build diversity in your personal Alpha pool.

# Will my Alphas with OSTEST-FAIL status get retested in future?

Answer: An Alpha with OSTEST-FAIL status would imply that the Alpha is failing at least one of the out sample tests. The Alphas won’t be retested for the same tests. But if the Alpha is failing some non-mandatory out sample tests, then the testing process continues and the Alpha goes through further testing. However, if the Alpha fails some mandatory tests, it is not tested further. You can find more information about OSTEST-FAIL in Question 1.

# When exactly does my Alpha get simweight? I have few OSTEST-PENDING Alphas which have not been allocated sim weight while some PROD-DECM Alphas have sim weight.

Answer: Once the Alphas are OS tested, they get sim weight. This is based on performance of the Alpha in out sample testing. Your Alphas would start getting sim weights once they are evaluated in out sample testing.
You may find PROD-DECM Alphas getting sim weight but this does not contribute to sim weight on leader board rankings.

# Which one (weight) should I look at when I evaluate the performance of my Alpha? Which one determines the Tier?

Answer: The Alpha’s performance cannot be evaluated by judging a single parameter. The performance is evaluated on the basis of actual weight, sim weight, PNL, meta score, average fitness and few other proprietary metrics. In accordance with these parameters we derive a composite metrics and rank all the consultants. Depending on the distribution, we decide the criteria for each tier. This criterion is at the firm’s discretion and might be revised to ensure a normalized distribution across tiers as consultant numbers increase.

# Which one (weight) should I look at when I evaluate the performance of my Alpha? Which one determines the Tier?

Answer: The Alpha’s performance cannot be evaluated by judging a single parameter. The performance is evaluated on the basis of actual weight, sim weight, PNL, meta score, average fitness and few other proprietary metrics. In accordance with these parameters we derive a composite metrics and rank all the consultants. Depending on the distribution, we decide the criteria for each tier. This criterion is at the firm’s discretion and might be revised to ensure a normalized distribution across tiers as consultant numbers increase.

# I would like to know the reason why my Tier changed from Tier I to "Unassigned”?

Answer: Once you become a research consultant, you need to sign one year agreement with WorldQuant. Your tier is allotted to you and reshuffled on a regular basis, depending on your performance as a consultant. This introduces healthy competition and consultants to stay motivated to put in their best efforts. Further, it takes care that compensation is fair and performance based.
As you complete one year, we expect you to have contributed to the Alpha pool substantially and accumulated good actual weight. This allows you to reap significant rewards from bonuses. As a result, the system automatically marks a consultant unassigned as he/she completes a year with us. Your new tier will be allocated after the next tier-reshuffle. In case your status is Unassigned and you have not completed a year with us, please reach out to BRAIN platform Support.

# Why do I get “Cannot submit Alpha, D0 submission quota has been reached” error?

Answer: As a consultant, you will be able to submit up to 5 D0 Alphas in a given calendar month. So, please submit only your best D0 Alphas or just work on D1 Alphas.

# My Sim3 Weight increased/decreased few days after the tier-reshuffling date. Will I be assigned a revised tier?

Answer: The SimWeight values are taken on the same snapshot date for all the consultants. Since the simweight score is dynamic, it may increase or decrease based on the OS performance of the Alphas. There is no ideal date for pulling the simweight details. Some consultants may experience a decrease in their simweight while some may notice an increase. However, your tier will be decided based on the simweight and other performance metrics on the snapshot date.
