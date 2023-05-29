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
  <img class="img-fluid" src="../img/robomaster/robo.png" class="img-thumbnail" >
  <img class="img-fluid" src="../img/robomaster/rob.png" class="img-thumbnail" >
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

<div class="text-center p-4">
  <img class="img-fluid" src="../img/robomaster/flowchart.png" class="img-thumbnail" >
</div>

we have devised a 6-stage process that transforms the 3D model into a deployable computer vision model. Let me briefly walk you through each stage.

The first stage involves importing the 3D models of our robots and environment into Autodesk Maya. 
In the second stage, we use an extensive randomization framework to simulate different scenarios the robot might encounter.
In stage three, we render the images and extract metadata from the virtual environment.

These steps are then repeated multiple times to generate any amount of data we want, providing a virtually limitless supply of diverse training samples. 

With the synthetic dataset prepared, we custom train a YOLOv5 object detection model and evaluate its performance against various real-world scenarios. This evaluation allows us to identify areas in which the model may be lacking and pinpoint specific edge cases. To address these shortcomings, we generate thousands of variations for each identified edge case, thereby strengthening the model's performance. Through iterative improvements and fine-tuning, the model becomes increasingly robust and accurate.

<div class="text-center p-4">
  <img class="img-fluid" src="../img/robomaster/flow.png" class="img-thumbnail" >
</div>

After setting up the 3D model, we begin to randomize the parameters. This involves generating variations of the 3D model by altering certain parameters and attributes of the model, which helps create a diverse range of datasets that reflect real-world variation.

We focus on randomizing four parameters in particular: lighting, camera, 3D meshes, and post-processing.

For lighting, we adjust the intensity, color, location, and rotation offset. The competition lighting is very different from what we would normally be in, so doing this covers almost all of the conditions that the robot may encounter. For the camera, we adjust the field of view, focal length, as well as location and rotation offset. For this new season, our team is switching our camera, so these parameters helps the model to adapt to this change.

For 3D meshes, we adjust the background, armor plate, and robot variations. By changing these parameters, the model can adapts to different enemy robot types. Lastly, we use the OpenCV library for post-processing to adjust the exposure, bloom effect, white balance, and color balance after the datasets have been generated, further improving the variation of the dataset.

