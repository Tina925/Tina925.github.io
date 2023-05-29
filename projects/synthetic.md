---
layout: project
type: project
image: img/robomaster/roboProfile.png
title: "Synthetic Datasets"
date: 2022
labels:
  - Robotics
  - Autodesk Maya
  - mel
summary: "My team generated a synthetic datasets using Autodesk Maya to get in use in Purdue Robomaster competition."
---

<div class="text-center p-4">
  <img width="200px" src="../img/robomaster/robo.png" class="img-thumbnail" >
  <img width="200px" src="../img/robomaster/rob.jpg" class="img-thumbnail" >
</div>

Our goal for this project is to augmented Robomaster's datasets in order to get a larger datasets for traning, and also generate  synthetic datasets for different angle of the robots by changing camera angles in Maya application. This is a year long project

Our team expand the existing datasets in order to improve the accuracy and train the datasets in different methods in order to achieve it. The method we used including scaling, rotation, position, and brightness.

In order to improve dataset size and variation, we implemented a synthetic data generation pipeline using Autodesk Maya and allowed us generate any amount photorealistic synthetic images with high randomization and expandability. Synthetic data generation offers a solution by allowing the extraction of large amounts of images and metadata directly from a virtual environment, while maintaining precise ground truth annotations.

Here is some code that illustrates how we can detect multiple armor plate at once and also set up the camera angle:

```cpp
select -r "ap_front" "ap_front1";
	
	ConvertSelectionToVertices;
	string $selected [] = `ls -sl`;


	
	int $numVert = 0;
	int $sizeSelected = size($selected);
	print($sizeSelected);
  
  
  // -------------------- Start Loop --------------------
	for ($numfile=0; $numfile<$datasetSize; ++$numfile) { // start numfile
		
		// Randomize Camera attributes
		$mode = rand(0,100);
		if ($mode < 20) {
			$rotX = rand(-80,-10);
		} else {
			$rotX = rand(-10,0);
		}
		$rotY = rand(-80,80);
		$dolly = rand(104,555);
		print("rotX : "+$rotX+"\n"+"rotY : "+$rotY+"\n");
		
		
		// Setup camera
		viewLookAt -pos 0 20.67 20 $camera;
		rotate -pivot 0 20.67 20 $rotX $rotY 0 $camera;
		dolly -abs -d $dolly $camera;
```
