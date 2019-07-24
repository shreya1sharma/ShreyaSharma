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
	* take second derivative in x and y directions (mexican hat filter)
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
* for scale invariance, keypoints need to be detected at several scales. So 2 questions arise:
	1. how to decide window size (sigma) at each scale?
	2. how to combine different scales?
* SIFT relies on spatial coincidence assumption. It means that if edge (zero-crossing) is detected at same location over several scales, then it truly exists.
* this gave rise to the concept of scale space : plot zero-crossings v/s scale. As we increase scales, number of zero-crossings become lesser.
* interval tree is another representation of scale space which tells how stable is a zero-crossing across scales. A zero-crossing which can sustain several scales before
breaking into more zero-crossings is considered stable.
* in order to create scale space in 2D, we use LOG. Interest points are local maxima in the scale space of LOG. Now the derivatives are computed in 3 directions - X,Y and Scale.
	* also works as a blob detector (?)
* To simplify computation of scale space, LOG is approximated by Difference of Gaussian (DOG). Compute Gaussian with different scales (different sigma/filter size), take difference
of the gaussians.
* After computing DOG, keypoint is selected by comparing a pixel with neighbourhood at 3 different scales. The maximum point is detected as keypoint.
* To localize most valuable keypoints out of all potential keypoints, some methods have been proposed. First is to remove point whose DOG value is less than some predefined threshold. Second,
remove the keypoints that lie on edge by computing eigen values of DOG matrix (similar concept as Harris)
* To extract orientation of keypoint:
	* take a nbhd and compute derivatives in X and Y direction- magnitude and orientation
	* make histogram of orientation to divide nbhd orientations into 36 bins
	* give magnitude as weight (frequency) to each orientation
	* in the histogram, plot orientation v/s weight (frequency) and  find the peak. The peak implies the dominant direction at that keypoint.
* To describe the keypoint, use orientation information as it make the keypoint decription robust to tranformations and lighting variations. Intensity based descriptor is not robust to such changes.
Steps to make a descriptor:
	* take 16x16 nbhd around the keypoint pixel. Divide it into 16 blocks each of 4x4.
	* compute orientation histogram in each block with 8 bins
	* Flatten all the histograms to make 128 1D feature vector/descriptor (16x8)
* for matching, find patches that have the most similar appearance or SIFT descriptor using Euclidean Distance.
* for robustness in matching, take both first match and the second best match into account.
	* if ratio of first/second best is  high -> select the first match, else the match is ambiguous.
**6. HOG**

**7. Optical Flow**

**8. Image Pyramids**

**9. Face Recognition**

**10. Stereo**
* recovering 3D information about an object from a pair of 2D images
* the 3D information is captured in the form of a depth map. Using the depth map, we can synthesize image from different viewpoints- a useful application in computer graphics.
* assumes that images are recified. Image rectification is a method of image correction. The images are aligned such that there is displacement only in X direction and NO displacement in Y direction.
* the depth is computed from disparity. Disparity is the difference in image locations of a same 3D point when projected under perspective of two different cameras (like left and right eye). It arises due to the horizontal difference in location of sensors, known as baseline (parallax). 
* depth is inversely proportional to disparity. 
* to compute disparity, we compare patches along the same rows in the left and right images using correlation measures. The patches which give high correlation area a match. Then, the displacement in x direction of the left and right patch gives disparity (block matching method).
* Important correlations measures are:
	* Sum of squares difference (SSD)
	* Normalized correlation 
	* Mutual correlation
	* Mutual information
	* Minimum absolute difference
* Another method for estimating disparity is Bernard's Stereo method. 
	* Based on two assumptions - similar intensity and smoothness of disparity
	* based on these, an energy funcion is defined which is minimized with any minimization (optimization) technique
	* Bernard's method used simulated annealing
* Current research is on how to estimate depth map from a single image. For ground truth, depth information can be collected through low cost sensors like Kinect. 

**11. Bag-of-words**
* Bag-of-words is a histogram of features (textons) in an image
* Originally designed for comparing two documents. Plotting histogram of words in each document and matching the histograms. If histograms are very similar, the documents match.
* In images, the word is represented by a visual word which represents a particular pattern/texture/feature
* Image classification with bag-of-words has 4 steps:
	* Extract Patches of key-points from image (Harris, SIFT, Dense)
	* Describe patches with a feature descriptor (SIFT, HOG)
	* Clusters the decriptors in feature space. Each cluster repesents a visual word.
	* Create histogram of visual words (bag-of-features), ie how many patches in each cluster
* A classifier compares two images using their bag-of-words. If their bag-of-words are similar, the two images are assigned same class else not.
* Two popular classifiers used in pre-deep learning era were k-means and SVM

**12. Hough Transform**  
* Hough transform is used to detect shapes in an image- lines, circles, ellipses anfd arbitary shapes
* Shapes are high-level features while edges and texture are low-level features
* 3 methods to fit a line on a set of edge points
	* Least square fit (over constraint)
	* RANSAC (constraint)
	* Hough Transform (under constraint)
* Least squares method: simply linear regression
	* fails in case of outliers because it considers all points while fitting line
* RANSAC method (Random Sample Concensus): this method is robust to outliers and noise
	* Randomly selects two points, estimates a line and finds the error between the estimated line and all other possible points
	* Since it is controlled by only 2 points at a time, it estimates the most general line model which satisfies maximum number of points.
	* Assumptions:
		* majority of the good points agree with the underlying model
		* bad samples does not consistently agree with the single model
* The above methods are suitable when the image contains only one line. What if the image contains multiple lines? How to decide which point belongs to which line?
* To solve this, hough transform was invented. In this method an edge-point in X-Y plane is projected as a line in m-c plane.
	* Each edge point is giving a vote for the m-c values.
	* the m-c value which gets maximum votes is selected
* m becomes infinity in case of vertical lines. To tackle this, instead of m-c plane, parametric plane of radius-theta was introduced
* however, noise affects hough transform too
	* if the noise becomes very high, the votes are scattered and becomes difficult to find a single m-c values with maximum votes
	* second if there is no line in an image, hough transform can wrongly give high votes to some m-c value due to noisy points
* same method is also used for detecting circles/ellipses/any shape with no analytical expressun


#### Summary of CV algorithms (algorithm/purpose/use-case)
* 
### To-do
* Motion
* 3D
* Multi-view

[OpenCV python tutorials](https://opencv-python-tutroals.readthedocs.io/en/latest/py_tutorials/py_tutorials.html)

---
