---
title: How to Excel at Microsoft Excel with Python Library openpyxl
layout: post
author:  jhdegn
post-image: /assets/images/blogimages/figs-10-19/titleImage.png
description: Getting started with using Microsoft Excel in Python
tags: 
- Excel
- openpyxl
- Microsoft Office
- spreadsheets
---

For many in the world, Microsoft Excel is the most advanced tool in their toolbox of data analytics. And to be fair, it is an extremely powerful software. You can manipulate data in all sorts of ways, write functions and equations, create insightful graphics, and format data in a way that pleases the eye. However, many times as a data scientist, simply using Excel is not going to cut it. In today’s post, I want to go over some helpful functions that are introduced by using the library openpyxl, as well as some helpful ones found in pandas. We will cover reading in Excel files, writing to Excel files, as well as working in real time with an Excel file.
To start, we are going to go over what is possible with simply using the pandas library. Reading in an Excel sheet is quite similar to reading in a .csv file. A unique difference is the ability to specify a sheet name, for workbooks that have more than just one sheet. Using the below syntax, the Excel sheet is read in as a pandas DataFrame that can easily be used for feature engineering and further analysis.

