---
layout: post
title: >
    CNN-BinaryClassificationProblem 
tags: [CNN]
---

* TOC
{:toc}

# Link to the problem and jupyter notebook files

This is the final project for my Data Science class. 
- Here is the [link of the problem from Kaggle](https://www.kaggle.com/paultimothymooney/chest-xray-pneumonia)
- Here is the [my presenation file](https://github.com/tranktle/porfolio/blob/master/pdfs/CNN_ChestImage.pdf)
- Here is the [jupyter notebook file that applies basic CNN models](https://github.com/tranktle/porfolio/blob/master/jupyternotebook/Final_ChestImage.ipynb)
- Here is the [link to CNN_tuning jupyter_notebook](https://github.com/tranktle/porfolio/blob/master/jupyternotebook/Tune_ChestImage.ipynb)

Overall, my accuracy is arround 90% 

# Detail of the project 

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

## Some problems and common solutions to be considered

1. Vanishing/Exploding Gradient Problems: the gradients/signals die out or explode and saturate.
    - Glorot and He Initialization: 
    - Nonsaturating Activation Functions: leaky ReLU.
    - Batch Normalization

2. Callbacks - A  solution to prevent overfitting and wasting of time and resouces. Common callbacks are:
   
    - `ModelCheckpoint`: helps save checkpoint (by default) at the end of each epoch . Helps return the best model on the validation set. 
    - `Earlystopping`: will interrupt training when it measures no progress on the validation set for a number of epochs and it will optionally roll back to the best model.

3. Overfitting and some common solutions
    - Simplifying The Model: decrease the complexity of the model by remove layers or reduce the number of neurons.
    - Early Stopping: 
    - Use Data Augmentation:
    - Use Regularization (L1, L2, Max-Norm regularization)
    - Use Dropouts (with fixed dropout rate) and Monte-Carlo 

## A better CNN model for the problem
```python
seed = 240
np.random.seed(seed)
tf.random.set_seed(seed)

input_shape = Input(shape=(img_dims, img_dims, 3))

model2 = keras.Sequential([
    Conv2D(filters=16, kernel_size=(3, 3), activation='relu', padding='same', input_shape=[img_dims, img_dims, 3]),
    BatchNormalization(), # use Batch Normalization to address the vanishing/exploding gradients problems
    MaxPool2D(pool_size=(2, 2)),
    
    Conv2D(64, 3, activation='relu'),
    Conv2D(32, 3, activation='relu'),
    
    #Note: Instead of using a convolutional layer with a 5 × 5 kernel, 
    # it is generally preferable to stack two layers with 3 × 3 kernels:
    # it will use less parameters and require less computations, and will usually perform better (page447 Hand_on)
    SeparableConv2D(filters=64, kernel_size=(3, 3), activation='relu', padding='same'),
    SeparableConv2D(filters=64, kernel_size=(3, 3), activation='relu', padding='same'),
    BatchNormalization(), 
    MaxPool2D(pool_size=(2, 2)),
    
    #Note: Note that the number of filters grows as we climb up the CNN towards the output layer (64, 128, 256) (page448 Hanh-on)
    SeparableConv2D(filters=128, kernel_size=(3, 3), activation='relu', padding='same'),
    SeparableConv2D(filters=128, kernel_size=(3, 3), activation='relu', padding='same'),
    BatchNormalization(),  
    MaxPool2D(pool_size=(2, 2)),
    Dropout(0.2),   
    
    SeparableConv2D(filters=256, kernel_size=(3, 3), activation='relu', padding='same'),
    SeparableConv2D(filters=256, kernel_size=(3, 3), activation='relu', padding='same'),
    BatchNormalization(),  
    MaxPool2D(pool_size=(2, 2)),
    Dropout(0.2), 
    
    #Note: we must flatten its inputs, since a dense network expects a 1D array of features for each instance
    Flatten(),
    Dense(128, activation='relu'),  #add another dense layer before doing the output layer
    Dropout(rate=0.5),     #NOte: dropout to prvent overfitting
    Dense(units=64, activation='relu'),
    Dropout(rate=0.5),
    Dense(1, activation='sigmoid')
])
```
With this approach, the model stops training at echo=9 and gives testing accuracy is  0.901315

## Tuning the CNN model 

The detail can be found on [jupyter notebook file that applies basic CNN models](https://github.com/tranktle/porfolio/blob/master/jupyternotebook/Final_ChestImage.ipynb) and 
[link to CNN_tuning jupyter_notebook](https://github.com/tranktle/porfolio/blob/master/jupyternotebook/Tune_ChestImage.ipynb), over all, the accuracy is not much better than the modified CNN model. 

| | 1.Simple Model | 2. A mmodified model| 3.A model with tuned hyper-parameter with callbacks | 4.A model with tuned hyper-parameter without callbacks|
|-|-|-|-|-|
|Validation accuracy|  0.8438 | 0.8887 | 0.9232 | 0.9587
|Test accuracy| 0.7796| 0.9013 | 0.8026 |  0.9086













