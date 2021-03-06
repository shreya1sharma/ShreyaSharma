---
layout : page
title: Machine Learning and Deep Learning

---

**Important Articles**
1. [Machine learning glossary by Google](https://developers.google.com/machine-learning/glossary/)
2. [Essentials of Machine Learning Algorithms](https://www.analyticsvidhya.com/blog/2017/09/common-machine-learning-algorithms/?utm_source=twitter.com)
3. [Deep learning course summary by analytics vidya](https://www.analyticsvidhya.com/blog/2018/11/neural-networks-hyperparameter-tuning-regularization-deeplearning/)
4. [Cheatsheet – Python & R codes for common Machine Learning Algorithms](https://www.analyticsvidhya.com/blog/2015/09/full-cheatsheet-machine-learning-algorithms/)
5. [Troubleshooting Deep Neural Networks by Josh Tobin]({{site.url}}{{ site.baseurl }}/assets/docs/troubleshooting-deep-neural-networks-01-19.pdf) 


---
**Topics**

1. **Cross-validation**

2. **Multi-task Learning**

* a kind of regularization or conditioning with auxillary tasks. Reduced model complexity by adding additional priors which reduces overfitting.
* dual benefits- improvement in main task and additional outputs from auxillary tasks
* can train the model with multiple losses and weigh each loss as per our requirement. Also we can distribute the losses at multiple layers taking inspiration from human cortex.
* can help the model focus its attention on those features that actually matter as other tasks will provide additional evidence for the relevance or irrelevance of those features.
![image]({{site.url}}{{site.baseurl}}/assets/images/multi-task.jpeg){:style="centre;margin-right: 200px;margin-top: 7px;" height="400px" width="400px" }

* Why does different close tasks help to learn the main task or why they can learn jointly together?
	
	* <u>Regularization</u> - additional loss adds regularization, smoothes the loss function, minimize the complexity of model and gives very informative priors to the model.
	
	* <u>Representation Bias</u> - when you train a model over an intersection of several tasks, you push your learning algorithm to find a solution on a smaller area of representation on the intersection rather than on a large area of a single task. It leads to better and faster convergence. 
	
	* <u>Feature Selection Double Check</u> - if one feature is importnat for more than just one task, then most probably this feature is indeed very important and representative of your data.
	
	* <u>O/Ps that can't be inputs</u> - certain past observations have an influence on future observations, so we can use them as auxillary loss functions to regularize our model for 'knowing about them. Same goes with features that are too difficult to calculate in testing phase but we can add them as extra info in our model.

	* <u>Transfer Learning</u> - instead of first learning one task and then using the same model to learn another task over it, we jointly learn the tasks and has shown better performance.

References:
1. [An Overview of Multi-Task Learning in Deep Neural Networks](http://ruder.io/multi-task/)
2. [Multitask learning: teach your AI more to make it better](https://towardsdatascience.com/multitask-learning-teach-your-ai-more-to-make-it-better-dde116c2cd40)


* Why deep learning?
- conventional machine learning methods can not utilize the power of big data

* Why sudden boom?
- lots of data
- computational power
- new algorithms for fast optimization

* types of data
- structured
- unstructured (deep learning very strong here)

* Logistic regression
- classification algorithm
![image]({{site.url}}{{site.baseurl}}/assets/images/lr.jpg){:style="centre;margin-right: 200px;margin-top: 7px;" height="400px" width="400px" }
- steps:
	forward propagation
	- data : (x,y)
	- compute z = w1x1+w2x2+b
	- compute a = sigmoid(z)
	- compute loss = L(a,y)
	- compute cost J(w) = average loss calculated over all training samples
	
	backward propagation
	- compute gradient of loss/cost wrt to weights : dL/dw = dL/da * dL/dz * dz/dw
	- update weights using gradient descent: w := w - alpha*dL/dw
	
	compute forward propagation again
	
* loss function
- mean squared error : does not work well in logistic regression (?)
- cross-entropy : -log(likelihood)

* Shallow Neural Network
- series of logistic regression units
![image]({{site.url}}{{site.baseurl}}/assets/images/nn.jpg){:style="centre;margin-right: 200px;margin-top: 7px;" height="400px" width="400px" }


* Activation functions
1. Sigmoid - binary classification, output layer
2. Tanh - normalized sigmoid, centers the data to avoid extremes which improves learning
3. Relu - removes negative activations, hidden layer, removes vanishing gradient
4. Leaky relu - to avoid undefined slope at (0,0)

- with no activation a = z, so no non-linearity is learnt by the network. Thus, the whole neural network simply becomes linear regression

* Initialization of weights
- if all weights are intialized to zero, all activations are same, all nodes have same effect on output, all weights are 
updated by same amount. Al units learn exactly the same features - no new learning
- to break this symmetry, weights are initialized randomly
- also, weights should be small to prevent extreme values of activation which cause vanishing gradient
	
* Deep neural network 
- learn more complex features than shallow networks
- require lot of data and computation power
	
	

