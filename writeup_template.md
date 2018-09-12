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

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I applied Canny algorithm for edges detection. Next I created a masked edges image. Then, I used Hough Transform to detect line segments. And finally, I used "weighted_img" function to draw lines on the original image.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by calculate the slope of each lines found by "hough_lines" function. Then i differentiate left and right line and i average the position of each of 
    the lines and extrapolate to the top and bottom of the lane.

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when "hough_lines" function will give us a wrong result. These result, considering my code, will be nevertheless taken into account for the average calcul. And it's not good.

Another shortcoming could be my parameters for "hough_lines" function. I first sought to detect most of the white pixels in the region of interest, even when they form very short line, without considering the average calcul of slope. And so, my code detects very short lines. So it is not robust and it can be seen in optional challenge.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to consider a low variation of slope, like 5 or 10%, between two images in order to avoid false detection due to "hough_lines" function wrong result.

Another potential improvement could be to reconsider parameters for Hough Transform with the average function now established.
