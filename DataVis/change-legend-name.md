---
layout: recipe
title: Change Legend Name
language: R
author: Andrew Rohne
libraries-needed: ggplot2
category: visualization
---
Many times the legend is "colour", which has a nice British look to it, but
generally doesn't have the right name that we'd want.

When using a discrete scale color (when `color = "Value Name"` or `color = {field}`
is used in the aesthetic of a plot)

```
  ggplot(...) + (...) + scale_color_discrete(name = "Legend")
```
