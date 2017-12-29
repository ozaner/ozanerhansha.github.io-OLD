---
layout: post
title: Breast Cancer Classification
tags: computer-science neural-networks
---
A single-layer perceptron network, coded with Google's [*TensorFlow*](https://www.tensorflow.org/) library.
It was trained on the [Wisconsin Breast Cancer Data Set](https://archive.ics.uci.edu/ml/datasets/breast+cancer+wisconsin+(original)), hosted by UC Irvine.

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
