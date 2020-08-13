## Description

This program is a fully end-to-end video face recognition system. 
This program was writting in C++ 11, using OpenCV 3.1 C++ API and Dlib. 

## Table Of content
* [Setup](#setup)

## Information

The step-by-step pipeline is as follows:

1. Collect a set of photos for each user using the mobile app. The user can take photos of themself from several angles for better results in training the face recognizer. Alternatively, a video can be taken and frames that have a high similarity to each other will be discarded. 

2. To run the program, build and run the `FLD.cpp` program. This will access the current available webcam. 

3. Firstly, the Local Binary Patterns Histograms<sup>1</sup> (LBPH) Face Recognizer will be trained using the set of collected photos, along with their classification labels/ID. Video capture will then begin via webcam. 

4. Faces are initally detected using the Viola-Jones<sup>4</sup> (VJ) face detector, by searching through the entire image frame. As this is a bit slow, we use a smart speed up technique. If a face was detected in the previous frame, then we only search for a face using the VJ detector in a small region-of-interest (ROI) around where that previous face was detected, as depending on how far away from the camera the face was, it may not have moved or changed in orientation very much. If we can't find a face within that small ROI, then either the face has completely moved, has changed orientation, or is slightly occluded. We will then run a template matching. A template of the face detected in the previous frame is saved and is used as a reference for matching in the current framce. We found this to be a bit more robust to occlusions and changes in orientation as the VJ frontal face detector is largely trained on straight, unoccluded faces. We find that this pipeline runs very fast, acheiving a speed of 26 FPS on an i5-2500k processor for 640x480 video frames. It also provides some robustness to occlusions and rotations. 

5. Next, we apply a facial landmark detection using the dlib library, which uses the method of Kazemi et al<sup>2</sup>. Since the LBPH<sup>1</sup> face recognizer is only trained on a small number of images, we would prefer the images being fed in for recognition to be the same orientation e.g perfectly straight and upright. Thus, we use the detected landmarks to align the face, by rotating the face such that the angle between two corresponding points are the same. For example, the angle between the points on the corners of the left and right eye should be zero if the head is perfectly upright. 

6. Before passing the aligned faces to the face recognizer, we must first pre-process them. We reject false positives used a simple skin detection based on the Hue, Saturation, and Value in the HSV colour space. Secondly, we apply the pre-procesisng of Tan et al<sup>3</sup> to normalize lighting and contrast, and to combat noise and aliasing. 

7. The final step is to pass the processed faces to the face recognition object for recognition. 
