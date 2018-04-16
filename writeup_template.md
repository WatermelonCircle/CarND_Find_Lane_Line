# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps as following:
1) converted the images to grayscale.
2) use canny edge detection to extract the all the edges satisfiying canny algorithm.
3) use cv2.fillpoly to mask the unneccesery region.
4) use cv2.HoughLinesP to extract the lines over the lane lines and plot it on a black image which has idential size as our images.
5) superimpose the image from step 4 to the original image using cv2.addWeighted function
 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

1) group the left lane and right lane by their slope ( slope_left>0, slope_right<0)
2) averaging the slope and bias of both groups respectively to get slope and bias of both lanes
3) define the length of drawing lanes by using Y axis of pixel value
4) calculate the X value of two ends using slope and bias respectively.
5) plot the left and right lanes on a black image


If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be that when the hough algorithm is not good enough to extract a line, no line would be drawed over that specifc frame image... 

Another shortcoming could be the canny edge detector could not detect the edge due to the low gradient...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to make hough algorithm robust so that we can always have a line detected on both side of lanes...

Another potential improvement could be to make canny edge detector robust to detect the lanes even when the gradeint is small due to light effect of that specific days...
