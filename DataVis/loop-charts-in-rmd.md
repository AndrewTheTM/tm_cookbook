---
layout: recipe
title: Read and Summarize OMX Files in R
language: R
author: Andrew Rohne
libraries-needed: ggplot2, RMarkdown
category: analysis
---
Reusable code is always smart. This recipe takes an iterable object, such as a
list of dataframes (which could easily be data tables or tibbles) and plots
data from each of the objects.

This is the r markdown component. Using "results = 'asis'" will parse this
differently, and that is why the ggplot statement is inside a print function.

```
```{r charts, results = 'asis'}

for(otc in outTripCompare){
  print(
    ggplot(otc, aes(x = pctObs, y = pctMod)) + geom_point() +
      geom_abline(slope = 1, intercept = 0, color = "red") +
      ggtitle("Trip Comparison") +
      xlab("Observed Percent of Trips") +
      ylab("Modeled Percent of Trips")
  )

}

```
