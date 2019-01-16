[//]: # (Image References)
[image_0]: img/chosen_original_images.png
[image_1]: img/gray.png
[image_2]: img/blur_gray.png
[image_3]: img/edge_detected.png
[image_4]: img/masked_edges.png
[image_5]: img/combo.png

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

## Converting original image to gray scale

We'll convert our original RGB image to gray scale image. This can reduce noise from original three color channels. So, we can apply more powerful algorithms to isolate lines.

![alt text][image_1]

## Applying Gaussian Blur to smoothen edges

Gaussian Blur is another pre-processing technique to smoothen the edges of an image to reduce noise.

![alt text][image_2]

## Applying Canny Edge Detection on smoothed gray image

Now, after pre-processed the image, we'll use popular **Canny Edge Detector**, whose role is to identify lines in an image and remove other datas. Below is the comparison of images after edge detection applied to our original blurred gray image.

![alt text][image_3]

## Tracing region of interest

Our next step is to choose a region of interest and remove every line outside of this region.

![alt text][image_4]

## Performing Hough Transform

Next, we'll apply **Hough Transform** to extract lane lines and color them in red. For this, we will use openCV Hough Transform. You can find more information about the implementation of Hough Transform in OpenCV [here](https://docs.opencv.org/trunk/d6/d10/tutorial_py_houghlines.html).

Below is the output result of the Hough Transform:

![alt text][image_5]

## Future Improvements

We can improve our pipeline by tuning different parameters, separating left and right lines by their slope and average the position of each of the lines and extrapolate to the top and bottom of the lane.

Further more, we can also use deep learning to identify lane lines and compare the results against with this only Computer Vision approach.
