---
title: Basic Chi-Square, Confidence Interval, Standard Deviation Run Down
layout: post
author: fseng98
post-image: '/assets/images/blogimages/figs-11-20/12.png'
description: Comparison of a simple linear regression model performed in R and Python
tags:
- Chi-square
- Confidence Interval
- Standard Deviation
---


## Basic Chi-Square, Confidence Interval, Standard Deviation Run Down
## Abstract
This blog post tests out 3 different kinds of experiments to help readers understand the usage of standard deviation, confidence interval, and Chi-Square test. Each experiment comes with its own background, theory, and explanation to help the reader follow along step-by-step.
 
## Standard Deviation
## Introduction
My study is based on the “Student Ethnicity” data from the “Facts and Figures” webpage of Brigham Young University’s website. The data consists of the percentage of different ethnicities on campus. This is my data of interest since I have received an email from the university’s assistant to the president for assessment and planning. In the email, she asked students to fill out a survey in regards to the student diversity and equity. While I think there are many ways to define diversity, the topic of students’ ethnicities may represent the idea well. 
Theory
Data distribution and sampling distribution are very different from each other. Data distribution is collected through a whole population while sampling distribution is collected through the samples of a population. With different numbers of samples, the data of the sampling distribution may have different values from the data distribution. Such values include the mean, standard deviation, and variance. With different values, the properties of the sample distribution’s histogram may differ also. Central Limit Theorem states that the distribution of sample means approximates a normal distribution as the sample size gets larger. Sample sizes equal to or greater than 30 are considered sufficient for the CLT to hold.
To see the properties of a data distribution, we will first have to look at the probability distribution. The probability distribution or probability mass function (pmf) of a discrete rv is defined for every number x by
p(x) = P(X = x) = P(all s ∈ S: X(s) = x)
In words, for every possible value x of the random variable, the pmf specifies the probability of observing that value when the experiment is performed. The conditions p(x) ≥ 0 and Σp(x) = 1, where the summation is over all possible x, are required of any pmf.
To make sure that the population data I collected is a valid form of pmf or probability mass function, I have applied the condition Σp(x) = 1 and p(x) ≥ 0.
Σp(x) = 0.81 + 0.06 + 0.04 + 0.03 + 0.01 + 0.01 + 0.04 = 1
Standard deviation looks at how spread out a group of numbers is from the mean, by looking at the square root of the variance. The variance measures the average degree to which each point differs from the mean—the average of all data points.
To find mean, let X be a discrete random variable with a set of possible values D and pmf p(x). The expected value or mean value of X, denoted by E(X) or μ X or just μ, is

![image](/assets/images/blogimages/figs-11-20/2.png)

It is stated that the data distribution’s mean is equal to the sample distribution’s mean. The calculated mean from the data of student ethnicity for both the data distribution and sample distribution would be 
0.81· (1) + 0.06· (2) + 0.04· (3) + 0.03· (4) + 0.01· (5) + 0.01· (6) + 0.04· (7) = 1.56
To find variance, let X have pmf p(x) and expected value μ. Then the variance of X, denoted by Var(X) or σ X 2or just σ2, is

![image](/assets/images/blogimages/figs-11-20/3.png)


Using this equation within R program, the calculated population variance from the data of student ethnicity would be 
Var(X) = 2.0264
It is stated that the data distribution’s variance differs from the sample distribution’s variance. The sampling distribution’s variance would then be the population’s variance divided by the number of samples. I have chosen n = 5, 10, 50, 100, 500 to be the numbers of my samples.
The variance for sampling distribution would then be:
For n = 5, var = 0.40528
For n = 10, var = 0.20264
For n = 50, var = 0.040528
For n = 100, var = 0.020264
For n = 500, var = 0.0040528
The standard deviation (SD) of X, denoted by SD(X) or σ X or just σ, is simply

![image](/assets/images/blogimages/figs-11-20/4.png)


Using this equation within R program, the calculated standard deviation from the data of student ethnicity would be 
SD = 1.4235
It is stated that the data distribution’s standard deviation differs from the sample distribution’s standard deviation. The sampling distribution’s standard deviation would then be the population’s standard deviation divided by the square root of the number of samples. 
The standard deviation for sampling distribution would then be:
For n = 5, StDev = 0.90623
For n = 10, StDev = 0.64080
For n = 50, StDev = 0.28657
For n = 100, StDev = 0.20264
For n = 500, StDev = 0.09062





Graphs of Data Distribution and Sampling Distribution

![image](/assets/images/blogimages/figs-11-20/1.png)


Graphs of Data Distribution and Sampling Distribution with Mean, Median, and Density

![image](/assets/images/blogimages/5.png)


Compare Data Distribution and Sampling Distribution
To compare data distribution and sampling distribution in order to show the difference, I have coded in R to create the histograms of the data distribution and the sampling distribution with n = 5, 10, 50, 100, 500. One thing to notice from all graphs is that the graphs are all right skewed. This is because of the data obtained. Within the data, the chance of getting 1 is at 80% making the chance of getting other values incredibly small. Thus, the data distribution graph itself is right skewed with a normal curve. 
Comparing the shapes of the graphs, we can see that some graphs from the sampling distribution can be uniform, bimodal, and close to normal. Yet, none of the graphs itself seem normal. When n = 500, the graphs may seem very close to normal, yet we can still see that it is not completely normal compared to the data distribution. When n = 5, n = 10, and n = 50, we can see that there are outliers from the graph. Compared to the normal curve of the data distribution the outliers exist because an outlier is a data point that differs significantly from other observations. An outlier may be due to variability in the measurement or it may indicate experimental error.
Comparing the graphics from the “Graphs of Data Distribution and Sampling Distribution with Mean, Median, and Density” section of the report, we can see that the mean, median, and density are labeled and drawn onto the graph. We can see that within the sampling distribution graphs, the line of blue for mean and the line of red for median do not completely overlap since we can see both colors on the graph. This means that the mean and the median of the sampling distribution are not exactly the same. Within a normal curve, the mean and the median would be the exact same. As shown in the graph for data distribution, we can see that we cannot see the red line at all. This is because through the R code, the blue line has completely covered the red line. The red line is barely visible at n = 500 but because n = 500 is not a normal curve, it is not covered by the blue line. (Did not change opacity because with purple it may throw off seeing the red and blue in n = 500)
The density curve shown in the graphics of “Graphs of Data Distribution and Sampling Distribution with Mean, Median, and Density” section of the report also varies. A density plot attempts to visualize the underlying probability distribution of the data by drawing an appropriate continuous curve. It is apparent that the probability distribution is not as compacted as the data distribution since the data distribution’s density plot is very flat and the sampling distribution’s density plot is more curved.
With all of the comparisons listed and the difference in standard deviation and variance, we can conclude that data distribution and sampling distribution are very different yet the sampling distribution is slowly getting to the true mean from the data distribution. We can also understand the data distribution is a normal curve while the sampling distribution is not. 

Effect of Sample Size on Sampling Distribution
To compare the effect of sampling size from a sampling distribution, I have coded in R to create the histograms of the sampling distribution with n = 5, 10, 50, 100, 500. Comparing the shapes of the sampling distribution graphs, we can see that when n = 5, the graph is bimodal. The graph is uniform when n = 5. From n = 50 to n = 100 to n = 500, we can see that the graph is slowly getting to normal on a left skewed level. The graphs are all right skewed due to the population data that p(1) = 0.81. Thus, the chance of getting 1 is very high. 
Looking at the mean and the median lines from “Graphs of Data Distribution and Sampling Distribution with Mean, Median, and Density” section of the report, we can see that from n = 5 to n = 500, the red line for median and the blue line for mean is slowly getting closer and closer. This proves the Central Limit Theorem correct that as n increases, the normality of the dataset and the graph approaches closer and closer to normal. 
We can also see from the density curve that as n increases, the curve gets more and more flat. This also proves that the probability distribution is becoming even across the graph. The span of the graph is slowly getting smaller from the density curve since the graph is slowly getting more compact and closer to normal The outliers of the graph were present from n = 5 to n = 50 yet it is decreasing when n is increasing. From n = 100 and on, we can see that the outliers are not present at all. This also proves that the graphs are slowly approaching normal when the sample size increases.
With the above observations, we can conclude that as the sample size increases in a sampling distribution, the normality within the distribution becomes more and more closer to normal. As stated in the Central Limit Theorem, the distribution of sample means approximates a normal distribution as the sample size gets larger. We can also conclude that as the size of the sample increases, the sample distribution slowly approaches closer and closer to the true mean. 

## Further Readings

Now that you understand what is standard deviation, the links below may help you calculate standard deviation!
https://www.calculator.net/standard-deviation-calculator.html
Read more at: 
https://www.investopedia.com/terms/s/standarddeviation.asp
https://www.mathsisfun.com/data/standard-deviation.html


## Confidence Interval
## Introduction
My study is based on a dataset that contains the nutrition table from seventy-seven popular breakfast cereal brands. I understand that as college students, we tend to eat a lot of cereals for breakfast because it is fast and easy. I have a lot of friends who try to lose weight and would abandon cereals for “healthy” breakfast choices like oatmeal. I have always wondered if oatmeal is a better alternative for weight loss. 
We know that within a package of food the calories per serving would not be exactly the number written on the nutrition table. For a lot of my friends that tend to count calories to lose weight, having the correct calories is very important to them. Thus, I believe conducting a 95% confidence interval on μ to make inference on a population from a sample can help everyone understand if cereal is low calories or not. 
By creating such confidence intervals and making an inference on the population from the sample, we can best see the estimated calories from true mean with 95% confidence. By doing so, we can then understand if cereal is a good source of breakfast for weight loss. 
Theory
The purpose of taking a random sample from a lot or population and computing a statistic, such as the mean from the data, is to approximate the mean of the population. How well the sample statistic estimates the underlying population value is always an issue. A confidence interval addresses this issue because it provides a range of values which is likely to contain the population parameter of interest.
Confidence intervals are constructed at a confidence level, such as 95 %, selected by the user. What does this mean? It means that if the same population is sampled on numerous occasions and interval estimates are made on each occasion, the resulting intervals would bracket the true population parameter in approximately 95 % of the cases. A confidence stated at a 1−α level can be thought of as the inverse of a significance level, α. (Eng & Stats Handbook, 2010)
For a simple random sample of n from a normal distribution with unknown μ and σ, the 95% confidence interval for μ is given by
(L, U) = Ybar ± t(0.025,n−1) √s /n


## Results from One Simulated Sample
From the results given for one simulated sample, I was able to look at the two-thousand-three-hundred-and-nineteenth sample of seventy-seven different simulated cereal calories. To do so, I coded a function which then ran through ten-thousand times randomly. Within those ten-thousand times, I took out the two-thousand-three-hundred-and-nineteenth sample and made it into a table or data frame. I also plotted a histogram to see and check the normality of the dataset. 
Because I set the SRS with rnorm in the function to make every dataset a normal distribution, my graph comes out looking close to a normal distribution. Central Limit Theorem states that the distribution of sample means approximates a normal distribution as the sample size gets larger. Sample sizes equal to or greater than thirty are considered sufficient for the CLT to hold. My sample size is seventy-seven which is close to thirty, the graph is normal but does not look quite normal. As sample size gets larger, the graph would look more and more like a normal distribution. 
Within my graph, I have highlighted the confidence interval and the two means (sample and true mean). This way, we can tell if the mean is within the 95% interval. In return, we can see in the graph that the lines representing the means are within the upper and lower values of the confidence interval. Within the table, we can see that the upper value of the confidence interval is 112.9558 and the lower value of the confidence interval is 104.3742. The true mean and the sample mean are 106.88 and 108.665. The logistic that I have written within the function to see whether or not the mean is within the interval returned as TRUE. 
This is all within my expectation because the math equation I have coded for the lower and upper value of the confidence interval is (L, U) = Ybar ± t(0.025,n−1) √s /n. The 95% confidence interval is a range of values that you can be 95% certain contains the true mean of the population. The confidence interval is 95% effective, thus there's a 95% chance that if a sample out of the ten-thousand tries, the true mean would fall between the confidence interval. 
Graph for One Simulated Result 2319
![image](/assets/images/blogimages/6.png)

Table for One Simulated Result 2319
![image](/assets/images/blogimages/figs-11-20/7.png)
![image](/assets/images/blogimages/figs-11-20/8.png)




## Confidence Interval Coverage, Sampling Distribution of L and U

![image](/assets/images/blogimages/figs-11-20/9.png)


The graph above is the confidence interval coverage of lower and upper values of the 95% confidence interval. The graph is created as a density level graph which means it can be used to observe the distribution of the lower and upper values in a dataset. The solid line represents the lower bound of the confidence interval. The dashed line represents the upper bound of the confidence interval. The interval is created from the ten-thousand simulations created from the function. Thus, the graphs look extremely close to normal distribution. 
![image](/assets/images/blogimages/figs-11-20/10.png)
Upon further inspection, I have noticed that the peak of the distributions are evenly spaced out from the mean. Thus, with calculation I added and subtracted the margin of error onto the true mean. With the resulting numbers, I put it into the graph as a red and blue line to see that the distributions peaked exactly where the lines are placed. I have also noticed that the tails of the distributions crossed at where the true mean is placed.
The scale of the graph contains density and calories. The density is scaled from 0 to 0.15. The numbers should be less than 1 so it can show the percentage of where the numbers are distributed.

## Repeated Sampling
![image](/assets/images/blogimages/figs-11-20/11.png)


The graph I created to show repeated sampling contains a forty-nine confidence interval between 5051 and 5100. The true mean is identified as the horizontal green line. If the true mean does not lie within the confidence interval, then the vertical lines representing the intervals would not intersect perpendicularly with the horizontal green line. Upon the graph it is apparent that all of the forty-nine vertical lines intersected with the green line. The pattern, however, would not be surprising if one or two of the lines did not intersect with the horizontal green line. Since this is a 95% confidence interval, this means that there is a 5% chance that within the ten-thousand simulations, there are around five-hundred simulations of the confidence interval that do not contain the true mean. I have run the simulation twice to get another set of ten-thousand simulations and I was able to see that from 5051 to 5100, there were five confidence intervals that did not contain the true mean. (pictured below)

![image](/assets/images/blogimages/figs-11-20/12.png)

## Further Readings

Now that you understand the confidence interval ,the links below may help you calculate the confidence interval!
https://www.mathsisfun.com/data/confidence-interval-calculator.html
Read more at: 
https://www.statisticshowto.com/probability-and-statistics/confidence-interval/
https://www.investopedia.com/terms/c/confidenceinterval.asp
https://www.sciencedirect.com/topics/nursing-and-health-professions/confidence-interval



## Chi-Square Test
## Introduction
This experiment is conducted to see if there is a preference present between restaurants when it comes to choosing. Suppose there are 6 different restaurants that 52 individuals can choose on a given Friday evening and that each individual makes an independent decision. The 52 individuals I have selected belong to a group of tourists driving by Salt Lake City to Arches Park. These tourists arrived at Salt Lake City airport and plan on taking a roadtrip to Arches National Park. They are leaving Salt Lake in the afternoon so they will arrive at Arches by night and visit the park the next day. The choices of restaurants that the tour guide has given them contains six restaurants. These restaurants are on the way from Salt Lake to Arches Park. The choices of restaurants are Texas Roadhouse, Mr.Shabu, Sicilia Mia, In-N-Out, Ombu Grill, and Paik’s Noodle. 
If there is no preference present, then the probability of choosing each restaurant should be one-sixth. 
## Theory
In order to conduct this experiment correctly, we must use the Chi-Square test. The Chi Square statistic is commonly used for testing relationships between categorical variables. The null hypothesis of the Chi-Square test is that no relationship exists on the categorical variables in the population; they are independent.  The null hypothesis in the experiment would be that there is no preference between the restaurants, meaning that the probability of choosing each restaurant is the same for all restaurants. The alternative hypothesis would state the contrary. 
The null hypothesis for this experiment would be that there is no preference between the restaurants, meaning that the probability of choosing each restaurant is the same for all restaurants. The alternative hypothesis would be that there is a preference between the restaurants, meaning that the probability of choosing each restaurant is different for all restaurants.
To find the test statistics for chi-square test we use the equation, where Oc stands for observed count and Ec stands for expected count.
![image](/assets/images/blogimages/figs-11-20/13.png)


In hypothesis testing, a critical value is a point on the test distribution that is compared to the test statistic to determine whether to reject the null hypothesis. Critical values are essentially cut-off values that define regions where the test statistic is unlikely to lie; for example, a region where the critical value is exceeded with probability α (alpha) if the null hypothesis is true. Alpha, the significance level, is the probability that you will make the mistake of rejecting the null hypothesis when in fact it is true. If the observed value of the test statistics of your test statistic is greater than the critical value, you can declare statistical significance and reject the null hypothesis.
To find the critical value, we can use a chi square table that contains chi square critical values with degrees of freedom for lower tail or upper tail. To check if we will need an upper tail table or a lower tail table, we will need to see the alternative hypothesis. Depending on the alternative hypothesis, we can use 1-alpha (upper tail) or alpha (lower tail) itself to find the critical value. 
The p-value is the probability of obtaining results at least as extreme as the observed results of a statistical hypothesis test, assuming that the null hypothesis is correct. The p-value is used as an alternative to rejection points to provide the smallest level of significance at which the null hypothesis would be rejected. A smaller p-value means that there is stronger evidence in favor of the alternative hypothesis. If the p-value is less than alpha then the null hypothesis is rejected.
Power ranges from 0 to 1, showing the percentage or the probability of rejecting the null hypothesis when, in fact, it is false. The higher the statistical power, the smaller of a chance that we accepted a false null hypothesis. A Type I Error is rejecting the null hypothesis in favor of a false alternative hypothesis, and a Type II Error is failing to reject a false null hypothesis in favor of a true alternative hypothesis. The probability of a Type I error is typically known as Alpha, while the probability of a Type II error is typically known as Beta. Power in another term, is avoiding Type II error, Beta.
For this experiment, a chi-square test will be simulated ten thousand times to see the density distribution and make further analysis. 
Obtained Critical Value
Because the alpha is 0.1, this means that 90% of the observations are below the critical value. Using the quantile function, we can set the probability to 0.9 (90%). The resulting number was 9.153846. However, using the qchisq(0.90, 6), the critical value came out to be 10.64464. The difference in number is due to the method of finding the critical value. The quantile function finds the critical value where 10% of the observations are greater than the critical value. 
The qchisq function uses the chi-square table to find the critical value with a degree of freedom at 6. This means that the function assumes that 10% of the observations are greater than the critical value at 10.64464 due to the degrees of freedom and alpha. 
The picture below shows us where the critical value lies when alpha is 0.1 using the quantile function. From the red line, 10% of the observations are greater than the critical value using the quantile function. With the blue line, it shows where the critical value lies from the chi square table. It is stated that if the observed value is greater than the critical value, then we reject the null hypothesis and declare significance. (This would be the same with the qchisq function since observed value is 12.1 and qchisq returns 10.64464)
![image](/assets/images/blogimages/figs-11-20/14.png)
Obtained P-Value
To find the p-value, I looked for the mean when the simulated null hypothesis sampling distribution was bigger than or equal to the observed value, 12.1. This resulted in 0.0343. This means that the chance of having a value greater than 12.1 within the null hypothesis sampling distribution is 3.43%. 
To explain further, looking at the graph below, we know that the observed value lies on 12.1 within the density graph. By finding critical value, we know that 9.153846 is where 90% of the observed values are below 9.153846 and 10% of the observed values are above 9.153846. Because 12.1 is higher than 9.153846, this means that the graph is divided at a different percentage at 12.1. This percentage can be calculated as the p value. The alpha is at 0.1, this means that where the critical value lies is where the alpha should be. Because 0.0343 is less than 0.1, p value is less than the alpha, thus we reject the null hypothesis and conclude significance. 
![image](/assets/images/blogimages/figs-11-20/15.png)
## Power
To find the power, I looked for the sum of when the simulated alternative hypothesis sampling distribution is greater than the critical value. Then, I divided that by the number of simulations. The power was returned as 0.7017. Because power is the probability of rejecting the null hypothesis when, in fact, it is false and alpha is the probability that you will make the mistake of rejecting the null hypothesis when in fact it is true, finding the alternative hypothesis above the critical value (where alpha lies on the sampling distribution) can help us find power. 
The graph below shows where the critical value lies on the alternative and null hypothesis. On the null hypothesis, we know that values that are above the critical is known as alpha. Where the critical value lies on the alternative hypothesis shows where the percentage lies that it is likely that we failed to reject the null hypothesis (left of the green line on the alternative hypothesis sampling distribution). This is also known as the Beta. 
With the power being 0.7017, this means that the study has a 70.17% chance of the test having significant results. Within the graph below, power lies within the alternative hypothesis right to the critical value, avoiding Beta. 
![image](/assets/images/blogimages/figs-11-20/16.png)


## Test Summary

In conclusion, we can say that because both the critical value and the p-value reject the null hypothesis with a power of 70%, we accept alternative hypotheses. There is a preference between the restaurants, meaning that the probability of choosing each restaurant is different for all restaurants. The tourists might favor one restaurant over another due to personal preference or allergies, cravings, etc. Asian or Italian restaurants might be rejected because they want American food for the tourist experience. 

## Further Readings

Now that you understand the Chi-Square test ,the links below may help you calculate Chi-Square!
https://www.socscistatistics.com/tests/chisquare2/default2.aspx
Read more at: 
https://www.bmj.com/about-bmj/resources-readers/publications/statistics-square-one/8-chi-squared-tests
https://www.jmp.com/en_us/statistics-knowledge-portal/chi-square-test.html


## Conclusion

With hypothesis testing and different experiment methods, we have learned the concepts of standard deviation, confidence interval, and chi-square tests. These statistical concepts may help us further on into the studies of statistics. Comment below  some topics we can test on through these concepts and what may come of it! :)
