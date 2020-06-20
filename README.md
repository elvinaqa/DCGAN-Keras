# DCGAN-Keras
Deep Convolutional Generative Adversarial Networks with Tensorflow Keras Application

# Application is shown on MNIST dataset

![w5Jsjt](https://user-images.githubusercontent.com/57037068/85211059-877e9280-b356-11ea-8d51-eb9ee530cd5c.gif)

Deep Convolutional GANs are used since they are better in handling image data (MNIST numbers)

The generator in GAN does not see the actual images of numbers, but learns gradients going back through the Discriminator. 
More strong discriminator means, more info in the gradients of the discriminator and better performance on spotting the fake zeros, ones, etc.
