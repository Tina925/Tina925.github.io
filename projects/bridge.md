---
layout: project
type: project
image: img/bridge sensor/pro1.png
title: "Bridge Sensor"
date: 2022
labels:
  - Python
  - Data Analysis
  - GitHub
summary: "A data analysis project with python on determining sensor adding on bridges"
---
<div class="text-center p-4">
<img class="img-fluid" src="../img/bridge sensor/python.jpg">
</div>
Above is the first part of the prject which my partner and I decided to put three sensors on Brooklyn, Queensboro, and Manhattan bridges. 
We used the maximum, minimum, mean, and standard deviation with code support to get the final graph of each bridges' spreadout, and then choose three of four most unique bridges to put on sensors. 

For the next part of the project I did code analysis on given data of number of bicycles on bridges related to weather, in order to make prediction on number of bicycles by giving the forecast. 
By using the crossed validation and split the data, I normalize the data based on the given sets in order to build the linear model. 
In python, I mainly used the sklearn python technics to determine the coefficients of the model, by knowing the model it is easy to predict the final number of bicycles based on next day's forecast. 

For the last part of this project my group member construct the code analysis and I concluded the final conclusion. By giving the number of bicycles, we are trying to predict if that day is rainy or not. 
We construct a linear regression model based on relationship between precipitation and number of bicycles, and plugged in the number of bicycles in order to see if its rainy or not, if result is 1 than its rainy, is is 0 then its not rainy. 
The final display is as following below:
<div class="text-center p-4">
<img class="img-fluid" src="../img/bridge sensor/pro1-3.png">
</div>
