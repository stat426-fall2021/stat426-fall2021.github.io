---
title: Automating a Python Script on a Mac
layout: post
author: rexxmoss
post-image: 
description: Automating a Python Script on a Mac
tags:
- crontab
- pandas
- terminal
- mac
---

# Automating a Python Script on a Mac
### First up, you need a python script that you want to run. Mine is pulling COVID data from an API. Don't worry too much about all the specifics of the code, I will comment next to the relevant lines.

### post image here

### Now that I have my python script, it's time to automate it. To do this, I first need to make my script executable. Follow the steps below to do this.
1. Open the terminal and run pip install pyinstaller. This will install PyInstaller.
2. Inside the terminal, navigate to the directory where your script is located.
3. Once you‘re in the path where your script is located, run the following 'pyinstaller --onefile example.py' in the terminal to make the script executable.
4. You should see a message that includes "completed successfully." Then in the directory where your script is located, you should see a folder named "dist". Click inside that folder and you will find the executable. You'll need to know the path to this executable, so keep this in mind for later.

### Okay now your python script is executable - hooray! Next up, we are going to automate this script to run at a specified interval by using crontab.

1. Open the terminal and run crontab -e.
2. Press 'i' to activate the INSERT mode.
3. Use crontab.guru to write how often you want the script to run.
(example: '* * * * *' would make the script run every minute)
4. After you specify when the script will run, press SPACE, put the path to the executable you just created, press SPACE again, and put the path to your script.
(example: * * * * * /path/to/my/executable /path/to/my/script)
5. Press esc. and then type :wq to save and exit (w - write, q - quit) and then press enter.

To make sure that the crontab was created, type 'crontab -l' in the terminal and you should see it. To edit the crontab, type 'crontab -e'. To remove the crontab, type 'crontab -r'.

## Congrats, you just automated your python script!

### A few things to know: 
### - If you have don't have the right permissions, you need to give full disk access. Click System Preferences, Security and Privacy, Privacy, and Full Disk Access and then grant access.
### - If for whatever reason your crontab is not working, you can type 'mail' in the terminal and then press enter to see potential error messages.