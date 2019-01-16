[//]: # (Image References)
[image_0]: img/chosen_original_images.png

# **Finding Lane Lines on the Road**
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

<img src="img/laneLines_thirdPass.jpg" width="480" alt="Combined Image" />

The goal of the project is to create a pipeline that find lane lines on the road. We are going to use various Computer Vision techniques to identify lane lines in different situations. You can find the original Udacity repository of the project [here](https://github.com/udacity/CarND-LaneLines-P1).

## Setup

Udacity provides the following sample images of 960 x 540 pixels to train our pipeline against.

![alt text][image_0]

## The Pipeline

We'll cover in details of different steps to create our pipeline which will enable us to identify and classify lane lines in different situations. The followings are the pipeline and the input to each step is the output of the previous step.

- Convert original image to gray scale
- Apply Gaussian Blur to smoothen edges
- Apply Canny Edge Detection on smoothed gray image
- Trace region of interest
- Perform Hough Transform to find lane lines within our region of interest and trace them in red
- Separate left and right lanes
- Interpolate line gradients to create two smooth lines
