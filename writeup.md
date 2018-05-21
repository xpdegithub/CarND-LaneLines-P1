#**Finding Lane Lines on the Road** 

##Writeup Template

###You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

---

### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 6 steps.
1. I converted the images to grayscale
2. The grayscale images are smoothed by gausssian function to remove the noises
3. Canny edge detection is applied to detect edges
4. interested area is selected with some parameter tuning
5. Hough transform is used to detect lines, the lines are drawn by draw_line()function.
6. The detected lines are combined to original image and showed.


In order to draw a single line on the left and right lanes, I modified the draw_lines() function by following steps:
1. calculate the slope of lines
2. delete noise lines (vertical, parallel and small slope lines)
3. seperate lines to right and left lane groups use calculated slope infomation
4. save the start and end points of all reasonable lines (seperate to left and right lane)
4. average the start and end points of each lane
5. set y value of bottom point to y size of image, set y value of top point to smallest y value of all lines
6. use averaged point,slope and bottom/top value in y direction to calculate the corresponding bottom/top value in x direction
7. draw lanes 



###2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when a car jump into the detected lanes.

Another shortcoming could be the pipeline may not able to work properly in case of uneven roads.

Another shortcoming could be occured during lane change scenario  



###3. Suggest possible improvements to your pipeline

A possible improvement would be to use the steering angle and heading of the car as input
Another potential improvement could be to design function to adjust the parameters online
