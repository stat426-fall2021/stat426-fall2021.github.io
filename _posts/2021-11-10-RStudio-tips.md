---
layout: post
title: "Writing Code in RStudio - Helpful Tips and Tricks"
author: germckay
post-image: /assets/images/blogimages/figs-11-10/RStudio.jpg
description: RStudio is a very useful IDE that comes with a host of features to provide an efficient coding environment.
tags:
- R
- Interface
- RStudio
- Shortcuts
- Custom
- Efficient Coding
---
RStudio is a widely used platform for coding. It has a host of shortcuts and cool features that streamline the coding process. Here are 10 that have been a huge benefit to me.

## Access All Shortcuts

- *Alt + Shift + K*

If you ever want a reminder on a particular shortcut, you can pull up a list of all shortcuts available in RStudio by pressing **Alt + Shift + K**.

## Navigating Open files
- *Ctrl + Tab*
- *Ctrl + Shift + Tab*
- *Ctrl + Shift + .*

If you are like me, you probably have multiple files open at once in RStudio. Instead of having to drag your mouse and click on a file you want to pull up, you can instead skim over tabs by pressing **Ctrl + Tab** (to go one tab to the right) or **Ctrl + Shift + Tab** (to go one tab to the left). If you have a ton of tabs open, it may be simpler to press **Ctrl + Shift + .** which allows you to search by name all of the files you have open.

## Multiple Cursors / Selections
- *Alt + Ctrl + Click*
- *Ctrl + Alt + Shift + M*

Have you ever felt yourself wanting to edit similar parts of your code at once? RStudio has a few features that make this easy. The multiple cursor feature is one of my favorites. If you hold **Alt + Ctrl**, you can click and put multiple cursors in your code, which is very helpful if you need to cut/copy and paste multiple sections of code, or if you need to make small adjustments in several places. Holding **Alt + Ctrl + Up/Down** will add additional cursors directly above or below where the current cursor is.

If you want to select all instances of a particular phrase or section of code within a script, select one instance, then hold **Ctrl + Alt + Shift + M.** All instances of that selection within the script will be selected, making it easy to make quick adjustments.

## Pipe Operators

- *%>%*
- *%<>%*
- *%$%*

As with many other languages, R has a piping function (available from the magrittr package) which allows for more streamlined and easy-to-follow code. For example, the code:

````md
x <- data.frame(“V1” = c(1, 2, 3), “V2” = c(“a”, “b”, “c”))
mean(pull(filter(x,V1 %in% c("a","b")),V2))
# 1.5
````

Can be rewritten as the following using the pipe function:

````md
x %>% filter(V1 %in% c("a","b")) %>% pull(V2) %>% mean()
# 1.5
````
In RStudio, instead of having to manually type out the function, press **Ctrl + Shift + M** for an efficient way to insert the function.

There are a couple of other pipe operators as part of the magrittr package that I think are interesting. The operator %<>% allows you to simultaneously pipe an object and save the updates to that object. For example:
```{r}
x <- data.frame(“V1” = c(1, 2, 3), “V2” = c(“a”, “b”, “c”))
x <- x %>% select(V1)
```
can be rewritten as
```{r}
x %<>% select(V1)
```

The operator %\$% allows you to pull a specific column from a data frame, which can be useful, especially when used as part of a sequence of piped functions. For example, the code:

```{r}
x %$% V1
```
will extract the vector c(1, 2, 3) from the data frame.

## Quick Code Manipulations
- *Alt + Up/Down*
- *Alt + Shift + Up/Down*

These next tricks are helpful for editing lines of code in your document. Holding **Alt + Up/Down** allows you to move whichever line(s) your cursor is on Up or Down, respectively. It allows you to move code pretty effectively around your document.

If you would like to make a quick copy of a line of code, just add shift to the mix (**Alt + Shift + Up/Down**) to copy the selected line(s) in the direction you specify.

## Snippets
A really cool feature of RStudio is the ability to define custom shortcuts to generate code, called snippets. RStudio has several snippets predefined and ready to use. For example, if you type “mat” and press **Tab**, RStudio returns a template for the matrix function, and allows the user to quickly tab over to specify the contents of the matrix and specify the number of rows and columns. To see what snippets are available in RStudio, as well as to define your own snippets, go to Tools > Global Options > Code > Edit Snippets… I have saved several presets for repetitive tasks that I do often, such as generating a header for scripts and setting the working directory to the file’s location. This has saved me a ton of time. For more information on snippets visit [this website](https://support.rstudio.com/hc/en-us/articles/204463668-Code-Snippets?version=1.4.1717&mode=desktop).

## Jumping from script to console
- *Ctrl + 1* / *Ctrl + Shift + 1*
- *Ctrl + 2* / *Ctrl + Shift + 2*

There are several shortcuts that allow you to jump around to the different panes in RStudio. The keys **1-9** and **F1-F7** are each associated with a particular pane in RStudio (a complete list of associations can be found by holding **Alt + Shift + K**). Holding **Ctrl + {Pane #}** will bring the particular pane to the foreground along with the cursor. Holding **Ctrl + Shift + {Pane #}** will maximize that pane so that it fills the window. I most often use these shortcuts to jump from the source pane to the console pane and back (**Ctrl + 1/2**) or to maximize one of these panes (**Ctrl + Shift + 1/2**).

## Comments

- *Ctrl + Shift + C*
- *Colored Comments*

You probably know that adding a pound sign at the beginning of a line of code will comment it out. It can be a pain to manually add the sign to several lines that we want to comment out. Instead, we can select the lines of code that we want to comment out and press **Ctrl + Shift + C**.

Sometimes it can be helpful to have different colored comments in your code (for example, having a particular color for notes, alternate code, etc…). While RStudio does not directly support this capability, we can hack it by using the following additions to the pound sign:

```{r}
#'[comment_here_in_color_1]
#'*comment_here_in_color_2*
#'@comment_here_in_color_3
```
The colors will differ based off of your selected theme

## Theme

The default RStudio theme is very light. Users can select a different color scheme by going to Tools > Global Options > and appearance. If your aren't satisfied with any of them, you can create your own custom theme, and load it into RStudio (see this [webpage](https://rstudio.github.io/rstudio-extensions/rstudio-theme-creation.html) for more details).

## Setting Working Directory

Sometimes it can be a pain to set the working directory, especially if you have to type out the entire file path. There is a nice function as part of the rstudioapi package that will set the working directory to the current file location:

```{r}
setwd(dirname(rstudioapi::getActiveWorkingContext()$path))
```
I have created my own snippet that will generate this line with a couple keystrokes. It saves a lot of time.

It is important to note that this code only works in RStudio, and for an RScript. If you are working within an R Markdown document, it is a little harder to set the working directory, but the following code will work:

````md
```{r}
knitr::opts_knit$set(root.dir = 'your/file/path')
```
````
Again, snippets work great here in allowing you to type the code quickly and effectively.

## R Markdown

- *message*
- *warning*
- *cache*

Many who read this article will undoubtedly be familiar with R Markdown files, which provides a nice way to format code and text for reports or presentations. I have been using R Markdowns for a few years now, and I keep discovering new features that I wish I had known from the beginning. Here are a few pointers that will make your experience more enjoyable. (As a quick comment, the knitr package must be installed in order to knit an R Markdown file)

To quickly insert a new code chunk, press **Ctrl + Alt + i**.

At the beginning of each code chunk there is a heading contained in curly braces:
````md
```{r chunk_name, additional_options...}
```
````

Text immediately following the "r" is the chunk's name, which, beyond idenitfying the portion of code, can be used to access the chunk quickly in the source pane in RStudio. Additional options that control specific display features of the chunk can be set following the name.

If you want to have all the same options specified for all chunks in the document, include the following line of code in the document:

```{r}
knitr::opts_chunk$set(options_for_all_chunks)
```

The space within the parantheses is where the user can specify the options that apply to every chunk in the document.

I often have been frustrated by the appearance of unwanted messages or warnings that were generated by the code in the R Markdown. Specifying the options **message=FALSE** and **warning=FALSE** in the heading will remove this output from the knitted document.

Another frustration was that knitting required all the code in the document to compile before generating a report. This was especially frustrating as I neared the end of projects and needed to see how the document looked as I was making final adjustment changes. Adding the option **cache=TRUE** makes it so that any chunk that has already been compiled and has no adjustments does not have to be recompiled in order to generate a report. This option has saved me a lot of time and frustration.

To see more available options for R Markdown code chunks, along with other useful features, check out [this pdf](https://ethz.ch/content/dam/ethz/special-interest/math/statistics/sfs/Education/Advanced%20Studies%20in%20Applied%20Statistics/course-material-1921/Datenanalyse/rmarkdown-2.pdf).

## Conclusion

This is by no means a comprehensive list of all the helpful features in RStudio, but these are several that I have found useful in my educational and career experience. I hope that they can be helpful to you as well. If you have any tips or tricks that you find useful, please comment them below!

Happy coding!
