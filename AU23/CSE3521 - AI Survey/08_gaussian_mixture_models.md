## Mixture Model

A **mixture model** (specifically Gaussian) is a model where the data is a mixture of values from different sources. It is one of the simplest examples of a generative model.

While we normally are able to recover original source Gaussians, we can only sometimes recover original sources for our datapoints.

Original source Gaussians can be recovered with [[07_probabilistic_graphical_models#Maximum Likelihood Estimation|MLE]]. However, applying MLE will leave you with no closed-form solution. This is where we will apply parameter estimation by splitting hidden and visible variables separately. We have two things to work through in doing so:

- Expectation, what are the possible values for hidden variables and how likely do we think they are?
- Maximization, where we try to maximize the likelihood of our visible variables using data from expectations.  
  This is the **expectation-maximization** (EM) algorithm.

## Expectation-Maximization

The expectation-maximization algorithm is an _iterative-improvement_ algorithm. It takes a set of guesses for parameters and then gives you more likely/better values for those parameters. It has to be repeated many times to get the "best" values, and it may become stuck at local maxima. This is why we run a few times using different starting values.

Given $\Theta^t$ at iteration $t$, $Z$ (hidden variables), and $X$ (visible variables), we calculate $\theta^{t+1}$ as $\text{argmax}_{\hat{\Theta}}\sum_Z{P(Z=z|X,\Theta^t)L((X,Z=z|\hat{\Theta}))}$

First, we need to calculate the **expectation** probabilities of $Z$.

Start by calculating $P_{ci}$ for every data point $x_i$ where $c$ is the source in question. For later use, we denote $N_C=\sum_iP_{ci}$.

Next comes the **maximization** step. We need to calculate $\hat{\pi}_C=\frac{N_C}{\sum_jNj}=\frac{N_C}{N}$.  
Then we need $\hat{\mu}_C=\frac{1}{N_C}\sum_i{P_{ci}x_i}$ and $\hat{\sigma}_C=\sqrt{(\frac{1}{N_C}\sum_i{P_{ci}x_i^2})-\hat{\mu}_C^2}$. These are our weighted mean and standard deviation.

Finally, we can plug in $P_{ci}=\alpha_C(\frac{1}{\sqrt{2\pi}\sigma_c}e^{-\frac{(x_i-\mu_c)^2}{2\sigma_c^2}})\pi_C$ for every $c$,$i$ in our table.

Then, we repeat these steps until we give up or reach a convergence.

## Unsupervised Learning

**Unsupervised learning** places parameter estimation as the goal rather than a means to getting inference. There's no target variable, just parameters.

**Clustering** is a very common example of unsupervised learning, where datapoints are grouped based on similarity. Mixture models are different because they are probabilistic clustering, so no actual decision is made.

Sometimes, we have difficulty determining choices. A solution to not being sure is K-means clustering. **K-means clustering** is an iterative clustering algorithm that picks K random cluster centers, updates cluster assignments, and then updates cluster centers.

**Agglomerative clustering** merges similar instances, then with those new groups, merges the similar ones, and so on until there is only one cluster left. FYI, by "similar", the algorithm just chooses instances to merge by distance to each other. We can define different behaviors, though, like farthest pair, average of all pairs and minimum variance (Ward's method).

By running this clustering until failure, a **dendrogram** is produced, displaying a family of clusters.
