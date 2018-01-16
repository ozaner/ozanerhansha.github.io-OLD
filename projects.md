---
layout: page
title: Projects
---
# Some of My Projects
* [Breast Cancer Classification](#breast-cancer-classification)
<!-- * [Quantum Computing]() -->
* [FileToPNG](#filetopng)
* [Handwritten Digit Classifier](#handwritten-digit-classifier)
<!-- * [Neurosky EEG App]() -->
* For my other projects see [my Github](https://github.com/ozanerhansha)

<br>

## Breast Cancer Classification
An artificial neural network trained on the [Wisconsin Breast Cancer Dataset](https://archive.ics.uci.edu/ml/datasets/breast+cancer+wisconsin+(original)). It can classify breast cancer cells as benign or malignant based on 10 pieces of data regarding its size, shape and other variables. The network has around a 90% accuracy on random samples.

[Click here for the full write-up with code.](/2017/06/15/breast-cancer-classification)

<br>

## FileToPNG
A program written in Java that converts any file into an encoded PNG file that can then be sent to a recipient (via a text message for example), received, and decoded back into the original file.

An interesting consequence of how the image is directly encoded from the bits of the file is that similar types of files share similar structures. Here's an example:

![Text in FileToPNG](/assets/2016/09/filetopng/text_diagram.png){:width="500px"}

[Click here for the full write-up of the program](/2016/09/12/filetopng)

<br>

## Handwritten Digit Classifier
#### Neural Network
A model for classifying handwritten digits (0-9) using a convolutional neural network trained for image recognition. It was trained on the [MNIST Dataset](http://yann.lecun.com/exdb/mnist/) for over 20,000 iterations of 50 images each (1,000,000 total examples). The network was programmed in python with Google's [*TensorFlow*](https://www.tensorflow.org/) library.

<!-- [Click here for the full write-up of the neural network.](/2016/12/28/digit-classifier-network) -->
Click [here](https://github.com/ozanerhansha/NeuralNetworks/blob/master/src/MNIST/conv/mnist_convolutional.py) to see the code.


#### Android App
The model was then exported and, via TensorFlow's Inference API in Java, implemented into an Android App. It includes a canvas for drawing the digits and percentages of confidence in its guess.

![Two & Six Example](/assets/2016/12/digit-classifier-app/test_screenshots.png)

You can download the app [here](https://github.com/ozanerhansha/DigitClassifier/releases).

<!-- [Click here for the full write-up of the app](/2016/04/15/digit-classifier-app) -->

