---
title: Selenium - Building Your First Internet Bot
layout: post
author: andrustn
post-image: /assets/images/blogimages/figs-10-2/Title_Picture.png
description: Scrape and Interact with web pages using the Python package Selenium.
tags:
- Python
- Webscraping
- Automation
---

Webscraping in recent years has become a buzzword for technology and innovation. Modern companies often seek employees who are literate in current technological trends, and being well versed in webscraping can make you one of these well-qualified candidates. In Python specifically, there are many packages that  boast impressive webscraping capability. Of these, some of the most popular are packages such as Beautifulsoup and Selenium. In this tutorial, we outline the installation, implementation, and possible use cases of the latter of these two. Consider this your introduction to web automation and building web scraping robots.

Below is a list of links that will be referenced within the post (accumulated here for your convenience).


* [Chrome Webdriver Download](https://sites.google.com/chromium.org/driver/downloads?authuser=0)
* [GDP Data](https://fred.stlouisfed.org/series/GDP)
* [Selenium Documentation](https://www.selenium.dev/documentation/)
* [Sample Code](/assets/images/blogimages/figs-10-2/Selenium.ipynb)

---

# Introduction

Selenium is a Python packaged aimed at browser automation. For those familiar with BeautifulSoup, the gathering information through accessing the HTML of webpages will be very similar. However, Selenium and Beautiful soup access and use this information in slightly different ways. In BeautifulSoup, one often creates a string object that represents the entire HTML content of a webpage. This string is then used to create a BeautifulSoup object which can be parsed to gather information. Selenium, on the other hand, creates an independent instance of the webpage using a webdriver. It opens a separate browser window specifically to access the page, and in this instance can *interact* with the HTML. This allows us to write scripts that can perform searches, click on links, download files, and much more.

# Installation

The first step in getting a working instance of Selenium is installing a webdriver. I chose to use the Chrome webdriver Chromium. This is a development version of Chrome that we can access remotely. From [This Link](https://sites.google.com/chromium.org/driver/downloads?authuser=0) you can download the Chrome webdriver. Once installed, move the 'chromedriver' file to a place where you can find it. We will need to reference this via filepath in our code.
Detailed instructions for installing a webdriver can be found [here](https://blog.testproject.io/2019/07/16/installing-selenium-webdriver-using-python-chrome/).

After the installation if the webdriver, use pip in the command line to install the Selenium package if you don't already have access to it through a distribution like Anaconda.

**( pip3 install selenium )**

After these two items are installed, we are ready to start coding our bot!

# Demonstration

To demonstrate what Selenium can do, I originally intended on making some sort of club penguin account that would walk around and say dumb things, but it turns out it's pretty hard to code a robot to prove that it's not a robot. So instead, I decided to actually try and do something useful and code a program that could scrape the Federal Reserve website for GDP Data.

The URL for the FED website is can be found [here](https://fred.stlouisfed.org/series/GDP).

The first thing we good need to do is import our desired packages into Python.


![screenshot](/assets/images/blogimages/figs-10-2/import_packages.png)

We import the webdriver attribute from Selenium to initialize our driver and open a browser window. We import the Keys attribute to send keys to input instances within the HTML page. We import Select to use for picking from dropdown menus, and we import time to pause our program to allow the web page to load.



![screenshot](/assets/images/blogimages/figs-10-2/initialize_webdriver.png)

We then initialize our PATH variable with file path that points to the driver we downloaded, and initialize our webdriver, specifying that we will be using Chrome. In the second cell featured above, the driver.get() function is what launches the browser. When we pass in a URL to this function and run it, a browser window will be opened that looks like the following:


![screenshot](/assets/images/blogimages/figs-10-2/FED.png)


Notice the bar at the top that says "Chrome is being controlled by automated test software." - Chrome knows that we are using a robot to control it. This means you can run into issues when trying to access certain websites. If the site has blocked access for automated process, you may not be able to access it.

In the newly opened Chrome window, Right click on any element and click inspect.


![screenshot](/assets/images/blogimages/figs-10-2/Inspect.png)


![screenshot](/assets/images/blogimages/figs-10-2/Inspected.png)

This will allow you to access the HTML for the page in question. From clicking inspect on specific elements of the page, the HTML that composes that element will be highlighted on the right. From there, we can reference each HTML element in our Python script to begin automation.

The first task we will do is to change the dates for the data we want to download. Say we want to gather data for the first decade of the 21st century - we will change the start date to '2000-01-01' and the end date to '2010-01-01'.

First, we need to find the HTML reference for the start date input bar. We do this by right clicking on the bar, and clicking inspect again. From there, we find the highlighted HTML code on the right that corresponds to the element we want to interact with. There are a couple ways of referencing this element. We can reference it by ID, by class, by x_path etc. While it's generally considered best practice to reference elements by ID, I chose to do it by xpath (because some elements that I found had non-unique ID's). From the picture below, we can see the process of finding and copying the xpath for the HTML element we want to interact with.


![screenshot](/assets/images/blogimages/figs-10-2/Inspect_element.png)


We then copy that xpath, and reference it using the driver.find_element_by_xpath function from Selenium. You can choose to save this as a variable, or apply functions straight to the reference itself. I chose to save the reference as a variable because I will be sending it multiple commands.



![screenshot](/assets/images/blogimages/figs-10-2/Change_Start.png)


From the code above we can see the process of changing the start date:
1. Click on the input bar
2. Clear the input bar of the default text
3. Send the new text to the input bar
4. Send a return key to confirm changes

This process is then repeated for the end date.


Using the same process as above to find the HTML element, we create a command to open the "Edit Graph" settings. This allows us to change how our data is organized before downloading.


![screenshot](/assets/images/blogimages/figs-10-2/Edit_Graph.png)


Once open, we find the element of the first drop down menu. We then use Selenium's Select command to help us pick an option from the drop down box. We repeat this process, change a couple of settings, then finally close the Edit Graph window.

The final steps of our code consist of much of the same - we find the element we want to interact with in the HMTL, create a reference to that element in Python, then apply the interaction function we want in Selenium. With these steps we click the download button, and select the CSV option.



![screenshot](/assets/images/blogimages/figs-10-2/Final_code.png)


And there we have it! We've created a robot that will open a webpage, transform the data found, and download it as a CSV all by itself. In looking through the code, you may notice a couple instances where "time.sleep()" is called. This just pauses the script during execution to allow the webpage to render fully. If the webpage isn't fully rendered when you try to make a request, you may get an error from Selenium saying the element you are trying to access does not exist. This is not an issue if you run the code line by line, but in making repeatable scripts it may be necessary to manually incorporate some wait time for the page to load.


# Conclusion

This blog post, though brief, should give you at least a small introduction into the automation possible with Selenium. The few functions featured in this demonstration barely scratch the surface of what is possible with web automation through Python. Looking at the above link for Selenium documentation, there are dozens of functions and methods that allow you to interact with web pages. Hopefully this post inspires you to go build a robot of your own - think of a fun project you want to automate and give it a shot!

The example code can be downloaded [here](/assets/images/blogimages/figs-10-2/Selenium.ipynb). (You will need to change the file path to your driver).
