#**Finding Lane Lines on the Road** 

##Writeup

---

### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

1- Image is converted to gray scale (grayscale).
2- The image is blur to get rip of edges that I dont care about (gaussian_blur).
3- Get edges (canny)
4- Using the image shape I get the vertices to isolate the area with the lane lines.
5- Get the specific area with the edges that I care about (region_of_interest).
6- Get an image with the left and right lines (hough_lines).
    6.1- Get lines in parameter space (HoughLines).
    6.2- Split of the lines according to its slope (getLinesBySide).
    6.3- Getting the mean of all left lines.
    6.4- Getting the mean of all right lines.
    6.5- Draw lines (draw_line).
7- Again, using the same vertices I limit the size of the right and left lines (region_of_interest).
8- I get the combination of the original image with the image that only contains the left and right lines (weighted_img).

The draw_lines() function was interchanged by draw_line. This function takes a line in the parameter space form and transform it to the Cartesian form.

###2. Identify potential shortcomings with your current pipeline


The calculation of the vertices needs to be more dynamic. 


###3. Suggest possible improvements to your pipeline

Try to keep a history of the lines through out the frames could help to calculate a better average.