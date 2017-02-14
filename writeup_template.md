#**Finding Lane Lines on the Road** 

##Writeup Template

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

---

### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consists of 7 steps. First I converted to gray scale, then applied a gausian blur, next is canny edge detection,
follwed by selecting only points from the region of interest which is about 1 third of the screen. To this region of the image
I applied a hough space translation to determine which of the points detected formed part of a line. The last two steps are to take 
these detected lines, separate them in those who belong to the right lane and those of to the left lane and drawing them on 
the original image.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by using the slop of each line 
to determine if it belonged to the left lane or the right lane. Then I averaged the points to take the average position of both 
lanes. With this I calculated the equation y = mx + b of both lines and extended them from the botton of the screen to the top of 
the region of interest.

###2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the images have different sizes. The current algorithm doesn't adapt to 
images with different dimensions

Another shortcoming could be a variety of other lines from objects different from the lanes that would throw off the median slope 
of the lines detected (this happens on the optional video).


###3. Suggest possible improvements to your pipeline

A possible improvement would be reducing the region of interest to a more tight zone. Calibrating the parameters to avoid 
smaller and thinner line like objects. Setting maximun and minimun values for the slop of the line to avoid completely off 
lines.

Another potential improvement could be to calculate not only lanes but ending of the road and then extrapolate the lanes from that. 
This would help in roads that aren't marked