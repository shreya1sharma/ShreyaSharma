---
layout : page
title: Computer Vision

---

**1. Overview** 
* computer vision is the ability of the computers to see 
* can be divided into 4 broad categories:
	1. low-level vision : image to image 
		* image processing techniques
		* template matching
		* optical flow
		* motion models
	2. mid-level vision : image to features
		* interest point detection
		* harris corner detector
		* SIFT
		* HOG
		* Hough Transform
		* RANSAC, Least Squares
		* Segmentation and clustering (watershed, grabcut etc.)
		* foreground extraction
		* deformable contours
	3. high-level vision : features to analysis [Deep learning part]
		* face recognition
		* classification/detection/segmentation
		* OCR
		* emotion recognition
		* action recognition
	4. multiview
		* local-invariant feature detection and decription
		* image tranformations and alignment
		* planar homography
		* epipolar geometry and stereo
		* stereo vision
		* object tracking
		* 3D scene understanding
		* 3D segmentation and modelling
* Image formation depends on - 
	* light source
	* camera (intrinsic and extrinsic parameters)
	* scene (surface shape, surface reflectance)
* Real world 3D points are mapped to a 2D image planes through projection models. Two famous projection models are:
	* perspective projection (also called pin hole camera projection) : takes object depth into account (perpective)
	* orthographic projection : object and camera are so far away that the depth cannot be estimated
* Shape from X : estimating the shape of an object from certain cues. The cues are obtained from X which can be:
	* stereo - it is about estimating the depth map which tells the distance between the object and camera. Depth map has many useful apps.
	* motion (Structure from motion SfM)- good application in 3D reconstruction
	* shading
	* texture - gives an idea of 3D information
	* contours
* some mathematical tools used commonly in CV algos
	* neighbourhood (context) 
	* taking derivatives (gradient)
	* taylor series to approximate a function at a point
	* eigen vectors and eigen values to reduce dimensionality span the most dominant information space
	* pseudo-inverse to find inverse of non-square matrix

**2. Filtering**

* Filtering means transforming image pixel values using a function (filter) of the neighbourhood
* can be linear filtering (output value is linear combination of neighborhood pixels) or non-linear filtering (non-linear)
	* Linear Filtering (enhance image - blur & sharpen, edge detect, image countours, convolution)
	* Non Linear Filtering (Median, Bilateral Filter, morphology)
* image has noise due to several factors: light variations, camera reflectance, surface reflectance, lens
	* additive noise model : I'(x,y) = I(x,y) + n(x,y) where n(x,y) is a noise generally modelled as gaussian distribution
* derivative means taking difference of neighbourhood pixels. image derivatives measure the rate of change of intensity in x and y directions
	* forward difference, backward difference, central difference
	* detects edges
	* taking derivatives over a window reduces noise by distributing it in the neighbourhood
* averaging means taking mean of neighbourhood pixels
	* smoothens the image
	* the mean can be weighted or unweighted. If weighted, the weights come from gaussian distribution.
	* a filter of size 3x3 covers full gaussian distribution with sigma = 1
	
**3. Egde Detection**

* edges are discontinuities in intensity in an image
* several models: step, roof, ramp, spike
* noise strongly affects edge detection. To tackle this, neighbourhood info is take into account and smoothing. Smoothing forces the pixels
different in neighbourhood to look alike. Amount of smoothing is controlled by sigma.
* edge detectors:
	* gradient operators (1st dereivative) : prewitt, sobel
	* laplacian of gaussian (2nd derivative) : Marr-Hildreth
	* gradient of gaussian (Canny)
* gradient operators
	* compute derivatives in x and y direction
	* compute gradient magnitude
	* threshold gradient magnitude
* Laplacian of gaussian : taking 2nd derivative of gaussian
	* smooth the image with gaussian filter
	* take second derivative in x and y directions
	* find zero crossings 
	* compute slope of the zero crossings. Slope tells the strength of the edge.
	* apply threshold to the slope 
* Quality of edge:
	1. true edge (less number of FP)
	2. robust to noise (less number of FN)
	3. localized (1 pixel width)
	4. not too many or too less responses
* Canny Edge Detector is based on three criteria : 1) good detection (less FN and FP), 2) good localization (as close as possible to true edge), 3) single response contraint (return 1 point only for each edge point)
* Steps of canny:
	1. smooth the image with gaussian filter
	2. compute derivative (gradient)
	3. compute magnitude and orientation of gradient. Using orientation is the inventive step.
	4. apply non-maximum suppression
		* check the magnitude of neighbouring pixels along the edge direction. Mark the pixel with the largest magnitude.
		Note edge direction (gradient direction) is always perpendicular to edge.
	5. apply hysterisis threshold
		* uses dual threshold - high and low
		*  <low -> no edge, >high -> edge, between high-low -> if connected to an edge point then edge else not
	
**4. Interest Point Detection**
* 3 main components with local features extracted using neighbourhood- 1. Detection 2. Description 3. Matching
	* Detection : we want to find same points in the two images independently. 
	* Description : we want to be able to describe each point in order to reliably determine which point goes with which	
	* Matching : we want to match the corresponding points
* interest point should have a very expressive texture. The point at which the direction of the boundary of an object changes abruptly.
* a good interest point detector should detect all true keypoints with well localization and robust to noise.
* corner is a key point which is unique, can be localized and robust to noise. Harris corner detector is used for detecting corners.
	* unlike edges and flat areas, corners do not suffer from aperture problem. Aperture probelm occurs when there is ambiguity in matching points when we look a very small area
* Harris corner detector:
	* Main idea is that corner occurs where there is a strong change in intensity in all directions. For this, auto-correlation is computed between intensities in a window and those in a slightly shifted window. The window which gives strong autocorrelation has a corner.
	* The autocorrelation equation reduces to the equation of an ellipse by apporximating using taylor series. 
	* Compute the eigen values of ellipse to find the axis of maximum variation
		* if both eigen values are small -> flat region (no variation along any axis)
		* if one eigen value is large while other is small -> edge (variation along only one axis)
		* if both eigen values are large -> corner (variation along both axis)
	* there are different measures of 'cornerness' derived from eigen values- Triggs, shi-tomasi etc
* traditionally, harris corner detection with template matching was used for image matching.	
* problem with corner keypoint : when the scale of the image changes, the corner may appear as an edge.
* also, template matching does not work when the image rotates

**5. SIFT**
* so we needed a keypoint detection which is invariant to scale and rotation, hence SIFT
* advantages are:
	* uses local information so robust to occlusion and clutter
	* distintiveness so can be used to match with large database of images with many variations
	* quantity, many features for even small objects
	* efficient and fast
* main 4 steps (PLOD):
	1. detect potential key points 
	2. localize key point
	3. assign orientation to the keypoint
	4. describe the keypoint

	
**4. Interest Point Detection**

**5. SIFT**

**6. HOG**

**7. Optical Flow**

**8. Image Pyramids**

**9. Face Recognition**

**10. Stereo**

**11. Bag-of-words**

**12. Hough Transform**  

#### Summary of CV algorithms (algorithm/purpose/use-case)

### To-do
* Motion
* 3D
* Multi-view

---
