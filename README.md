# Visualizing VGG16 Feature Maps in Keras

This repository contains code for visualizing the feature maps of VGG16 Convoutional Neural Network using Keras. Particular layer of CNN can be visualized by defining it as an output layer. For brevity please check some examples given below. 

The code is written in and tested only for Google Colab Notebooks only. However, minor changes are needed to run it locally.

# Feature Maps
Feature Maps of Bear
![Bear](https://raw.githubusercontent.com/mynkpl1998/visualize-vgg16/master/Images/bear_conv_features.png)

Feature Maps Beer Glass
![Beer](https://raw.githubusercontent.com/mynkpl1998/visualize-vgg16/master/Images/beer_conv_features.png)

# Dependencies
The dependencies can be installed using the command given below.

`pip install keras==2.2.4 opencv-contrib-python==3.4.3.18 pillow==4.3.0`

* keras >= 2.2.4
* opencv-contrib-python >= 3.4.3
* pillow >= 4.3.0

# Setup Steps

If you are using Google Colab then you need to authorize and upload the required weights, images files to your google drive account.

1. Mount the google drive.

```
from google.colab import drive`
drive.mount("/content/drive", force_remount=True)
```
2. Define the path to your pre-trained, images and imagenet labels file. You can find all these files [here](https://drive.google.com/drive/folders/1XQvsR5Q7pXWE9XojCSBVCGZ78jJ921cS?usp=sharing). You can add this to your drive and modify the path of the files to match yours.

```
drive_weights_path = "/content/drive/My Drive/VGG16 Visualization/weights.h5"
imagenet_labels_file_path = "/content/drive/My Drive/VGG16 Visualization/imagenet_class_index.json"
image_name = "/content/drive/My Drive/beer.png"
```

# Steps to Visualize a layer

In order to visualize a layer of VGG16, the user need to provide the name of the layer to visualize. The name of layers are given below and the same can be obtained by printing the summary of the model.

```
_________________________________________________________________
Layer (type)                 Output Shape              Param #   
=================================================================
input_1 (InputLayer)         (None, 224, 224, 3)       0         
_________________________________________________________________
block1_conv1 (Conv2D)        (None, 224, 224, 64)      1792      
_________________________________________________________________
block1_conv2 (Conv2D)        (None, 224, 224, 64)      36928     
_________________________________________________________________
block1_pool (MaxPooling2D)   (None, 112, 112, 64)      0         
_________________________________________________________________
block2_conv1 (Conv2D)        (None, 112, 112, 128)     73856     
_________________________________________________________________
block2_conv2 (Conv2D)        (None, 112, 112, 128)     147584    
_________________________________________________________________
block2_pool (MaxPooling2D)   (None, 56, 56, 128)       0         
_________________________________________________________________
block3_conv1 (Conv2D)        (None, 56, 56, 256)       295168    
_________________________________________________________________
block3_conv2 (Conv2D)        (None, 56, 56, 256)       590080    
_________________________________________________________________
block3_conv3 (Conv2D)        (None, 56, 56, 256)       590080    
_________________________________________________________________
block3_pool (MaxPooling2D)   (None, 28, 28, 256)       0         
_________________________________________________________________
block4_conv1 (Conv2D)        (None, 28, 28, 512)       1180160   
_________________________________________________________________
block4_conv2 (Conv2D)        (None, 28, 28, 512)       2359808   
_________________________________________________________________
block4_conv3 (Conv2D)        (None, 28, 28, 512)       2359808   
_________________________________________________________________
block4_pool (MaxPooling2D)   (None, 14, 14, 512)       0         
_________________________________________________________________
block5_conv1 (Conv2D)        (None, 14, 14, 512)       2359808   
_________________________________________________________________
block5_conv2 (Conv2D)        (None, 14, 14, 512)       2359808   
_________________________________________________________________
block5_conv3 (Conv2D)        (None, 14, 14, 512)       2359808   
_________________________________________________________________
block5_pool (MaxPooling2D)   (None, 7, 7, 512)         0         

```

For example to visualize layer block1_conv2 layer, we need to set end_layer variable to the same.

```
end_layer = block1_conv2
```
