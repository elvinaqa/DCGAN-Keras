# DCGAN-Keras
Deep Convolutional Generative Adversarial Networks with Tensorflow Keras Application

# Application is shown on MNIST dataset

![w5Jsjt](https://user-images.githubusercontent.com/57037068/85211059-877e9280-b356-11ea-8d51-eb9ee530cd5c.gif)

Deep Convolutional GANs are used since they are better in handling image data (MNIST numbers)

The generator in GAN does not see the actual images of numbers, but learns gradients going back through the Discriminator. 
More strong discriminator means, more info in the gradients of the discriminator and better performance on spotting the fake zeros, ones, etc.

Layer (type)                 Output Shape              Param #   
=================================================================
dense (Dense)                (None, 6272)              633472    
_________________________________________________________________
reshape (Reshape)            (None, 7, 7, 128)         0         
_________________________________________________________________
batch_normalization (BatchNo (None, 7, 7, 128)         512       
_________________________________________________________________
conv2d_transpose (Conv2DTran (None, 14, 14, 64)        204864    
_________________________________________________________________
batch_normalization_1 (Batch (None, 14, 14, 64)        256       
_________________________________________________________________
conv2d_transpose_1 (Conv2DTr (None, 28, 28, 1)         1601      
=================================================================
Total params: 840,705
Trainable params: 840,321
Non-trainable params: 384


Got better results for image data in DCGANs than GANs because of the fact that of using Convolutional layers (Conv2d vs Conv2dTranspose)
In the first example, had Mode Collapse issues (model only generated the similar images, since it already fooled the discrimnator to be "real" images). However, in the Deep Convulutional Nets, diversity of generated images is observed, thus, proving the superity of DCGAns.


