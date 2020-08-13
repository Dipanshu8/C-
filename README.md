## Description

This program is a fully end-to-end video face recognition system. 
This program was writting in C++ 11, using OpenCV 3.1.

## Getting Started
* Download OpenCV [Click here](https://sourceforge.net/projects/opencvlibrary/)
* Setting Up: There's a comprehensive guide on setting up OpenCV
in various environments at the official wiki: [click here](https://opencvlibrary.sourceforge.net)

## Creating A Face Detector
* Collection of training images, positives and negatives
* Run AdaBoost to distill a set of Haar-like features
  which give good classifiers
* Combine the yielded classifiers appropriately into a
  cascade
* Three tools to use – “createsamples”, “haartraining” and
  “performance”
