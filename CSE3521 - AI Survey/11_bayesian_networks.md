Most real-world data contains high-dimensional and correlated variables. Even data instances are not independent at times. 

A large probability can be broken down like this: $p(X[1]=x[1],...,X[D]=x[D])=\Pi_dp(x[d]|x[1:d-1])$. 

Similarly, we can break down $P(X,Y|Z)$ into $P(X|Z)P(Y|Z)$. 
A **Markov model** shows that the future is independent of the past given the present. $P(x1,...,xn)=P(x1)(Px2|x1)P(x3|x1,x2)...$
This is much cheaper and first order Markov models are useful for one dimensional sequence data. 

# Bayesian Networks
We can represent a join distribution by drawing a directed, acyclic graph (DAG), where nodes are variables and edges represent a dependency. These are known as **Bayesian networks**. 

![[Bayes Network.png]]

The above can be written as $P(x_1)P(x_2|x_1)P(x_3|x_1)P(x_4|x_2,x_3)P(x_5|x_3)$. We can also reverse the process and create a DAG from the equation.  
# Naïve Bayes
In a naïve bayes graph, edges represent a dependency. It does not imply cause and effect. Gray nodes are observed and white nodes are unknown . 

# Markov Models

First order Markov models: Each layer depends on the last. 
Second order: Each layer depends on the past two layers. 
Hidden: Each layer depends on the last and also contains a hidden layer with unknown nodes. 

# Maximum a posteriori
We should choose the safest choice. If we flip a coin 10 times and 90% is heads, then we choose heads because it is the safest choice. 
$P(\lambda|D)$ where $\lambda$ is a boolean random variable and D is a single effect( data/evidence). 
$\text{argmax}_{\lambda}P(\lambda|D)=\text{argmax}_{\lambda}\frac{P(D|\lambda)p(\lambda)}{P(D)}=\text{argmax}_{\lambda}P(D|\lambda)p(\lambda)$  $p(\lambda)$ prior distribution over $\lambda$ before seeing D
$P(D|\lambda)$ likelihood of the data given $\lambda$
$P(\lambda|D)$ posterior distribution over $\lambda$ after seeing D

# Probabilistic Queries