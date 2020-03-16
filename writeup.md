# **Finding Lane Lines Writeup 

[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

### 1. The Pipeline

This pipeline takes a photo/video as input, detects the cars lane lines, and draws two red lines over the image so you can see what the pipeline sees as your lane lines

The first few functions in the pipeline prepare the image for detecting lines in the image. This involves removing the color channels from the image, using the canny algorithm to map out edges in the image, and using hough transform and a region mask to reduce the edges down to just where enough edges come together to be a line and just where we'd generally expect the road to be in the image. 

Once we have the lines we'll discern which could be related the the left lane and which to the right by taking the slopes of all the lines and bucketing them based on if they have a possitive or negative slope. Then we'll take the avg of each bucket to be the slope of our final, drawn left and right lane lines. From here it's just solving y = mx + b to get our final lane line (x,y) coordinates.  

### 2. Identify potential shortcomings with your current pipeline


The hough lines function parameters and the slope filter function are two critical variables to the final result that are both hand tuned from testing on a small sample of images. 


### 3. Suggest possible improvements to your pipeline

The pipeline would be much more accurate if the main parameters of the function could be chosen automatically from testing on thousands of images. Using a loss function to judge improvement over time. 
