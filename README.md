## Brain Tumor Localization and 
The aim of this project is to build a model that can perform Brani Tumor localization and segmentation from Magnetic Resonance Imaging (MRI).Brain tumor segmentation has evolved as an important task in medical image processing.Traditionally,tumors in the Brain are detected manually from MRI images that are generated via clinical procedures. However,for a large number of MRI Images,the task of identifying tumors manually becomes increasingly difficult. This stems the ardent need of automation in Brain Tumor recognition. Using advanced Deep Learning Techniques, it becomes possible to localized Brain Tumors from MRI images,thus enabling automatic Brain Tumor detection. This is achieved by semantic segmentation.

### Semantic Segmentation:
The goal of semantic image segmentation is to label each pixel of an image with a corresponding class of what is being represented.This can be achieved via using Convolutional Neural Networks.It performs the task of classifying each pixel of an image into a specified class,thus identifying those pixels which are closely related.

![d](https://user-images.githubusercontent.com/83832850/152694560-256bf267-e3ed-4461-95f6-550dddf9c690.jpeg)
                       
Image  Source : https://towardsdatascience.com/unet-line-by-line-explanation-9b191c76baf5



### Architecture: 
A basic apporach to build a deep neural network architecture for Semantic Segmentation is to stack Convolutional Neural Networks in the conventional "Sequential" manner which
takes input as the image to be segmented and outputs the segmentation map with dimensions same as that of the image(execpt possibly the number of channels in the image).This might
be achieved via simply stacking Convolutional Neural Layers with "same padding" to preserve dimensions.This architecure thus gives a direct mapping from input image to the output
image via successive transformations of feature mapping.Since, to extract more features,the number of feature channels must be high, it becomes quite difficult  to preserve the 
resolution of an image via the above mentioned architecture.
    
## Enocder-Decoder Based Approach:
   This approach relies on upsampling and downsampling. In this architecture,we follow an encoder cum decoder network. The encoder network which performs downsampling,is a stack of Convolutional Neural Layers which provide lower-resolution feature mappings.
   The encoder network is followed by a decoder network.The decoder network perform the task of umsampling feature representations into a full-resolution segmentation map.Transpose convolutions are widely used to upsample the feature representations.
   To prevent vanishing gradients,the encoder layers are concatenated to decoder layers using skip connection.Using skip connections in the encoder-decoder structure enables us to  recover fine-grained details in the prediction.
![1_f7YOaE4TWubwaFF7Z1fzNw](https://user-images.githubusercontent.com/83832850/152694227-741edca8-b314-4c23-89d7-434fb6734c6d.png)
  Image Source : https://towardsdatascience.com/unet-line-by-line-explanation-9b191c76baf5
  
  
## Project Description and Results:

# Dataset:

The dataset used for this project can be obtained from : https://www.kaggle.com/mateuszbuda/lgg-mri-segmentation
It has 3500+ images which are MRI scans of various patients with the correponding masks which indicate the presence of tumor.
This dataset contains brain MR images together with manual FLAIR abnormality segmentation masks.
The images were obtained from The Cancer Imaging Archive (TCIA).
They correspond to 110 patients included in The Cancer Genome Atlas (TCGA) lower-grade glioma collection with at least fluid-attenuated inversion recovery (FLAIR) sequence and genomic cluster data available.


This githup repo contains the following directories:
1.U_Net
2.ResNet50_plus_UNet
3.Classification

Looking at the directories:

### 1.U_Net;
In this directory, a model based on encoder decoder approach with skip connections similar to UNet architecture has been trained on the dataset to localize brain tumors.
Model Parameters Used:
 1.Batch Size : 16
 2.Number of Epochs : 100 set manually but reduced due to callbacks
 3.Loss Function: Binary Crossentropy Loss function addeed with Dice Coefficient Loss Function
 4.Metrics:
    4.1 Dice Coefficient
    4.2 Jaccard Coefficient
 5.Training examples: 3693
 6.Validation examples : 196
 7.Testing examples :197
 Results: 
 
 ### ResNet50:
 
