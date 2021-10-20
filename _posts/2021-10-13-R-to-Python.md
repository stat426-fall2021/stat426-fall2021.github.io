---
title: "Expanding Your Tools as a Data Scientist: Learning Python After R"
layout: post
author: erstewart14
post-image: /assets/images/blogimages/figs-10-13/python_to_r.png
description: Here are some quick tips to streamline your experience in learning Python after R.
tags:
- R
- Python
- Packages
---
## Introduction
In my data science education, I started with learning R to manipulate datasets and create visualizations. There are, however, many different coding languages that can be used to accomplish these tasks. Different companies and people have different preferences as far as coding languages, so it is important to be familiar with many different types of languages. Learning different types of languages can be difficult as it involves learning syntax, packages, and setups.
One of the most popular coding languages for data science is Python. Python is an object-oriented, high level programing language. The purpose of this post is to suggest some different tips for learning Python after R to make for a smoother transition.
## Data Types
The first thing that one needs to understand when learning Python after R is the differences in the data types. Data types are important because they tell the computer how to interpret the value. It ensures that the data will be collected in the preferred format. When your data is reported as a certain datatype it will prevent you from using certain functions unless you change the data type. Due to that it is important to know the different data types, what you can do with them, and how to change them. Both R and Python use predefined datatypes. Python supports the following data types:
1.	Numbers- Python stores numeric values. They can be stored in 4 different data types.
•	Integers- Whole numbers. Python’s integer is the same as R’s integer.
•	Long- long integers that are represented in octa and hexadecimal. In R you have to use the bit64 packages to read hexadecimal values.
•	Complex- Complex numbers like i. They are the same in both R and Python.
•	Float- Decimal values. Unlike in Python, R uses the numeric data type.
2.	Boolean- Stores true and false values. The difference between R and Python in this data type is that in R the Boolean values are store in all capital characters, TRUE and FALSE, and in Python the first character in capital and the rest are lower case, True and False. In R Boolean values can be stored in factor or character data types.
3.	Lists- They can be used to store strings, Boolean, integers, and etc. Lists are the same in R and Python.
4.	Strings- As mentioned above strings can be store in list. Strings themselves store character data. This would be the same as R’s character data type.
5.	Tuples- These do not exist in R but they would be like a R vector whose values would be immutable.
6.	Dictionary- Has a two-dimensional structure that has a key and value pair.
## Packages
Another helpful thing to know when transitioning from Python after learning R would be to know what packages help to preform data manipulation and machine learning. This allows you to use python like you would R. Some of the helpful packages are:
1.	Scikit Learn- This package allows you to preform machine learning algorithms. This package contains all the functions that you would need to build a model.
2.	Numpy- This allows you to preform numerical computing in python. With numpy you can preform things like linear algebra, statistics etc. In the documentation you can see the different functions that you can see and their options.
3.	Pandas- In R you can use libraries like dplyr to preform data manipulation. In Python you would use Pandas. Pandas allows you to make data frames and then manipulate them. You can tidy your data set and determine what data you want to use to do calculations and make visualizations.
4.	Matplotlib- I remember when I was first learning R the first thing we were taught was how to make plots using the library ggplot2. In Python you can use Matplotlib. There are also many other packages you can use to preform data visualization so you can experiment with different ones. Some different ones are plotly express and seaborn.
## Why Would You Learn Python?
With so many similarities one might wonder why it would be important to learn Python if they already know R. Some strengths of Python are:
1.	Scrapping Data- Python packages, like Beautiful Soup, make it much simpler to scrape data from the internet.
2.	Text processing- With different packages available in Python it is much easier to process text data. Python is an object-oriented langue that has a clean syntax that helps when working with text data. One such package is regex which allows you to work with regular expressions.
With these helpful tools available in Python, data collection, manipulation and visualization is aided. This is not to say that knowing R is not important, but that knowledge of both tools is helpful when pursuing a career in Data Science.
## Conclusion
In conclusion, there are many different programming languages that you can use in data science. Two such languages are Python and R. It can be difficult to learn different languages. If you’re like me and trying to learn Python as your second language after R there are some important things to know before starting. It is important to know how data types differ in the two languages and what packages you can use to fo the same things that you would do in R. In the sometimes frustrating process of learning a new language it is also important to remember the strengths of the programming language that will allow you to do things simpler or that you couldn’t do before.  
