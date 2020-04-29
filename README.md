# Neural Artistic Style Transfer using Deep Learning

### Problem Definition:
- Given two images, content image and style image, the task is to produce a new stylized image using deep learning

![output](output/100.png)

These were the input images used (museum and painting):

![input-content](louvre_small.jpg)

![input-style](monet.jpg)


### Recipe:

Here's what I did-

We define a cost function that tells how good is particular image. The cost function includes contest cost that tells how similar contents of generated iamge is with respect to the content image and also includes contest cost that tells how similar style of generated iamge is with respect to the style image.
We also define two hyper parameters alpha and beta that define relative weighting between two costs.

### Algorithm
First we intialise generated image randomly. Use graident descent to minimize J(G).

### Content Cost

We use pretrained VGG-19 network(19 layers) and specifically middle layers to measure how similar content and generatd image is. 
Let's say if I took hidden layer L and A[c][l] and A[g][l] be activations of these layers on two images.So, if these two activations are similar, then that would seem to imply that both images have similar content.We'll take the element-wise difference between these hidden unit activations in layer l, between when you pass in the content image compared to when you pass in the generated image, and take that squared.

### Style Cost
We need to do is define the style as the correlation between activations across different channels in this layer L activation. So here's what I mean by that. Let's say you take that layer L activation. So this is going to be nh by nw by nc block of activations, and we're going to ask how correlated are the activations across different channels.How this correlation corresponds to style.
Refer this video-
https://www.coursera.org/learn/convolutional-neural-networks/lecture/AzcCW/style-cost-function. 

#### Intuition
So the correlation tells yus which of these high level texture components tend to occur or not occur together in part of an image and that's the degree of correlation that gives you one way of measuring how often these different high level features, such as vertical texture or this orange tint or other things as well, how often they occur and how often they occur together and don't occur together in different parts of an image.

More formally, given an image we computes something called a style matrix, which will measure all those correlations. Let's let a superscript l, subscript i, j, k denote the activation at position i,j,k in hidden layer l. So i indexes into the height, j indexes into the width, and k indexes across the different channels. 

So what the style matrix will do is we're going to compute a matrix G[l]. This is going to be an nc by nc dimensional matrix, so it'd be a square matrix. We have nc channels and so you have an nc by nc dimensional matrix in order to measure how correlated each pair of them is. So particular G, l, k, k prime will measure how correlated are the activations in channel k compared to the activations in channel k prime.

![input-style](https://github.com/sahilee26/Neural-Artistic-Style-Transfer/blob/master/Style%20matrix.PNG)

### Solving the optimization problem
Create an Interactive Session. Load the content image and the style image. Randomly initialize the image to be generated.Load the VGG19 model. Build the TensorFlow graph. Run the content image through the VGG19 model and compute the content cost. Run the style image through the VGG19 model and compute the style cost. Compute the total cost. Define the optimizer(adam in our case) and the learning rate. Initialize the TensorFlow graph and run it for a large number of iterations, updating the generated image at every step.

### Developers:
- Sahil Aggarwal [GitHub](https://github.com/sahilee26)
