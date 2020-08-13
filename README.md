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
## Instructions
Requirements for running the program:
1) OpenCV must be installed on the local machine.
2) Paths to the classifier XML files must be given before the execution of the program. These XML files can be found in the OpenCV directory “opencv/data/haarcascades”.
3) Use 0 in capture.open(0) to play webcam feed.
4) For detection in a local video provide the path to the video.(capture.open(“path_to_video”)).
