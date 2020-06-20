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

![download (19)](https://user-images.githubusercontent.com/57037068/85211490-ee9e4600-b35a-11ea-8633-284b005e7f22.png)
![download (18)](https://user-images.githubusercontent.com/57037068/85211491-f0680980-b35a-11ea-8eda-a093b4de2668.png)




DeepNote:
Autoencoders

The job of an autoencoder is to simultaneously learn an encoding network and decoding network. This means an input (e.g. an image) is given to the encoder, which attempts to reduce the input to a strongly compressed encoded form, which is then fed to the decoder.

The network learns this encoding/decoding because the loss metric increases with the difference between the input and output image - every iteration, the encoder gets a little bit better at finding an efficient compressed form of the input information, and the decoder gets a little bit better at reconstructing the input from the encoded form.

Summarised: An autoencoder learns to represent some input information very efficiently, and subsequently how to reconstruct the input from it's compressed form.

Generative Adversarial Networks

Here, we have a "generator" whose job is to take some noise signal and transform it to some target space (again, images is a popular example). The other component (the adversary) is the "discriminator", whose job is to distinguish real images drawn from the desired target space from the fake images created by the generator. In this case, the network is trained in two alternating phases, each with a different loss:

Firstly, the discriminator is given labelled samples from the real set of images, and fake images generated by the generator (of course, at the start, these images are just noise). Loss is calculated according to some binary classification loss metric (e.g. crossentropy). The discriminator thus begins to learn the difference between a fake image and a real image.

Before it can learn too much, though, we switch over to the generator. To train the generator, we once again feed in some noise and check the output of the discriminator. This time, we want the discriminator to detect that the image (generated by the generator) is real - this means that we have successfully fooled the discriminator, and therefore the generator has begun to learn how to make an image that resembles a "real" image from the training set.

Summarised: A GAN uses an adversarial feedback loop to learn how to generate some information that "seems real" (i.e. looks the same/sounds the same/is otherwise indistinguishable from some real data)

The difference

Hopefully that shows that there is a very fundamental structural difference between the two networks, and the goals that each of them are trying to achieve during the learning process. I don't really know if GANs are necessarily "more successful", but for certain generative problems they have been observed to give more "realistic" outputs. Why? My gut says that a GAN probably learns more about "how can I make an image look real in general" rather than "how can I memorise this particular set of images with the greatest accuracy/efficiency". But there are certainly similarities, in particular between the generator (of the GAN) and the decoder (of the autoencoder).
