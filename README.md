# Neural Artistic Style Transfer using Deep Learning

### Problem Definition:
- Given two images, content image and style image, the task is to produce a new stylized image using deep learning


### :Recipe

Here's what I did:

-Create an Interactive Session
-Load the content image
-Load the style image
-Randomly initialize the image to be generated
-Load the VGG19 model
-Build the TensorFlow graph:
-Run the content image through the VGG19 model and compute the content cost
-Run the style image through the VGG19 model and compute the style cost
-Compute the total cost
-Define the optimizer and the learning rate
-Initialize the TensorFlow graph and run it for a large number of iterations, updating the generated image at every step.

### Developers:
- Sahil Aggarwal [GitHub](https://github.com/sahilee26)
