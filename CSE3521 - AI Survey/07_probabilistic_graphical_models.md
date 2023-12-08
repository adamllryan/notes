Most real-world data contains high-dimensional and correlated variables. Even data instances are not independent at times. 

A large probability can be broken down like this: $p(X[1]=x[1],...,X[D]=x[D])=\Pi_dp(x[d]|x[1:d-1])$. 

Similarly, we can break down $P(X,Y|Z)$ into $P(X|Z)P(Y|Z)$. 
A **Markov model** assumes that the future is independent of the past given the present. $P(x1,...,xn)=P(x1)(Px2|x1)P(x3|x1,x2)...$
This is much cheaper and first order Markov models are useful for one dimensional sequence data. 

# Bayesian Networks
We can represent a joint distribution by drawing a directed, acyclic graph (DAG), where nodes are variables and edges represent a dependency. These are known as **Bayesian networks**. 

![[Bayes Network.png]]

The above can be written as $P(x_1)P(x_2|x_1)P(x_3|x_1)P(x_4|x_2,x_3)P(x_5|x_3)$. We can also reverse the process and create a DAG from the equation.  
## Naïve Bayes
In a naïve bayes graph, edges represent a dependency. It does not imply cause and effect. Gray nodes are observed and white nodes are unknown . 

## Markov Models
A Markov model is a sequential DAG. Each node depends on the last n nodes, where n is the order of the model. Markov models may also have a hidden layer, where our main sequence of nodes are now all unobserved. They each will depend on the next hidden node as well as an observed value, which previously was in the hidden node's place. 

## Maximum a posteriori
We should choose the safest choice. If we flip a coin 10 times and 90% is heads, then we choose heads because it is the safest choice. 
$P(\lambda|D)$ where $\lambda$ is a boolean random variable and D is a single effect( data/evidence). 
$\text{argmax}_{\lambda}P(\lambda|D)=\text{argmax}_{\lambda}\frac{P(D|\lambda)p(\lambda)}{P(D)}=\text{argmax}_{\lambda}P(D|\lambda)p(\lambda)$  $p(\lambda)$ prior distribution over $\lambda$ before seeing D
$P(D|\lambda)$ likelihood of the data given $\lambda$
$P(\lambda|D)$ posterior distribution over $\lambda$ after seeing D
How do we determine the probability of a value when we have a Bayesian Network?

# Probabilistic Inference
The first step is to survey what data we have. We are going to have the following categories of data:
- Query variable ($x_q$), what we are asking about. 
- Visible variable ($x_v$), what we know. 
- Hidden variable ($x_h$), what we don't know. 

Once we divide our variables into these categories, we can continue. 

1. Begin with Bayes' Rule:
$P(x_q|x_v, \theta)$ becomes $\alpha P(x_q, x_v|\theta)$. 

Next, we need to marginalize. 
2. For every hidden variable, we need to repeat this process:

$P(x_q|x_v, \theta)=\alpha \sum_{x_h}{P(x_q,x_h,x_v|\theta)}$ . 

Every hidden variable results in an additional summation. 

3. Expand out the joint probability using the Bayesian Network. 
4. Using known values, fill out what we can. A query variable should be left without a true or false value because we need to determine both. 
5. Factor out as much as you can to simplify calculations. Any known values on the outside can be absorbed into the $\alpha$. 
6. Begin to evaluate. Summations should just be the sum of the hidden variable when it is true and when it is false. The query variable should be evaluated for true and false, so it becomes a vector. 
7. Once complete, normalize against the true and false vector that you have for $x_q$. 

Notice: this is time-intensive and long! We want to skip as much as we can. One solution is to **pre-marginalize**, or create a new BN with its hidden variables preprocessed (exponential cost, but makes inference linear). Another solution is to create a special algorithm like tree structure to create a polynomial time algorithm. Finally, we can always approximate a guess. 

# Probabilistic Parameter Estimation
How do we get these values in our joint probability tables? We have mostly been using Bernoulli distributions. Two other methods are categorical distribution and Gaussian distribution. 

## Bernoulli Distribution
The **Bernoulli distribution** for a binary random variable is depicted as $P(\text{True})=\lambda$ and $P(\text{False})=1-\lambda$. We produce a likelihood function of $\lambda$ as $\lambda^T(1-\lambda)^{N-T}$ where $N$ is the total number of samples collected and $T$ is the number of true values observed. A **likelihood function** is treated as a measure of the goodness of fit of a model to a set of data instances. 

It's built from the joint probability distribution of the samples and is a function of the parameters only, forcing random variables as fixed. 

## Maximum Likelihood Estimation
**Maximum likelihood estimation** is the process of choosing the parameters that will result in the maximum probability (maximizing the weight of our observed data, not it being true) in the observed data. A useful trick is to apply log to the likelihood function and then take the derivative. This will let us find the maximum point with minimal effort. We can set it equal to zero because the derivative must be zero. 

An alternative to MLE is Bayesian Parametrics, where we treat parameters as variables themselves. This is problematic, though, because the new parameter variables also need distributions. 

## Determining Truth Tables
To determine a table, we have to isolate conditions. A $P(+a|+b)$ is the number of samples with both true values divided by the number of samples where just A is true. This only works when we can measure every variable, though. 
