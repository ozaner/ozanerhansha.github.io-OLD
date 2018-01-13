---
layout: post
title: Breast Cancer Classification
tags: computer-science neural-networks
---
## Background
I made this model to test how easily I could use external datasets to create and train a neural network with Google's [*TensorFlow*](https://www.tensorflow.org/) library. In this post I'll atempt to explain the code, its results, and its accuracy. The [entire program](https://github.com/ozanerhansha/NeuralNetworks/blob/master/src/test/bcDiagnosis.py) is in my [NeuralNetwork](https://github.com/ozanerhansha/NeuralNetworks) repository on Github as well as at the end of this post.

## The Training Data
All the training data comes from the [Wisconsin Breast Cancer Data Set](http://archive.ics.uci.edu/ml/datasets/breast+cancer+wisconsin+%28diagnostic%29), hosted by the University of California's [Machine Learning Repository](http://archive.ics.uci.edu/ml/index.php).

The training data consists of 569 subjects each with 3 values (mean, worst value, and standard error) for each of 10 categories:
* Radius (mean of distances from center to points on the perimeter)
* Texture (standard deviation of gray-scale values)
* Perimeter
* Area
* Smoothness (local variation in radius lengths)
* Compactness ($\frac{perimeter^2}{area} - 1$)
* Concavity (severity of concave portions of the contour)
* Concave points (number of concave portions of the contour)
* Symmetry
* Fractal dimension (measure of edge complexity)

All the training examples are stored on a CSV (Comma Separated Value) file called `wdbc.data`, so our first job is to import the file into our program:

<!--more-->

~~~ python
import os #Used for finding file path

#Get dataset file path
path = os.path.dirname(__file__)
file_name = os.path.join(path, 'wdbc.data')
file_object = open(file_name, 'r')
~~~

Now we can start 'cleaning' the data (that is turning this large string of numbers into a list of training examples labeled  **benign** or **malignant**).

First off we have to split up the dataset (which is currently just one massive string) into a bunch of strings, one for each subject (patient):

~~~ python
#Split dataset into separate points (as strings)
string_points = file_object.read().split('\n')
string_points.pop(-1)
~~~

If you take a look at the actual [`wdbc.data`](https://github.com/ozanerhansha/NeuralNetworks/blob/master/src/test/wdbc.data) file, you'll see that some of the subjects are grouped together benign and malignant. If we trained the network with the subjects in this order it bias the network's guesses. So we shuffle the subjects to avoid this:
~~~ python
random.shuffle(string_points) #Randomize (avoid bias)
~~~

Next we create a list of feature vectors (a list of all the statistical data for each subject) and y labels (whether the subject is benign or malignant).

This is the first part where we'll need the [numpy](http://www.numpy.org) library, so let's import it as well:

~~~ python
import numpy as np

num_input_features = 30 #30 data points per subject

#Initialize dataset class arrays
point_array = np.empty((0,num_input_features))
y_labels = np.empty((0,2))

#Trim data points
#Format as np.arrays
#Add to class arrays (Benign or Malignant)
for point in string_points:
    point = point.split(',')
    if 'M' in point: #if malignant
        y_labels = np.append(y_labels, [[0,1]], axis=0)
    else: #if benign (can only be labeled 'B' or 'M')
        y_labels = np.append(y_labels, [[1,0]], axis=0)
    point = point[2:] #trim for only the 10 important features
    temp = np.array(point) #convert to numpy array
    temp = temp.astype(float) #cast as float array
    point_array = np.append(point_array, [temp], axis=0)
~~~

All that is left is to split up the subjects into training and testing sets. Testing using the same data as the network was trained on encourages the network to memorize the data rather than generalize the dataset make meaningful predictions.

Of the 569 subjects, the first 400 will be used to train the network while the remaining 169 will be used to test the network's accuracy:

~~~ python
#Split training and testing data
experience_matrix = point_array[0:400]
experience_matrix_y = y_labels[0:400]
test_matrix = point_array[400:]
test_matrix_y = y_labels[400:]
~~~

## Constructing the Network
A single layer perceptron network seems to do well enough in fitting the test data, so we'll build one here. The standard model fo such a network in matrix notation is:

$$\hat{y}=\text{softmax}(Wx+b)$$

* $x$ is the input (a 30 dimensional vector of all the cancer cell's statistical values)
* $\hat{y}$ is the network's  approximation of $y$, the right answer ($\hat{y}$ is a 2D vector with the first/second value corresponding to its confidence that the cell is benign/malignant)
* $W$ is a matrix of weights (the matrix is 30x2 so that it turns 30 dimensional vectors into 2D vectors)
* $b$ is a vector of 'bias' values (a 2D vector that allows the network more freedom when training)
* The [$\text{softmax}$](https://en.wikipedia.org/wiki/Softmax_function) function is the network's [activation function](https://en.wikipedia.org/wiki/Activation_function), which introduces a nonlinearity to the network. This is integral for any neural network to learn from the data it's provided. The function also equalizes the network's confidence predictions so that they add up to 100%. The mathematical description of softmax is:

![softmax graph](https://upload.wikimedia.org/wikipedia/commons/thumb/5/5b/Mplwp_logistic_function.svg/1280px-Mplwp_logistic_function.svg.png)

We'll use TensorFlow to write this network so we should import it first:
~~~ python
# End of data import/cleanup. Begin construction of neural network
with tf.name_scope('Hidden_Layer'):
  #nx10 Matrix (Input)
    x = tf.placeholder(tf.float32, shape=[None, num_input_features])
  #10x1 Matrix (Weights)
    W = tf.Variable(tf.zeros([num_input_features,2]))
  #1x2 vector (Bias)
    b = tf.Variable(tf.zeros([2]))
  #A scalar (x*W + b)
    y_noSoftmax = tf.matmul(x,W) + b

#Apply softmax (scales y_noSoftmax to be between 0 & 1)
y_hat = tf.nn.softmax(y_noSoftmax, name='y_Hat')
~~~

## Training the Network

## Assessing the Network

## The Full Code
~~~ python
'''
Created on Jun 6, 2017
@author: Ozaner Hansha
'''
import os
import numpy as np
import tensorflow as tf
import random

#Get dataset file path
path = os.path.dirname(__file__)
file_name = os.path.join(path, 'wdbc.data')
file_object = open(file_name, 'r')

#Split dataset into separate points (as strings)
string_points = file_object.read().split('\n')
string_points.pop(-1)
random.shuffle(string_points) #Randomize (avoid bias)

num_input_features = 30

#Initialize dataset class arrays
point_array = np.empty((0,num_input_features))
y_labels = np.empty((0,2))

#Trim data points
#Format as np.arrays
#Add to class arrays (Benign or Malignant)
for point in string_points:
    point = point.split(',')
    if 'M' in point: #if malignant
        y_labels = np.append(y_labels, [[0,1]], axis=0)
    else: #if benign (can only be labeled 'B' or 'M')
        y_labels = np.append(y_labels, [[1,0]], axis=0)
    point = point[2:] #trim for only the 10 important features
    temp = np.array(point) #convert to numpy array
    temp = temp.astype(float) #cast as float array
    point_array = np.append(point_array, [temp], axis=0)

#Split training and testing data
experience_matrix = point_array[0:400]
experience_matrix_y = y_labels[0:400]
test_matrix = point_array[400:]
test_matrix_y = y_labels[400:]

# End of data import/cleanup. Begin construction of neural network
with tf.name_scope('Hidden_Layer'):
  #nx10 Matrix (Input)
    x = tf.placeholder(tf.float32, shape=[None, num_input_features])
  #10x1 Matrix (Weights)
    W = tf.Variable(tf.zeros([num_input_features,2]))
  #1x2 vector (Bias)
    b = tf.Variable(tf.zeros([2]))
  #A scalar (x*W + b)
    y_noSoftmax = tf.matmul(x,W) + b

#Apply softmax (scales y_noSoftmax to be between 0 & 1)
y_hat = tf.nn.softmax(y_noSoftmax, name='y_Hat')

#Session
sess = tf.InteractiveSession() #Create Session
sess.run(tf.global_variables_initializer()) #Init Variables

#Training Model
with tf.name_scope('Training'):
  #nx2 Matrix (One-Hot Vector, Label Data)
    y = tf.placeholder(tf.float32, shape=[None, 2],name='y_Labeled')
  #Loss Function (cross entropy between y and y_hat)
    cross_entropy = tf.reduce_mean(tf.nn.softmax_cross_entropy_with_logits
    (logits = y_noSoftmax, labels = y),name='Loss_Function')
  #Performs Gradient Descent on loss function
    train_step = tf.train.GradientDescentOptimizer(0.5).minimize(
        cross_entropy,name='Train_Step')

#Run train step repeatedly
for i in range(1000):
  #Run training step on that batch
    train_step.run(feed_dict={x: experience_matrix, y: experience_matrix_y})

#Evaluation
with tf.name_scope('Validation'):
  #Returns whether model made correct prediction (List of booleans)
    correct_prediction = tf.equal(tf.argmax(y_hat,1),
        tf.argmax(y,1), name='isCorrect')
  #Average of correct prediction (%Accuracy)
    accuracy = tf.reduce_mean(tf.cast
        (correct_prediction,tf.float32),name='Accuracy')

#Print Accuracy
print("Accuracy:", '{0:.2%}'.format(accuracy.eval
  (feed_dict={x: test_matrix, y: test_matrix_y})))
~~~
