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
To start, we are going to go over what is possible with simply using the pandas library. Reading in an Excel sheet is quite similar to reading in a .csv file. A unique difference is the ability to specify a sheet name for workbooks that have more than just one sheet. Using the below syntax, the Excel sheet is read in as a pandas DataFrame that can easily be used for feature engineering and further analysis.

![open](/assets/images/blogimages/figs-10-19/image1.png)

Writing a DataFrame into an Excel workbook can also be done. I find this quite helpful for when your intended audience will want to see the cleaned up version of your data, or if you plan to use Excel to add color and formatting. Below is an example of how this is done. Once again, the arguments for the to_excel() function are unique in the fact they cater to things only found in Excel. For example, you are able to specify the sheet name, as well as on which row or column you would like your data to begin placing information.

![open](/assets/images/blogimages/figs-10-19/image3.png)
![open](/assets/images/blogimages/figs-10-19/image4.png)

These functions are found simply in the pandas library and are quite valuable. However, using the openpyxl library will enable you to go a little bit further. There is a plethora of ways to use it, but today I want to go over the three main functions needed to get started. The first is loading an existing Excel workbook into python as a Workbook object.

After importing Workbook and load_workbook from the library, and having an existing Workbook in a callable directory, we are good to get started. Using load_workbook(‘file_path’) allows us to call an Excel Workbook.

![open](/assets/images/blogimages/figs-10-19/image5.png)

As seen above, workbook object types have a several unique aspects. First, they can have multiple sheets, which needs to be called in order to access their data. In addition, you can specify certain cells by referencing their location in Excel fashion, or also by specifying the row and column. Just be sure to add .value to the end in order to actually access the value within the cell.

Cell values can also be changed while in Python. Just make sure you specify .value！

![open](/assets/images/blogimages/figs-10-19/image65.png)

Saving your python code by itself does not save the changes you have made in the Excel workbook. To do this, you can simply call the .save('file_name.xlsx') off of the workbook object. Keep in mind, the file needs to be closed to both load and save it.

![open](/assets/images/blogimages/figs-10-19/image7.png)

You can also initialize a new workbook in python by calling Workbook(), as seen below. Know that it automatically starts with one sheet, but you can create more if you want. By default, it adds new sheets to the end, but this can be changed in the .create_sheet() syntax. Check out my example below.

![open](/assets/images/blogimages/figs-10-19/image8.png)

You can loop both through the Worksheets, and through the cells. Personally I think this is a super powerful tool, because it is something that is quite difficult to pull off in Excel, but rather straightforward in Python.

![open](/assets/images/blogimages/figs-10-19/image9.png)

Again, your workbook only exists in Python until you use the .save() function to create a .xlsx file on your computer.

![open](/assets/images/blogimages/figs-10-19/image91.png)

In a world that loves Microsoft Office, having the ability to perform Python level analysis on Excel files is a must for any data scientist. I hope that my quick tutorial helps get you started. Keep in mind, the openpyxl library has a lot more to offer, as I really only scratched the surface. Good luck!
