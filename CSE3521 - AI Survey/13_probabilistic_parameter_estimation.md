How do we get these values in our joint probability tables? We have mostly been using Bernoulli distributions. Two other methods are categorical distribution and Gaussian distribution. 

# Bernoulli Distribution
The **Bernoulli distribution** for a binary random variable is depicted as $P(\text{True})=\lambda$ and $P(\text{False})=1-\lambda$. We produce a likelihood function of $\lambda$ as $\lambda^T(1-\lambda)^{N-T}$ where $N$ is the total number of samples collected and $T$ is the number of true values observed. A **likelihood function** is treated as a measure of the goodness of fit of a model to a set of data instances. 

It's built from the joint probability distribution of the samples and is a function of the parameters only, forcing random variables as fixed. 

# Maximum Likelihood Estimation
**Maximum likelihood estimation** is the process of choosing the parameters that will result in the maximum probability in the observed data. A useful trick is to apply log to the likelihood function and then take the derivative. This will let us find the maximum point with minimal effort. We can set it equal to zero because the derivative must be zero. 

An alternative to MLE is Bayesian parametrics, where we treat parameters as variables themselves. This is problematic, though, because the new parameter variables also need distributions. 

# Determining Truth Tables
To determine a table, we have to isolate conditions. A $P(+a|+b)$ is the number of samples with both true values divided by the number of samples where just A is true. This only works when we can measure every variable, though. 