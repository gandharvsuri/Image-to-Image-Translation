# IMAGE TO IMAGE TRANSLATION

## DATA

Domain X : Images of Yosemite national park in summer.

![Alt text](./Images/dowload.png?raw=true)

Donain Y : Images of Yomesite national park in winter.

![Alt text](./Images/download(1).png?raw=true)

## MODEL

### Discriminator 

Two Discriminators Dx and Dy to classify images as real or fake.

This network sees a 128x128x3 image, and passes it through 5 convolutional layers that downsample the image by a factor of 2. The first four convolutional layers have a BatchNorm and ReLu activation function applied to their output, and the last acts as a classification layer that outputs one value.

![Alt text](./Images/discriminator_layers.png?raw=true)

### Generator

Two Genearators to generate real looking 'fake' images of the Yosemite national park in summer (by Gx) and in winter (by Gy).

This network sees a 128x128x3 image, compresses it into a feature representation as it goes through three convolutional layers and reaches a series of residual blocks. It goes through a few (typically 6 or more) of these residual blocks, then it goes through three transpose convolutional layers (sometimes called de-conv layers) which upsample the output of the resnet blocks and create a new image!

![Alt text](./Images/cyclegan_generator_ex.png?raw=true)



## Loss Functions and Optimizers
 
Mean Squared Error Loss (MSE) for the discriminator.

Absolute Mean Error as a cycle consitency loss for to minimize the fake generated image and the original image.

## Training Loss 

After 100 epochs of training. 

Dx loss : 0.39

Dy loss : 0.50

G loss : 4.04
 
## Results 

Original winter pics and corresponding generated winter pics.

![Alt text](./Images/X2Y.png?raw=true)

Original winter pics and corresponding generated summer pics.

![Alt text](./Images/Y2X.png?raw=true)


