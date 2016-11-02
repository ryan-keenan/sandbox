## Advanced Lane Finding

The goals / steps of this project are the following:  

* Compute the camera calibration matrix and distortion coefficients given a set of chessboard images.
* Apply the distortion correction to the raw image.  
* Use color transforms, gradients, etc., to create a thresholded binary image.
* Apply a perspective transform to rectify binary image ("birds-eye view"). 
* Detect lane pixels and fit to find lane boundary.
* Determine curvature of the lane and vehicle position with respect to center.
* Warp the detected lane boundaries back onto the original image.
* Output visual display of the lane boundaries and numerical estimation of lane curvature and vehicle position.

---

Please see the included Ipython notebook (in the "code" folder) for a detailed description of the techniques I used to complete each step.  

The main areas where this pipeline could be improved are the following:

1) I'm only using 10 or so images to calibrate the camera.  More calibration images would likely improve the distortion correction.

2) At this point, I'm only using the thresholded red channel for color selection.  A more careful study of the color of the lines and pavement, in and out of shadow could likely improve this selection.

3) I'm only using thresholded SobelX for the gradient selection part.  Exploring other kernels might improve this step.

4) The perspective transform is hardcoded at this point.  When the vehicle bounces or the road is not a flat surface, the result changes, which will affect the measurement of curvature and position.  Having a dynamic perspective transform that is based on some knowledge of the pitch angle of the vehicle (IMU measurement for example) could improve this step.

5) As it is, my pipeline can process around 6 frames per second, which is still a factor of 5 below the framerate of the camera.  To do this in real time, I would need a faster computer or a faster algorithm.  No doubt the speed of the algorithm could be improved if I studied more closely where the bottlenecks are

6) As it is now, my pipeline requires both lines to be detected to find the lane.  I would like to incorporate a mode where one or the other line could be sufficient to attempt to map the lane.  