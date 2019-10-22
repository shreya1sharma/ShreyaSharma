---
layout : page
title: Deep Learning Theory

---

### Introduction

1. Why deep learning?
- conventional machine learning methods can not utilize the power of big data
- their performance saturates after a certain number of data

2. Why sudden boom?
- lots of data
- computational power
- new algorithms for fast optimization

3. Types of data
- structured - housing prices, financial
- unstructured - Images, Audio, Speech, Text (deep learning very strong here)

4. Logistic regression
- classification algorithm

![image]({{site.url}}{{site.baseurl}}/assets/images/lr.jpg){:style="centre;margin-right: 200px;margin-top: 7px;" height="200px" width="400px" }
- 2 steps:

	step 1: forward propagation
	- data : (x,y)
	- compute z = w1x1+w2x2+b
	- compute a = sigmoid(z)
	- compute loss = L(a,y)
	- compute cost J(w) = average loss calculated over all training samples
	
	step 2: backward propagation
	- compute gradient of loss/cost wrt to weights : dL/dw = dL/da * dL/dz * dz/dw
	- update weights using gradient descent: w := w - alpha*dL/dw
	
	Then, compute forward propagation again and repeat the process
	
5. Loss function
- measures how good is our classifier by comparing the predicted value with the true value
- we minimize the loss function to achieve the best parameters for the classifier
- minimization of loss function (or cost function) is done using gradient descent
- common loss functions are:
	- mean squared error : does not work well in logistic regression (?)
	- cross-entropy : -log(likelihood)
- cost function is summation of loss over all the training samples

6. Gradient descent
7. Maximum likelihood estimation
8. Perceptron



. Shallow Neural Network
- series of logistic regression units

![image]({{site.url}}{{site.baseurl}}/assets/images/nn.jpg){:style="centre;margin-right: 200px;margin-top: 7px;" height="200px" width="400px" }


8. Activation functions

1. Sigmoid - binary classification, output layer
2. Tanh - normalized sigmoid, centers the data to avoid extremes which improves learning
3. Relu - removes negative activations, hidden layer, removes vanishing gradient
4. Leaky relu - to avoid undefined slope at (0,0)

- with no activation a = z, so no non-linearity is learnt by the network. Thus, the whole neural network simply becomes linear regression

9. Initialization of weights
- if all weights are intialized to zero, all activations are same, all nodes have same effect on output, all weights are 
updated by same amount. All units learn exactly the same features - no new learning
- to break this symmetry, weights are initialized randomly
- also, weights should be small to prevent extreme values of activation which cause vanishing gradient
	
10. Deep neural network 
- learn more complex features than shallow networks
- require lot of data and computation power
	
	

