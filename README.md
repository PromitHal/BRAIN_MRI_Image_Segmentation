## Brain Tumor Localization and 
The aim of this project is to build a model that can perform Brani Tumor localization and segmentation from Magnetic Resonance Imaging (MRI).Brain tumor segmentation has evolved as an important task in medical image processing.Traditionally,tumors in the Brain are detected manually from MRI images that are generated via clinical procedures. However,for a large number of MRI Images,the task of identifying tumors manually becomes increasingly difficult. This stems the ardent need of automation in Brain Tumor recognition. Using advanced Deep Learning Techniques, it becomes possible to localized Brain Tumors from MRI images,thus enabling automatic Brain Tumor detection. This is achieved by semantic segmentation.

### Semantic Segmentation:
The goal of semantic image segmentation is to label each pixel of an image with a corresponding class of what is being represented.This can be achieved via using Convolutional Neural Networks.
### Architecture: 
    A basic apporach to build a deep neural network architecture for Semantic Segmentation is to stack Convolutional Neural Networks in the conventional "Sequential" manner which takes input as the image to be segmented and outputs the segmentation map with dimensions same as that of the image(execpt possibly the number of channels in the image).This might be achieved via simply stacking Convolutional Neural Layers with "same padding" to preserve dimensions.This architecure thus gives a direct mapping from input image to the output image via successive transformations of feature mapping.Since, to extract more features,the number of feature channels must be high, it becomes quite difficult  to preserve the resolution of an image via the above mentioned architecture.
    
## Enocder-Decoder Based Approach:
   This approach relies on upsampling and downsampling. In this architecture,we follow an encoder cum decoder network. The encoder network which performs downsampling,is a stack of Convolutional Neural Layers which provide lower-resolution feature mappings.
   The encoder network is followed by a decoder network.The decoder network perform the task of umsampling feature representations into a full-resolution segmentation map.Transpose convolutions are widely used to upsample the feature representations.
   Using skip connections in the encoder-decoder structure we can recover fine-grained details in the prediction.

