# Bag-of-Words

**Bag-of-words representation** is a simplified representation of sentences that counts the occurrences of each word or phrase. It creates a vector that stores the number of occurrences of an instance. It misses grammar and word order, is not normalized, highly-sparse and dimensional, and words have no linkage. However, it is simple and fixed-size. 

For an **n-gram vector**, every set of n words is saved in a vector. For example, 1-gram would save "sheep", "follow", "wolfs" while 2-gram would save "sheep-follow", "follow-wolfs". The size of vocabulary is $\sum_n{D^n}$. It solves the issue of sequence loss, but it is much more expensive. We can normalize this, though. 

# Dataset Representation
## Histogram
A **histogram** displays each feature variable grouped into bins with the height being the count of occurrences. They are simple, discontinuous, are not scalable to higher dimensions, and need the right locations to place bins. 
## Kernel Density Estimation
Also known as **Parzen window**, **Kernel density estimation** represents the probability of an occurrence as a probability density function. The probability of seeing a value $u$ given a set $\{u_1,u_2,...,u_n\}$ is $p(u)=\frac{1}{N}\sum^N_{n=1}{k(u-u_n)}$. Unlike histograms, KDE needs to keep all data, has better resolution, has more computations, is scalable, and automatically creates bins. 

[[08_correlation_and_normalization|continued here]]
