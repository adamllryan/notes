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

### Notation

NOTATION
## Principal Component Analysis: Linear dimensionality Reduction

### Karhunen-Loeve Transform

z

Maximize variance fro x to z
Minimize reconstruction error from z back to x
### PCA where M=1
Maximize variance, minimize loss

z_n

to find w1, calculate COV, calculate eigenvalues of COV, find largest eigenvalue of COV corresponding to w1
### PCA M > 1
Maximize variance of projection strengths. Largest eigenvalues/vectors are our values for w1 and second is w2 and so on. 
#### How to choose M
Where sum of eigenvalues of m / EV of D >= Threshold (normally 90/95%)
##### Minimize Error (Projection)



# Nonlinear Dimensionality Reduction

It can fail at times. We want to be able to reduce dimensionality without losing information. 

## General Idea (M < D)

Most fail, Laplacian eigenmap is kind of close for the swiss roll problem

# t-SNE

T distributed stochastic Neighbor embedding. Uses pairwise joint probabability to characterize every set of instances. It preserves the probability of something being this far from sometihng else. 

# Summary

DR: Curse of dimensionality, visualization, noise redundancy removal. Need to define criterion to preserve properties
PCA: Linear method to preserve data variance. Use normalized Eigenvectors of data covariance matrix
Nonlinear DR: Preserve structures