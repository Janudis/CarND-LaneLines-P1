# **Finding Lane Lines on the Road** 
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

<img src="examples/laneLines_thirdPass.jpg" width="480" alt="Combined Image" />

Overview
---

When we drive, we use our eyes to decide where to go.  The lines on the road that show us where the lanes are act as our constant reference for where to steer the vehicle.  Naturally, one of the first things we would like to do in developing a self-driving car is to automatically detect lane lines using an algorithm.

In this project you will detect lane lines in images using Python and OpenCV.  OpenCV means "Open-Source Computer Vision", which is a package that has many useful tools for analyzing images.  

To complete the project, two files will be submitted: a file containing project code and a file containing a brief write up explaining your solution. We have included template files to be used both for the [code](https://github.com/udacity/CarND-LaneLines-P1/blob/master/P1.ipynb) and the [writeup](https://github.com/udacity/CarND-LaneLines-P1/blob/master/writeup_template.md).The code file is called P1.ipynb and the writeup template is writeup_template.md 

To meet specifications in the project, take a look at the requirements in the [project rubric](https://review.udacity.com/#!/rubrics/322/view)


Pipeline
---
<img src="test_image_output/solidWhiteRight.jpg" width="480" alt="Combined Image" />

[original]: test_images/solidYellowCurve.jpg "Original"
[yellow]: test_image_output/yellow.jpg "Yellow"
[white]: test_image_output/white.jpg "White"
[gray]: test_image_output/gray.jpg "Gray"
[canny]: test_image_output/canny.jpg "Canny"
[mask]: test_image_output/mask.jpg "Mask"
[hough]: test_image_output/hough_2.jpg "Hough"
[final_result]: test_image_output/solidYellowCurve.jpg "Final result"
[no_grey]: test_image_output/solidYellowCurve_noGrey.jpg "No grey"
[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Here are the few steps that each image goes through

My pipeline consists of of 9 steps. Let's see the result of each of them on this image.

![alt text][original]

1. I extract an image with only the yellow component.

![alt text][yellow]

2. I extract an image with only the white component.

![alt text][white]

3. I extract a grayscale image.

![alt text][gray]

4. I merge these 3 images into 1. It visually gives the same image as above.
5. I blur a little bit the image to smooth out the contours to enhance the result of the next step.
6. I detect the edges (strong gradient in the pixel values) using the canny edges algorithm.

![alt text][canny]

7. I mask the region of the image where I do not expect the lines to be.

![alt text][mask]

8. I perform a hough transform to detect where the lines are.

![alt text][hough]

9. I average, extrapolate and filter the lines I obtain before drawing them on the image with a slight transparency. Here is the final result.

![alt text][final_result]


