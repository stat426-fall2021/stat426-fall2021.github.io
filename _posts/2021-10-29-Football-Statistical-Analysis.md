---
title: The Importance of Play Type and Location in the NFL
layour: post
author: bradhy97
post-image: /assets/images/blogimages/figs-10-29/title.jfif
descripton: A deeper look into how play type and play location affect yards gained per play in the NFL through parametric and non-parametric methods.
tags:
- R
- Non-Parametric Methods
- Sports Analytics
---

## Introduction

Data analytics have become an increasingly prevalent tool used to help make important decisions in the field of professional sports.  In particular, the National Football League has implemented a wide variety of data analytic methods to aid in evaluating NFL draft prospects.  Similarly, this study aims to use data analytic methods to evaluate the relationship between type of play, play location, and yards gained, and whether any of these relationships are statistically significant. When attempting to determine whether results are significant, certain assumptions have to be met in order to use standard parametric methods, such as data being homoscedastic and following a Gaussian distribution.  However, what can we do if our data does not meet these assumptions?  For cases such as this we can turn to non-parametric methods in order to determine statistical significance. The number of yards gained (or lost) for each field location and type of play was compared through both parametric and non-parametric methods.

---

## Overview


In order to determine which play location and type of play are the best, this study compares the yards gained for each type of play, as well as the yards gained for each play location.  The dataset was obtained from Kaggle.com, and contains a plethora of information pertaining to the National Football League.  This data was filtered down to three pertinent columns: “Yards.Gained”, “RunLocation”, and “PassLocation”, from which further statistical analysis was performed.  This statistical analysis will include both parametric and non-parametric tests, and the results of both types of tests will be compared to each other in order to draw the most accurate conclusions possible.  For the parametric methods, a two sample t-test was used to compare the mean yards gained for each type of play (run versus pass), as well as a one-way analysis of variance (ANOVA) was performed to compare the mean yards gained for each type of play location (left versus middle versus right).  For these parametric tests to be conducted, certain assumptions are made, specifically that all data points follow a Gaussian distribution, and all points must have similar variances. If these assumptions were not met, then non-parametric methods were performed as well.  The non-parametric equivalents to the parametric test we use is a Mann-Whitney U test for the two sample t-test, and a Kruskal-Wallis one-way analysis of variance for ANOVA.  

The null hypothesis for the two sample t-test and the Mann-Whitney U test is that the mean number of yards gained per run play is equal to the mean number of yards gained per pass play.  The alternative hypothesis for these tests will be that there is a difference between these two groups, and the threshold for this statistical significance is an alpha level of 0.05.  Additionally, the null hypothesis for the ANOVA and the Kruskal-Wallis test is that there is no difference between the mean number of yards gained for each run location, and the alternative hypothesis will be that there is a difference between any of the three means, with an alpha level of 0.05, the same as the previous tests.  The results of each test were compared to its parametric or non-parametric counterpart, and these results were then interpreted in conjunction with each other.

---

## Exploratory Data Analysis

### Run Location

Looking at the summary statistics for yards gained by run location, we see that the means appear to differ by a small amount, though there are two outliers that could explain these differences. The medians and standard deviations are also different, in particular the median and standard deviation pertaining to runs in the middle location compared to the other run locations.

![runinfo](/assets/images/blogimages/figs-10-29/runlocationinfo.png)

### Pass Location

The summary statistics for yards gained by pass location differ from each other as well, similar to the yards gained by run location. Passes from the left location seem to especially differ from the other pass location, with the mean and standard deviation both being close to twice as large as the respective measurements for the other pass locations, though this could be due to the two outliers present in the data.

![passinfo](/assets/images/blogimages/figs-10-29/passlocationinfo.png)

### Play Type

Finally, we can see that the summary statistics comparing play type show a clear difference in means, standard deviations, and medians. However, this difference is largely attributed to the two outliers present in the data, with the maximum yards gained for passes being 43 yards, and the maximum yards gained for runs being 28 yards.

![playinfo](/assets/images/blogimages/figs-10-29/playtypeinfo.png)

### Q-Q Plots

After looking at the summary statistics of the data, we can now check for normality through the use of Q-Q plots. The data looks normal, but due to the small sample size, the results are inconclusive. We can also check for skewness, and after doing so, can see that the data based on run location and the data based on pass location are both fairly skewed, so we can perform a variety of data transformations in order to attempt to remedy this.

![qqplots](/assets/images/blogimages/figs-10-29/qqplots.png)

By looking at the skewness for each possible data transformation, we can see that the fourth root transformation and the square root transformation bring the skewness values closer to zero than any other transformation for run data and pass data, respectively. After seeing this, we can now view Q-Q plots of the transformed data and see that plots appear to be more normal than the pre-transformed data. Going forward, we will use this transformed data when conducting our two sample t-tests and ANOVA, as the transformed data better adheres to the assumptions necessary to do so. For the non-parametric methods of Mann-Whitney U test and Kruskal-Wallis test, there is no need to use the transformed data, as the assumptions needed to perform parametric tests do not need to be met.

![transqqplots](/assets/images/blogimages/figs-10-29/transformedqqplot.png)

### Permutation Tests

Another way that we can calculate the p-value for our tests of significance is through permutation tests. For comparing yards gained versus play location for both run and pass plays, we create a function that takes our sample data and the amount of groups we wish to divide the the sample data into as parameters, which in this case is three groups, as the amount of different play locations is equal to three. Our function then randomly divides the data into the desired amount of groups and conducts a Kruskal-Wallis test on the newly created groups, finally returning the calculated chi-squared statistic. For the permutation test, we run this function a total of 100000 times and save the results as a variable, as this creates a list of 100000 calculated chi-squared statistics. We then view the frequency of our chi-squared statistics in a histogram and see the proportion of calculated statistics that are greater than the chi-squared statistic we calculated from our original, non-shuffled data. This proportion gives us an estimate for our p-value, which we then compare to the p-value from the Kruskal-Wallis test on our original dataset.

Similarly, when comparing yards gained versus play type, we create a function that accepts our dataset as a parameter, and then randomly divides this dataset into two equal sized groups. A Wilcox test is then performed on the two resulting groups and the calculated w-statistic is returned as the result. Like the previous permutation test, this function is run 100000 times and the calculated statistics are saved as a list. This list is then displayed as a histogram, where we see the proportion of w-statistics that are as extreme or more extreme (in this case, less than or equal to) than the w-statistic we calculated for our original dataset. This gives us the p-value for a one-sided test of significance, but we need to find the p-value for a two-sided test of significance. In order to find the desired p-value, we find the quantile for our original dataset’s w-statistic and then find the corresponding quantile on the opposite side of our histogram, which is equal to 1 minus our first quantile value. We then find the proportion of w-statistics that are as extreme or more extreme (in this case, greater than or equal to) than the original dataset’s w-statistic and add this proportion to the first proportion we calculated, which finally gives us the p-value for our two-sided test of significance.

![permtests](/assets/images/blogimages/figs-10-29/permtests.png)

The above plots help to illustrate how our permutation tests work. The histograms show the spread of the calculated statistics for both our Kruskal-Wallis permutation test and our Wilcox permutation test, and the vertical lines on each plot show the value of the statistics we calculated for our original dataset. For our Kruskal-Wallis permutations, the area to the right of our vertical line is equal to our p-value, as this is the probability of obtaining the chi-squared statistic we got or one more extreme. For our Wilcox permutations, the two vertical lines correspond to the quantiles we calculated earlier, and the p-value is equal to the area to the left of the first line plus the area to the right of our second line. For all of the above plots, the p-value we obtained from our permutation tests is labeled on the plot and is discussed further in the results section of this report.


### Bootstrap Methods

For our bootstrap methods, we create two functions that are nearly identical to the previously created permutation test functions. However, the one difference between our bootstrapping functions and our permutation test functions is found in how we sample our data. For the permutation tests, we sample from the original dataset without replacement, whereas for bootstrap methods, we sample from the original dataset with replacement. After changing our functions accordingly, we run the functions 100000 times for both our Kruskal-Wallis bootstrap method and our Wilcox bootstrap method and generate lists of the statistics we calculated from these methods. We then determine the p-values from these tests in the same way as we did for our permutation tests, and then compare these results with the results we obtained from the tests we conducted on our original dataset as well as the results from our permutation tests.

![bootmethods](/assets/images/blogimages/figs-10-29/bootstrapmethods.png)

As we can see from the previous plots, the obtained p-values are very similar to those we obtained from our permutation tests, as well as the parametric tests and the non-parametric tests we conducted on our original dataset. The p-value for a specific test is the probability of obtaining a single test statistic or one more extreme than what we have, and we can see how this concept is illustrated in our plots. For
our Kruskal-Wallis bootstrap methods, the p-value is equal to the area to the right of the vertical line on our plots, as this line represents the test statistics calculated for our original dataset. For our Wilcox test bootstrap method, the p-value is equal to the area moving away from the mean on either side of the two vertical lines in the plot, as these lines represent the appropriate quantiles for a two-sided test of significance.

---

## Results

The results of the run location data analysis show that the p-value for the ANOVA test is 0.4085286, which is higher than our alpha of 0.05. The Kruskal-Wallis test returned a p-value of 0.169678, which further reinforces that our null hypothesis cannot be rejected: there is no difference in the average amount of yards gained based on run location. Additionally, our permutation test and bootstrap methods for run location returned p-values of 0.51042 and 0.51311 respectively, which are both p-values that result in us failing to reject the null hypothesis.

The results based on the pass location data analysis are similar to those based on the run location. The pvalue for the ANOVA test is 0.2928736 and the p-value for the Kruskal-Wallis test is equal to 0.5012825, which are both higher than the predetermined threshold of an alpha level of 0.05. In addition, our permutation test and bootstrap methods for pass location resulted in p-values of 0.16931 and 0.16907 respectively. The
p-values from these four type of tests lead to the conclusion that our null hypothesis cannot be rejected.

Finally, the results of our play type data analysis show that there is a statistically significant difference between the average number of yards gained per run play and the average number of yards gained per pass play. The p-value of the two sample t-test is 0.0279695, and the p-value from the Mann-Whitney U test is equal to 0.0237371, which both support rejecting the null hypothesis and using the alternative hypothesis. This conclusion is further supported by the permutation test and bootstrap methods for play type, as the returned p-values are 0.02202 and 0.02132 respectively, with both of these p-values being below our alpha threshold of 0.05.

---

## Conclusion

Based on the previously stated results, we see that although the location of a play does not make a difference, the type of play conducted does make a difference. This information could prove invaluable to any and all teams belonging to the National Football League, as it could influence a wide variety of decisions each team makes. Because pass plays results in a significantly larger average amount of yards gained than run plays, teams looking to improve could allocate more of their resources into improving their quarterbacks and wide receivers, as well as any other individuals involved in passing plays. Additionally, this information can influence which players are prioritized in the NFL Draft, as it could place an increased emphasis on drafting players that specialize in conducting passing plays. Alternatively, because the location of a play was found to not be significant, teams do not need to consider whether their players have a preference for a certain location on the field when drawing up a game plan, such as a left-handed versus a right-handed quarterback.

The dataset used for this analysis was too small to effectively check that the assumptions for equal variance and normality were met; however, because both the parametric methods and non-parametric methods agreed with each other, we can conclude that is not worth using non-parametric tests in lieu of parametric tests for this dataset, due to the loss of power associated with conducting non-parametric tests. Despite reaching these conclusions, we should consider how these conclusions may have changed if the sample size had increased. Would the data follow a Gaussian distribution and/or would the resulting conclusions have differed? Finally, though the difference in yards gained by pass plays and run plays was found to be statistically significant, how practically significant does this result turn out to be?

---

## Future Recommendations

Though this study may have found a difference in play type yard gain (as well as not finding a difference in play location), the dataset the study was based on contained information based on all NFL teams, which may not necessarily apply to every individual team. If a specific team wanted to determine how these results/conclusions apply to themselves, it would be important to obtain a sample solely based on data from that specific team. Additionally, comparing the average amount of yards gained based on other variables would allow us to draw more accurate conclusions, as the differences found in the analysis could have possibly been influenced by any number of confounding variables.