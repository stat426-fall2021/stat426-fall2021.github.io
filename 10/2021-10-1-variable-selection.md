---
title: Variable Selection Models
layout: blog
author: emliu
post-image:
description: Summary of commonly used variable selection models used in linear regression such as best subsets model, backward, and sequential replacement
tags:
- Variable selection models
- Multicolinearity
- Best subset
- Backward
- Sequential Replacement
---

## Introduction
Linear regression models are one of the most basic and stastistical predictive modeling methods because of their simplicity and interpretability. They are extremely useful in quantifying how one variable can impact an outcome variable as well as how multiple variables may interact with one another. These models, however, are not without its own obstacles. One of the most common obstacles that statisticians encounter while fitting linear models is multicolinearity in which explanatory variables are linearly related thus unsatifying the assumption of variable independence and greatly affecting the final results of a linear model. This blog discusses variable selection models such as best subsets model, backward selection, and sequential which are remedial measures available to fit an effective and reliable linear model. We use an example dataset regarding body fat to illustrate these methods.

First, let's import a few libraries and read in the data:
```
import pandas as pd
from sklearn import linear_model

bodyfat = pd.read_csv("BodyFat.txt", sep = " ")
bodyfat.head()
```
(Picture)

Brozek is the outcome variable that measures the percentage of body fat found in the 252 men whose various health metrics are found in this dataset. Explanatory variables include the men's ages, weight (lbs),	height (in), and the circumference of the neck (cm), chest (cm), and abdomen (cm).

I will not include the detailed processes of EDA and the checking of linear model assumptions as part of this article, but after going through these processes, we find that there is high multicolinearity found in the model and the assumptions are not met. So what can we do? This is where variable selection models can help.

## Variable Selection Models
Variable selection models help statisticians choose which variables of a dataset would help create the best linear model by recommending which variables to drop and which variables to keep. There are a variety of these methods each with its own benefits and setbacks. Here, we'll discuss three of the most common methods.

### 1. Best subsets
The best subsets variable selection method includes each variable in the linear model one at a time and measures if the accuracy of the model improves or not. If the accuracy of the model improves, then the variable is kept in the model. If the accuracy worsens, the variable is discarded.

Code


### 2. Backward selection
Code


### 3. Sequential replacement
Code


### Conclusion
