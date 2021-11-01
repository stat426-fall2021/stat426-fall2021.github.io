---
title: Mastering Data Science Through Sports Betting
layout: post
author: nland13
post-image: /assets/images/blogimages/figs-10-30/chance.png
description: Learn why sports betting is an amazing way to perfect your data science skills and get ideas on how to get started. 
tags:
- Sports Betting
- Sports Analytics
- Monte Carlo
- Skill Development
---

Okay, so you might be thinking that sports betting seems like a pretty frivolous application of data science. Perhaps it conjures up images of an addicted degenerate like the one Adam Sandler plays in *Uncut Gems*, and adding statistics to it just makes it nerdier. While I can't argue with the nerdy aspect, I do believe that sports betting, when used properly, can actually be a uniquely suited place for a burgeoning data scientist to learn and hone their skills. In this article I describe why I think that is, explain how you can get started, give an example of an actual successful bet powered by statistics, and list some of the best resources to learn more. 

![sandler](/assets/images/blogimages/figs-10-30/sandler.png)

---

## First off, what is sports betting?

To begin, let's make sure we are all talking about the same thing. Sports betting is when you place a bet on the outcome of a sporting event. Oftentimes this can take the form of simply betting which team wins, but it can also be about the total amount of points scored in a game or even about the color of the Gatorade poured on the winning coach. Terms like the spread, the moneyline, and over/under all have to do with sports betting.

Sports analytics on the other hand is a related but distinct field. In sports analytics, instead of betting on outcomes of a sporting event, you use data and statistical methods to make better strategic decisions to improve your odds of winning. Think Jonah Hill in Moneyball using statistics to guide their team. This is a very interesting field that has gained popularity in recent years, but it is not the subject of this article.

Maybe the best way to make clear the distinction is that in general, if you are participating in the sporting event in some way (athlete, coach, etc.), you are likely to be using sports analytics, and if you are simply an observer making predictions, you are likely to be engaged in sports betting. The one exception to this would be NBA refs, who are obviously more interested in sports betting. The analogy to the business world would be the distinction between running a business (sports analytics) and investing in businesses (sports betting).

![jonah](/assets/images/blogimages/figs-10-30/jonah.png)

## Why is sports betting a uniquely suited place to practice data science?

Now that we have clearly defined what sports betting is and isn't, we can talk about why I think it makes such a great playground for aspiring data scientists:

* **For sports fans, it can be incredibly fun.** While for some having a deep understanding of the variables that affected a person's chance of survival on the Titanic is fascinating, for many others it isn't. Sports betting is a great way for people to use their passion and excitement for sports to fuel their statistical learning. Actually applying the skills learned in the classroom is absolutely essential to truly learn concepts, but if you don't have exciting projects to work on, the chances that you will complete that crucial learning step on your own are very low. The sports betting world offers many projects that are naturally exciting and thus conducive to learning.

* **It forces you to have skin in the game.** Data science is about using statistics to make decisions. Too often as learners we complete the first step (use statistics) without completing the crucial second step (actually make decisions). Decoupling these two steps hinders our development because if we don't actually have something on the line with our conclusions, we will lack the rigor and practicality that comes through the natural learning process of feeling the high of being correct and the sting of being wrong. Actually risking something based on your conclusions will force you to understand more deeply the logic of what you are really doing in a way that is very hard to replicate otherwise. Nassim Taleb says this best:

> “Let us return to pathemata mathemata (learning through pain) and consider its reverse: learning through thrills and pleasure. People have two brains, one when there is skin in the game, one when there is none. Skin in the game can make boring things less boring. When you have skin in the game, dull things like checking the safety of the aircraft because you may be forced to be a passenger in it cease to be boring. If you are an investor in a company, doing ultra-boring things like reading the footnotes of a financial statement (where the real information is to be found) becomes, well, almost not boring.”

* **You get to actually do something about your findings.** In sports betting, when you have a conviction in an idea, it is very easy for you to implement it; you simply make a bet or a prediction. This is part of the reason why it can be so fun and why it is so unique. In other fields, especially as a student with limited resources, your opportunities to do something about your findings are limited. Even in sports analytics you can run all the analyses you want on going for it on fourth down, but ultimately the only thing you can do about it is pray Kalani agrees with you.

* **Gives you a chance to clearly communicate statistical ideas to non-statistical folk.** Communicating ideas clearly is always emphasized as one of the most important skills for a data scientist, but the problem is that in order to practice it, you have to have someone interested in hearing your explanations. I have never had so many non-statistics friends be really interested in me explaining to them logistic regression until the topic was the game that night and the $10 dollar bill in their wallet.  

* **Tons of easily available information and constant opportunities for new projects.** Sports fans can be quite nerdy and so tons of data ready for analysis can be easily found online and there are new games all year round.

## How do I get started?

Like anything, sports betting can be intimidating at first. Nevertheless, it doesn't have to be complicated at all, and below I will walk through 3 simple steps to get you started using a simple project I worked on during the 2020 NBA playoffs.

**1\. Qualitatively define your investment thesis by finding a difference in opinion.** When competing in markets, you can't just be right; you have to be right where most others are wrong. For example, saying the Bucks are a great basketball team does nothing, but saying they are better than what most other people think they are could be the basis for a bet.

In my example, I noticed that the odds for the player to score the first point in a game during the NBA playoffs seemed to be based off of the proportion of points each player scored for their team, but I believed that this was wrong and that the odds should actually be based off of the proportion of first points each player scored. I believed this because oftentimes teams will run set plays for certain players at the beginning of the game. My belief was based off a smaller sample size (only first points scored vs all points by starters), but I believed it would be more predictive regardless.

**2\. Calculate the expected value of a single bet based off of your unique probabilities.** If you have a difference in opinion, your implied probabilities will be different than those implied by the odds. This means you will likely see a bet with an expected value higher than 1x (getting more than 1 dollar back for every dollar you put in). 

In my case, I found my unique probabilities by scraping data for who scored the first points and then calculating the expected values using the published payouts. Below are the results for a game with the Lakers. As you can see, betting on Danny Green to score the first point had an expected value greater than 1x.

![ev](/assets/images/blogimages/figs-10-30/ev.png)

**3\. Determine the variance of your bet**. Just because a bet has an expected value above 1x does not mean it is a good bet because you may not be able to make enough similar bets to ensure you end up winning money most of the time with that strategy. For example, if you were offered a .1% chance at winning $10B dollars if you pay $1M, you would have an expected value of earning 10x your money, but you would only actually win money .1% of the time. The other 99.9% of the time you would lose $1M. If you could do this bet a large number of times, it would be worth it, but doing it only once is probably too risky for most.

Applying this concept to my bet, I ran a Monte Carlo simulation with my calculated probability, first with 24 games played and then with 100 games played. As you can see, in both cases my returns are ~36% (as expected based on the expected value), but in the 100-game case I end up winning money overall much more often (81%) than in the 24-game case (52%). Thus, I only decided to proceed after verifying that I would be able to make bets with similar probabilities in a relatively high number of games. This is especially important for a strategy such as this where you expect to lose more often than you win but win big and lose little.

```python
games = 24
prob = .226415/2
bet = 100
multiplier = 11
n = 100000
total = []

for i in range(n):
    score = 0
    for i in range(games):
        value = random.choices([0,1], weights=[1-prob, prob], k=1)[0]
        if value == 0:
            score -= bet
        elif value == 1:
            score += bet*multiplier
    total.append(score)
```

![mc](/assets/images/blogimages/figs-10-30/mc.png)

## Where can I go to learn more?

If this type of thing is exciting to you, there are many resources you can find online that are both entertaining and useful. Here are three that I have personally enjoyed:
* [Podcast](https://podcasts.apple.com/us/podcast/bet-the-process/id1291010585) focused on data science in sports betting called *Bet the Process*. Hosted by the real-life protagonist of the book/movie *21*
* [Interview](https://www.youtube.com/watch?v=FeOOpuDrZaQ) from DataCamp about the future of data science in sports betting and the unique innovations that are occurring in the space 
* [Simple article](https://www.justintodata.com/improve-sports-betting-odds-guide-in-python/) detailing the practical steps for using python for sports betting

## Conclusion

Sports betting can be a fantastic way to train and test your data science skills. It offers real-world decision making, a variety of problem types, plenty of easily accessible data, and a whole lot of fun. In addition, the financialization of culture and the automatic market-making/smart-contract capabilities of blockchain technology (both topics for another post) mean there will be an incredible amount of interesting opportunities in the future and ensure that the sports betting hobby will only get better. 

Comment below if you have any interesting "investment theses" that could be worth looking into. It could be as simple as an idea for a collecting a new data type and thus having a proprietary predictor, applying a type of statistical model to a bet, or even just that the University of Utah will lose every football game for the rest of the season! 

<iframe src="https://giphy.com/embed/eHx5A2SWQtYRrG4WM2" width="480" height="270" frameBorder="0" class="giphy-embed" allowFullScreen></iframe>

*Disclaimer: Sports betting can of course be considered a form of gambling and can be addictive. Though it is important to note that in several places sports betting is considered similar to investing, and you can even raise outside capital to form sports betting investment funds (zero correlation to the market is attractive). Nevertheless, considering the risks, it is totally possible to simply make "paper bets", where you make predictions but don't actually wager any money. You can still get the learning benefits the sports betting context provides without ever actually betting anything.*

 
