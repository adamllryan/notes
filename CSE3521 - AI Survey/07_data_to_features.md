# Bag-of-Words

**Bag-of-words representation** is a simplified representation of sentences that counts the occurrences of each word or phrase. It creates a vector that stores the number of occurrences of an instance. It misses grammar and word order, is not normalized, highly-sparse and dimensional, and words have no linkage. However, it is simple and fixed-size. 

For an **n-gram vector**, every set of n words is saved in a vector. For example, 1-gram would save "sheep", "follow", "wolfs" while 2-gram would save "sheep-follow", "follow-wolfs". The size of vocabulary is $\sum_n{D^n}$. It solves the issue of sequence loss, but it is much more expensive. We can normalize this, though. 
# Dataset representation
Histogram and parzen window
## Histogram
Each feature variable has its values grouped into bins with the height being the count of occurrences. 

### Feature Distributions

We can create a distribution with interval size $\Delta$, which controls the shape and smoothness. 

### Kernel Density Estimation

AKA Parzen window. It is the probability density of a variable given already seen variables. 

$p(u)=\frac{1}{N}\sum^N_{n=1}{k(u-u_n)}$
Has a probability density function and gaussian distribution is popular k(u). 
$\sigma=h$ controls shape. too small h is less smooth

#### Comparison
Histograms:
Simpler, Discontinuous, not scalable to higher dimensions, need right locations
KDE:
Need to keep all training data, smoother/better resolution, more computation, scalable, automatic bins
# Dimensionality Reduction