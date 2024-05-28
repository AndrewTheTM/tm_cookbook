---
layout: concept
title: Biogeme Output Analysis
language: python
author: Andrew Rohne
libraries-needed: biogeme
category: Biogeme
---
# Estimated Parameters Table

Name: Name of Parameter
Value: Estimated Value of Parameter

Standard Error:

t-test: The t statistic of the test comparing the estimated value of the parameter to zero. High absolute values of the t-statistic reject the
null hypothesis that the parameter is equal to zero. Low absolute values of the t-statistic imply that the variable does not contribute significantly to the explanatory power of the model and can be considered for exclusion[1]. Absolute values of the t-statistic greater than 1.645 indicate a confidence level
of 90%, and absolute values greater than 1.96 indicate a 95% confidence level. If the absolute value of the t-statistic is greater than 3.29, that indicates
a level of confidence of 99.9%.


[1]: Self Instructing Guide to Mode Choice Modelling, 83
