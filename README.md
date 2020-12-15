# ColorizerGAN
This repository for Colorization GAN which basically takes gray scale image and produces RGB formatted image.

The work flow for this GAN is similar to as of all. A Generator generate an image and a critic tries to differentiate it from real. 
But here the beauty of Generator is due to its implementation done by Enco-Deco model.

Instead of giving a random latent vector as input to generator, here it takes Black & White image as imput to GAN where Encoder process it to convert to
**(1, 512)** shaped vector and then Decoder does reverse process for re-creating the colored image from the latent-vector.


## Training Procedure

### Generator 
**Input** : Gray scale image. Passed through multiple stages of encoder-decoder and reconstruct the entire image.
**Output**: The reconstructued output image has 3 channels resepctively for RGB.

### Discriminator
**Input**: Takes colored images as input.
**Output**: Output probability of the image being _TRUE_ or *FAKE*

The use of gradient tape here enchance the training capabilites as it allow creation of custom training loop. As a GAN training require a huge dataset and
loading one such might crash RAM, here that obstacle is overcomed by use of Input-pipeline. One of the attractive feature of this project.
This pipeline instead of loading entire dataset at once, allows loading of only desired batched data and also perform preprocessing over it.
That result and ensure in a stable GAN training.

### Outputs

#### Epoch 10
<img src="https://github.com/Gruhit13/ColorizerGAN/blob/master/Plot_10_epoch%20(1).png" alt="Board" width="550" height="550">

#### Epoch 20
<img src="https://github.com/Gruhit13/ColorizerGAN/blob/master/Plot_20_epoch.png" alt="Board" width="550" height="550">

#### Epoch 30
<img src="https://github.com/Gruhit13/ColorizerGAN/blob/master/Plot_30_epoch.png" alt="Board" width="550" height="550">

## Note
A more better results can be obtained by choosing as smaller batch size as possible. So that the GAN can understand color-variation for each image.
More powerful GPU can be of great use and some hyper-parameter tuning can serve as a cherry on cake. Here I traing this GAN for 50 epoch but with 
more powerful GPU/TPU a training for 150 epochs can serve very astonishing results.
