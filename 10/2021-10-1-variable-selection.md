---
title: Variable Selection Models
layout: blog
author: emliu
post-image: '/linearcars.png'
description: Summary of commonly used variable selection models used in linear regression such as best subsets model, backward, and sequential replacement
tags:
- linear regression
- sklearn
- matplotlib
---

## Let's begin
Linear regression models are one of the most basic and stastistical predictive modeling methods because of their simplicity and interpretability. They are extremely useful in quantifying how one variable can impact an outcome variable as well as how multiple variables may interact with one another. R is one of the most common coding languages to perform these types of statistical analyses. However, there are other languages that you can use to perform linear regression models. This article specifically discusses how to perform a simple linear regression model in Python compared to R for all you Python users out there! We use a simple dataset about vehicle speeds (mph) and stopping distances (ft) to illustrate this process. This article includes both R code and Python code to compare syntax and reinforce knowledge of how to perform linear regression models. Let's get started.

## Car speeds and stopping Distances
An important factor in determining appropriate speed limits is the amount of distance that is required to stop at a given speed. For example, in residential neighborhoods, it is important to be able to stop in a short distance to ensure pedestrain safety because people are commonly found on the streets. Therefore, the purpose of this analysis is to determine what distance is required to stop at a given vehicle speed. With this knowledge, public officials can determine area speed limits and make better traffic control decisions.

Let's read in the data.

In R, this can be done with the ```read.csv``` function.

````md
```{r}
stop <- read.csv("StoppingDistance.txt", sep = " ", header = TRUE, stringsAsFactors = FALSE)
```
````
In Python however, it is common to use the ```pandas``` library in order to read in the data. The ```pandas``` library is a library commonly used for for data manipulation and analysis in Python. It allows users to manipulate data frames and structures easily and efficiently. More information about the ```pandas``` library can be found at https://pandas.pydata.org/. Let's import the ```pandas``` library and read in the data set.

````md
```{python}
# import pandas library
import pandas as pd

# read in data set
stop = pd.read_csv("StoppingDistance.txt", sep = " ")
stop.head()
```
````

![Stop head - python](SpeedDist.png)
![Stop head - python](/assets/images/blogimages/figs-mm-dd/file.png)

Next, we want to perform some exploratory data analysis (EDA) to better understand our data. In R, it is common to use ```ggplot``` or R-base plotting packages to create EDA graphs. In python, we can also create the same things using the ```matplotlib``` package. Let's compare the two languages.

```{r}
stop_plot <- ggplot(data = stop, mapping = aes(x = Speed, y = Distance)) +
  geom_point() +
  theme_bw() +
  theme(aspect.ratio = 1) +
  scale_x_continuous(limits = c(0, 40)) +
  scale_y_continuous(limits = c(0, 150))
```

```{python}
# create scatterplot of speed and distance variable
plt.scatter(stop["Speed"], stop["Distance"])
```
![Scatterplot - python](pythonscatter.png)
![Scatterplot - python](/assets/images/blogimages/figs-mm-dd/file.png)

We see that speed and distance have a linear relationship. This encourages us to run a linear regression model since we see that these variables are linearly related. Now let us run a linear regression model. We run the model in R and we run the model in Python. 

```{r}
stop_lm <- lm(Distance ~ Speed, data = stop)
```

```{python}
# import sklearn package and linear_model library
from sklearn import linear_model

# save variables as x and y variables
x = stop[["Speed"]]
y = stop["Distance"]

# fit linear regression model 
lm_model = lm.LinearRegression(fit_intercept = True)
lm_model.fit(x, y)
```

Notice the difference in syntax between R and Python. Also note that although the ```lm``` function in R is a built in function, we need to import the ```sklearn``` package and ```linear_model``` library in Python because Python does not have these statistical computing capabilities on its own. ```sklearn``` is one of the most useful machine learning libraries for Python and allows users to perform various machine learning and statistical modeling including classification, clustering, regression, and preprocessing. More about this package can be learned at https://scikit-learn.org/stable/.

Great! You have successfully run a simple linear regression model! Let's look at the regression outputs.

```{r}
summary(stop_lm)
```
![R lm output](rlmoutput.png)
![R lm output](/assets/images/blogimages/figs-mm-dd/file.png)

```{python}
# print model intercept and model coefficients
print(lm_model.intercept_)
print(lm_model.coef_)
```
![python lm output](pythonlmoutput.png)
![python lm output](/assets/images/blogimages/figs-mm-dd/file.png)

Notice that another difference between R and Python is that with R, you can get a full summary of the linear model whereas in the ```sklearn``` library, you can only get certain model parameters individually.



### Conclusion
