---
title: Dashboards in R Shiny
layout: post
author: BryceFuller1
post-image: "https://www.google.com/url?sa=i&url=https%3A%2F%2Fblog.efpsa.org%2F2019%2F04%2F24%2F7-easy-steps-to-building-your-own-shiny-app-from-scratch%2F&psig=AOvVaw0kN3qC3DtlFD_SVVHAtC5y&ust=1636514861250000&source=images&cd=vfe&ved=0CAgQjRxqFwoTCLDf9ZOrivQCFQAAAAAdAAAAABAD"
description: An introduction to why shiny dashboards are useful and how to create a simple one.
tags:
- R
- Shiny
- Web Applications
---

# Introduction

This post will provide an introduction into what an R shiny application is, why they are useful, and how to create a simple web application. 

# What is an R Shiny Application?

R Shiny is a framework that was created by Rstudio in order to convert programs written in R into a web application. Often we see people coming out with Shiny applications that are very diverse in their purposes. One of the most common types of applications we see have to deal with geospatial data, allowing users to see trends in data across different geographic areas. They often have feature sliders which allow users to set different features across the data in order to explore the data more in depth. A good example of this is an application that enables users to see crime rates with feature sliders that can show crime rates based on important characteristics such as average income in the area, percentage below the poverty level, and even features you might not initially deem important such as daily average temperature. The following image is an example of an application taken from the Rstudio gallery that tracks crime rates in different parts of the world.

![](https://github.com/BryceFuller1/blogpost/blob/master/Screen%20Shot%202021-11-01%20at%202.43.31%20PM.png)

# Why are they useful? 
One of the biggest reasons why R Shiny applications are useful is that they allow users who are not proficient in R to explore and experiment with data in new and exciting ways that they would not be able to do on their own if they just had access to the raw data. Another reason these applications are useful is that R programmers who wish to publish these applications don't actually need any web development experience. They simply need to learn the framework for Shiny and suddenly they are able to publish very interactive and useful applications for people who may not have any experience with R or even statistics for that matter. 

# How to Make A Simple App

We will now learn how to make a simple app that functions as a calculator that can add two numbers with a calculate button. In Shiny there are two parts to every app. The first is the user interface side and the second is the server side of the application. In the user interface side we can define what the user of the app is able to see such as different input systems and how reactive the application is. We can make it to where the app constantly refreshes after the user enters a character if there is a text box, changes the value on a slider, or we can make it to where the user enters all the requested input and then presses a button to refresh the app with the new information when they are ready,

# User Interface Side
We first start with the user interface side where we create two input boxes along with a button that when clicked calculates the difference between the two numbers.

```R

ui <- pageWithSidebar(
  headerPanel("Simple Action Button"),
  sidebarPanel(
    numericInput("one", "First Number:", min = 0, max = 100000, value = 1),
    numericInput("two", "Second Number:", min = 0, max = 100000, value = 0),
    br(),
    actionButton("goButton", "Go!"),
    p("Click the button to update the value displayed in the main panel.")
  ),
  mainPanel(
    verbatimTextOutput("result")
  )
)
```
We first define a user interface function that gives us a webpage starting with the pageWithSidebar function. Inside this is where we can customize the output however we like. We first give a header and then move on to the sidebarPanel. Here is where we have decided to place our input boxes and action button. Here we can add text for the user to see that tell the user what kind of input is desired. We can also set default values along with a range of possible values that the input boxes can accept. The values that are entered in can be referenced later on in the server side of the application. It is important to note that we are naming the two input boxes "one" and "two" respectively, along with "goButton" for the action button and "result" for the output we wish to display. These names are not displayed on the interface but are strictly behind the scenes. This is because we use these names to refer to these inputs in the server side of the Shiny application to do the actual calculations. We will now look over the server side of the application and walk through what is happening.

# Server Side

```R
server <- function(input, output) {
  
  ntext <- eventReactive(input$goButton, {
    input$one-input$two
  })
  
  output$result <- renderText({
    ntext()
  })
}

```

In the first line we create a server function that can take two variables "input" and "output". We then create a reactive expression called ntest that only runs once the calculate button is pressed by the user. It takes the input from the two input boxes and subtracts the second from the first. Notice how in this function we use the names "goButton", "one", and "two" which we created in the UI side. This is how the server side can communicate with the UI side. We then see that we are storing a value into output$result. We first call the function renderText and pass it the ntext function. This then gets the visual output from the ntext function and stores it into output$result. We then see back in the ui side of the application there is a main panel function which takes the result stored in output$result and outputs it for the user to see using a function called verbatimTextOutput("result").

# Final Output

Putting it all together we get the following code which produces a functioning Shiny application:

```R
library(shiny)

ui <- pageWithSidebar(
  headerPanel("Simple Action Button"),
  sidebarPanel(
    numericInput("one", "First Number:", min = 0, max = 100000, value = 1),
    numericInput("two", "Second Number:", min = 0, max = 100000, value = 0),
    br(),
    actionButton("goButton", "Go!"),
    p("Click the button to update the value displayed in the main panel.")
  ),
  mainPanel(
    verbatimTextOutput("result")
  )
)

server <- function(input, output) {
  
  ntext <- eventReactive(input$goButton, {
    input$one-input$two
  })
  
  output$result <- renderText({
    ntext()
  })
}

shinyApp(ui, server)
```
The top of the code imports the shiny library which allows us to write Shiny applications. The last line of code calls the shinyApp function which takes the ui and server functions as input and actually runs the application. The following image is what the application looks like after the user has entered the input and clicked on the calculate button. 

![](https://github.com/BryceFuller1/blogpost/blob/master/Screen%20Shot%202021-11-08%20at%206.17.15%20PM.png)

# Conclusion

In conclusion we have learned what an R shiny application is, why they are useful, and how to create a simple application that we can use as a template to develop more complicated applications in the future. Another feature that is important to note is the ability to publish the application for free through Rstudio so that others can utilize the application. All that is required is an Rstudio account. As a final note I would like to invite you to create an application that interests you. There are many different ideas out there ranging from simple data visualization apps to complicated machine learning models, the decision is yours!
