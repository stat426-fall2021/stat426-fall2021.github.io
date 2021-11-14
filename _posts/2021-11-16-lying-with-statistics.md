---
title: "Lies Damn Lies and Statistics: A Review of Darrell Huff's Book How to Lie With Statistics"
layout: post
author: smbjohnson
post-image: '/assets/images/blogimages/figs-11-16/Blog-Post-Cover-Image2.jpg'
description: "In a world full of personal agendas and even more data we take a look at Darrell Huff book *How To Lie With Statistics* to avoid common pitfalls of understanding statistics"
tags:
- Book Review
- Data Science
- Data Science Ethics
- Statistics
- Data Literacy
- Darrell Huff
---

![Book-Cover](/assets/images/blogimages/figs-11-16/Book-Cover-Image.jpg)

# Introduction

As data becomes more prevalent, the ability to correctly interpret that data becomes more crucial. This is particularly true when, either nefariously or out of ignorance, some individuals or organizations report data in a way that misrepresents what it says. In Darrell Huff's book, *[How to Lie with Statistics](https://www.amazon.com/How-Lie-Statistics-Darrell-Huff/dp/0393310728)*, Huff discusses nine common ways in which people misrepresent data through statistics and or graphs. This review covers five of the most common ways and how to best identify and react to these misrepresentations. 

# Samples with Built-in Bias

The first question Huff has us ask of a statistic is how the data was gathered that led to that statistic. Huff gives the example of a survey in which graduates from Yale University were asked what their current annual income was. This question has bias because people making more money may be more likely to report their salary, while those not making their desired income may not report or may over report their actually salary. Certain questions come with inherit bias. To make matters worse, the group being surveyed can carry similar bias. If we go to a university and ask how many people suffer from back pain, their answers will not be an accurate representation of the number of cases of back pain for a more general population. When collecting data we must consider whether the question or the group being surveyed introduces bias to the data.

# Unreported figures

Many reported figures lack important information that make the figure misleading. Two examples of this are not disclosing range of data or the survey sample size. An example of the problem of not showing the range of the data is if you are simply told the average summer sales representative makes $10,000 a summer without the information that one representative made $505,000 while the other ninety-nine all made $5,000 each, then you might misguidedly forego an guaranteed $9,000 internship. Similarly, not knowing the sample size behind a statistic can mislead. For example, if a test compares two cough medicines and one relieves coughs in five out of the ten people and the other relieves coughs in four out of five people, the 30% difference seems large until you know too few people were tested. When viewing data-based figure, it is important to recognize that unreported figures might change one's conclusion. 

# Comparing Apples to Almost Apples

Sometimes people report statistics comparing unlike groups as if they were more alike than they actually are. An example Huff uses in *How to Lie with Statistics* is the reported death rates during the Spanish American war. The Navy recruiting station reported that only nine in every one thousand sailors died compared to sixteen in every one thousand civilians living in New York City. This presentation makes signing up for war with the Navy feel safe, until you consider that the New York City death rate included death due to old age, infant deaths, and those already suffering from aliments. With this additional information, the Navy doesn’t seem quite as safe as presented. We must be vigilant in ensuring that the groups being compared are actually alike. 

# Graphs

The media is filled with graphs and charts trying to convey information in an intuitive and easy to digest way. However, some of these easy to read graphs can be misleading. Such graphs prey on those who take the chart at face value. One of the most common ways in which graphs take advantage of the unassuming consumer is to truncate the y axis of a graph. If we look at the plot of the left, it appears as though horror movies make substantially more money that action movies. It is only when we take a closer look that we see there is a much smaller difference (see plot of the right). In fact, there is only a 5% difference between money made in each movie genre. People also apply this trick by changing the x axis. Having unequal spaces between observations can cause havoc when it comes to graph interpretation. Special care must be taken when looking at graphs, like looking at the x and y axis and considering the units being expressed on each. 

<img src="/assets/images/blogimages/figs-11-16/Movie-Plot-Truncated.png" width="400"/> <img src="/assets/images/blogimages/figs-11-16/Movie-Plot.png" width="400"/>

# Correlation Doesn’t Mean Causation

Perhaps the most common deception in statistical reporting is inferring that one outcome *caused* the other when in fact there is only a *correlation*. An exaggerated example of this type of thinking might be seen in ice cream sales and crime rates. Often as the sales of ice cream rise so do crime rates. Does that mean police should be sent out to impound all ice cream trucks? Obviously not. There might be other factors that cause both ice cream and crime to rise at the same time -- like hot summer weather. Another example Huff touches on in his book is the correlation between students who drink and smoke and getting bad grades. One might assume that students get bad grades because they drink and smoke, but it is also probable that students who get bad grades are driven to smoking and drinking to cope with the stress. We are often too quick to draw a causal relationship between to variables without first putting in the work to create a test in which all variables can be controlled for in some way.

# Conclusion
This post only covers a few ways in which statistics and graphs can be misleading. Huff suggests several questions to help identify many misleading numbers.

* Who says so?
* How do they know?
* What’s missing?
* Did someone change the subject?
* Does it make sense?

When it comes to interpreting numbers and data, it is important to slow down and think about what has led to this number that we are now seeing. When we do this, we can often avoid making rash decisions on numbers that don’t really mean anything or don't mean what is being sugested. So the next time you see a staistic, take a minute to really think about what it is saying and if there might be any ulterior motives.

If you are looking for examples of the misleading use of statistics, there is no better place than a [reddit forum](https://www.reddit.com/r/badstats/).
