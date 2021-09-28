---
title: Time Series Analysis
layout: post
author: joshegladwell
post-image: 
description: Time Series Analysis is a way to analyze continuous, fluid data.
tags:
- Modelling
- R
- Python
- Data Science
---

# Time-Series Analysis
Time-Series analysis is a way of analyzing time-series data. The main characteristic of time-series data is that they are collected over time, usually at equal intervals. These data are frequently plotted with time on the x-axis and will track observations for every day, month, quarter, year, or other set unit of time. Some common examples of time-series data include measuring a country’s Gross Domestic Product, deaths by a certain illness, environmental or weather patterns, etc. There are limitations to using this type of data in linear regression because the nature of these data are generally to make inference about the future. Projecting a linear model into the future, however, is extrapolation and is often very unwieldy. That is why we use different kinds of statistical analysis tools for time-series data.

# Interpreting Time-Series Graphs -- Deaths by Pollution
To illustrate some of the things to look for in time-series graphs, we will follow an example with data gathered by Hannah Ritchie and Max Roser on yearly deaths due to air pollution. We will start by taking a look at a basic line plot of the data.

![World Deaths by Pollution](/assets/images/blogimages/figs-09-28/pollutions_plot.png)

As we can see, these data meet the criteria for time-series data. The data are measured over time with the observations evenly separated—being measured once every year. There seems to be a recurring pattern in these data above, as every five years or so the number of deaths drops for a couple years and then comes back up.

# Sources
Hannah Ritchie and Max Roser (2017) - "Air Pollution". Published online at OurWorldInData.org. Retrieved from: 'https://ourworldindata.org/air-pollution' [Online Resource]
