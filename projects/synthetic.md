---
layout: project
type: project
image: img/micromouse/micromouse-square.jpg
title: "Synthetic Datasets"
date: 2022
labels:
  - Robotics
  - Autodesk Maya
  - mel
summary: "My team generated a synthetic datasets using Autodesk Maya to get in use in Purdue Robomaster competition."
---

<div class="text-center p-4">
  <img width="200px" src="../img/micromouse/micromouse-robot.png" class="img-thumbnail" >
  <img width="200px" src="../img/micromouse/micromouse-robot-2.jpg" class="img-thumbnail" >
  <img width="200px" src="../img/micromouse/micromouse-circuit.png" class="img-thumbnail" >
</div>

Our goal for this project is to augmented Robomaster's datasets in order to get a larger datasets for traning, and also generate  synthetic datasets for different angle of the robots by changing camera angles in Maya application. This is a year long project

Our team expand the existing datasets in order to improve the accuracy and train the datasets in different methods in order to achieve it. The method we used including scaling, rotation, position, and brightness.

Here is some code that illustrates how we read values from the line sensors:

```cpp
byte ADCRead(byte ch)
{
    word value;
    ADC1SC1 = ch;
    while (ADC1SC1_COCO != 1)
    {   // wait until ADC conversion is completed   
    }
    return ADC1RL;  // lower 8-bit value out of 10-bit data from the ADC
}
```