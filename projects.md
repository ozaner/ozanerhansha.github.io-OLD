---
layout: page
title: Projects
---
# Some of My Projects

### Table of Contents
* [Breast Cancer Classification](#breast-cancer-classification)
* [Handwritten Digit Classifier](#handwritten-digit-classifier)
* [FileToPNG](#file-to-png)
* [Neurosky EEG Viewer](#neurosky-eeg-viewer)

### Breast Cancer Classification
An artificial neural network trained on the [Wisconsin Breast Cancer Dataset](https://archive.ics.uci.edu/ml/datasets/breast+cancer+wisconsin+(original)). It can classify breast cancer cells as benign or malignant based on 10 pieces of data regarding its size, shape and other variables. The network has around a 91% accuracy on random samples.

[Click here for the full write-up with code.](/2017/06/15/breast-cancer-classification)

### Handwritten Digit Classifier
#### Neural Network
A model for classifying handwritten digits (0-9) using a convolutional neural network trained for image recognition. It was trained on the [MNIST Dataset](http://yann.lecun.com/exdb/mnist/) for over 20,000 iterations of 50 images each (1,000,000 total examples). The network was programmed in python with Google's [*TensorFlow*](https://www.tensorflow.org/) library.

[Click here for the full write-up of the neural network.](/2017/06/15/breast-cancer-classification)

#### Android App
The model was then exported and, via TensorFlow's java API, implemented into an Android App with a canvas and percentages of confidence.

![Two & Six Example](/assets/test_digit-classifier.png)

[Click here for the full write-up of the app](/2017/06/15/breast-cancer-classification)

### Neurosky EEG Viewer

### FileToPNG
A program written in Java that converts any file into an encoded PNG file that can then be sent to a recipient (via a text message for example), received, and decoded back into the original file.

An interesting consequence of how the image is directly encoded from the bits of the file is that similar types of files share similar structures. Here's an example:

![Text in FileToPNG](/assets/text_file-to-png.png){:width="600px"}

<!-- ##### What a random file looks like for comparison:
![Random Noise](/assets/random_file-to-png.png){:width="500px"} -->

[Click here for the full write-up of the program](/2017/06/15/breast-cancer-classification)