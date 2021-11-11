---
title: The heart of Deep Learning
layout: post
author: jpablo
post-image: /assets/images/blogimages/figs-11-09/file-20201210-18-elk4m.jpg
description: Basics and example of a neural network.
tags:
- Keras
- Neural Network
- Deep Learning
- Layers
- Sequential
---

### Introduction - What is a neural network?

![nn](/assets/images/blogimages/figs-11-09/neural%20network.PNG)

Neural networks are a form of machine learning composed of layers of nodes whose role is to learn patterns in the training data fed to it and match those patterns 
to the label set for each item. The example we will run through is a data set which contains images of numbers 0 through 9 with their respective labels. Our goal
is to effectively determine which number corresponds to each image.

In simple words, a neural network has an input layer (we input each image), an output layer (the layer that outputs which number the image represents), and several
hidden layers in between through which each image runs. Weights are assigned to each node that represent the importance of that particular characteristic in the data
in order to eventually determine the final prediction. The following is an example of how we might think of this process.

![example](/assets/images/blogimages/figs-11-09/example%20nodes.PNG)

When we determine whether the image above is a six, we might perhaps look for certain characteristics. For example, we might be looking for a circle or an oval connected to
a diagonal or curved line above it. A neural network works similarly in the sense that it looks for patterns that will help it determine whether it is looking at a six or
another number. Each layer and node will look at a different piece and, in the end, it will put all those pieces together. Now, let’s dive a little deeper.

### Install Keras

On your terminal window, run the following command:
`pip install keras`

### Dependencies for this example

For our example, you will need to install the following libraries 
```
import numpy as np
from random import randint
import matplotlib.pyplot as plt
from sklearn.metrics import confusion_matrix
import itertools
import os.path as path

import keras
from keras.datasets import mnist
from keras.models import Sequential
from keras.layers import Dense
```

We will not go through the cleanup and prepping of the data in this article but you can find the complete jupyter notebook with more detail [here]().

### Creating a neural network

Keras is equipped with different ways to build your model. However, the Sequential model is the simplest and for our basic example, it will suffice. We instantiate our
model object with the command `model = Sequential()`.

Next, we have to create layers. Some of the most common types of layers are:
- Dense (Fully interconnected)
- Convolucionary (Image data)
- Recurrent (For time series)

In our prep work of the data, we have vectorized and normalized each image into an array of values between 0 and 1. Therefore, we will use Dense layers to analyze the data.
We add a layer to our model like so:
```
# Define input layer
layer_input = Dense(units=512, activation='sigmoid', input_shape=(image_size,))
# Add layer to model
model.add(layer_input)
```
The units are the number of neurons within the layer and choosing the number is outside the scope of this article. The activation function determines the output from the node
based on the input. In this case we use the Sigmoid function because it takes in input between 0 and 1. The correct activation function depends much on the type of input of output in your data.

![activation](/assets/images/blogimages/figs-11-09/activation%20functions.png)

- Identity (linear)
- Binary (Non-negative input outputs 1 and negative input outputs 0)
- Sigmoid (Logistic; contains input from 0 to 1)
- TanH (Similar to sigmoid but from -1 to 1)
- ArcTan (Contains from -pi/2 to pi/2)
- ReLu (Negative input returns 0 and positive input is linear)
- Leaky ReLu (Negative input's magnitude is reduced, positive input is linear)
- Softmax (To impart probabilities, returns probability distribution)

We now add an additional layer and finally our output layer.
```
# Define another layer
new_layer = Dense(units=512, activation='sigmoid')
model.add(new_layer)

layer_output = Dense(units=10, activation='softmax', input_shape=(image_size,))
model.add(layer_output)
```
For the output layer, we choose 10 units because we are trying to determine which number (from 0 to 9) corresponds to each image. We can see a summary of what our model looks
like before we compile it by running `model.summary()`.

![summary](/assets/images/blogimages/figs-11-09/modelsummary.PNG)

Before we compile it is important to understand two concepts that come into play in the compilation process: Loss functions and Optimizers.

#### Loss functions

Loss functions are functions that predict error in the within the neural network. The output of this function is called gradient and it is use to adjust the weights of each node.
The following are different loss functions available within Keras but we will not go into the specifics of each function:

- mean_squared_error
- mean_absolute_error
- mean_absolute_percentage_error
- mean_squared_logarithmic_error
- squared_hinge
- hinge
- categorical_hinge
- logcosh
- categorical_crossentropy
- sparse_categorical_crossentropy
- binary_crossentropy
- kullback_leibler_divergence
- poisson
- cosine_proximity

#### Optimizers

Simply put, optimizers adjust features of the neural network to minimize losses. They use the gradients outputted by our loss functions. Some optimizers are:

- Gradient Descent
- Stochastic Gradient Descent
- Mini-Batch Gradient Descent
- Adam
- Momentum

Now that we understand these concepts, we can go ahead and compile the model with:
```
model.compile(loss='sparse_categorical_crossentropy',
             optimizer='sgd',
             metrics=['accuracy'])
```
The metrics argument lets us chose what we will see in the output as we fit our model. In this case, we want to know how accurate our model is. We fit our model by running:
```
# Fit the model to data and labels - also validate
model.fit(x_train, 
          y_train, 
          batch_size=10, 
          epochs=20, 
          shuffle=True, 
          verbose=True, 
          validation_split=.01)
```
![metrics](/assets/images/blogimages/figs-11-09/metrics.png)

You can learn more about what each argument means [here](https://keras.io/api/models/model_training_apis/). However, an important argument to understand is the `validation_split`. This argument is the portion of your training data that will be used to validate your model (not the same as testing) at the end of each time the data
goes through the model.

### Testing our model

We can make predictions with:
```
# Make prediction on test data
predictions = model.predict(x=x_test, batch_size=10, verbose=0)

# round to nearest int to get the most likely prediction
rounded_preds = np.argmax(predictions, axis=-1)
y_true = np.argmax(y_test, axis=-1)
```
We can create a confusion matrix to visualize the accuracy of our model's predictions. This matrix contains the predicted value on the x axis and the true value on the y axis.

![matrix](/assets/images/blogimages/figs-11-09/confusion.png)

Finally, Keras gives us the option to reuse an already trained model by saving it with `model.save('/model.ext')`.

### Conclusion

This is a very simple and basic example of how a neural network works. However, can you see some of the potential uses of neural netwokrs? Neural networks are the basis of
facial recognition, hand-writting recognition among many others. It is the most basic way of deep learning and artificial intelligence. Because of this, it is important to
learn and understand how they work. 




