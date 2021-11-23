---
title: What Coding Language Should I Learn?
layout: post
author: nmaustill
post-image: ![Post Image](/assets/images/blogimages/figs-11-17/post_image.jpeg)
description: find out which coding languages are helpful to know and why
tags:
- Python
- Learn to code
- R
- Tableau
- Excel
---

## Intro

I want to be a data analyst, which coding language should I learn? What if I want to be a business analyst, does that make a difference? Can I just learn one language or do I need to be able to write code for multiple platforms? Based on my own experience applying for jobs, there are many different coding languages that people can learn, but not all are used on a regular basis. Here are some of those languages and platforms that might help you get a head start in the world of data.

## Is there one language to rule them all?

The short answer to all of these questions is start with Python. In my experience applying to jobs as well as viewing data and reading articles all over the internet, this seems to be the language that everyone wants to use. Python is extremely versatile due to the fact that it is open source and already has one of the largest databases of packages. If you can't find a package that suits your needs, you can always create your own. Python is also one of the easiest coding languages to learn. Because of that it is the language of choice for many companies, which means you see it in a lot of job descriptions.

Using Python checks all the boxes as far as analyzing data goes. You can read in data from just about anywhere or from any format and convert it to whatever you'd like. You can clean it relatively simply. There are also packages that allow you to run and manipulate statistical models without doing it all from scratch. Then you can predict future values based on the data. Finally, there are also many packages dedicated to data visualization. This final point is key because you have to be able to show people what you have done in a way that is easily readable and readily available. Not every coding language out there has the number of features that Python does when it comes to creating charts and graphs. They range from simple line graphs and scatter plots to pie charts and even multi-dimensional graphs.

Another advantage to learning Python is that it can be used as the backbone for many websites and applications. This isn't something that will interest everyone or even be of use to most people. However, if software engineering or building websites sounds appealing, I would look into this a little bit more. There are design spaces dedicated to building applications and websites using only Python code and it works quite well. In fact, bigger companies like Google, or Meta (once Facebook) use it in some applications like YouTube and Instagram on the backend because it is that powerful and easy to work with.

Example graphs:

![Basic Graph](/assets/images/blogimages/figs-11-17/python_example_3.png)   ![3D Graph](/assets/images/blogimages/figs-11-17/python_example_1.jpg)    ![Color Coded Graph](/assets/images/blogimages/figs-11-17/python_example_2.jpg)

## The next best thing

Python is awesome but that doesn't mean it is the only coding language out there worth looking at. R is the coding language that was built specifically for data analysts. R is the place to be for statistics and numbers. You can do a lot of the same stuff with Python, but R is the specialized language for statisticians and is therefore a little more intuitive for those in a statistics background. Larger datasets are also going to be more better suited for R, especially when using RStudio. R has a very large amount of packages (called libraries in R) which allow you to read, write, manipulate and visualize data with just a few keystrokes in many cases.

Even though R isn't built for creating web applications like Python is, you can use R Shiny for building interactive databases that allow people to do some of the manipulating or graphing with a few clicks in their browser. This is a great option for when the needs of the client are always changing or they need a lot of different graphs more than once.

Here is an example of R code that adds numbers:
```
> x
[1]  2 NA  3  1  4
> sum(x)    # if any element is NA or NaN, result is NA or NaN
[1] NA
> sum(x, na.rm=TRUE)    # this way we can ignore NA and NaN values
[1] 10

```

## The database code

SQL is the structured query language. This language is built for a very specific purpose, which is communicating with, searching in and extracting data from databases. Many databases contain millions of rows of data which means it isn't easy to sort through it all when you're looking for something specific. That's where SQL comes in handy. You can sort through all of that data to pull out just what you need for the project you're working on. One of the other great things about this language is that you can call it inside other languages. For example, you can write Python code to read in and manipulate the data, but you find the correct data by writing your own SQL query. An example is below. There are a few more steps than this, but I am just trying to show you that it is possible to write it inside other languages.

```
import sqlite3
import pandas as pd

#This is the SQL code to select all rows from the factbook dataset
query = "SELECT * FROM factbook;"
sql_connect = sqlite3.connect('factbook.db')
pd.read_sql_query(query,sql_connect)
```

## The data visualization languages

Python and R do pretty well when it comes to data visualization and there are many ways you can show off your data through these two. However, there are some specialized platforms that allow you to get even more out of your graphs. In my experience there are two main platforms that stand out and are asked for often. These are Tableau and Power BI. With these platforms you can take data visualization to a whole new level. Tableau is built for the ease of use when you try and show off a dataset for a presentation. Power BI is a little more specialized because it allows other people to go in and pull the reports that you have written up for just one department or date range depending on the needs of that specific person.

According to what I have seen, these platforms aren't always something that companies care to see that you have experience in, but for those that generally work with clients and need to show their work to others that don't know the data side of things this is a popular way to go.

Example of what Tableau can do:

![Tableau](/assets/images/blogimages/figs-11-17/tableau_example.png)

Example of Power BI:

![Power BI](/assets/images/blogimages/figs-11-17/powerbi_example.jpg)

## The one you didn't expect

The final language I recommend you look into is Excel. I know what you're thinking, "This isn't a coding language. I can't do any of the bigger picture stuff with Excel.". In general, you would be right, but there are many cases where this is very important. Excel usually just displays data in columns and rows for you to be able to see it all in one place, but there is a background language in there called VBA (Visual Basic for Applications). This is where you can write code to manipulate the cells and data in the worksheets to be what you need. Using Excel isn't something that would be used all the time, but many companies that store data in Excel spreadsheets would require you to know more advanced techniques in Excel.

VBA allows you to pull in data from databases using SQL as well as Microsoft Access, among others. Then you use VBA to write code that manipulates that data into something that everyone viewing the worksheet can utilize in their day to day work. You can write code to create graphs, fill in the blanks, sort and filter data based on user input, add on to the data based on user input and check that it's valid, and so much more. The best part is that you can write this code and someone who knows nothing about Excel can go in, hit a button or start typing and everything you wrote in VBA starts up and allows them to do everything they need.

A lot about coding in Excel VBA isn't about modeling data or even data visualization (although it could be), it's about making sure everyone else that uses this same spreadsheet can input correct data and then press a button (or do nothing) and have everything get sorted, cleaned, manipulated, and even graphed exactly how they need it without ever having to learn to code themselves. This is the best suited for a business analyst because the end user would be within the company.

Here is an example of VBA where the user hits the button 'Roll' and the code runs in order to randomize the letters on the game board:

![Excel VBA](/assets/images/blogimages/figs-11-17/excel_vba_example.jpg)

## Conclusion

The list I have here isn't a perfect list of coding languages that everyone should learn. Out there in the real world, there are many other languages and platforms that you could learn in order to help out a company in your role as an analyst. I have found that these ones often come up in job applications as popular choices for companies to work with. There isn't just one language to rule them all because they all have their strengths. If you are just starting out, I would say start exploring Python because that is the most versatile and generally the easiest. If you are more advanced and have specific needs based on your interests or current job, look into something like Tableau for data visualization or Excel to help others handle their data needs. Regardless of where you are in your education though, more languages exist to help you accomplish the goals of your company or client so don't stop at these 6, keep learning and find the one(s) that fit your needs the best.

### Learn More

Python: (https://www.python.org/doc/essays/blurb/)

R: (https://www.r-project.org/)

SQL: (https://www.w3schools.com/sql/sql_intro.asp)

Tableau: (https://www.tableau.com)

Power BI: (https://powerbi.microsoft.com/en-us/)

Excel VBA: (https://docs.microsoft.com/en-us/office/vba/library-reference/concepts/getting-started-with-vba-in-office)
