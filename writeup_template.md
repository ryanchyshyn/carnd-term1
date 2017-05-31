# **Finding Lane Lines on the Road** 

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/image1.png "Final image"

---

### Reflection

### 1. Pipeline descriptiopn.

The pipeline consists of several steps:
1. Grayscale
2. Gaussian blur
3. Canny edge detection
4. Clipping using vertices mask
5. Finding lines using Hough alghorithm and drawing them on separate image
6. Combining previous image with original one

draw_lines() function was modified to draw augment lines along real lines from the bottom to the center of image (defined by mask).
The implementation divides all lines for left inclined and right inclined by comparing line's slope with zero. In case it is greather than 0 the line is left side, otherwise it is right side.
Next the line center point and its slope are saved into the array. There are two sets of arrays for both left and right side. At the end each set will be used to calculate mean values for center point and slope.
And final step is to draw two line from the bottom to the center passing obtained points and using calculated slope:

![alt text][image1]


### 2. Potential shortcomings


There are some shortcoming:
1. Lines drawing alghorithm supports only two lines.
2. The mask is hardcoded.
3. Implementation adjustments are not well tuned so the augment lines sometimes does not fit on actual lines. I believe that fine tuning them will not work in real cases because real cases can be too different. So some sort of automatic adjustments are needed to solve the problem.


### 3. Possible improvements

1. Add some sort of filtering to lines drawing to avoid lines jitter (especially because real lines can't change the location too frequent).
