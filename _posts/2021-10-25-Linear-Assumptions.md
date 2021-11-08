---

title: Check your Assumptions
layout: post
author: rachelpourre
post-image: /assets/images/blogimages/figs-10-25/FIGURE3.png
description: 6 assumptions to check when using linear regression
tags:
- Assumptions
- Linear Regression
- Python

---


### “If you torture the data enough, nature will always confess.” – Ronald Coase

## The Set Up

Throughout this blog post, we will be going back to the basics: statistical assumptions.

Of course, we all know that linear regressions are the most basic but also one of the most used statistical modeling techniques. However, on rare occasions we consider whether the linear regression's assumptions are being met on the underlying distribution of the data for our models to fully succeed. In specific, we need to check whether certain assumptions are being met in order to draw inferences from the model.

Today we will go over 6 assumptions for a Linear Regression:

**Assumption #1**

Linearity: the relationship between the independent(s) variable(s) and the dependent variable is/are linear! That one is pretty intuitive, right?!

**Assumption #2**

The residuals are normally distributed.

**Assumption #3**

Homoscedasticity: the variance of the residuals is constant across all values of the independent(s) variable(s).

**Assumption #4**

No multicollinearity.

**Assumption #5**

No missing variables.

**Assumption #6**

Independence: the observations are not correlated with each other.

Before diving into it, let's start with the data.

This data set can be found at https://archive.ics.uci.edu/ml/datasets/Wine+Quality and it collects data about red wine.

Here is what this data set looks like:

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn import datasets

%matplotlib inline

wine = pd.read_csv('wine.csv', sep = ";")
wine.head(10)
```
![image](/assets/images/blogimages/figs-10-25/FIGURE1.png)

First, before we start with each one of the assumptions, we need to start with fitting the linear regression model. There are many ways to do that, but here we will use sklearn and statsmodel. Either way is fine, of course, so feel free to pick whatever is more convinient.

From this data set, we will try to predict alcohol levels, the dependent variable, using citric acid, residual sugar, and quality as independent variables. For the sake of learning, we will use these variables because we have reasons to expect some of the linear regression assumptions to be violated in this case.

```python
from sklearn.linear_model import LinearRegression

# Set up variables
X = wine[['residual sugar', 'citric acid', 'quality']]
y = wine['alcohol']

data = wine[['residual sugar', 'citric acid', 'quality', 'alcohol']]

# Instantiate model
lin_mod = LinearRegression()

# Fit model
lin_mod.fit(X, y)

# Print intercept and coefficient
print("Intercept: ", lin_mod.intercept_)
print("Coefficients: ", lin_mod.coef_)

import statsmodels.api as sm

## Refit the model
X = sm.add_constant(X)
lin_mod = sm.OLS(y, X)

linear = lin_mod.fit()

print(linear.summary())
```
![image](/assets/images/blogimages/figs-10-25/FIGURE2.png)

We can see a summary of the model, including the coefficients and the intercept in the ouput above.

Now, to the assumptions!

## Assumption #1

Linearity: the relationship between the independent(s) variable(s) and the dependent variable is/are linear.

The most beautiful way to check for this assumption is using Seaborn, through scatter plots.

```python
import seaborn as sns

sns.pairplot(data)
```
![image](/assets/images/blogimages/figs-10-25/FIGURE4.png)

To find out whether there this assumption is met, we need to check the scatter plots between the dependent variable "alcohol" and each of the independent variables seem to be linear.

Unfortunately, there does not seem to be a very strong linear relationship (or any discernible relationship really) between any of the independent variables and the dependent variable. It is also noticeable that quality is a categorical variable.

## Assumption #2

The residuals are normally distributed.

We can test this assumption by doing a histogram or a QQplot. Let's focus on how to make the QQplot.

```python
## Get the residuals

residuals = linear.resid

# Plot!
sm.qqplot(residuals, line = '45')
plt.show()
```
![image](/assets/images/blogimages/figs-10-25/FIGURE5.png)

In the QQplot, we can check if all the points are on the red straight line. In the graph above, we can see that there is significant curvature to the line and some disperse points at the right and left. Therefore, we can say that the data does not satisfactorily meet this assumption.

## Assumption #3

Homoscedasticity: the variance of the residuals is constant across all values of the independent(s) variable(s).

One way to check for homoscedasticity is to make a scatterplot with the residuals and the dependent variable.

```python
plt.scatter(y, residuals)
plt.plot(y, [0]*len(y))
```
![image](/assets/images/blogimages/figs-10-25/FIGURE6.png)

Wow. Okay... I guess not.
Homoscedasticity means the error or the residuals are constant, so we should see a cloud-like figure on the scatterplot. There aren't just lines (because of the categorical variables) in the present scatterplot, but there is also a clear positive relationship, which is no good when checking this assumption.
We have a clear case of heteroscedasticity, and this assumption is not violated.

## Assumption #4

No multicollinearity. This just means that the independent variables are not correlated between themselves. In the case that they are correlated, this indicates that more than one variable explains the same information from the raw data, which can cause problems in modeling the data.

One way to check for multicollinearity is using the Variance Inflation Factor, or just VIF.

```python
from statsmodels.stats.outliers_influence import variance_inflation_factor
{X.columns[i]: variance_inflation_factor(X.values, i) for i in range(1, X.shape[1])}
```
![image](/assets/images/blogimages/figs-10-25/FIGURE7.png)

Okay, but how to interpret the mysterious numbers above? First, recall that VIFs start from 1 and go to infinity (well, there is no upper limit). The lower the VIF, the better, since it means there is lower multicollinearity or correlation between the variables. Generally speaking, a VIF greater than 6 can cause trouble.

In our selected independent variables, however, the VIFs are pretty close to 1, so there are no problems with multicollinearity here.

## Assumption #5

Assumption 5 is that the model uses all important independent variables that explain the dependent variable. In this case, we are trying to predict alcohol levels using information about citric acid, residual sugar, and quality, which are intuitively and logically not enough to predict alcohol levels. In reality, we might have good reasons do doubt there is any correlation between some of these variables and the response in the first place.

In this dataset, we have other variables that could be incorporated to the model in order to predict alcohol levels, including perhaps total sulfur dioxide or even sulphates. Of course, we can also think of many other explanatory variables to add to this model, including brand or age of the wine, for example.

## Assumption #6

Our last assumption is independence, or all observations are not correlated with each other. We can say that this assumption has little to do with our modeling or anything observable in the data, but it's mostly about data collection.

The most classic example of independent variables are randomly assigned or collected observations, like in experimental studies where each different treatment can be randomly assigned.

In the present case, we have no information on how the data was collected, and therefore, we cannot infer that this assumption was satisfied.

## Comment below!

And that's it! We just went through the process of verifying assumptions for linear regressions. Please comment below on other ways we can check these assumptions or ways we can deal with the data when you notice of the assumptions are violated. And remember, it is important to verify assumptions every time we are dealing with parametric models, like the linear regression, in order to draw inferences and fit a good model.
