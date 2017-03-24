**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./result_images/graystyle.png "graystyle"
[image2]: ./result_images/guassian.png "gaussian"
[image3]: ./result_images/canny_img.png "canny"
[image4]: ./result_images/hough_lines_img.png "hough_lines"
[image5]: ./result_images/result.png "result"

---

### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps: 
1) I converted the images to grayscale. There is no advateges to use color image
2) gaussian blur to remove noises
3) region_of_interest to use only the interesting part of the image / video
4) hough_lines transformation to convert pixels to the lines
5) weighted_img to combine 2 images (before and after) and check the results

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by the next algorithm:
1) ((y2-y1)/(x2-x1)) to get slope
2) group lines by slope < 0 and slope > 0
3) concatenate grouped line into two lines

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]
![alt text][image2]
![alt text][image3]
![alt text][image4]
![alt text][image5]


###2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when we will not have lines on the road.

Another shortcoming could be thet every student tried to find parameters in empirical way. Tried to find what suits best.


###3. Suggest possible improvements to your pipeline

A possible improvement would be to train system to learn parameters for the functions dynamically. I mean parameters like: threshold, min_line_length, max_line_gap...