# **Finding Lane Lines on the Road** 

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


### Reflection

### 1. Pipeline description 

My pipeline consists of 5 steps as follows: 
* Converting the image to gray-scale 
* Smoothing the gray-scaled image with Gaussian filter
* Applying canny edge detection algorithm on the image to extract the edges
* Using Hough transform in order to find the lines
* Drawing the detected lines on the original image

In order to draw a single line on the left and right lanes, I modified the draw_lines() function. For detecting the lane lines it's important to first understand which of the two lines you are detecting. The lane line on the right hand side of the street has a positive derivative and the lane line on the left has a negative derivative. Another important thing is that the derivative should be bounded because we don't want o consider a line with any slope as part of the lane lines. So the first part will iterate over all the lines detected by the Hough algorithm and divide them in the groups of left and red lane lines and other lines that are ignored. 
For drawing a single line for the left and right line the average slope of all the detected lines is taken and a solid line is drawn in the selected area that we want to consider, where the lane lines are. 


### 2. Potential shortcomings of the pipeline 

The designed pipeline will not perform well on every scenario. Depending on the video streams, and hence the single pictures, the pipeline has some shortcomings. One of the shortcomings is that when there are some other lines on the street, like some damages in the asphalt or temporarily road construction lines, the pipeline will not work. 

Another shortcoming of the pipeline is if the camera position changes on the car and hence the position of the lines relative to the picture change. Also another thing would be sharp curves that the slope o line is really big and the selected region becomes more congested with the lines. 

Also a shortcoming is the dimension of the image and scale of the objects in the image that might cause problems for detecting the lane lines. 


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to not only work with gray scale images but also with other color spaces to identify the lines better in any lightning condition. 

Another potential improvement could be to use some other information, for example how far the lane lines are normally apart from each other to also omit some points and lines that not satisfy this condition. 

Also another improvement could be to use image transformations to view the images from above and find the lane lines better. 

