---
layout: page
title: Projects
---
# Some of My Projects
* [Reinforcement Learning Pong AI](#reinforcement-learning-pong-ai)
* [Breast Cancer Classification](#breast-cancer-classification)
* [Quantum Computing](#quantum-computing)
* [FileToPNG](#filetopng)
* [Handwritten Digit Classifier](#handwritten-digit-classifier)
* For my other projects see [my Github](https://github.com/ozanerhansha)
<!-- * [Neurosky EEG App]() -->
<br>

## Reinforcement Learning Pong AI
This is an artificial neural network trained to play pong against a competent bot. Learning starts to appear after 500 games (a game goes on until one player reaches 20 points) and it reaches a 50% win-rate at 8000 games. The network seems to asymptote at a 90% win-rate but more testing needs to be done.

![bc](/assets/projects/pongai.gif?style=centerme)

[Read more...](/2018/03/18/reinforcement-learning-pong)

## Breast Cancer Classification
An artificial neural network trained on the [Wisconsin Breast Cancer Dataset](https://archive.ics.uci.edu/ml/datasets/breast+cancer+wisconsin+(original)). It can classify breast cancer cells as benign or malignant based on 10 pieces of data regarding its size, shape and other variables. The network has around a 90% accuracy on random samples.

![bc](/assets/2018/01/breast-cancer-classification/breastcancer.png?style=centerme)

[Read more...](/2018/01/15/breast-cancer-classification)

## Quantum Computing
When IBM made their 5 qubit quantum computer available to the public (or more specifically those who signed up for research purposes) I was one of the first to sign up, despite the fact I had no formal knowledge of quantum computation or quantum algorithms.

It wasn't until 2017 that IBM released a python API, [QISkit](https://github.com/QISKit/qiskit-sdk-py), to interact with their quantum computer rather than the web-based GUI that was available before. There wasn't much bombast regarding it's release but, critically, it allowed for the creation of quantum circuits programmatically and thus the implementation of general purpose quantum algorithms.

And so, using QISkit, I implemented Shor's algorithm in it's entirety (classical and quantum parts). You can find the code [here](https://github.com/ozanerhansha/QuantumComputing/blob/master/shorsalgo.py).

[Write-up and explanation of Code coming soon...]

## FileToPNG
A program written in Java that converts any file into an encoded PNG file that can then be sent to a recipient (via a text message for example), received, and decoded back into the original file.

An interesting consequence of how the image is directly encoded from the bits of the file is that similar types of files share similar structures. Here's an example:

![Text in FileToPNG](/assets/2018/01/filetopng/text_diagram.png?style=centerme){:width="500px"}

[Read more...](/2018/01/16/filetopng)

## Handwritten Digit Classifier
#### Neural Network
A model for classifying handwritten digits (0-9) using a convolutional neural network trained for image recognition. It was trained on the [MNIST Dataset](http://yann.lecun.com/exdb/mnist/) for over 20,000 iterations of 50 images each (1,000,000 total examples). The network was programmed in python with Google's [*TensorFlow*](https://www.tensorflow.org/) library.

<!-- [Click here for the full write-up of the neural network.](/2016/12/28/digit-classifier-network) -->
Click [here](https://github.com/ozanerhansha/NeuralNetworks/blob/master/src/MNIST/conv/mnist_convolutional.py) to see the code.


#### Android App
The model was then exported and, via TensorFlow's Inference API in Java, implemented into an Android App. It includes a canvas for drawing the digits and percentages of confidence in its guess.

![Two & Six Example](/assets/2018/01/digit-classifier-app/test_screenshots.png?style=centerme){:width="500px"}

You can download the app [here](https://github.com/ozanerhansha/DigitClassifier/releases).

<!-- [Click here for the full write-up of the app](/2016/04/15/digit-classifier-app) -->
