---
layout: post
title: Deep Learning  on MNIST Datasets

---

Deep Learning is the sublte extraction of machine learning into domains of feature extraction via a more deep stack of neural network.Machine Learning is science of learning the essence of data given extracted features but the method seems to be less computationally feasible as the number of features increase dramatically,like in images.eg, a 28*28 image would have a total of 784 features,i.e. the 784 pixel values.So we try to train models that learn the important features of the datasets themselves,rather than hogging on the entire feature space.

<div class="divider"></div>

Convolutional Neural Nets are the state-of-the-art techniques to learn from large feature space type datasets. They work extremely well with Images,and can be used for a variety of tasks such as Classification,Image localization and detection.They are primarily inspired by the mammalian Visual Cortex after the experiments performed by Hubel and Weasel in the 1950's.
[Here](https://www.google.co.in/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=0ahUKEwinue3B-azWAhWBO48KHULCB_4QtwIIKDAA&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DFTr3n7uBIuE&usg=AFQjCNGd5-mWM-mKXPQ_dRYnYPq5oqBTEA) is a great resource to learn about ConvNets!

<div class="divider"></div>

I trained a Convolutional Neural Net using keras on my local machine to classify handwritten digits.Side by Side I trained a multi-layered perceptron on the image datasets! I had lesser patience in training my convnet so I restriced the training to 1000/60000 samples on 100 epochs.Surprisingly, the network gave an accuracy of 95% on the test datasets of 10000 samples and was trained in under five minutes! 


Details of Multi-layered perceptron:

*Hidden layers=2
*Hidden layer size=900 units
*Input size=784 units
*Dropout rate=0.5
*Optimizer='adam'
*Loss function='categorical_crossentropy'



The multi-layered perceptron after training for two hours on the datasets could only go upto 94%. The ConvNet trained for less than 5 minutes and went up to 95% accuracy! Behold the power of deep learning!

Check out the source code [here](https://github.com/blackeagle01/MNISTDeepLearn)!
