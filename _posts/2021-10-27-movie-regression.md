---
title: Oh, you're a Stats major? What're you going to do with that?
layout: post
author: bradenwellman
post-image: "https://raw.githubusercontent.com/thedevslot/WhatATheme/master/assets/images/SamplePost.png?token=AHMQUEPC4IFADOF5VG4QVN26Z64GG"
description: A personal, real world example of a Statistician's work. 
tags:
- Introduction
- Data Science
- Personal Project
---

# Stat 101
Maybe I’m biased - considering I’m a statistics major - but it feels like other university majors are far easier to talk about colloquially. Marketing, psychology, accounting; even though most of us don’t have domain knowledge in these fields, it’s easy to conceptualize what a 9 to 5 might look like for them. If you’re unfamiliar with the discipline of Statistics, though, it’s hard to imagine why anyone would go into it. “What do you do as a statistician? You just do... Statistics?” There isn’t a great elevator pitch for the degree - which is why I want to illustrate, in layman's terms, some of the practical applications of the major using real world examples.
  
![sports](https://user-images.githubusercontent.com/81715243/139620094-0206024f-6f4b-453b-8032-ffedc5a30fbc.jpg)

The easiest statistics-related application for individuals to understand is usually sports. It’s relevant, there’s numbers for everything, and they’re all *highly* interpretable; the best players usually score the most points and the bad teams have losing records. If you’re in a sports argument it’s really easy to point to X, Y and Z statistics to prove your point. Although I love sports stats like this, they are really just a rudimentary “Stat 101” implementation of the field. I mean, we all learned about means, medians and modes in the third grade - it seems pretty asinine to build an entire discipline around it… So what else can statisticians do?
  
One of the most common methods of statistical analysis used in the field is called “regression.” It’s a term most have probably heard, at least tangentially, even if they couldn’t tell you what it means. Regression analysis, simply put, is a set of statistical processes used to examine the relationship between two different things (often called variables). Simple examples would be “how much you eat and how much you weigh,” “smoking and heart disease” or “socio-economic inequality and murder rates.” 
 
Regression is an umbrella term with a lot of complexity underneath the hood. There are different types of regression (logistic, non-linear, multiple, Bayesian) and different “assumptions” that need to be met before it can be performed (the data needs to be formatted a certain way).  All of that is beyond the scope of this post, though. Instead I’m going to try and concretize the abstract by giving an easily digestible example of two different types of regression; namely “simple linear regression” and “multiple linear regression”.

# A Personal Example
There are a million datasets I could use to illustrate regression; the most common datasets used in Stats classes are usually things like “weight of car V. miles per gallon” or “sepal length V. pedal width” in flowers. How about something a little bit more interesting that hits closer to home though? For a little over 2 years now, everytime my roommates and I have watched a movie or television show we’ve given it a score out of 100. Then I’ve gone in and scraped other information about it on the internet: IMDB score, Rotten Tomatoes score, Audience score, what it’s rated, box office numbers, genre etc… The dataset looks like this. 

![Dataset](https://user-images.githubusercontent.com/81715243/139620118-91a8c0f0-a33c-4d44-833d-11be8b9e0b83.png)

Simple linear regression looks at the relationship between only 2 variables. In this case, we could examine how the score given to a film by Rotten Tomatoes is correlated with the score that I (Braden) have given to the same film. Before doing any sort of complex analysis to see if there is a statistically significant relationship, we can use the humble scatterplot to graphically examine the association. 
  
  ![scatter](https://user-images.githubusercontent.com/81715243/139620146-7c08f0bf-2976-4ac6-8fc2-e5c543bfda70.png)

Even without the blue line to cue your eye to the relationship it would still be intuitively clear that there is a loose, positive linear relationship between “Rotten Tomatoes Score” and “Braden’s Score”. In other words, the higher a movie scores on Rotten Tomatoes, the more likely that same movie (generally) is to score higher in Braden’s score. 
  
# Beyond Graphics
Of course, statisticians have tools to prove the relationship mathematically instead of just relying on graphs or instinct. For example, the coefficient estimation of the Rotten Tomatoes variable is .33214. In other words, on average, for every one point increase in Rotten Tomatoes score, Braden’s score increases by .33214. The p-value for this relationship is .000863 - which is the probability we would observe this data if there really was no relationship between the two variables. In other words, it’s very, *very* unlikely the positive correlation does not exist. Finally the adjusted r-squared for this model is .1344 - which means that roughly 13% of why Braden picks a score that he does can be explained by the Rotten Tomatoes score. An example of the code used to ascertain this information, as well as the summary statistics, is shown below.
  
![Code : Summary](https://user-images.githubusercontent.com/81715243/139620213-5d3f9f91-e669-451f-82f2-ebb8c8323f9f.png)
  
All of that is very jargoney; p-values, coefficient estimations and adjusted r-squared values are very domain-specific knowledge. The big picture idea is that we (statisticians) can model a relationship between variables and then use mathematical tools to test whether or not the correlation is actually significant. However, most regression problems are never this simple. If the Rotten Tomatoes score explains 13% of the variance in Braden’s score, that still leaves 87% of the variance unexplained! Most phenomena aren’t explained by just 1 thing so, consequently, we usually need to do a multivariate analysis to make good predictions - which is where “multiple linear regression” comes in. 
  
# Multiple Linear Regression
Going back to the dataset above, you’ll notice that there are more variables than just “Braden” and “Rotten Tomatoes” - there’s IMDB, Audience Score, whether or not it was recommended and other variables. The goal in multiple linear regression is to create a model that maximizes the combination of different variables in order to raise whatever metric we’ve chosen (in this case, r-squared). This should make intuitive sense - with more information, more of the variance in Braden’s score would be explained.  
  
A lengthier process than simple linear regression is done to select which variables are most important in predicting Braden’s score - and then coefficient estimations, p-values and adjusted r-squared values can be calculated. Ultimately, I landed on a model that used whether or not the movie was recommended, IMDB score and audience score to predict Braden’s score. The model achieved an adjusted r-squared of .68611 - meaning nearly 69% of the variance in Braden’s score could be explained by these 3 variables. All had extremely low p-values and positive coefficient estimations. 
  
# In Summary
You can easily imagine how this type of process might scale - with bigger, messier datasets containing hundreds of variables and tens of thousands of observations. Regression isn’t the only weapon statisticians have in their arsenal, oftentimes there are better methods for more complex data, but it’s a good micro example of the macro discipline. Generally, statisticians are simply trying to figure out the story that data is telling, and then communicating it in a meaningful, interesting way. So, next time you run into a Stats major, instead of asking them "What're you going to do with that?" ask them to tell you about the datasets they're working with, and the questions they are trying to answer.
