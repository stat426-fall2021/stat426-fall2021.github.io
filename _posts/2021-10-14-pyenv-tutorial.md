---
title: "What is Pyenv and Why You Should Use It"
layout: post
author: 18katesmit
post-image: "https://files.realpython.com/media/Getting-Started-With-pyenv_Watermarked.7b1dd55b32a1.jpg"
description: A Brief Intro to Multiple Python Versions with Pyenv
tags:
- python
- python libraries
- virtual environment
- versions
---

When you install Python on your computer, you should constantly update your Python version as new ones come out. Unfortunately, some libraries can become obsolete because they are not supported by the current version making code that once worked a major headache to update. Additionally, if you have ever tried to collaborate with other people in a project, they could have different libraries and python versions making it so you have to spend lots of time updating and debugging something that should be a fix. Fortunately, there is a tool that can help mitigate this, so you always know what python version you're using and what libraries are being used in a project.

# What is Pyenv?

Pyenv is a tool to manage different python versions on your computer for each project. Essentially you can have Python 2.7.15, Python 3.6.8, ect ... what ever you need, all on your computer and create virtual environments in these versions to make your projects run smoothly. In short, pyenv lets you change the global Python version, install multiple Python versions, set project-specific Python versions, and create and manage virtual python environments. Instructions to install pyenv on your computer can be found [here](https://github.com/pyenv/pyenv#installation).


# Pyenv Order

Pyenv organizes your system, global, local, and shell versions and can be thought about in a pyramid.

![pyenv-pyramid](https://files.realpython.com/media/pyenv-pyramid.d2f35a19ded9.png)


* System - this is what is installed on your computer when you download python
* Global - global python version can be changed with `< pyenv global 3.6.8 >`
* Local - this is often project specific python versions
* Shell - for shell specific python versions


Using the command `<pyenv versions>` will Show what versions of python you have installed and will denote your current global version with and asterisk.

This example shows what this could look like in your computer.

[pyenv example](/assets/images/blogimages/figs-10-14/pyen_versions)

You can see that there are several versions of python installed but I am currently working off the system version. Additionally, I have created some virtual environments for specific projects. `< 3.9.6/envs/pyenv_practice >` being one of them. For a full tutorial on how to set different versions and virtual environments, use the sources at the the end of this blog post.

## Example

Typically, things like this can be hard to understand until it is put into practice. Below I have done the following to demonstrate how a local python version can be made for a specific project:

* Set the local version to `<pyenv local 3.9.1>`
* Show the versions and that my local has been set to `<3.9.1>` as denoted by the astrisk
* Create a `<practice.py script>`
* Show all file in the directory with `< ls -a >` and show that in  `<.python-version>` the version is `<3.9.1>`
* Go up a level to show that global python is still set to the system and the practice folder is different.

[quick Example](/assets/images/blogimages/figs-10-14/Example)


# Conclusions

Hopefully you can see how useful pyenv can be when working on different project! Setting your local version can help you manage what packages you are using and know what all the dependencies are for what you are doing. Some next steps you can do on your own are learning how to use pyenv while collaborating and creating/installing your requirements.txt or other python managers.



Sources :
  [Real Python](https://realpython.com/intro-to-pyenv/)
  [North Western](https://amaral.northwestern.edu/resources/guides/pyenv-tutorial#:~:text=Meet%20pyenv%3A%20a%20Simple%20Python,environments%20(%22virualenv's%22).)
![image](https://user-images.githubusercontent.com/75935407/138190483-eb2596d2-0689-4691-a1e6-fd01d8b165f1.png)
---
title: "What is Pyenv and Why You Should Use It"
layout: post
author: 18katesmit
post-image: "https://files.realpython.com/media/Getting-Started-With-pyenv_Watermarked.7b1dd55b32a1.jpg"
description: A Brief Intro to Multiple Python Versions with Pyenv
tags:
- python
- python libraries
- virtual environment
- versions
---

When you install Python on your computer, you should constantly update your Python version as new ones come out. Unfortunately, some libraries can become obsolete because they are not supported by the current version making code that once worked a major headache to update. Additionally, if you have ever tried to collaborate with other people in a project, they could have different libraries and python versions making it so you have to spend lots of time updating and debugging something that should be a fix. Fortunately, there is a tool that can help mitigate this, so you always know what python version you're using and what libraries are being used in a project.

# What is Pyenv?

Pyenv is a tool to manage different python versions on your computer for each project. Essentially you can have Python 2.7.15, Python 3.6.8, ect ... what ever you need, all on your computer and create virtual environments in these versions to make your projects run smoothly. In short, pyenv lets you change the global Python version, install multiple Python versions, set project-specific Python versions, and create and manage virtual python environments. Instructions to install pyenv on your computer can be found [here](https://github.com/pyenv/pyenv#installation).


# Pyenv Order

Pyenv organizes your system, global, local, and shell versions and can be thought about in a pyramid.

![pyenv-pyramid](https://files.realpython.com/media/pyenv-pyramid.d2f35a19ded9.png)


* System - this is what is installed on your computer when you download python
* Global - global python version can be changed with `< pyenv global 3.6.8 >`
* Local - this is often project specific python versions
* Shell - for shell specific python versions


Using the command `<pyenv versions>` will Show what versions of python you have installed and will denote your current global version with and asterisk.

This example shows what this could look like in your computer.

[pyenv example](/assets/images/blogimages/figs-10-14/pyen_versions)

You can see that there are several versions of python installed but I am currently working off the system version. Additionally, I have created some virtual environments for specific projects. `< 3.9.6/envs/pyenv_practice >` being one of them. For a full tutorial on how to set different versions and virtual environments, use the sources at the the end of this blog post.

## Example

Typically, things like this can be hard to understand until it is put into practice. Below I have done the following to demonstrate how a local python version can be made for a specific project:

* Set the local version to `<pyenv local 3.9.1>`
* Show the versions and that my local has been set to `<3.9.1>` as denoted by the astrisk
* Create a `<practice.py script>`
* Show all file in the directory with `< ls -a >` and show that in  `<.python-version>` the version is `<3.9.1>`
* Go up a level to show that global python is still set to the system and the practice folder is different.

[quick Example](/assets/images/blogimages/figs-10-14/Example)


# Conclusions

Hopefully you can see how useful pyenv can be when working on different project! Setting your local version can help you manage what packages you are using and know what all the dependencies are for what you are doing. Some next steps you can do on your own are learning how to use pyenv while collaborating and creating/installing your requirements.txt or other python managers.



Sources :
  [Real Python](https://realpython.com/intro-to-pyenv/)
  [North Western](https://amaral.northwestern.edu/resources/guides/pyenv-tutorial#:~:text=Meet%20pyenv%3A%20a%20Simple%20Python,environments%20(%22virualenv's%22).)

