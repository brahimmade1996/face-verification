# Face-Verification
Repository for Face Detection and Verification Systems
- OpenCV [Cascade Classifiers](https://docs.opencv.org/3.3.0/d7/d8b/tutorial_py_face_detection.html) for Face Detection
- Keras Implementation of [FaceNet](https://arxiv.org/abs/1503.03832) for Face Verification


***
## Tasks
+ [x] Face Detection
    - [x] Haar Cascade Classifier
    - [x] LBP Classifier (not actually implemented)
+ [ ] Face Alignment
    - [ ] TBD
+ [x] Face Verification
    - [x] Base CNN model building and training
    - [x] Face verification metric measure
+ [ ] Liveness Verification
    - [ ] Eye-blink
    - [ ] TBD
+ [x] Interface or API


***
## Demo

#### 1. Face Detection --> [OpenCV Haar Feature-based Cascade Classifiers](https://docs.opencv.org/3.3.0/d7/d8b/tutorial_py_face_detection.html)
* Sample Input Images <br/>
<img src="./results/input_images.png" alt="Sample" style="width: 600px;"/>

* Frontal Face Detection <br/>
<img src="./results/face_detection.png" alt="Sample" style="width: 600px;"/>

* Frontal Face Crop <br/>
<img src="./results/cropped_faces.png" alt="Sample" style="width: 600px;"/>

* Check [Jupyter Notebook](https://github.com/JifuZhao/face-verification/blob/master/5.%20FaceNet%20Application%20Demo.ipynb) for details.

#### 2. Base CNN Model for Face Verification
+ Training Dataset: [VGGFace2 Dataset](http://www.robots.ox.ac.uk/~vgg/data/vgg_face2/)
+ Triplet Loss <br/>
![equation](https://latex.codecogs.com/gif.latex?%5Cdpi%7B150%7D%20%5Cbg_white%20L%28a%2C%20p%2C%20n%29%20%3D%20max%20%5C%7B%20%7C%7Cf%28a%29-f%28p%29%7C%7C_2%5E2%20-%7C%7Cf%28a%29-f%28n%29%7C%7C_2%5E2%20&plus;%20%5Calpha%20%2C%200%20%5C%7D)
    * a: anchor image
    * p: positive image
    * n: negative image
    * f(x): CNN model to encode the input image
    * $\alpha$: margin for triplet <br/>
    <img src="./results/triplet_loss.png" alt="Sample" style="width: 400px;"/>

#### 3. Face Verification
Give two input images, with the face verification api, the distance between to embedded images can be used to determine the identity of the input images. Below is the distance calculated for the sample input images.

<img src="./results/distance.png" alt="Sample" style="width: 400px;"/>

#### 4. Performance
Using the test dataset, the distance distribution between anchor image and positive image, and the distance distribution between anchor image and negative image, are shown below.

<img src="./results/margin-03-final.png" alt="Sample" style="width: 400px;"/>

#### 5. Extention: Face Recognition
Based on the pre-trained CNN models, face recognition can be performed using the encoded image vectors (in this project, a vector with 128 dimensions). Essentially, it can be performed using K-Nearest Neighbors (KNN) model.


***
#### Note
Currently the performance of pre-trained CNN models are mainly influenced by two factors: the quality of the input images and the iterations to train the model.

The input images used for training the CNN models have relatively low quality. With modern smart phones, the quality of the input image should be further improved. Thus, with better training images, the performance of the module should be further improved.

Limited by computation resources, a relatively small CNN model is used, and the model is only trained for 1,000 epochs. For better performance, please refer to other pre-trained models.


### Useful Links:
* [FaceNet: A Unified Embedding for Face Recognition and Clustering](https://arxiv.org/abs/1503.03832)
* [Deep face recognition with Keras, Dlib and OpenCV](https://krasserm.github.io/2018/02/07/deep-face-recognition/)
* [Face detection with OpenCV and deep learning](https://www.pyimagesearch.com/2018/02/26/face-detection-with-opencv-and-deep-learning/)
* [Face recognition using Tensorflow](https://github.com/davidsandberg/facenet)
* [The world's simplest facial recognition api for Python and the command line](https://github.com/ageitgey/face_recognition)


Copyright @ Jifu Zhao 2018
