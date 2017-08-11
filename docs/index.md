---
layout: default
---

![](2.jpg)

# [](#header-1)Training face landmark detector

This application helps to train your own face landmark detector. You can train your own face landmark detection by just providing the paths for
directory containing the images and files containing their corresponding face landmarks. As this landmark detector was originally trained on
[HELEN dataset](http://www.ifp.illinois.edu/~vuongle2/helen/), the training follows the format of data provided in HELEN dataset.

The dataset consists of .txt files whose first line contains the image name which then follows the annotations.
The format of the file containing annotations should be of following format :
       
>       /directory/images/abc.jpg
>       123.45,345.65
>       321.67,543.89
>       .... , ....
>       .... , ....
       
The above format is similar to HELEN dataset which is used for training the model.

```js
// Command to be typed for running the sample
./sample_train_landmark_detector -annotations=/home/sukhad/Downloads/code/trainset/ -config=config.xml -face_cascade=lbpcascadefrontalface.xml -model=trained_model.dat -width=460 -height=460
```

## [](#header-2)Description of command parameters

> * **annotations** a : (REQUIRED) Path to annotations txt file [example - /data/annotations.txt]
> * **config** c : (REQUIRED) Path to configuration xml file containing parameters for training.[ example - /data/config.xml]
> * **model** m :  (REQUIRED) Path to configuration xml file containing parameters for training.[ example - /data/model.dat]
> * **width** w : (OPTIONAL)  The width which you want all images to get to scale the annotations. Large images are slow to process [default = 460]
> * **height** h : (OPTIONAL) The height which you want all images to get to scale the annotations. Large images are slow to process [default = 460]
> * **face_cascade** f (REQUIRED) Path to the face cascade xml file which you want to use as a detector.

### [](#header-2)Description of training parameters

The configuration file described above which is used while training contains the training parameters which are required for training.

**The description of parameters is as follows :**

1. **Cascade depth :** This stores the depth of cascade of regressors used for training.
2. **Tree depth :** This stores the depth of trees created as weak learners during gradient boosting.
3. **Number of trees per cascade level :** This stores number of trees required per cascade level.
4. **Learning rate :** This stores the learning rate for gradient boosting.This is required to prevent overfitting using shrinkage.
5. **Oversampling amount :** This stores the oversampling amount for the samples.
6. **Number of test coordinates :** This stores number of test coordinates to be generated as samples to decide for making the split.
7. **Lambda :** This stores the value used for calculating the probabilty which helps to select closer pixels for making the split.
8. **Number of test splits :** This stores the number of test splits to be generated before making the best split.


To get more detailed description about the training parameters you can refer to the [Research paper](https://pdfs.semanticscholar.org/d78b/6a5b0dcaa81b1faea5fb0000045a62513567.pdf).

### [](#header-2)Understanding code

For understanding the code jump to this [page](another-page)

### [](#header-2)Error rate

**The error rate on trained images depends on the number of images used for training used as follows :**

![](train.png)

**The error rate on test images depends on the number of images used for training used as follows :**

![](test.png)

# [](#header-1)Face landmark detection in an image

![](facereg.jpg)

This application lets you detect landmarks of detected faces in an image. You can detect landmarks of all the faces found in an image and use them further in various applications like face swapping, face averaging etc.
This functionality is now available in OpenCV.

```
// Command to be typed for running the sample
./sampleDetectLandmarks -file=trained_model.dat -face_cascade=lbpcascadefrontalface.xml -image=/path_to_image/image.jpg
```
## [](#header-2)Description of command parameters

> * **model_filename** f : (REQUIRED) A path to binary file storing the trained model which is to be loaded [example - /data/file.dat]
> * **image** i : (REQUIRED) A path to image in which face landmarks have to be detected.[example - /data/image.jpg]
> * **face_cascade** c : (REQUIRED) A path to the face cascade xml file which you want to use as a face detector.

### [](#header-2)Understanding code

For understanding the code jump to this [page](another-page1)

# [](#header-1)Face landmark detection in a video

[Link to the video using face landmark detection]()

This application lets you detect landmarks of detected faces in a video.This application first detects faces in a current video frame and then finds their facial landmarks. You just have to pass the video as input.	

```
// Command to be typed for running the sample
./sampleDetectLandmarks -file=trained_model.dat -face_cascade=lbpcascadefrontalface.xml -video=/path_to_video/video.avi
```
## [](#header-2)Description of command parameters

> * **model_filename** f : (REQUIRED) A path to binary file storing the trained model which is to be loaded [example - /data/file.dat]
> * **video** i : (REQUIRED) A path to video in which face landmarks have to be detected.[example - /data/video.avi]
> * **face_cascade** c : (REQUIRED) A path to the face cascade xml file which you want to use as a face detector.

### [](#header-2)Understanding code

For understanding the code jump to this [page](another-page1)

# [](#header-1)Face swapping using face landmark detection using OpenCV.

This application lets you swap a face in one image with another face in other image. The application first detects faces in both images and finds its landmarks. Then it swaps the face in first image with in another image. You just have to give paths to the images run the application to swap the two faces.
```
// Command to be typed for running the sample
./sample_face_swapping -file=trained_model.dat -face_cascade=lbpcascadefrontalface.xml -image1=/path_to_image/image1.jpg -image2=/path_to_image/image2.jpg
```
## [](#header-2)Description of command parameters

> * **image1** i1 (REQUIRED) Path to the first image file in which you want to apply swapping.
> * **image2** i2 (REQUIRED) Path to the second image file in which you want to apply face swapping.
> * **model** m (REQUIRED) Path to the file containing model to be loaded for face landmark detection.
> * **face_cascade** f (REQUIRED) Path to the face cascade xml file which you want to use as a face detector.

## [](#header-2)Results

Consider two images to be used for face swapping as follows :

### [](#header-3)First image

![](2830279146_1.jpg)

### [](#header-3)Second image

![](100040721_1.jpg)

### [](#header-3)Results after swapping

![](Face_swapped.jpg)

## [](#header-2)Understanding code

For understanding the code jump to this [page](another-page2)
