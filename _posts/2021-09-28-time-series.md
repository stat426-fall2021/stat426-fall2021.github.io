---
title: Introduction to Time Series Analysis
layout: post
author: joshegladwell
post-image: 
description: Time Series Analysis is a way to analyze continuous, fluid data.
tags:
- Time-Series
- R
- Python
- Data Science
---

# Time-Series Analysis
Time-Series analysis is a way of analyzing time-series data. The main characteristic of time-series data is that they are collected over time, usually at equal intervals. These data are frequently plotted with time on the x-axis and will track observations for every day, month, quarter, year, or other set unit of time. Some common examples of time-series data include measuring a country’s Gross Domestic Product, deaths by a certain illness, environmental or weather patterns, etc. There are limitations to using this type of data in linear regression because the goal of analyzing these data is usually to make inference about the future. Projecting a linear model into the future, however, is extrapolation and is often very unwieldy. That is why we use different kinds of statistical analysis tools for time-series data. In this post, we will not dive deeply into the modelling process of time-series data but we will identify things to look for in exploratory data analysis.

# Plotting
![Air Passengers](/assets/images/blogimages/figs-09-28/passengers.png)

The plot above uses the R dataset AirPassengers. There are several aspects of this time-series data that we can identify before diving into modelling.

## Seasonality
Seasonality is a recurring pattern seen in the data. Seasonal patterns always repeat within units of years. This makes sense, as the patterns are associated with seasons. In the plot of monthly airline passengers above, there is clearly seasonality. The number of passengers peaks every summer as people fly to new destinations for summer vacations, but drops in the winter when the weather gets worse. It’s also worth noting that there is a slight peak around the liminal space between years, probably indicating an increase in travel for the holidays.

## Time Trends
The passenger data above also shows a time trend. A time trend is a pattern of overall change in the data as time increases. In the AirPassengers data, the time trend is positive. More people fly airplanes with time, likely due to improved technology, increased demand, and higher capability to meet that demand through technology. Time trends are very common in time-series data and can give us valuable insight into the nature of the data we are dealing with.

## Mean Reverting Data
Mean reverting data are data that surround a central mean, frequently jumping through the mean. This varies from time trend data in that the trend follows a horizontal line. The plot below shows an example of mean reverting data.

![Accidental Deaths](/assets/images/blogimages/figs-09-28/accdeaths.png)

The time series plot above shows the number of accidental deaths by month in the United States. As you can see, the mean falls just below nine thousand deaths, and the data follow this mean consistently across time. The presence of time trends or time-invariate means can help inform the approach we take in modelling the data.

# Autocorrelation
Autocorrelation is an important factor to consider in analyzing time-series data. Autocorrelation is the correlation of the same features in the same dataset at differing points in time, and it can invalidate ordinary least squares tests and standard errors. The easiest way to detect autocorrelation is to plot residuals against time and look for patterns. If the residuals are randomly distributed, not following any trends, then the data is likely free of autocorrelation. There are also more exhaustive ways of detecting autocorrelation, (for example, the Bruesch-Godfrey Test), if the plot of residuals is difficult to interpret.

# Conclusion
Time-series data can often require difficult solutions for modeling (which will not be covered in this post), but it is important to recognize when we are dealing with time-series data and treat it accordingly.


