## Sparseness & Dimensionalities
Data can have many features per sample, and grows as time progresses. Less information present, more likely o be true with greater dimensions. 
### Reduce this

# Dimensionality Reduction
We can reuce dimensions in cases where:
- Correlation means redundancy where knowing an element means we know another. 
Bins grow exponentially

### General Idea of DR
Linear dimensionality reduction: reduce linearly
### Notation

## Principal Component Analysis: Linear dimensionality Reduction

### Karhunen-Loeve Transform
$z=W^T(x-\mu)$ 
### PCA where M=1

### PCA M > 1

#### How to choose M

##### Minimize Error (Projection)

## PCA Summary

### Examples

### Reconstruction

### Applications of PCA

# Nonlinear Dimensionality Reduction

It can fail at times. We want to be able to reduce dimensionality without losing information. 

## General Idea (M < D)

Most fail, Laplacian eigenmap is kind of close for the swiss roll problem

# t-SNE

T distributed stochastic Neighbor embedding. Uses pairwise joint probabability to characterize every set of instances. It preserves the probability of something being this far from sometihng else. 

# Summary

do later lmao
