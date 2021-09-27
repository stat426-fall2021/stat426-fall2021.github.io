---
layout: post
title: reticulate
author: mrmorgan17
post-image: '/assets/images/blogimages/figs-09-27/reticulate.jpeg'
description: reticulate is an R package that interfaces with Python. The user can run Python code, create and manage virtual environments, and import modules all from R
tags:
- R
- Python
- Interface
- RStudio
---

In the data science field, the debate between R and Python rages on. Both languages claim to be superior to the other for data science. In my experience, both R and Python are good languages and each one has its strong-suits in certain areas. Recently, I came across reticulate, an R package leading the way in bringing R and Python together and allowing for data scientists to get the best out of both languages. Now, instead of having to choose between R and Python, you can have both!

![El Dorado - Both](https://media.giphy.com/media/3o7aCRloybJlXpNjSU/giphy.gif)

## reticulate::installation

To use the reticulate package, both [R](https://cran.r-project.org) and [Python](https://www.python.org) need to be installed on your machine.

Since reticulate is an R package, it is installed using `install.packages('reticulate')`

## reticulate::finding_python_interpreters

One aspect of this package that can get a little bit complicated is specifying which Python interpreter you want the reticulate package to use. Python can be installed from various places, some of which are:
  * [Python Website](https://www.python.org)
  * [Anaconda](https://www.anaconda.com) / [Miniconda](https://docs.conda.io/en/latest/miniconda.html)
  * [Homebrew (MacOS only)](https://brew.sh)

Additionally, Python virtual environments have their own executable files (*.exe*) so each virtual environment is another Python interpreter.

All in all, it's quite possible you could have multiple Python interpreters installed in multiple places on your computer.

The simplest solution that I have found is using [RStudio](https://www.rstudio.com). In the newest version of RStudio (1.4.1717), it is able to detect all the Python interpreters on your machine and allows you to choose which one to use.
  * **Tools**
  * **Global Options**
  * Click on **Python**  
 
![RStudio Global Options](https://support.rstudio.com/hc/article_attachments/1500011460282/Screen_Shot_2021-04-21_at_3.33.02_PM.png)

  * Then **Select...**
 
![Select Python Interpreter](https://support.rstudio.com/hc/article_attachments/1500011460302/Screen_Shot_2021-04-21_at_3.34.00_PM.png)  

  * After selecting a Python interpreter, click **Select** then **Apply**. *This will restart your R session.*

After this, you should be all good to go. To check which Python interpreter reticulate is using you can run the `py_config()` function. The output of which should look similar to something like this:

```
> py_config()
python:         /usr/local/bin/python
libpython:      /usr/local/opt/python@3.9/Frameworks/Python.framework/Versions/3.9/lib/python3.9/config-3.9-darwin/libpython3.9.dylib
pythonhome:     /usr/local/Cellar/python@3.9/3.9.7/Frameworks/Python.framework/Versions/3.9:/usr/local/Cellar/python@3.9/3.9.7/Frameworks/Python.framework/Versions/3.9
version:        3.9.7 (default, Sep  3 2021, 12:37:55)  [Clang 12.0.5 (clang-1205.0.22.9)]
numpy:          /usr/local/lib/python3.9/site-packages/numpy
numpy_version:  1.21.2

NOTE: Python version was forced by use_python function
```

If issues with selecting the right Python interpreter persist, these articles offer more details and troubleshooting:
  * [Python Version Configuration](https://rstudio.github.io/reticulate/articles/versions.html)
  * [Using Python with the RStudio IDE](https://support.rstudio.com/hc/en-us/articles/1500007929061-Using-Python-with-the-RStudio-IDE)

## reticulate::virtual_environments

One especially great feature of the reticulate package is that it permits the user to create and manage Python virtual environments. A Python virtual environment creates a folder with a separate Python interpreter. Virtual environments are great for managing Python packages and their dependencies. Sometimes, a Python package requires an older version of a package to be installed and instead of having to re-install an older version of the dependent package that could possibly mess up other packages, a virtual environment allows for the older version of the dependent package to be installed in a separate location and be kept separate.  

If you're familiar with R, I like to think that virtual environments are to Python what projects are to R.

To create a Python virtual environment with reticulate, there's the `virtualenv_create()` function. For example, if I wanted to create a Python virtual environment *Tatooine*, I would run the following:
```
> virtualenv_create('Tatooine')
Using Python: /usr/local/Cellar/python@3.9/3.9.7/Frameworks/Python.framework/Versions/3.9/bin/python3.9
Creating virtual environment 'Tatooine' ... Done!
Installing packages: 'pip', 'wheel', 'setuptools', 'numpy'
Requirement already satisfied: pip in /Users/matthewmorgan/.virtualenvs/Tatooine/lib/python3.9/site-packages (21.2.4)
Collecting wheel
  Using cached wheel-0.37.0-py2.py3-none-any.whl (35 kB)
Requirement already satisfied: setuptools in /Users/matthewmorgan/.virtualenvs/Tatooine/lib/python3.9/site-packages (57.4.0)
Collecting setuptools
  Downloading setuptools-58.0.4-py3-none-any.whl (816 kB)
Collecting numpy
  Using cached numpy-1.21.2-cp39-cp39-macosx_10_9_x86_64.whl (17.0 MB)
Installing collected packages: wheel, setuptools, numpy
  Attempting uninstall: setuptools
    Found existing installation: setuptools 57.4.0
    Uninstalling setuptools-57.4.0:
      Successfully uninstalled setuptools-57.4.0
Successfully installed numpy-1.21.2 setuptools-58.0.4 wheel-0.37.0
Virtual environment 'Tatooine' successfully created.
```

When a virtual environments created with this function are located in the `~/.virtualenvs` directory.

As you can see, when the Python virtual environment is created, it automatically installs the _pip_, _wheel_, _setuptools_, and _numpy_ packages along with it.

This package also allows the user to specify which Python interpreter and which Python version should be used with the new virtual environment.

To install additional packages in the virtual environment, the `virtualenv_install()` function can be used. Here, I installed the *pandas* package in the *Tatooine* virtual environment

```
> virtualenv_install('Tatooine', 'pandas')
Using virtual environment 'Tatooine' ...
Collecting pandas
  Downloading pandas-1.3.3-cp39-cp39-macosx_10_9_x86_64.whl (11.6 MB)
Collecting python-dateutil>=2.7.3
  Using cached python_dateutil-2.8.2-py2.py3-none-any.whl (247 kB)
Requirement already satisfied: numpy>=1.17.3 in /Users/matthewmorgan/.virtualenvs/Tatooine/lib/python3.9/site-packages (from pandas) (1.21.2)
Collecting pytz>=2017.3
  Using cached pytz-2021.1-py2.py3-none-any.whl (510 kB)
Collecting six>=1.5
  Using cached six-1.16.0-py2.py3-none-any.whl (11 kB)
Installing collected packages: six, pytz, python-dateutil, pandas
Successfully installed pandas-1.3.3 python-dateutil-2.8.2 pytz-2021.1 six-1.16.0
```

To list all the Python virtual environments on your machine, use the `virtualenv_list()` function.

```
> virtualenv_list()
[1] "r-reticulate" "SASPy"        "Tatooine"    
```

To use a specific virtual environment, you can:
  * Use the `use_virtualenv()` function
  ```
  use_virtualenv('Tatooine') # Telling reticulate to use the Tatooine virtual environment
  ```
  * Select the Python interpreter from RStudio's Global Options as shown previously

If you would like to remove a Python virtual environment, there's the `virtualenv_remove()` function. Here, I remove the *Tatooine* Python virtual environment:

```
> virtualenv_remove('Tatooine')
Remove virtual environment 'Tatooine'? [Y/n]: Y
Virtual environment 'Tatooine' removed.
```

Now, `virtualenv_list()` returns the following:

```
> virtualenv_list()
[1] "r-reticulate" "SASPy"  
```

Overall, the reticulate package is great for managing Python virtual environments all from R. More info on these functions can be found [here](https://rstudio.github.io/reticulate/reference/virtualenv-tools.html).

## reticulate::python_in_R

With reticulate, Python scripts can easily be run in RStudio.
  1. Open a _.py_ file
  2. Run `reticulate::repl_python()` in the **Console** to start a Python session
  3. Execute the _.py_ file
  4. Run `quit` in the **Console** to end the Python session

reticulate also allows for seamless integration of Python into R Markdown (_.Rmd_) files
  1. Initialize an R chunk:
  ````md
  ```{r setup, include = FALSE}
  library(reticulate)
  ```
  ````
  2. Create Python chunks by specifying `python` at the top of the chunk instead of `r`. After this, you can code in Python like you would in any other IDE (Jupyter, Spyder, etc):
  ```{python}
  import numpy as np

  def perfect_sq(n):
    sqrt_n = np.sqrt(n)
    if sqrt_n * sqrt_n == n:
      print(n, 'is a perfect square of', int(sqrt_n))
    else:
      return(False)

  perfect_sq(25)

  Python 3.9.7 (/usr/local/bin/python)
  Reticulate 1.22 REPL -- A Python interpreter in R.
  Enter 'exit' or 'quit' to exit the REPL and return to R.
  25 is a perfect square of 5
  ```
  _These Python chunks can be run the same way R chunks are run in R Markdown files_

  3. The output message displaying the Python and reticulate version info will always be output unless suppressed
  ````md
  ```{r}
  options(reticulate.repl.quiet = TRUE) # Could be added to the setup chunk in step 1
  ```
  ````

  ````md
  ```{python}
  import numpy as np

  def perfect_sq(n):
    sqrt_n = np.sqrt(n)
    if sqrt_n * sqrt_n == n:
      print(n, 'is a perfect square of', int(sqrt_n))
    else:
      return(False)

  perfect_sq(25)
  ```
  ````
  ```
  25 is a perfect square root of 5
  ```

The reticulate package has many more functions that allow R and Python to communicate with each other. The following article explains these functions in much greater detail:
  * [Calling Python from R](https://rstudio.github.io/reticulate/articles/calling_python.html)

## reticulate::conclusions

The main aspect that I like about the reticulate package is that it's allowed me to use RStudio as my IDE for both R and Python which is great because I am already familiar with RStudio. Although, I still have a lot to learn about the reticulate package. My personal goal is to continue to learn and practice with this package so that I can become well-versed in both R and Python.  

Hopefully, this post has piqued you interest and served as a tutorial that helps you in getting up and running with the reticulate package yourself.

Best of luck!
