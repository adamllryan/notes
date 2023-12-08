# Neural Networks

We define a neuron as a functional unit. A neural net is composed of *nodes* which are connected by *links*. Every link has a weight associated with it, intended to be modified so that passing in data from one end through a network will produce a goal response. Nodes have an *activation level* given inputs and weights, or a local computation based on inputs from neighbors. 

In order to use a neural network, we have to decide how many, what kind, and how to connect nodes we want. We normally assign random weights initially and then change them over time. Neural Networks are bottom-up models.  

# Computing Elements

Every node performs a simple computation before passing to another node. A computation is split into two components: 
- Linear input function (compute weights from inputs)
- Nonlinear activation function: transform weighted sum into final activation value
# Activation Functions

We have 3 types of nonlinear functions:
- Step function (0, 1 at t)
- Sign function (-1, then 1 at x>=0)
- Sigmoid Function (1/(1+e^(-x)))
ReLU is another! Not sure what it is though. 
# Network Structures

There are two main varieties of network structures:
- Feed-forward, where our graph has no cycles (DAG)
- Recurrent, where links can contain cycles

Feed-forward networks have no internal state, other than weight values. It only computes functions of input values using weights. Dissimilar to us because we have memory and back connections! In this case learning just changes weights. We can't use linear activation functions because it will always be equivalent to a single node. 

There are 3 types of units in a network:
- Input, where we add our data
- Output, where we get our results
- Hidden, which are neither
Multilayer networks have one or more layers of hidden units. One hidden layer allows us to represent any continuous function. Two hidden layers allows us to represent discontinuous functions. 

Neural networks are very subject to overfitting if we use too many weights in the model. We use cross validation techniques to determine the right size of a network. 
# Perceptrons

Perceptrons were first studied in the late 1950's. A single perceptron has at least one input connected by weights. They represent functions that are linearly separable. Something something *step activation*. (Check definition, not provided in slides) Excitatory synapses increase potential and inhibitory decrease.
# Classification

*CHECK LATER THIS IS A GUESS*
Step activation for a perceptron outputs a 0 if our value is less than the *threshold value* and a 1 if our value is greater. 

If our step activation function is y=x and we pass in (1,2)=(x,y) into our perceptron, we will get 1 as the output, because our input is greater than our step activation function y=x. 

A perceptron can represent a function only if a line can separate ALL true and false values. A perceptron may have multiple correct solutions to separate positive and negative values. 

With boolean functions, AND and OR functions are linearly separable, but not XOR. 

# Learning Algorithm

First, we randomly assign weights. Then we train:
1. Divide process into epochs. 
2. Make small adjustments in weights to reduce difference between observed and predicted values. 

We can use gradient descent to update our weights. 

# Learning

The *perceptron convergence theorem* uses gradient descent. 

We can also use the *back-propagation* learning algorithm. This works by assessing blame for an error and dividing it locally among the weights that contributed to the error. Then we update layer by layer backwards. 
# Support Vector Machines

SVMs attempt to maximize the margin between positive and negative training examples. In other words, it tries to adjust the threshold line to be as equally as possible in between our true and false training examples. 

Non-linear SVMs may handle this better because it attempts to map the input space to a higher dimension where the training set is more likely to be linearly separable. 