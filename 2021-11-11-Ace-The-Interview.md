---
title: Ace Your Data Science Interview
layout: post
author: ashtynfiala
post-image: /assets/images/blogimages/figs-11-11/interview.jpg
description: prepare for your next job interview by brushing up on some popular data science interview questions
tags:
-machine learning
-job search
-algorithms
-interview questions
---
Going into a data science related job interview, you can be sure that they will ask you questions about machine learning. We are going to go over some of the most common questions asked related to machine learning during data science job interviews so **you** can be ready to catch your dream job. 

![you](/assets/images/blogimages/figs-11-11/you1.png)

Machine learning uses artificial intelligence and computer science on data and algorithms to imitate human learning. It automates processes like model building and classifying that originally could only be done with human reasoning. Through machine learning, we can teach algorithms with data to identify patterns and make decisions. 

Machine learning is growingly popular because instead of hard coding to solve problems, we can give the computers the data and let them learn from it. Companies are then able to identity risks or areas for profit or even implement machine learning into the product they are creating. The point is, any business can benefit from machine learning. 

We are going to look over 5 popular machine learning interview questions and talk about how to answer them. 

## 1.	What are different types of machine learning algorithms?

Supervised Learning- generally the model is trained with an input data set until it can correctly predict the output when given the same features it was trained on. 
-	An example of this would be housing prices. A data set might include features relating to when the house was built, how big it is, how many bedrooms it has, and the sale price. The classification method we choose would then identify the patterns of house features compared to their sale prices. In the end, we would hope to come out with a model that could be given data about a house and give you an accurate prediction of its sale price.  
Unsupervised Learning- using unlabeled datasets, these methods will attempt to identify the structure of the data and group it based on its similarities. 
-	An example of unsupervised learning would be inputting images of cities and rural landscapes and letting the machine identify features common to cityscapes and features common to rural landscapes, hopefully then allowing it to receive an image and categorize it correctly as city or rural.

![ML](/assets/images/blogimages/figs-11-11/MLgraphic.jpeg)
[Supervised vs. Unsupervised Learning](https://medium.com/@dkatzman_3920/supervised-vs-unsupervised-learning-and-use-cases-for-each-8b9cc3ebd301)

## 2.	What is ‘Naïve’ about Naïve Bayes?
Naïve bayes is an algorithm used for predictive modeling that falls under the supervised learning category. The part that is naïve is that it assumes that every input variable is independent. Wikipedia gives a good example related to the following: A naïve bayes algorithm could be used to classify emails as spam or not spam. Features might count occurrences of certain words and then the email would be classified as spam or not spam. The algorithm would calculate the probability of it being spam based off the assumption that the occurrence of one word is independent from the occurrence of any other word. 
This algorithm is commonly used with text classification problems or with multi-class prediction. 

## 3.	 How much data should you allocate for your training, validation, and test sets?
A good rule of thumb is 80% in the train dataset and 20% in the test. However, each problem varies so there isn’t an answer that is always correct. You want to optimize for low variance on your model performance statistic and well as low variance on your actual model parameters. 

## 4.	What are the advantages and disadvantages of decision trees?
Pros: Decision trees are easy to interpret, robust to outliers, and have fewer parameters to tune
Cons: More likely to be overfit, meaning a higher variance. 

## 5.	How can we handle outlier values? 
Some tools used to discover outlier values include box plot, z-score, and scatterplots. 
To handle any outliers we find, we can drop those observations from the dataset, impute a different value (ex. the mean), or you could segment them and analyze what insights you might gain from those data points. 

## 6.	What is the ROC Curve and what is AUC?
ROC stands for receiver operating characteristics. The ROC curve is a graph that shows the tradeoff between the true positive rate and the false positive rate. The ROC curve displays how good your model is at distinguishing between classes. The AUC is the area under the ROC curve and will always be between 0 and 1. Siladittya Manna on medium says it well - 

> "AUC score is equal to the probability that a classifier will rank a randomly chosen positive instance higher than a randomly chosen negative one."

![ROC](/assets/images/blogimages/figs-11-11/ROC.png)
[ROC Curve](https://medium.com/@dkatzman_3920/supervised-vs-unsupervised-learning-and-use-cases-for-each-8b9cc3ebd301)

Just as a reminder, the true positive rate (TPR) is when a model correctly predicts a positive class. Think of a covid test: a 1.0 TPR means that every person with active Covid who took a Covid test would get a positive test result. 
The False positive rate (FPR) measures how often the model incorrectly classifies a negative as a positive. This would be like a Covid test coming back positive when the person does not actually have covid. 
The goal for any model is to correctly classify positives as positives and negatives as negatives, so a ROC curve with an AUC close to 1 is a good indicator that your model is performing well. 




![cheer](/assets/images/blogimages/figs-11-11/cheer.png)

These 5 questions don’t even begin to cover the scope of what interviewers might want to pry out of you during an interview, but it’s a good start to thinking about what you might want to freshen up on before heading into your next interview. Either way, be confident in what you do know and try to derive answers from that if a question trips you up. Preparation is key and practicing explaining these concepts to another person is one of the best ways to see how well you really know what you think you know. Thanks for reading and best of luck!


### Sources
-------
Below are the sources used for the interview questions and information used in the answers. 

[IBM Machine Learning](https://pages.github.com/)

[Machine Learning Q&A (Elite Data Science)](https://pages.github.com/)

[Machine Learning Q&A (Interview Bit)](https://pages.github.com/)

[Machine Learning Algorithms](https://pages.github.com/)

[Naive Bayes](https://pages.github.com/)

Image Links:

[Stock Photos](https://unsplash.com/)

[ROC Curve](https://medium.com/@dkatzman_3920/supervised-vs-unsupervised-learning-and-use-cases-for-each-8b9cc3ebd301)

[Supervised vs. Unsupervised Learning](https://medium.com/@dkatzman_3920/supervised-vs-unsupervised-learning-and-use-cases-for-each-8b9cc3ebd301)

