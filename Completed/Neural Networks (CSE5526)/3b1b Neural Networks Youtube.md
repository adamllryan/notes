---
id: 3b1b Neural Networks Youtube
aliases: []
tags: []
---

Neural networks are inspired by the brain. Simply put, we can describe a neuron as a thing that holds a number, between 0 and 1. The value in a neuron is its "activation", or how much it is stimulated. In the output layer, we can think of the values as the confidence of the network that something is that.

For each connection between neurons, we assign it a weight. To compute the activation level of a neuron, we take the sum of each previous connection multiplied by its respective weight. For each neuron, we can also assign a weight to offset it from zero.

Once we randomly initialize a network, we need to determine a cost function, which will tell us what our error is. We want to minimize the cost function

The cost function and error function are used interchangeably. We can add the squares of the differences of expected vs actual. or

$$
\sum_{i=1}^{n} (a - e)^2
$$

where a is the actual value and e is the expected value.

Then, for each input, we take the average of the cost to get the overall error.

As a whole, the cost function takes all of the weights and biases as input using our training examples as parameters and outputs one number telling us our cost.

But how do we teach the computer to do better? We can try to minimize the cost function, which will give us better answers.

To minimize the cost function, we can use gradient descent. We want to find the gradient of the cost function and move in the opposite direction to get closer to our local minima.

We take the output from the network and add the squares of the differences, which gives the total cost of the network.

## Back-propagation

We can think of the negative gradient
