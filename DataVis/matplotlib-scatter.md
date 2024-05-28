---
layout: recipe
title: Matplotlib Scatter Plot
language: Python
author: Andrew Rohne
libraries-needed:
category: Data Visualization
---

This makes a scatterplot, and is setup for multiple fields.

```
fig = plt.figure(figsize=(16,10))
ax = fig.add_subplot()
ax.scatter(data['x_field'], data['y_field_1'], marker='o', label = 'Name 1')
ax.scatter(data['x_field'], data['y_field_2'], marker='s', label = 'Name 2')
ax.scatter(data['x_field'], data['y_field_3'], marker='s', label = 'Name 3')
plt.title("Title Here")
plt.legend(loc='upper left')
ax.set_xlabel('X Label Name')
ax.set_ylabel('Y Label Name')
plt.show()
```