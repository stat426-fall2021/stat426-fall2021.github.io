---
title: "Lies Damn Lies and Statistics: A Review of Darrell Huff's Book How to Lie With Statistics"
layout: post
author: smbjohnson
post-image: ![Cover](/assets/images/blogimages/figs-11-16/.Blog-Post-Cover-Image2.jpg)
description: "In a world full of personal adjendas and even more data we take a look at Darrell Huff book *How To Lie With Statistics* to avoid common pitfalls of understanding statistics"
tags:
- Book Review
- Data Science
- Data Science Ethics
- Statistics
- Data Literacy
- Darrell Huff
---

![Book-Cover](/assets/images/blogimages/figs-11-16/.Book-Cover-Image.jpg)

# Introduction

As data becomes more prevalent the ability to interpret that data will only become more crucial. However, either nefariously or out of ignorance, some individuals or organizations will report the data in a way that misrepresents what it says. In Darrell Huff's book, *[How to Lie with Statistics](https://www.amazon.com/How-Lie-Statistics-Darrell-Huff/dp/0393310728)*, Huff discusses nine common ways in which data is misrepresented through statistics and or graphs. For this review we will only cover five of the most common ways and how to best identify and subsequently handle. 

# Samples with Built-in Bias

The first question Huff has us ask of a statistic is how the data was gathered that led to that statistic. Huff gives the example of a survey in which graduates from Yale University what their current annual income was. This question comes with bias. Those who are making more money may be more likely to report their salary. While those who are not making their desired income may not report or even over report their actually salary. Certain question comes with inherit bias. To make matters worse, whose asking certain populations can carry the same bias. If we go to a university and ask how many people suffer from back pain their answers will not be an accurate representation of number of cases on back pain for a more general population. We have to think about what bias might be introduced to the data based on either the question or the sample.


# Unreported figures

Many of the reported figures lack important information that if not stated make the figure uninterpretable. Two examples of this might be standard deviation and sample size. An average value without a standard deviation or some other measurement of range can leave a lot to be interpreted. For example if you are told the average summer sales representive makes $40,000 a summer but in actuallity some sales people make $80,000 while others only make $10,000. This can also happen with sample sizes. I have two cough medicines I am trying to compare. Cough medicine one relieves coughs in 5 out of the 10 people tested. Cough medicine two relieves coughs in 8 out of 10 people tested. Although a difference of 30% might seem large when you consider, so few people were tested it no longer seems significant. It is important to always look for number of observations or standard errors around statistics. 

# Comparing Apples to Almost Apples

Often when statistics are reported they will only focus on one possible reason for the statistic. An example that Huff uses in *How to Lie with Statistics* is the reported death rate during the Spanish American war. The Navy recruiting station reported that nine in every one thousand sailors died, while in New York City sixteen in every thousand civilians died. This might seem shocking until you consider that the New York City death rate includes death due to old age, infant deaths, and those already suffering from aliments. After knowing this the Navy doesn’t seem to be as safe as it used to. We have to be vigilant in making sure that the groups we are looking to compare are actually comparable. 


# Graphs

The media is filled with graphs and cart trying to convey information in an intuitive and easy to digest way. However, some graphs do the exact opposite. They prey on those who take the figure at face value. One of the most common ways in which graphs take advantage of the unassuming consumer is to truncate the y axis of a graph. If we look at figure 1 below it appears as though horror movies make substantially more money that action movies. It is only when we take a closer look that we see there is a much smaller difference, see figure 2. In fact, there is only a 5% difference. This trick can also be applied by changing the x axis. Having unequal spaces between observations can cause havoc when it comes to graph interpretation. Special care must be taken when looking at graphs. It is important to look at the x and y axis while also taking into consideration the units the are being expressed on each. 

![Trunc-fig](/assets/images/blogimages/figs-11-16/.Movie-Plot-Truncated.png "Figure 1")

![Movie-fig](/assets/images/blogimages/figs-11-16/.Movie-Plot.png "Figure 2")

# Correlation Doesn’t Mean Causation

Perhaps the most well know deception in statistical reporting is inferring that one outcome caused the other when in fact all we know is that there is a correlation. An exaggerated example of this type of thinking might be seen in ice cream sales and crime rates. Often as the sales of ice cream rise so do crime rates. Does that mean police should be sent out to impound all ice cream trucks? Obviously not. There might be other factors that cause both ice cream and crime to rise at the same time. Another example Huff touches on in his book is the correlation between students who drink and smoke and getting bad grades. One could assume that students get bad grades because they drink and smoke, but it is also probable that students who get bad grades are driven to smoking and drinking to cope with the stress. We are often too quick to draw a causal relationship between to variables without first putting in the work to create a test in which all variables can be controlled for in some way.

# Conclusion
In this post we only went over a couple of way in which statistics and graphs can be misleading. However, Huff suggestion several questions that can help us identify many misleading numbers.

* Who says so?
* How do they know?
* What’s missing?
* Did someone change the subject?
* Does it make sense?

In the end when it comes to interpreting number and data it is important to slow down and think about what has led to this number that we are now seeing. When we do this, we can often avoid making rash decisions on number that don’t really mean anything. So the next time you see a staistic take a minute to really think about what it is saying and if there might be any ulterior motives.

If you are looking for practice there is no better place than a [reddit forum](https://www.reddit.com/r/badstats/).
