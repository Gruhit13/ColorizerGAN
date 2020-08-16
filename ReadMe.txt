ColorizerGAN work as similar to all other GANs. Here I have used Pix2Pix GAN with U-Net Architecture.

Input: It takes gray scale image as an input. It passes through multiple stages of encoder and decoder stages and recsonstruct the entire image.
Output: The reconstructued output image has 3 channels resepctively for RGB.

Here I have used gradient tape to have well structured and desirable training.