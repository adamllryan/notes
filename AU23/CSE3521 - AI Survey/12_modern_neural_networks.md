## Deep Learning

Suppose we have a 3 layer neural network. Both hidden layers have 4 neurons, so we have 4x4 weights or 16 weights. Now if we increase the neurons to 8, we have 8x8 or 64 weights. As we increase our number of neurons, we have extreme growth which is expensive to handle. This is *quadratic* growth. 

The solution to this is *deep learning* networks. While 3-layer networks are all we technically ever need, increasing the layers to more than 3 will give us our increased neurons while limiting the growth of weights. It does not let us solve more complex problems but it reduces the amount of weights required. It gives us linear increase in weights.

In this class, we will consider anything with more than 3 layers deep, however in practice: 
- Early examples of deep networks use 10-20 layers
- Current networks can use 100s of layers

Adding more layers introduces problems into the network. 

The *vanishing gradient* problem: Back propagation calculates gradients one layer at a time, starting with the output. This problem refers to the phenomena where gradient values approach zero as we get further from the output layer. And we need these gradient descent values to make adjustments proportional to the magnitude of the gradient. As our gradient gets smaller, our rate of adjustment drops. 

In other words, as our network gets deeper, our rate of learning decreases and becomes more shallower near the start of the network. In short, the longer the network, the less impact those earlier layers have on the output. 

*Dropout* is a technique used to avert deep network issues. It randomly disables segments of the network (temporarily set weights to 0) while training so that, temporarily, the network becomes narrower and neurons are forced to be prioritized. 

It comes with the side effect of high redundancy in a network, where it can learn multiple ways to solve a problem and then combine them to produce more reliable results. 

A second technique is *stochastic gradient descent*. This method trains the network with random subsets from our dataset, changing them each iteration. This means that each epoch represents one pass through the entire dataset. We call this *batch training*.

It introduces *helpful noise*, pushing it into an unstuck state. However, we need to know how *much* noise is optimal, because too much can introduce bias. 

A third method (10 layers to 100 layers): *residual networks* are a newest method. The idea of a residual network is to start every weight at zero instead of fixed. This way, they do nothing. Then we start at the top of the network and start training on the top layer. If that is not enough, we use the top two layers, then the top 3, until we have a sufficient model. 

The issue with this is that the earlier layers tend to do nothing. While we might have a 200 layer network, there is a chance that only 100 are doing something. This is an area of active work. 

Currently, we are working on *skip connections*. These let layers skip between layers and travel between layers. 

## Computer Vision

We can think of computer vision as the opposite of graphics rendering. Instead of generating an image from a representation of data, we turn an image into a representation of data. 

Our perception is the action of taking raw input and transforming that into ideas about the world. 

**Convolution** is the method of applying a filter to a signal. It transforms an image into a different image that is easier to parse or process. 

A *blur* filter blurs an image. We also have *vertical edge* and *horizontal edge* detection filters. 

Nodes are not directly affected by all nodes in the previous layer. Weights on the edges may be reused. Additionally, local patterns can show up at different locations. 

The benefits of weight reuse are: 
- Smaller training datasets
- More efficient computation
- Max pooling (reduces size of filtered image)
- Fully connected final information

We can use filters as a feature detector! We can have the CNN learn its own filters to have automated feature detection. 

## Text and Language

Our original approach was to use [[05_machine_learning#Bag-of-Words|one-hot encoding]] to turn words into vectors. However, this leads to many inputs and weights while having mostly zeros for everything. 

A much better approach is **Word2Vec**, which uses one-hot encoding as a first layer weight, then use its first layer weight as a vector for each word. It creates a vector in linear subspace, and we notice that subtle meanings can be encoded as well. We also noticed that bias can become encoded, too. 

But what if we want to input sentences into a neural network? A naive approach would be to append word vectors together. This results in two problems:
- NNs want fixed-size inputs, but sentences have variable length. 
- Grammar in human languages are flexible, where we can have different meanings based on ordering or different orderings to represent the same meanings. 

Instead, we can feed words in one at a time, and then use a **recurrent neural network** to recursively address the meaning of the sentence as more words are added. 

With a recurrent neural network, we run into the issue of oscillation when we pass output back into input. However, we can simply use deep network concepts to solve the issues of RNNs. By treating each reinput iteration as its own layer, we solve the issue of oscillation. 

**Machine Translation** uses encoder and decoder segments to translate text. The encoder's role is to collect information from the input and turn it into a universal meaning. The decoder uses this information to reverse the process but in another language. 

Not too important, but machine translation often uses symbols to help translate. Some such symbols are `<GO>` and `<STOP>` to indicate the start and end of the statement.  

**Image Labelling** can also work similarly, where we use the same model but replace the encoder with a CNN that processes an image down to a descriptive vector. Then our RNN decoder converts that to text. 

We can also just flip this process and now we have **image generation**. The tool [Stable Diffusion](https://github.com/Stability-AI/stablediffusion) encodes text, then decodes into an image. This output is fed back into an image encoder and then decoded repeatedly until it is stable.  

**Transformers** take our input and predicts the next output from the current output sequence along with the *entire* input sequence. It has an attention mechanism that matches each input word with every other input word. 

**Large Language Models** is the idea of taking our current approach and scaling it massively. GPT-3 is a massive transformer scaled to run in data centers. ChatGPT is not GPT-3, it takes our input, understands it, and then creates a DIFFERENT response instead of translating. 

## Flaws

As models become more capable of doing useful work, we have to worry more about their shortcomings. Some main areas of focus are:
- Bias, or incorrect assumptions based on factors that don't really matter. Such as race/gender bias. 
- Hallucination, or the ability to deal with inputs that are not training data. AKA the issue with genAI and creating correct-seeming data while actually making it up. 
