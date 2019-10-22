---
layout : page
title: Deep Learning Practical

---

### How to deal with highly imbalanced data?

1. Data - 
  * undersampling
  * oversampling
  * SMOTE
  * synthetic samples
  
2. Model -
  * class-weights proportional to number of samples
  * large batches so that each batch contains at least a few positive samples
  * monitor precision and recall, not accuracy
  * focal loss
  
  References\
  [How to handle imbalance data](https://blogs.oracle.com/datascience/how-to-handle-imbalanced-data%3a-an-overview)\
  [Handling imbalance dataset in deep learning](https://towardsdatascience.com/handling-imbalanced-datasets-in-deep-learning-f48407a0e758)\
  [Keras Notebook by F. Chollet](https://colab.research.google.com/drive/1xL2jSdY-MGlN60gGuSH_L30P7kxxwUfM#scrollTo=pdzsLQQgJMib)\
