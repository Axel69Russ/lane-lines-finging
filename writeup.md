# **Finding Lane Lines on the Road** 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

---

## 1. Pipeline description.

My pipeline consist of following steps:

### 1. Convert image to grayscale. 
At this step we'r converting image into grayscale. To detect edges we don't need any color information:

[image1]: ./test_images_pipeline/grayscale.jpg "Grayscale"

![alt text][image1]

### 2. Applying Gausian blur. 
At this step we'r applying Gausian blur to the image. It helps us to get rid of noise.

[image2]: ./test_images_pipeline/blur.jpg "Blur"

![alt text][image2]

### 3. Finding edges using Canny. 
 At this step we'r applying Canny transform to the image to get image that contains only edges:

[image3]: ./test_images_pipeline/canny.jpg "Canny"

![alt text][image3]

### 4. Defining region of intrest.
At this step we define region of intrest to exclude all pixels that are beyond this region

[image4]: ./test_images_pipeline/region.jpg "Region"

![alt text][image4]

### 5. Finding lines. 
Probobly most important step in this pipeline. In this step Hough transform are applyed to the image. After that, we gets a lot of short lines, but we need only two dense line. To get them, we need to average this lines. But first, we should decide if line is left or right. To do that, I calculated line's slope and add condition that if slope is negative - line is left, if positive - line is right. As well, I added threshold to exclude lines that are close to horisontal. After that, I average all left and right lines to find two extrapolated lane lines.

[image5]: ./test_images_pipeline/final.jpg "Lines"

![alt text][image5]

## 2. Potential shortcomings with your current pipeline

One potential shortcoming would not stable behevior at too bright and too dark regions.

Another shortcoming could be if some car or somthing diffirent from lane lines apear in the region of intrest then lane lines could be finded incorrectly.


## 3. Suggest possible improvements to your pipeline

A possible improvement would be to play with different parameters of Hough and Canny transworms to get more reliable behavior in diffirent light condition.

Another potential improvement could be to make region fo intrest shorter to except getting into this region other objects.
