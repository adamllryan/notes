## Sparseness & Dimensionalities
Data can have many features per sample, and grows as time progresses. Less information present, more likely o be true with greater dimensions. 
### Reduce this

# Dimensionality Reduction
We can reduce dimensions in cases where:
- Correlation means redundancy where knowing an element means we know another. 
Bins grow exponentially
Curse of dimensionality: Feature space becomes more sparse for increasing number of dimensions of a fixed-size training set. 
### General Idea of DR
Linear dimensionality reduction: reduce linearly

SEE SLIDES
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