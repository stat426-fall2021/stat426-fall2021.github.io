---
title: "Non-Parametric Tests: Statistically Efficient or Technically Cheating?"
layout: post
author: ghman12345
post-image: https://sphweb.bumc.bu.edu/otlt/mph-modules/bs/bs704_nonparametric/Nonparametric%20Wordle.png
description: An overview of non-parametric tests, when they should be used, what forms they come in, and how to use them
tags:
- R
- Non-Parametric tests
- Mann-Whitney U Test
- Utah Car Crashes
---

# Non-Parametric Tests: Statistically Efficient or Technically Cheating?
![This is an image](https://i.ibb.co/xLgsGZV/Frank-Wilcoxon.png)
## Introduction
Tired of memorizing countless distributions and their parameters? Well, you're in luck, because through non-parametric tests, you can run all of the same types of tests that you learned in your former statistics courses without worrying about distributions or parameters. Not only that, but, as it turns out, a lot of the data that we encounter in the real world is not normally distributed, which makes non-parametric tests that much more useful.
## So What Are They?
In statistics, non-parametric tests are methods of statistical analysis that do not require a distribution to meet the required assumptions to be analyzed. For this reason, they are sometimes referred to as distribution-free tests. Nonparametric tests serve as an alternative to parametric tests such as a t-test or ANOVA which can only be employed if the data satisfies certain specific assumptions. Although using non-parametric tests results in losing power if the data is normally distributed, if the data is not normally distributed, using non-parametric tests will almost always be more powerful than using parametric tests.
## Specifically When to Use Them
- ***Data does not meet the assumptions about the population sample***

Generally, the application of parametric tests requires various assumptions to be satisfied. Some of them include the data following a normal distribution and the population variance being homogeneous. However, many datasets are not like this. Sometimes, the dataset might be skewed.The skewness makes the parametric tests less powerful because the mean is no longer the best measure of central tendency because it is strongly affected by the extreme values. However, nonparametric tests work well with skewed distributions and distributions that are better represented by the median.

- ***The population sample size is too small***

The sample size is an important assumption in selecting the appropriate statistical method. If a sample size is reasonably large, the applicable parametric test can be used. However, if a sample size is too small, it is possible that you may not be able to validate the distribution of the data. Thus, the application of nonparametric tests is the only suitable option.

- ***The analyzed data is ordinal or nominal***

Unlike parametric tests that can work only with continuous data, nonparametric tests can be applied to other data types such as ordinal or nominal data. For such types of variables, the nonparametric tests are the only appropriate solution.
## Types of Tests

![image.png](https://cdn.corporatefinanceinstitute.com/assets/nonparametric-tests.png)

 - ***Mann-Whitney U Test***

The Mann-Whitney U Test is a non-parametric version of the independent samples t-test. The test primarily deals with two independent samples that contain ordinal data. Like the t-test, it is used to test whether two samples are likely to derive from the same population. Unlike its parametric brother, however, the Mann-Whitney U test bases its outcomes on rank, not raw numbers. This makes the test more robust, as it would not be affected by outliers as much as the t-test.[^1]
[^1]: (https://sphweb.bumc.bu.edu/otlt/mph-modules/bs/bs704_nonparametric/bs704_nonparametric4.html)

- ***The Kruskal-Wallis Test***

The Kruskal-Wallis test, proposed by Kruskal and Wallis in 1952, is a nonparametric method for testing whether samples are originated from the same distribution. It works in a similar way to the Mann-Whitney U test, except it uses more than two groups. The null hypothesis of the Kruskal-Wallis test is that the mean ranks of the groups are the same, while the alternative hypothesis is that at least one of the mena ranks is different. It is the nonparametric equivalent one-way ANOVA, but unlike the one-way ANOVA, the nonparametric Kruskal-Wallis test does not assume a normal distribution of the underlying data.[^2]
[^2]:https://sphweb.bumc.bu.edu/otlt/MPH-Modules/BS/R/R4_One-TwoSampleTests-ANOVA/R4_One-TwoSampleTests-ANOVA5.html

## Example

Enough talk, lets try to understand non-parametric tests through an actual example. Let's use an easy and clear dataset to demonstrate a particular type of non-parametric test, the Mann-Whitney U Test. We will compare the number of accidents caused by distracted driving and drinking and driving in Utah from 2010 to 2020,[^3] and we will be using R throughout the entire process, so you can do it yourself when this is all done.
[^3]:https://publicsafety.utah.gov/

- ***EDA***
```r
Distracted <- c(4267,4363,4667,5138,5581,5816,5831,5825,5772,5601,4801)
Alcohol <- c(1633,1406,1572,1624,1700,1883,1925,1825,1915,1923,1971)
year <- c(2010,2011,2012,2013,2014,2015,2016,2017,2018,2019,2020)

Utah_crash <-data.frame(Distracted, Alcohol, year)
```
![image](https://i.ibb.co/58bzRTj/EDA.jpg)

As we can clearly see, distracted driving causes many more accidents. We probably don't even need any type of formal test to prove that there is a statistically significant difference, but, again, we are using an easy example to see how non-parametric tests work.

```r
hist(Utah_crash$Distracted, main = "Distracted Driving", xlab= "Number of Crashes")
hist(Utah_crash$Alcohol, main = "Drinking and Driving", xlab= "Number of Crashes")
```

![image.png](https://i.ibb.co/LC5bX7Q/Histograms.jpg)

Our sample size is low with only eleven and not normally distributed, so we will go ahead and use the Mann-Whitney U test

- ***Test***

The code for running this test is as simple as running a t-test in R. Just input the datasets inside the function "Wilcox.test"
```r
wilcox.test(Utah_crash$Alcohol,Utah_crash$Distracted)
```

Much like the t-test, this will provide a p-value to show if there is a statistically significant difference. In this case, the p-value was   
<img src="https://render.githubusercontent.com/render/math?math=2.8351422*10^{-6}">. If the alpha level was 0.05 (or even much lower than that),
this value would show that there is a statistically significant difference (as expected).

## Conclusions
Using non-parametric tests will expand your statistical analysis skill set.
You can use them when parametric tests will not be as effective or just obsolete.
Sometimes it is best to use both and compare which test is more effective, then use the better one. As you can imagine,
non-parametric tests do not end with the two tests we talked about. Bootstraping and permuation tests are forms of
non-parametric tests that are also very effective under certain circumstances.
With this knowledge, we encourage you to use both parametric and non-parametric tests on a couple of datasets to see how
they compare and how effective non-parametric tests can be in certain circumstances.
