---
layout: post
title: >
    CNN-BinaryClassificationProblem 
tags: [CNN]
---

* TOC
{:toc}

# Applying Convolution Neural Network to a binary classification problem

This is the final project for my Data Science class. 
- Here is the [link of the problem from Kaggle](https://www.kaggle.com/paultimothymooney/chest-xray-pneumonia)
- Here is the [my presenation file](https://github.com/tranktle/porfolio/blob/master/pdfs/CNN_ChestImage.pdf)
- Here is the [jupyter notebook file that applies basic CNN models](https://github.com/tranktle/porfolio/blob/master/jupyternotebook/Final_ChestImage.ipynb)
- Here is the [link to CNN_tuning jupyter_notebook](https://github.com/tranktle/porfolio/blob/master/jupyternotebook/Tune_ChestImage.ipynb)

Overall, my accuracy is arround 90% 

# Detail of the project: 

## A basic CNN model 

```python
np.random.seed(35675)
tf.random.set_seed(1352)

model1 = keras.Sequential([
   AveragePooling2D(6,3, input_shape=(img_dims,img_dims, 3)), 
   Conv2D(64, 3, activation='relu'),
   Conv2D(32, 3, activation='relu'),
   MaxPool2D(pool_size=(2,2)),  # so we use max pool to reduce size of image
   Dropout(0.5),    # we can drop out some connection
   Flatten(),
   Dense(128, activation='relu'),  #add another dense layer before doing the output layer
   Dense(1, activation='sigmoid')
])
```
When applying basic CNN model, the accuracy on the test set is 0.77960. We can improve the accuracy better and prevent some problems that can arrive with a CNN problem. 
Some common problems and solutions are

## Some problems and common solutions to be considered: 

1. Vanishing/Exploding Gradient Problems: the gradients/signals die out or explode and saturate.
    - Glorot and He Initialization: 
    - Nonsaturating Activation Functions: leaky ReLU.
    - Batch Normalization

2. Callbacks - A  solution to prevent overfitting and wasting of time and resouces. Common callbacks are:
   
    - `ModelCheckpoint`: helps save checkpoint (by default) at the end of each epoch . Helps return the best model on the validation set. 
    - `Earlystopping`: will interrupt training when it measures no progress on the validation set for a number of epochs and it will optionally roll back to the best model.

3. Overfitting and some common solutions:
    - Simplifying The Model: decrease the complexity of the model by remove layers or reduce the number of neurons.
    - Early Stopping: 
    - Use Data Augmentation:
    - Use Regularization (L1, L2, Max-Norm regularization)
    - Use Dropouts (with fixed dropout rate) and Monte-Carlo 

## A better CNN model for the problem: 












