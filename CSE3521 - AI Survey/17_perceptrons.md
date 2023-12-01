# Neural Networks

We define a neuron as a functional unit. A neural net is composed of *nodes* which are connected by *links*. Every link has a weight associated with it, intended to be modified so that passing in data from one end through a network will produce a goal response. Nodes have an *activation level* given inputs and weights, or a local computation based on inputs from neighbors. 

In order to use a neural network, we have to decide how many, what kind, and how to connect nodes we want. We normally assign random weights initially and then change them over time. 

# Computing Elements

Every node performs a simple computation before passing to another node. A computation is split into two components: 
- Linear input function (compute weights from inputs)
- Nonlinear activation function: transform weighted sum into final activation value
# Activation Functions

We have 3 types of nonlinear functions:
- Step function (0, 1 at t)
- Sign function (-1, then 1 at x>=0)
- Sigmoid Function (1/(1+e^(-x)))

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
# Perceptrons


# Classification? (20-23)

# Learning Algorithm

# Weight

# Learning

# Support Vector Machines

