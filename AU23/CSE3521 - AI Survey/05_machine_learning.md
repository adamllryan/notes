## Machine Learning

Here are two definitions:

- **Machine learning** is a set of methods that can automatically detect patterns in data and then apply those patterns to predict future data (or perform some other form of decision making). 
- **Machine learning** refers to the automated detection of meaningful patterns in data. 

There are three key ingredients to machine learning:
- **data**, collected from past observations.
- **modelling**, devised to capture patterns in the data. 
- **prediction**, to apply the model to forecast what will happen in the future. 

All models are incorrect, but they may be useful. We must tolerate randomness and mistakes because many things are [[01_agent_design#Environment Types|stochastic]] by nature. 

Often, we can run into the issue where our training data is only memorized by our model. This is called **overfitting** and is noticeable when we observe good performance on training data but not new, unseen data. We want to achieve **generalization**, where the model generalizes patterns for future data. 

### Data

**Training data** is used to train the model. We often use batches to help mitigate errors or issues in segments of the data. However, batches may cause outliers be ignored because they effectively average all the batches.  
**Test data** is a smaller subset of the dataset, split off early on such that none of it is present in the training data. We want this so we can see if the model can accurately predict outcomes with new, unseen information. 

Our dataset is a collection of data instances or examples. Its definition depends on the problem. It is made up of **feature variables**, which store numerical or categorical values. Categorical values have no inherent ordering, like the color of a car. 

A **one-hot vector** is a vector that stores every feature variable. 0 and 1 represent false and true. 

## Feature Extraction

We can extract features from our data if our data contains a certain pattern or feature. **Feature extraction** starts from our initial measured data and builds derived values that are intended to be *informative*, *non-redundant*, *facilitating future learning and generalizing steps*, and *leading towards better human interpretations*. Feature extraction is used in [[12_modern_neural_networks#Text and Language|NLP]] and [[12_modern_neural_networks#Computer Vision|computer vision]]. 

## Bag-of-Words

**Bag-of-words representation** is a simplified representation of sentences that counts the occurrences of each word or phrase. It creates a vector that stores the number of occurrences of an instance. It misses grammar and word order, is not normalized, highly-sparse and dimensional, and words have no linkage. However, it is simple and fixed-size. 

For an **n-gram vector**, every set of n words is saved in a vector. For example, 1-gram would save "sheep", "follow", "wolfs" while 2-gram would save "sheep-follow", "follow-wolfs". The size of vocabulary is $\sum_n{D^n}$. It solves the issue of sequence loss, but it is much more expensive. We can normalize this, though. 

## Dataset Representation

### Histogram

A **histogram** displays each feature variable grouped into bins with the height being the count of occurrences. They are simple, discontinuous, are not scalable to higher dimensions, and need the right locations to place bins. 

### Kernel Density Estimation / Parzen Window

Also known as **Parzen window**, **Kernel density estimation** represents the probability of an occurrence as a probability density function. The probability of seeing a value $u$ given a set $\{u_1,u_2,...,u_n\}$ is $p(u)=\frac{1}{N}\sum^N_{n=1}{k(u-u_n)}$. Unlike histograms, KDE needs to keep all data, has better resolution, has more computations, is scalable, and automatically creates bins. 

### Feature Correlation

**Correlation** (Pearson's correlation coefficient) is the *degree* to which a pair of variables are linearly related. We take a training set and denote $x\in \mathbb{R}^D$, where D is the number of dimensions of each data instance. When we remove correlation from our data, it appears as if we are rotating it. 

We can determine the correlation between two dimensions, $d$ and $d'$, with the following formula:  
$\rho_{d,d'}=\frac{E_x[(x[d]-\mu[d])(x[d']-\mu[d'])]}{\sigma_d\sigma_{d'}}=\frac{\frac{1}{N}\sum^{N}_{n=1}{[(x[d]-\mu[d])(x[d']-\mu[d'])]}}{\sigma_d\sigma_{d'}}$.  
We'll need the mean $\mu$ and standard deviation $\sigma$ for these, which can be found with these:
- $\mu[d]=\frac{1}{N}\sum^N_{n=1}x_n[d]$ or $\mu=\frac{1}{N}\sum^N_{n=1}x_n$
- $\sigma_d=(\frac{1}{N}\sum^N_{n=1}(x_n[d]-\mu[d])^2)^{1/2}$

**Covariance** ($\Sigma$) is linearly related to our correlation, with the only difference being that covariance does not have correlation's denominator $\Sigma=\frac{1}{N}\Sigma^N_{n=1}{[(x_n-\mu)(x_n-\mu)]^T}$. This means while $\sigma \in [-1,1], \Sigma \in [-\infty,\infty]$. 

### Feature Normalization

If we want to remove scaling due to units, we use the z-score. **Z-score** from $x$ to $z$ is computed by:
1. Subtracting the mean,
2. Dividing by the training $\sigma$.  
Then, the $L_2$ distance becomes *unit-invariant*. Afterwards, $\mu=0$ (unbiased) and $\sigma=1$ (uniformly-scaled, or unitless). 

**Whitening** is the process of:
1. Subtracting the training mean,
2. Multiplying by $\frac{1}{\sqrt{\Sigma}}$.  
This results in an unbiased ($\mu=0$), uniformly scaled ($\sigma=1$), and uncorrelated ($\Sigma=0$, or zero $\Sigma$ between variables). Overall, it can be represented with $z=\Sigma^{-\frac{1}{2}}(x-\mu)$. We call it whitening because the process makes data look like it was sampled from white noise, or "isotrophic" Gaussian. 

$L_i$ normalization are examples of dataset *independent* normalization. These normalize the magnitude of feature vectors. Z-score and whitening are examples of dataset *dependent* normalization. These have the goal of removing feature correlation and removing scale difference. 

When we use split [[05_machine_learning#Data|test and train data]], we have to be sure that $\mu$ and $\Sigma$ both come from the training set. 

## Dimensionality

Data is large. It can have thousands to millions of features per sample, and the tendency is to grow as time progresses. It is often sparse, where there is less information than the dimensionality implies. High dimensionality increases the number of parameters and evaluation costs. 

The **curse of dimensionality** states that feature space becomes more sparse for increasing number of dimensions of a fixed-size training set. As the number of dimensions increases in a fixed-size training set, so does the likelihood of sparseness. In a histogram, our bins grow exponentially with dimension increases ($r^D$)!

## Dimensionality Reduction

Given highly-dimensional data $x \in R^D$, we want to find a representation $z \in R^M$ where $M<D$. This will:
- let us visualize data more easily. 
- save in computation and storage costs. 
- removes noise. 
- reduces curse of dimensionality. 

One way we can reduce dimensionality is where we have high correlation. When correlation exists between dimensions, we can eliminate all but one of those variables to reduce costs and redundancy. 

The general idea of dimensionality reduction is to *reduce linearly*. 

**Linear** dimensionality reduction aims to cut down on correlated dimensions, $z=W^Tx$ where $W \in R^{D \times M}$.  
**Nonlinear** dimensionality reduction aims to define a function that maps the original set to a lower dimension set, $z=g(x)$ where $g:R^D \mapsto R^M$. 

### Principal Component Analysis

**Principal component analysis** is conducted through the Karhunen-Loeve transform: $z=W^T(x-\mu)$ where $W \in R^{D \times M}$ and $W^TW=I$. We need to maximize variance from $x$ to $z$ and minimize reconstruction error from $z$ back to $x$. PCA is linear!

Maximizing *variance* helps us keep the most information and minimizing *reconstruction error* minimizes the loss. We must find a $W$ shared by all $x \in X=[x_1,...,x_n]$.

In order to maximize variance, we need to:
1. Calculate covariance matrix $\Sigma$ of the data. 
2. Calculate the eigenvalues and eigenvectors of $\Sigma$. 
3. Find the largest positive eigenvalue of $\Sigma$ and use the corresponding eigenvector as our value.  
If we need more eigenvalues and vectors, we can reuse the computation values and just order by descending size.  
Features are **decorrelated** if there is zero covariance between each other. Our eigenvalue represents the variance in a particular direction, eigenvector is is the direction of variance, covariance is how different features are correlated, and M is related to how much variance to keep or throw out. 

We can choose an M via: $\frac{\Sigma^M_{d=1}\lambda_d}{\Sigma^D_{d=1}\lambda_d}\geq \text{Threshold}$ where our threshold is a fraction we decide (most common .90 or .95). 

Minimizing the reconstruction, or projection, error also needs to be considered, but we didn't really focus on that. 

PCA is commonly used for pre-processing and feature extraction in order to remove noise and reduce data dimensionality. It is also used to *de-correlate* data. 

However, PCA sometimes fails. Here is a common example (swiss roll problem):  
![[Swiss Roll.png]]

## Nonlinear Dimensionality Reduction

Sometimes, linear dimensionality reduction fails. This is where nonlinear dimensionality reduction comes in ($z=g(x)$ where $g:R^D \mapsto R^M$). 

**T-distributed stochastic neighbor embedding** (t-SNE). Builds a pairwise joint probability to characterize every set of instances. It preserves the probability of something being this far from something else. 