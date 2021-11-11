---
title: The heart of Deep Learning
layout: post
author: jpablo
post-image: "https://user-images.githubusercontent.com/77635875/133832882-606db727-44cd-4202-9b30-5a44f69019be.jpg"
description: Basics and example of a neural network.
tags:
- Keras
- Neural Network
- Deep Learning
- Layers
- Sequential
---

## Introduction - What is a neural network?

[img]<img width="342" alt="Screen Shot 2021-09-24 at 2 06 23 PM" src="https://user-images.githubusercontent.com/77635875/134733773-8dd0e91f-6cb8-4fcc-b53c-bebe37752a2c.png">

Neural networks are a form of machine learning composed of layers of nodes whose role is to learn patterns in the training data fed to it and match those patterns 
to the label set for each item. The example we will run through is a data set which contains images of numbers 0 through 9 with their respective labels. Our goal
is to effectively determine which number corresponds to each image.

In simple words, a neural network has an input layer (we input each image), an output layer (the layer that outputs which number the image represents), and several
hidden layers in between through which each image runs. Weights are assigned to each node that represent the importance of that particular characteristic in the data
in order to eventually determine the final prediction. The following is an example of how we might thing of this process.

[img]<img width="342" alt="Screen Shot 2021-09-24 at 2 06 23 PM" src="https://user-images.githubusercontent.com/77635875/134733773-8dd0e91f-6cb8-4fcc-b53c-bebe37752a2c.png">

When we determine whether the image above is a six, we might perhaps look for certain characteristics. For example, we might be looking for a circle or an oval conected to
a diagonal or curved line above it. A neural network works similarily in the sense that it looks for patterns that will help it determine whether it is looking at a six or
another number. Each layer and node will look at a different piece and in the end, it will put all those pieces together. Now, lets dive a little deeper.

#### Install Keras

On your terminal window, run the following command:
`pip install keras`

#### Dependencies for this example

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

We will not go through the clean up and prepping of the data in this article but you can find the complete jupyter notebook with more detail [here]().

#### The model

Keras is equiped with different ways to build your model. However, the Sequential model is the most simple and for our basic example, it will suffice. We instanciate our
model object with the command `model = Sequential()`.

# Conclusion




# Challenge



