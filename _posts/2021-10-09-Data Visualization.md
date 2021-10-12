---
title: How to be a Data Viz Rockstar 
layout: post
author: amanwebb
post-image: ![Title image](https://github.com/amanwebb/stat426-fall2021.github.io/blob/cfc5ab2120ed1d86fb5808d1d13e8c660294d01e/assets/images/blogimages/figs-10-09/Title%20Image.jpg)
description: A post that teaches all, beginners and professionals alike, how to be an expert in data visualization. It will teach you about charts and graphs. How to make them look pretty and presentable. 
tags: 
  visualization
  python
  matplotlib
  graphs
---


# How to be a Data Viz Rockstar

So you want to be a data visualiztion rockstar? Well, you came to the right place! Here you will find out everyting you need to knwo about how to be a pro. 

Here, you will learn about what data visualization is, how to create amazing charts and graphs, and what the best practices are. Essentially, you will learn everything you need to know to impress your boss and get a raise (don't quote me on that...)

---

## So what the heck is data visualization?!?

Data visualization is extremely critical to a data scientist's job. Essentially, it is a way to make your analyses clearer and easier to understand. It is very beneficial for non-statisticians, for it helps them see what you see in the data. As the old adage states: A picture is worth a thousand words. A person with little to no knowledge in statistics or data analysis will not necessarily be able to understand your code, tests, or analyses; however, they might be able to understand a picture or a chart. Data visualization is important to be able to present your final results in a clear, concise, and compelling manner to your often non-technical audience. 

There are multiple ways to go about visualizing your data. One of the easiest ways is to use a popular Python library called Matplotlib. This library package allows you to easily and creatively show your data in a fun and presentable way. 

## Plots, Charts, and Graphs

So, what are all the ways you can visualize your data? You can use: scatter plots, line plots, histograms, and box plots, just to name a few. The type of visualization you use really depends on your data. Is your data quantitative? Qualitative? Categorical? Continuous? There are a few things to consider when deciding on the best graph to use. 

![Line Chart](https://github.com/amanwebb/stat426-fall2021.github.io/raw/cfc5ab2120ed1d86fb5808d1d13e8c660294d01e/assets/images/blogimages/figs-10-09/Lots%20of%20charts.png)

Let's take a look at a few of these different charts, and the code used to produce them. To start, we should add the matplotlib library with the following code: 

```python
import matplotlib.pyplot as plt
```

You can add this at the top of your code. We are importing it using the alias 'plt'. We will call this library later by using the alias. 

## Line Chart

First, we will start with something simple - line charts. We will just put random numbers in as our data points. Below you will find the syntax you need. It should be noted that you only have to import the library once. I will show it again, that way you can see how it looks all together. 

```python
from matplotlib import pyplot as plt
plt.plot([1,2,3],[1,2,3])
plt.show()
```

![Line Chart](https://github.com/amanwebb/stat426-fall2021.github.io/raw/cfc5ab2120ed1d86fb5808d1d13e8c660294d01e/assets/images/blogimages/figs-10-09/Graph%201.png)


You can easily add a title, labels, colors, legends, etc. You just use the alias followed by what you want to add. This is similar to all the charts and graphs, so we will just show this once. 
```python
# lines
plt.plot([1,2,3],[1,2,3], label = 'Line 1', color = 'g')
plt.plot([1,2,3],[2,3,4], label = 'Line 2', color = 'blue')
plt.plot([1,2,3],[3,4,5], label = 'Line 3', color = '#ff0000')
# labels
plt.xlabel('X axis')
plt.ylabel('Y axis')       
# title
plt.title('Title')       
# legend
plt.legend()       
# show the plot
plt.show()
```
![Line Chart 2](https://github.com/amanwebb/stat426-fall2021.github.io/raw/cfc5ab2120ed1d86fb5808d1d13e8c660294d01e/assets/images/blogimages/figs-10-09/Graph%202.png)

## Scatter Plots

Next, let's work with scatter plots. Scatter plots are a great way to show relationships between multiple variables, typically numeric variables. These plots are a wonderful way to see patterns in the data. You can assign the variables to color, size, shape. All of which help you see the relationships between the variables. 
```python
x = [5,7,8,7,2,17,2,9,4,11,12,9,6]
y = [99,86,87,88,111,86,103,87,94,78,77,85,86]
plt.scatter(x, y, marker='x');
```
![Scatter Plot](https://github.com/amanwebb/stat426-fall2021.github.io/raw/cfc5ab2120ed1d86fb5808d1d13e8c660294d01e/assets/images/blogimages/figs-10-09/Graph%203.png)

## Histograms

Histograms are very useful for viewing the distribution of data points. Each bar represents the frequency of smaples for each category. We can identify what type of distribution is being followed, and perform the correct tests and analyses. 

As you can probably see, the plots follow very similar code. The syntax is essentially the same, just with a few minor tweaks. The main difference is at the beginning when you pick what type of graph you want - plt.(insert type of graph).
```python
myList = [1,2,2,3,3,3,4,4,4,4,4,5,5,5,5,5,5,5,5,6,6,6,6,6,6,6,6,6,7,7,7,7,7,8,8,8,9,9,10]
plt.hist(myList)

plt.title('Dummy Data to Demonstrate Histograms')
plt.xlabel('variable X')
plt.ylabel('count')
plt.show()
```
![Histogram](https://github.com/amanwebb/stat426-fall2021.github.io/raw/cfc5ab2120ed1d86fb5808d1d13e8c660294d01e/assets/images/blogimages/figs-10-09/Graph%204.png)

You can also add text to your visualization. Such text could include a description of what the chart is showing. It could be the mean or standard deviation. And this is all very simple and easy to do. It is just one line of code (text = ''). This will be easier to understand in the context of the code below. 
```python
myList = [1,2,2,3,3,3,4,4,4,4,4,5,5,5,5,5,5,5,5,6,6,6,6,6,6,6,6,6,7,7,7,7,7,8,8,8,9,9,10]
plt.hist(myList)

text = 'This is an example of text' + '\n'
text += 'you can add.' + '\n'
# plt.text(horizontal position, vertical position, text)
# vertical and horizontal positions are percents on decimal form from 0 to 1
# vertical=0 starts at the far left; higher numbers push the text right
# horizontal=0 starts at the bottom; higher  numbers push the text up 
plt.text(0.6, 0.7, text, fontsize=10, transform=plt.gcf().transFigure)
plt.title('Dummy Data to Demonstrate Histograms')
plt.xlabel('variable X')
plt.ylabel('count')
plt.show()
```
![Histogram 2](https://github.com/amanwebb/stat426-fall2021.github.io/raw/cfc5ab2120ed1d86fb5808d1d13e8c660294d01e/assets/images/blogimages/figs-10-09/Graph%205.png)

## Box Plots

Box plots are great for getting more information about the variables than you can get from histograms. More information such as standard deviation, median, mean, and outliers. Box plots are a fantastic way of seeing the statistics within your data. The bottom and top of the solid-lined box are always the first and third quartiles (i.e 25% and 75% of the data), and the band inside the box is always the second quartile (the median). The whiskers (i.e the dashed lines with the bars on the end) extend from the box to show the range of the data.
```python
# This first section just helps us create some random data
np.random.seed(562201)
all_data = [np.random.normal(0, std, size=100) for std in range(1, 4)]
labels = ['x1', 'x2', 'x3']

#MultipleBoxplot
plt.boxplot(all_data, vert=True, patch_artist=True, labels=labels) 
plt.ylabel('observed value')
plt.title('Multiple Box Plot : Vertical Version')
plt.show()
```

![Boxplots](https://github.com/amanwebb/stat426-fall2021.github.io/raw/cfc5ab2120ed1d86fb5808d1d13e8c660294d01e/assets/images/blogimages/figs-10-09/Graph%206.png)

## Conclusion
Data visualization is a key aspect of statistics and analytics. It is clear that the field is rich in potential applications. Data visualization can get very detailed and complicated, but it can also be simple and easy. We briefly went over the basics here, but you can always go out and learn more yourself. There are tons of things to learn, and the field of data visualization is constantly growing and expanding. 

Some key things to remember are: 
  - You have to import matplotlib.pyplot
  - The type of chart you want to use is specified in the beginning of the code
  - Titles and labels are very important in data visualization

Now go out there and create some amazing graphics and visualizations! Don't forget to come back and share what you have done or comment things you have learned. 


