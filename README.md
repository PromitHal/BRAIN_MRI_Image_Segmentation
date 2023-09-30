# Brain Tumor Localization, Segmentation and Classification from MRI Images


![Examples-of-Normal-and-Abnormal-images-Brain-MRI-images-in-the-first-row-belong-to](https://user-images.githubusercontent.com/83832850/152699149-a7e2733c-9ff5-4771-aa02-72358fe40df9.png)





The aim of this project is to build a Deep Learning model that can perform Brain Tumor localization and segmentation from Magnetic Resonance Imaging (MRI). Brain tumor segmentation has evolved as an important task in medical image processing. Traditionally, tumors in the Brain are detected manually from MRI images that are generated via clinical procedures. However, for a large number of MRI Images, the task of identifying tumors manually becomes increasingly difficult. This stems from the ardent need for automation in Brain Tumor recognition. Using advanced Deep Learning Techniques, it becomes possible to localize Brain Tumors from MRI images, thus enabling automatic Brain Tumor detection. This is achieved by Image segmentation.


## Architecture: 

A basic approach to building a deep neural network architecture for Image Segmentation is to stack Convolutional Neural Networks in the conventional "Sequential" manner which
takes input as the image to be segmented and outputs the segmentation map with dimensions the same as that of the image(except possibly the number of channels in the image). This might
be achieved via simply stacking Convolutional Neural Layers with "same padding" to preserve dimensions. This architecture thus gives a direct mapping from the input image to the output
image via successive transformations of feature mapping. Since, to extract more features, the number of feature channels must be high, it becomes quite difficult  to preserve the 
resolution of an image via the above-mentioned architecture.

    
### Encoder-Decoder Based Approach:

   This approach relies on upsampling and downsampling. In this architecture, we follow an encoder cum decoder network. The encoder network which performs downsampling, is a stack of Convolutional Neural Layers which provide lower-resolution feature mappings.
   The encoder network is followed by a decoder network. The decoder network performs the task of upsampling feature representations into a full-resolution segmentation map. Transposed convolutions are widely used to upsample the feature representations.
   To prevent vanishing gradients, the encoder layers are concatenated to decoder layers using a skip connection. Using skip connections in the encoder-decoder structure enables us to  recover fine-grained details in the prediction.
![1_f7YOaE4TWubwaFF7Z1fzNw](https://user-images.githubusercontent.com/83832850/152694227-741edca8-b314-4c23-89d7-434fb6734c6d.png)
  Image Source: https://towardsdatascience.com/unet-line-by-line-explanation-9b191c76baf5
  
  
# Project Description and Results:

## Dataset:

The dataset used for this project can be obtained from: https://www.kaggle.com/mateuszbuda/lgg-mri-segmentation
It has 3500+ images which are MRI scans of various patients with the corresponding masks that indicate the presence of tumor.
This dataset contains brain MR images together with manual FLAIR abnormality segmentation masks.
The images were obtained from The Cancer Imaging Archive (TCIA).
They correspond to 110 patients included in The Cancer Genome Atlas (TCGA) lower-grade glioma collection with at least fluid-attenuated inversion recovery (FLAIR) sequence and genomic cluster data available.


This GitHub repo contains the following directories:

1.U_Net

2.ResNet50_plus_UNet

3. Localization

4. Classification


Looking at the directories:

## 1.U_Net:

In this directory, a model based on an encoder-decoder approach with skip connections similar to UNet architecture has been trained on the dataset to localize brain tumors.

Model Parameters Used:
 1.Batch Size: 16
 
 2. Number of Epochs: 100 set manually but reduced due to callbacks
 
 3. Loss Function: Binary Crossentropy Loss function added with Dice Coefficient Loss Function
 
 4.Optimizer: Adam
 
 5. Metrics:
 
    4.1 Dice Coefficient
    
    4.2 Jaccard Index
    
 6.Training examples: 3536
 
 7. Validation examples: 197
 
 8. Testing examples:196
 
  ### Results: 
 
  ### Training:  
    Jaccard_Index:0.7592 ,Dice_Coefficient:0.8591,loss=0.1525 
 
  ### Validation:
    Jaccard_Index: 0.7925 ,Dice_Coefficient:0.8832,loss=0.1255
    
    
  ![m](https://user-images.githubusercontent.com/83832850/152699047-1869ecce-aac8-4aad-b745-3788e466f93b.jpg)

   
 
## 2.ResNet_50_Unet:

 In this directory, a model based on an encoder-decoder approach with skip connections similar to UNet architecture has been trained on the dataset to localize brain tumors.
 However, the encoder layers are derived from pre trained ResNet_50 model, hence using Transfer Learning Techniques.
   Model Parameters Used:
   
 1. Batch Size: 16
 
 2. Number of Epochs: 100 set manually but reduced due to callbacks
 
 3. Loss Function: Binary Crossentropy Loss function added to Dice Coefficient Loss Function
 
 4.Optimizer: Adam
 
 5. Metrics:
 
    4.1 Dice Coefficient
    
    4.2 Jaccard Index
    
 6.Training examples: 3536
 
 7. Validation examples : 197
 
 8. Testing examples :196
 
  ### Results: 
 
  ### Training:  
    Jaccard_Index:0.8557 ,Dice_Coefficient:0.9211,loss=0.0860
 
  ### Validation:
    Jaccard_Index: 0.8444  ,Dice_Coefficient:0.9147,loss=0.0926
    
   
 
    
  

    
![t](https://user-images.githubusercontent.com/83832850/152698941-60b94d07-ab85-4e53-a775-5df51451d7db.jpg)

    
    
    
 
## 3.Localization:
    
Here, we have used the two trained models to predict the tumors and used the prediction masks to localize the tumors on the original MRI images. This is accomplished by using Canny edge detector on the predicted masks, finding contours, and superimposing the contours on the corresponding original MRI images.
    
![tt](https://user-images.githubusercontent.com/83832850/152731475-c74e25ba-e51d-4c7d-8a90-5a42d5c489f2.jpg)
    

 


 # References 
 1. Ronneberger, Olaf, Philipp Fischer, and Thomas Brox. "U-net: Convolutional networks for biomedical image segmentation." Medical Image Computing and Computer-Assisted Intervention–MICCAI 2015: 18th International Conference, Munich, Germany, October 5-9, 2015, Proceedings, Part III 18. Springer International Publishing, 2015.

 2. Oktay O, Schlemper J, Folgoc LL, Lee M, Heinrich M, Misawa K, Mori K, McDonagh S, Hammerla NY, Kainz B, Glocker B. Attention u-net: Learning where to look for the pancreas. arXiv preprint arXiv:1804.03999. 2018 Apr 11.

 3. He, K., Zhang, X., Ren, S. and Sun, J., 2016. Deep residual learning for image recognition. In Proceedings of the IEEE conference on computer vision and pattern recognition (pp. 770-778).
 
