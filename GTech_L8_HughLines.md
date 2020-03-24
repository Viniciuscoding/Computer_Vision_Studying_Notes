# Lesson 8 - Hough Transform: Lines

### cv2.HoughLines(image, rho, theta, threshold[, lines[, minLineLength[, maxLineGap]]]) → lines
**Parameters:**
```
  image – 8-bit, single-channel binary source image. The image may be modified by the function.
  lines – Output vector of lines. Each line is represented by a 4-element vector (x_1, y_1, x_2, y_2) , where (x_1,y_1) 
          and (x_2, y_2) are the ending points of each detected line segment.
  rho – Distance resolution of the accumulator in pixels.
  theta – Angle resolution of the accumulator in radians.
  threshold – Accumulator threshold parameter. Only those lines are returned that get enough votes ( >\texttt{threshold} ).
  minLineLength – Minimum line length. Line segments shorter than that are rejected.
  maxLineGap – Maximum allowed gap between points on the same line to link them.
```
  
**Python program to illustrate HoughLines: method for line detection**
```
import cv2 
import numpy as np 
  
# Reading the required image in which operations are to be done. Make sure that the image is in the same directory in which this python program is

img = cv2.imread('image.jpg') 
gray = cv2.cvtColor(img,cv2.COLOR_BGR2GRAY) # Convert the img to grayscale 
edges = cv2.Canny(gray,50,150,apertureSize = 3) # Apply edge detection method on the image 
  
lines = cv2.HoughLines(edges,1,np.pi/180, 200) # This returns an array of r and theta values 
  
# The below for loop runs till r and theta values are in the range of the 2d array 
for r,theta in lines[0]: 
      
    a = np.cos(theta)         # Stores the value of cos(theta) in a 
    b = np.sin(theta)         # Stores the value of sin(theta) in b 
      
    x0 = a*r                  # x0 stores the value rcos(theta)
    y0 = b*r                  # y0 stores the value rsin(theta) 
  
    x1 = int(x0 + 1000*(-b))  # x1 stores the rounded off value of (rcos(theta)-1000sin(theta)) 
    y1 = int(y0 + 1000*(a))   # y1 stores the rounded off value of (rsin(theta)+1000cos(theta)) 

    x2 = int(x0 - 1000*(-b))  # x2 stores the rounded off value of (rcos(theta)+1000sin(theta))
    y2 = int(y0 - 1000*(a))   # y2 stores the rounded off value of (rsin(theta)-1000cos(theta)) 
      
    # cv2.line draws a line in img from the point(x1,y1) to (x2,y2).
    # (0,0,255) denotes the colour of the line to be drawn. In this case, it is red.  
    cv2.line(img,(x1,y1), (x2,y2), (0,0,255),2) 
      
# All the changes made in the input image are finally written on a new image houghlines.jpg 
cv2.imwrite('linesDetected.jpg', img)
```  
  
# Lesson 8 - Hough Transform: Circles

### cv2.HoughCircles(image, method, dp, minDist[, circles[, param1[, param2[, minRadius[, maxRadius]]]]]) → circles
**Parameters:**
```
image – 8-bit, single-channel, grayscale input image.
circles – Output vector of found circles. Each vector is encoded as a 3-element floating-point vector (x, y, radius) .
circle_storage – In C function this is a memory storage that will contain the output sequence of found circles.
method – Detection method to use. Currently, the only implemented method is CV_HOUGH_GRADIENT , which is basically 21HT,                described in [Yuen90].
dp – Inverse ratio of the accumulator resolution to the image resolution. For example, if dp=1 , the accumulator has the same        resolution as the input image. If dp=2 , the accumulator has half as big width and height.
minDist – Minimum distance between the centers of the detected circles. If the parameter is too small, multiple neighbor                 circles may be falsely detected in addition to a true one. If it is too large, some circles may be missed.
param1 – First method-specific parameter. In case of CV_HOUGH_GRADIENT , it is the higher threshold of the two passed to the            Canny() edge detector (the lower one is twice smaller).
param2 – Second method-specific parameter. In case of CV_HOUGH_GRADIENT , it is the accumulator threshold for the circle                centers at the detection stage. The smaller it is, the more false circles may be detected. Circles, corresponding to            the larger accumulator values, will be returned first.
minRadius – Minimum circle radius.
maxRadius – Maximum circle radius.
```

**Python program to illustrate HoughCircles: method for line detection**
```
import cv2 
import numpy as np 
  
img = cv2.imread('eyes.jpg', cv2.IMREAD_COLOR)                # Read image.
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)                  # Convert to grayscale. 
gray_blurred = cv2.blur(gray, (3, 3))                         # Blur using 3 * 3 kernel. 

# Apply Hough transform on the blurred image. 
detected_circles = cv2.HoughCircles(gray_blurred,  
                   cv2.HOUGH_GRADIENT, 1, 20, param1 = 50, 
                   param2 = 30, minRadius = 1, maxRadius = 40) 
  
# Draw circles that are detected. 
if detected_circles is not None: 
  
    detected_circles = np.uint16(np.around(detected_circles)) # Convert the circle parameters a, b and r to integers. 

  
    for pt in detected_circles[0, :]: 
        a, b, r = pt[0], pt[1], pt[2] 
  
        cv2.circle(img, (a, b), r, (0, 255, 0), 2)            # Draw the circumference of the circle. 
        cv2.circle(img, (a, b), 1, (0, 0, 255), 3)            # Draw a small circle (of radius 1) to show the center. 

        cv2.imshow("Detected Circle", img) 
        cv2.waitKey(0)
```



