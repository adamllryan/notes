How do we get these values in our joint probability tables? We have mostly been using Bernoulli distributions. Two other methods are categorical distribution and Gaussian distribution. 

# Bernoulli Distribution
The **Bernoulli distribution** for a binary random variable is depicted as $P(\text{True})=\lambda$ and $P(\text{False})=1-\lambda$. We produce a likelihood function of $\lambda$ as $\lambda^T(1-\lambda)^{N-T}$ where $N$ is the total number of samples collected and $T$ is the number of true values observed. A **likelihood function** is treated as a measure of the goodness of fit of a model to a set of data instances. 

It's built from the joint probability distribution of the samples and is a function of the parameters only, forcing random variables as fixed. 
# Parameter estimation
Probability models often have parameters. Bernoulli distribution (two outcomes), categorical distribution (multiple discrete assignments, Bernoulli with 3+ assignments), Gaussian distribution (continuous). 

## Likelihood function
is the goodness fit of a model
## Maximum likelihood estimation
P(observations;parameters). Choose the params that maximize probability of observed data. 
Log-likelihood, differentiate, equate to zero and solve
d/dxlogx=0
## Gaussian distribution

P(X=x)=

MLE alternatives: bayesian parametrics. Uses parameters as vars themselves