---
layout: post
title: Quick Machine Learning with PyCaret
author: dteuscher1
post-image: '/assets/images/blogimages/figs-11-08/pycaret.png'
description: An overview of the capabilities of PyCaret and how to fit machine learning models quickly using PyCaret.
tags:
- PyCaret
- Machine Learning
- Model Comparison
- Model Fitting
---

## Introduction

When fitting a model for data, it can be a tedious process to fit many different models as you try to figure out which model is best for the data that you have. It is time consuming to code up multiple models and as a result only a few number of models are compared when trying to fit the best model. [PyCaret](https://pycaret.org/) is an open source low-code machine learning library in Python, which can be used to quickly fit many models and reduce the time spent coding and comparing models. 

## Installation

The first thing to do is to install PyCaret. It is highly recommended to use a virtual environment when installing PyCaret to avoid conflicts with other packages. A virtual environment can be created and activated with the following commands:

```
conda create --name yourenvname python=3.8
conda activate yourenvname
```

Once you have created your virtual environment, PyCaret can be install by running the line below:

```
pip install pycaret
```

PyCaret should then be installed as part of your virtual environment. It is recommended to be used in a notebook environment, such as Jupyter Notebook, Google Colab, or Azure Notebooks for example, because of html and interactive widgets that it uses. If you have issues installing PyCaret, you can refer to installation instructions found [here](https://pycaret.readthedocs.io/en/latest/installation.html). 

## Load Data
There are a number of built in datasets that can be used to show the abilities of PyCaret. The Boston housing dataset is available and it provides information about housing in the Boston MA area. The response variable for this dataset is the median value of owner occupied homes. There is a get_data function in PyCaret. The function takes the name of the dataset. 

```
from pycaret.datasets import get_data
boston_full = get_data('boston')
```

A test set is created from the data to be tried on the model for prediction. PyCaret will automatically take the data given and split it into a training set and a validation set. 

```
boston = boston_full.sample(frac=0.9, random_state=786)
boston_unseen = boston_full.drop(boston.index)
boston.reset_index(drop=True, inplace=True)
boston_unseen.reset_index(drop=True, inplace=True)
```

## Set up model

PyCaret can deal with regression or classification problems, as well as clustering, anomaly detection, and natural language processing. The Boston data set is a regression problem, so we import everything from pycaret.regression. It is easy to set up a model with PyCaret. The setup function is used to specify the model for your data, where you specify the dataset you are using and the target variable. There are other options available, but this is the minimum needed to set up the model. When setting up the model, a box will appear and show what variable type PyCaret is assuming from the dataset. 

```
from pycaret.regression import *
reg1 = setup(data = boston, target = 'medv')
```

![Model Input](/assets/images/blogimages/figs-11-08/input.png)

Once finished, there will be a printout that specifies information about the data, such as the response variable, whether there is missing values, what preprocessing steps should be taken and so forth. Any information about the model to be fit can be found in this table. 

## Compare baseline models

One of the best features of PyCaret in my opinion is the ability to fit a bunch of baseline models initially to get an idea of which model is best. A number of models are fit and multiple metrics are fit to determine which baseline model is the best. These baseline models use the default values for tuning parameters. The folds argument specifies the number of folds for cross validation when comparing models.

```
compare_modes(folds = 5)
```

![Model Comparison](/assets/images/blogimages/figs-11-08/modelcomp.png)

## Create a model
After comparing the baseline models, you can choose a model that fits the best so you can tune it. The gradient boosting regressor was the best for the Boston data for five of the six metrics, so I’ll create that one and work to tune the model. Printing out the model will provide the model that is originally created with the hyper parameters values. 

```
gb = create_model('gbr')
print(gb)

GradientBoostingRegressor(alpha=0.9, ccp_alpha=0.0, criterion='friedman_mse', init=None, learning_rate=0.1, loss='ls', max_depth=3,max_features=None, max_leaf_nodes=None, min_impurity_decrease=0.0, min_impurity_split=None, min_samples_leaf=1, min_samples_split=2, min_weight_fraction_leaf=0.0, n_estimators=100, n_iter_no_change=None, presort='deprecated', random_state=2183, subsample=1.0, tol=0.0001, validation_fraction=0.1, verbose=0, warm_start=False)
```

## Tune a model
The hyperparameters of a model can easily be tuned with the tune_model function, which only requires the model previously created. It then outputs the calculated metrics for 10 folds.

```
tuned_gb = tune_model(gb)
print(tuned_gb)

GradientBoostingRegressor(alpha=0.9, ccp_alpha=0.0, criterion='friedman_mse', init=None, learning_rate=0.1, loss='ls', max_depth=4, max_features='log2', max_leaf_nodes=None, min_impurity_decrease=0.0005, min_impurity_split=None, min_samples_leaf=3, min_samples_split=5, min_weight_fraction_leaf=0.0, n_estimators=190, n_iter_no_change=None, presort='deprecated', random_state=2183, subsample=0.45, tol=0.0001, validation_fraction=0.1, verbose=0, warm_start=False)
```

![Tuned Model](/assets/images/blogimages/figs-11-08/tuned.png)

## Model Plots
After the model has been tuned for best performance, you can create some plots to easily visualize results. Some examples of plots are a residuals plot, a prediction error plot, and a feature importance plot. Examples of these plots for the Boston dataset and the gradient boosting regressor are shown below

```
plot_model(tuned_gb)
```

![Residuals](/assets/images/blogimages/figs-11-08/Residuals.png)

```
plot_model(tuned_gb, plot = 'error')
```

![Error](/assets/images/blogimages/figs-11-08/error.png)

```
plot_model(tuned_gb, plot = 'feature')
```

![Feature Importance](/assets/images/blogimages/figs-11-08/feature_import.png)

## Predictions

Once you are satisfied with your tuned model and are ready to fit it and make predictions, you can use the predict_model function to make predictions for your validation set. This will use the validation set that was automatically created when setting up the model. In addition to giving the predictions for each observation, it calculates the six metrics for the validation set and returns those values as well. 
```
validation_preds = predict_model(tuned_gb)
```

![Validation Performance](/assets/images/blogimages/figs-11-08/validation.png)

After testing the model on the validation set, it is helpful to then fit the model using the training and validation sets since it will likely help the performance of the model improve on unseen data. Once again, there is a single function in PyCaret that will do all of this. The finalize_model function will refit the model using the training and validation sets and then it can be applied to additional unseen data.

```
final_gb = finalize_model(tuned_gb)
print(final_gb)

GradientBoostingRegressor(alpha=0.9, ccp_alpha=0.0, criterion='friedman_mse', init=None, learning_rate=0.1, loss='ls', max_depth=4, max_features='log2', max_leaf_nodes=None, min_impurity_decrease=0.0005, min_impurity_split=None min_samples_leaf=3, min_samples_split=5, min_weight_fraction_leaf=0.0, n_estimators=190, n_iter_no_change=None, presort='deprecated', random_state=2183, subsample=0.45, tol=0.0001, validation_fraction=0.1, verbose=0, warm_start=False)
```

Predictions are made using the same function as before, but you supply the predict_model function with the unseen data. The predict_model function returns a data frame of the unseen data with an extra column named Label, which includes the predicted value. The performance of these predictions can be checked with the check_metric function. 

```
from pycaret.utils import check_metric
print(check_metric(unseen_predictions.medv, unseen_predictions.Label, 'RMSE'))
print(check_metric(unseen_predictions.medv, unseen_predictions.Label, ‘R2’))

2.9136
0.8253
```

## Conclusion

In just a few lines of code, we were able to compare a number of baseline models, tune a model, check the performance of the model on a validation set, refit the model with the training and validation set, and make predictions on the test set and produce good predictions. Although it is important to understand how these models work, it can be tedious to code out multiple models when comparing which model might be best for a certain dataset. PyCaret automates a lot of that process and provides additional flexibility as well. There are options to implement preprocessing, such as dealing with missing values, normalization, categorical variable encoding and so forth. There are options for ensemble methods in PyCaret as well. 

With such flexibility, PyCaret seems to be an option that can save a lot of time when fitting a model to data. I will likely look for opportunities to use this to simplify projects that I am working on personally. If you have ever used PyCaret before, feel free to comment about how you used it in your work.

PyCaret has extensive [documentation](https://pycaret.org/guide/) and [tutorials](https://pycaret.readthedocs.io/en/latest/tutorials.html) for various levels, so feel free to dive into their tutorials to get yourself started or to explore additional capabilities of PyCaret that weren’t discussed in this post. 
