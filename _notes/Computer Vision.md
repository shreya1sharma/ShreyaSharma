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
