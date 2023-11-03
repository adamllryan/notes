# Bag-of-words representation

Simplified representation of sentences by counting the occurrences of each word or phrase. 

## N-gram vocabulary
for an n-gram vector, every set of n words is saved in a vector. For example, 1-gram would save "sheep", "follow", "wolfs" while 2-gram would save "sheep-follow", "follow-wolfs". The size of vocabulary is $\sum_n{D^n}$
Cons:
- This is not normalized though :(
We can solve this with feature normalization. We can take the $L_p$ norm. 
L1 normalization is just dividing the vector by sum of its components. L2 is widely used if angle has an important role. 
- Missing sequential information
- Words treated as independent
- Very sparse, lots of dimensions
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