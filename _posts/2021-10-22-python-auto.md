---
title: Automating a Python Script on a Mac
layout: post
author: rexxmoss
post-image: /assets/images/blogimages/figs-10-22/clock.jpeg
description: How to take a python script and have it run automatically on a scheduled interval.
tags:
- crontab
- pandas
- terminal
- mac
---
Automating a python script to run on a certain interval can be extremely convenient and useful. When working with dynaimc data, automating a script can be especially convenient in order to keep up with a constant influx of new data. It can save lots of time as well, so that you don't have to manually run your script each time you want it to be ran. No matter what your python script does, you can automate it - and that's pretty awesome. There are multiple ways to automate a python script to run on a specified schedule, and some may be better than others. I do not claim to be an expert about any of these ways, but I can show you one way to automate a python script. This post is for Mac users, unfortunately I will not be covering the different nuances for Windows users. I will essentially be covering the three steps necessary to automating/scheduling a python script. These steps are not limited to python files, but that will be the example I am using. The following steps can be summed up as:

1. Write a python script.
2. Make the script executable.
3. Automate/schedule the script to run.


# Let's get started!
 
## 1
First up, you need a python script that you want to run. The example I am using is a python script that is pulling COVID data from an API, converting the data into a pandas dataframe, and saving the data to a csv. Obviously there is much more you can do than just save a csv. Your script can send an email, populate a database, update a dashboard, etc. This is just a simple example, the focus of this post is meant to be on the automation of the script and not on the script itself. My code is fairly simple, but don't worry too much about all the specifics of the code, I will comment next to the relevant lines.

![image](/assets/images/blogimages/figs-10-22/pyscript.png)

As you can see from the comments in my code, there are a few important things to notice. First off is setting the path where you want the file to be downloaded. If you forget this step, it might take you a second to find where the output of your file was downloaded. In order to stay organized, I have set the file path so that I know where to find the output from my script. Additionally, getting the timestamp is really helpful. Because I add the timestamp to the name of my file, I will be able to discern when a specific file was output from my python script. Lastly, saving my data to a csv is essentially my end deliverable. I could have saved it in a different format,or perhaps emailed the data somewhere or uploaded it elsewhere, there are several possibilites as I mentioned earlier. In this case, I wanted to donwload a file each time the script ran so I could be extra sure that the automation of the file was working correctly. 

## 2
Now that I have my python script, it's time to automate it. To do this, I first need to make my script executable. Follow the steps below to do this.

1. Open the terminal and run pip install pyinstaller. This will install PyInstaller.
2. Inside the terminal, navigate to the directory where your script is located.
3. Once you‘re in the path where your script is located, run the following 'pyinstaller --onefile example.py' in the terminal to make the script executable.
4. You should see a message that includes "completed successfully." Then in the directory where your script is located, you should see a folder named "dist". Click inside that folder and you will find the executable. You'll need to know the path to this executable, so keep this in mind for later.

## 3
Okay now your python script is executable - hooray! Next up, we are going to automate this script to run at a specified interval by using crontab.

1. Open the terminal and run crontab -e.
2. Press 'i' to activate the INSERT mode.
3. Use https://crontab.guru/ to write how often you want the script to run.
(example: '* * * * *' would make the script run every minute)
4. After you specify when the script will run, press SPACE, put the path to the executable you just created, press SPACE again, and put the path to your script.
(example: * * * * * /path/to/my/executable /path/to/my/script)
5. Press esc. and then type :wq to save and exit (w - write, q - quit) and then press enter.

To make sure that the crontab was created, type 'crontab -l' in the terminal and you should see it. To edit the crontab, type 'crontab -e'. To remove the crontab, type 'crontab -r'.

## Congrats, you just automated your python script!
As I mentioned, this is not the only way to automate a script, but it is one simple and effective way that I have found. I hope this post was helpful in some way and that you learned something new!

### A few things to know: 
- If you have don't have the right permissions, you need to give full disk access. Click System Preferences, Security and Privacy, Privacy, and Full Disk Access and then grant access.
- If for whatever reason your crontab is not working, you can type 'mail' in the terminal and then press enter to see potential error messages.