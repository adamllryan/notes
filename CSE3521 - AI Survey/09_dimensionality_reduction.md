# Dimensionality
Data is large. It can have thousands to millions of features per sample, and the tendency is to grow as time progresses. It is often sparse, where there is less information than the dimensionality implies. High dimensionality increases the number of parameters and evaluation costs. 

The **curse of dimensionality** states that feature space becomes more sparse for increasing number of dimensions of a fixed-size training set. As the number of dimensions increases in a fixed-size training set, so does the likelihood of sparseness. In a histogram, our bins grow exponentially with dimension increases ($r^D$)!

# Dimensionality Reduction

Given highly-dimensional data $x \in R^D$, we want to find a representation $z \in R^M$ where $M<D$. This will:
- let us visualize data more easily. 
- save in computation and storage costs. 
- removes noise. 
- reduces curse of dimensionality. 

One way we can reduce dimensionality is where we have high correlation. When correlation exists between dimensions, we can eliminate all but one of those variables to reduce costs and redundancy. 

The general idea of dimensionality reduction is to *reduce linearly*. 

**Linear** dimensionality reduction aims to cut down on correlated dimensions, $z=W^Tx$ where $W \in R^{D \times M}$. 
**Nonlinear** dimensionality reduction aims to define a function that maps the original set to a lower dimension set, $z=g(x)$ where $g:R^D \mapsto R^M$. 

# Principal Component Analysis

**Principal component analysis** is conducted through the Karhunen-Loeve transform: $z=W^T(x-\mu)$ where $W \in R^{D \times M}$ and $W^TW=I$. We need to maximize variance from $x$ to $z$ and minimize reconstruction error from $z$ back to $x$. PCA is linear!

Maximizing *variance* helps us keep the most information and minimizing *reconstruction error* minimizes the loss. We must find a $W$ shared by all $x \in X=[x_1,...,x_n]$.

In order to maximize variance, we need to:
1. Calculate covariance matrix $\Sigma$ of the data. 
2. Calculate the eigenvalues and eigenvectors of $\Sigma$. 
3. Find the largest positive eigenvalue of $\Sigma$ and use the corresponding eigenvector as our value. 
If we need more eigenvalues and vectors, we can reuse the computation values and just order by descending size. 
Features are **decorrelated** if there is zero covariance between each other. 

We can choose an M via: $\frac{\Sigma^M_{d=1}\lambda_d}{\Sigma^D_{d=1}\lambda_d}\geq \text{Threshold}$ where our threshold is a fraction we decide (most common .90 or .95). 

Minimizing the reconstruction, or projection, error also needs to be considered, but we didn't really focus on that. 

PCA is commonly used for pre-processing and feature extraction in order to remove noise and reduce data dimensionality. It is also used to *de-correlate* data. 

However, PCA sometimes fails. Here is a common example (swiss roll problem): 
![[Swiss Roll.png]]
# Nonlinear Dimensionality Reduction

Sometimes, linear dimensionality reduction fails. This is where nonlinear dimensionality reduction comes in ($z=g(x)$ where $g:R^D \mapsto R^M$). 

**T-distributed stochastic neighbor embedding** (t-SNE). Builds a pairwise joint probability to characterize every set of instances. It preserves the probability of something being this far from something else. 
