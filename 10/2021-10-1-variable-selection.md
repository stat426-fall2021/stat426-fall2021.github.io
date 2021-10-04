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

### Introduction
Introduction
Linear regression models are one of the most basic and stastistical predictive modeling methods because of their simplicity and interpretability. They are extremely useful in quantifying how one variable can impact an outcome variable as well as how multiple variables may interact with one another. These models, however, are not without its own obstacles. One of the most common obstacles that statisticians encounter while fitting linear models is multicolinearity in which explanatory variables are linearly related thus unsatifying the assumption of variable independence and greatly affecting the final results of a linear model. This blog discusses variable selection models such as best subsets model, backward selection, and sequential which are remedial measures available to fit an effective and reliable linear model. We use an example dataset regarding body fat to illustrate these methods.

First, let's import a few libraries and read in the data:
```
import pandas as pd
from sklearn import linear_model

bodyfat = pd.read_csv("BodyFat.txt", sep = " ")
bodyfat.head()
```

Introduction of dataset
Code
Picture

Introduction of multicolinearity

Linear model does not meet assumptions


### Best subset model
Code


### Backward selection
Code


### Sequential replacement
Code


### Conclusion
