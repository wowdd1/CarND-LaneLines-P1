#**Finding Lane Lines on the Road** 

##Writeup
---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps:

    1. convert image to grayscale image
    2. do a gaussian blur to image, the kernel size is 5
    3. apply canny transform for find the edges
    4. find the interest region
    5. do a hough transform on image

In order to draw a single line on the left and right lanes, I modified the draw_lines() function

    1. computer slope by (y2-y1)/(x2-x1)
    2. if slope larger than zero, the line is on the right, else on the left
    3. calculate the mean slope and center for left and right lines
    4. calculate intercept by b = y - slope * x
    5. define y_min=320
    			 y_max=img.shape[0]
    6. calculate x coordinate by y_min and y_max for left and right line
    7. modify the thickness parameter to 8 for draw_lines function
    8. draw the left and right line on image


###2. Identify potential shortcomings with your current pipeline

The code can not find the curve on the road


###3. Suggest possible improvements to your pipeline

A possible improvement would be to convert the image from RGB to HSL color space for robustness (https://medium.com/towards-data-science/finding-lane-lines-on-the-road-30cf016a1165#.blan5k8qr)

Another improvement  is use Robust Extrapolation of Lines in Video Using Probabilistic Hough Transform (https://medium.com/@esmat.anis/robust-extrapolation-of-lines-in-video-using-linear-hough-transform-edd39d642ddf#.rgxbxlvx2)
