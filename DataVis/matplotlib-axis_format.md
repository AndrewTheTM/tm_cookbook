---
layout: recipe
title: Matplotlib Axis Formatting
language: Python
author: Andrew Rohne
libraries-needed:
category: Data Visualization
---

Matplotlib will format labels using Python format strings. The two examples below will add 
commas and dollars. Since much of what I work with is large numbers, the formats do not
have decimals.

```
ax.yaxis.set_major_formatter('{x:,.0f}') # y axis with commas
ax.xaxis.set_major_formatter('${x:,.0f}') # x axis in dollars
```
