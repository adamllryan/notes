# Mixture Model
A **mixture model** (specifically Gaussian) is a model where the data is a mixture of values from different sources. It is one of the simplest examples of a generative model. 

While we normally are able to recover original source Gaussians, we can only sometimes recover original sources for our datapoints. 

Original source Gaussians can be recovered with [[13_probabilistic_parameter_estimation#Maximum Likelihood Estimation|MLE]]. However, applying MLE will leave you with no closed-form solution. This is where we will apply parameter estimation by splitting hidden and visible variables separately. We have two things to work through in doing so: 
- Expectation, what are the possible values for hidden variables and how likely do we think they are?
- Maximization, where we try to maximize the likelihood of our visible variables using data from expectations. 
This is the **expectation-maximization** (EM) algorithm. 

# Expectation-Maximization
The expectation-maximization algorithm is an *iterative-improvement* algorithm. It takes a set of guesses for parameters and then gives you more likely/better values for those parameters. It has to be repeated many times to get the "best" values, and it may become stuck at local maxima. This is why we run a few times using different starting values. 

Given $\Theta^t$ at iteration $t$, $Z$ (hidden variables), and $X$ (visible variables), we calculate $\theta^{t+1}$ as $\text{argmax}_\hat{\Theta}\sum_ZP(Z=z|X,\Theta^t)L((X,Z=z|\hat{\Theta}))$

First, we need to calculate the probabilities of $Z$. 






## Parameter Estimation: EM Algorithm
It is a group of algorithms used to deal with problems that have hidden variables. 
Iterative-improvement algorithm