---
title       : Stock Data Explorer using R shiny
subtitle    : Project for Developing Data Products
author      : Victor Li
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Overview

* Using shiny to build interactive web app
* Using [quantmod](http://www.quantmod.com/) to query stock data
* Shiny app is uploaded to https://lilinvictor.shinyapps.io/StockAnalysis

--- .class #id 

## Usage

* Select stock code and time window in left panel:
    - Select the stock from the drop list;
    - Choose the time window as start/end date of stock price.

* Results are shown interactively in right panel:
    * In the tab "Stock price data":
        - Max and Min price during the time window are shown respectively;
        - Raw data for every day price in the time window
    * In the tab "stock price chart":
        - Price trend chart is shown for the specified time window.

--- .class #id 

## UI Layout

* UI Layout is defined in ui.R
    - Using navbarPage to define multiple pages:
        - Stock data explorer: interactive app to explore store price
        - About: document for using this app
    - Using tabsetPanel to define two tabs:
        - Stock data table
        - Stock price chart

--- .class #id 

## Server logic

* Business logic is defined in server.R
    - Using reactive() to capture user input and share logic
* Chart is rendered using renderPlot()


```r
    output$stockPlot <- renderPlot({
        plotStock(stockData())
    })    
```

![plot of chunk unnamed-chunk-2](assets/fig/unnamed-chunk-2-1.png) 
