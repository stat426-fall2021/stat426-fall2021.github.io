---
title: Variable Selection Models
layout: blog
author: emliu
post-image:
description: Summary of commonly used variable selection models used in linear regression such as best subsets model, backward, and sequential replacement
tags:
- linear regression
- sklearn
- matplotlib
---

## Let's begin
Linear regression models are one of the most basic and stastistical predictive modeling methods because of their simplicity and interpretability. They are extremely useful in quantifying how one variable can impact an outcome variable as well as how multiple variables may interact with one another. R is one of the most common coding languages to perform these types of statistical analyses. However, there are other languages that you can use to perform linear regression models. This article specifically discusses how to perform a simple linear regression model in Python for all you Python users out there! We use a simple dataset about vehicle speeds (mph) and stopping distances (ft) to illustrate this process.

## Car speeds and stopping Distances
The purpose of this analysis is to determine what distance is required to stop at a given vehicle speed. With this knowledge, public officials can determine speed limits and make better traffic control decisions.

There are base R packages that will allow you to compute linear regression models, however, in Python, we need to import certain packages and libraries to perform these types of analyses. The main package that is used is ```sklearn```.

First, let's import a few libraries and read in the data:

```
# import pandas library
import pandas as pd

# read in data set
stop = pd.read_csv("StoppingDistance.txt", sep = " ")
stop.head()
```

(Picture)

Next, we want to perform some exploratory data analysis (EDA) to better understand our data. In R, it is common to use ```ggplot``` or R-base plotting packages to create EDA graphs. In python, we can also create the same things using the ```matplotlib``` package. Let's create a scatterplot.

```
# create scatterplot of speed and distance variable
plt.scatter(stop["Speed"], stop["Distance"])
```

(Picture)

We see that speed and distance have a linear relationship. This encourages us to feel good about running a linear regression model to draw conclusions from this data. Next, let us run a linear regression model. We do this by using the ```sklearn``` package and its ```linear_model``` library.

```
# import sklearn package and linear_model library
from sklearn import linear_model

# save variables as x and y variables
x = stop[["Speed"]]
y = stop["Distance"]

# fit linear regression model 
lm_model = lm.LinearRegression(fit_intercept = True)
lm_model.fit(x, y)
```

Great! You have successfully run a simple linear regression model! Let's look at the intercept and coefficient of the speed variable.

```
# print model intercept and model coefficients
print(lm_model.intercept_)
print(lm_model.coef_)
```











### Conclusion
