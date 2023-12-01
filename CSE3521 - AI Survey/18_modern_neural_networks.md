# Deep Learning

Suppose we have a 3 layer neural network. Both hidden layers have 4 neurons, so we have 4x4 weights or 16 weights. Now if we increase the neurons to 8, we have 8x8 or 64 weights. As we increase our number of neurons, we have extreme growth which is expensive to handle. This is *quadratic* growth. 

The solution to this is *deep learning* networks. While 3-layer networks are all we technically ever need, increasing the layers to more than 3 will give us our increased neurons while limiting the growth of weights. It does not let us solve more complex problems but it reduces the amount of weights required. It gives us linear increase in weights.

In this class, we will consider anything with more than 3 layers deep, however in practice: 
- Early examples of deep networks use 10-20 layers
- Current networks can use 100s of layers

Adding more layers introduces problems into the network. 

The *vanishing gradient* problem: Back propagation  calculates gradients one layer at a time, starting with the output. This problem refers to the phenomena where gradient values approach zero as we get further from the output layer. And we need these gradient descent values to make adjustments proportional to the magnitude of the gradient. As our gradient gets smaller, our rate of adjustment drops. 

In other words, as our network gets deeper, our rate of learning decreases and becomes more shallower near the start of the network. In short, the longer the network, the less impact those earlier layers have on the output. 

*Dropout* is a technique used to avert deep network issues. It randomly disables segments of the network (temporarily set weights to 0) while training so that, temporarily, the network becomes narrower and neurons are forced to be prioritized. 

It comes with the side effect of high redundancy in a network, where it can learn multiple ways to solve a problem and then combine them to produce more reliable results. 

A second technique is *stochastic gradient descent*. This method trains the network with random subsets from our dataset, changing them each iteration. This means that each epoch represents one pass through the entire dataset. We call this *batch training*.

It introduces *helpful noise*, pushing it into an unstuck state. However, we need to know how *much* noise is optimal, because too much can introduce bias. 

A third method (10 layers to 100 layers): *residual networks* are a newest method. The idea of a residual network is to start every weight at zero instead of fixed. This way, they do nothing. Then we start at the top of the network and start training on the top layer. If that is not enough, we use the top two layers, then the top 3, until we have a sufficient model. 

The issue with this is that the earlier layers tend to do nothing. While we might have a 200 layer network, there is a chance that only 100 are doing something. This is an area of active work. 

Currently, we are working on *skip connections*. These let layers skip between layers and travel between layers. 

# Computer Vision

We can think of computer vision as the opposite of graphics rendering. Instead of generating an image from a representation of data, we turn an image into a representation of data. 

Our perception is the action of taking raw input and transforming that into ideas about the world. 

*Convolution* is the method of applying a filter to a signal. It transforms an image into a different image that is easier to parse or process. 

A *blur* filter blurs an image. We also have *vertical edge* and *horizontal edge* detection filters. 

# Text and Language



# Flaws

# 