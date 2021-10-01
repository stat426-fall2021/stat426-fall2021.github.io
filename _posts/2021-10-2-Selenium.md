---
title: Selenium - Creating Your First Internet Bot
layout: post
author: Trevor Andrus
post-image: /assets/images/blogimages/figs-10-2/Title_Picture.png
description: Short tutorial about setting up SSH keys for GitHub.
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
* [Sample Code](

---

# Introduction

Selenium is a Python packaged aimed at browser automation. For those familiar with BeautifulSoup, the gathering information through accessing the HTML of webpages will be very similar. However, Selenium and Beautiful soup access and use this information in slightly different ways. In BeautifulSoup, one often creates a string object that represents the entire HTML content of a webpage. This string is then used to create a BeautifulSoup object which can be parsed to gather information. Selenium, on the other hand, creates an independent instance of the webpage using a webdriver. It opens a separate browser window specifically to access the page, and in this instance can *interact* with the HTML. This allows us to write scripts that can perform searches, click on links, download files, and much more. 

# Installation

The first step in getting a working instance of Selenium is installing a webdriver. I chose to use the Chrome webdriver Chromium. This is a development version of Chrome that we can access remotely. From [This Link](https://sites.google.com/chromium.org/driver/downloads?authuser=0) you can download the Chrome webdriver. Once installed, move the 'chromedriver' file to a place where you can find it. We will need to reference this via filepath in our code. 
Detailed instructions for installing a webdriver can be found [here](https://blog.testproject.io/2019/07/16/installing-selenium-webdriver-using-python-chrome/).

After the installation if the webdriver, use pip in the command line to install the Selenium package if you don't already have access to it through a distribution like Anaconda. 

( pip3 install selenium)

After these two items are installed, we are ready to start coding our bot!

# Demonstration

To demonstrate what Selenium can do, I originally intended on making some sort of club penguin account that would walk around and say dumb things, but it turns out it's pretty hard to code a robot to prove that it's not a robot. So instead, I decided to actually try and do something useful and code a program that could scrape the Federal Reserve website for GDP Data. 

The URL for the FED website is can be found [here](https://fred.stlouisfed.org/series/GDP). 

The first thing we good need to do is import our desired packages into Python. 















# Using SSH Key
In GitHub, when cloning repositories, or setting up the remote repository, use SSH instead of HTTP:

![screenshot](/assets/images/blogimages/figs-09-13/github-ssh.png)
