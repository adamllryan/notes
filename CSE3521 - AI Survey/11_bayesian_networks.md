# Dependent Feature Variables
Most real-world data has high-dimensional/correlated variables. (Think pixels, words, genes)
We need a probabilistic model. 

# Chain rule of probability 

# Conditional Independence

# Markov Models

# Probabilistic Graphical Models

# Graph terminology

Clique is any sub complete graph
Child, parent, ancestor, decedents, neighbors, cycle, tree

# directed graphical models
Graphical model whose graph is a DAG. Also known as Bayes network/belief network. 

# Naïve Bayes
The arrow does not mean cause->effect, it just represents a dependency. 
A result points to a dependency. Gray colored nodes are observed  and white are unknown. 

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