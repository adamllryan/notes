>[!NOTE]
> This is incomplete. Lesser priority
# Correlation
**Correlation** (Pearson's correlation coefficient) is the *degree* to which a pair of variables are linearly related. We take a training set and denote $x\in \mathbb{R}^D$, where D is the number of dimensions of each data instance. When we remove correlation from our data, it appears as if we are rotating it. 

We can determine the correlation between two dimensions, $d$ and $d'$, with the following formula: 
$\rho_{d,d'}=\frac{E_x[(x[d]-\mu[d])(x[d']-\mu[d'])]}{\sigma_d\sigma_{d'}}=\frac{\frac{1}{N}\sum^{N}_{n=1}{[(x[d]-\mu[d])(x[d']-\mu[d'])]}}{\sigma_d\sigma_{d'}}$. 
We'll need the mean $\mu$ and standard deviation $\sigma$ for these, which can be found with these:
- $\mu[d]=\frac{1}{N}\sum^N_{n=1}x_n[d]$ or $\mu=\frac{1}{N}\sum^N_{n=1}x_n$
- $\sigma_d=(\frac{1}{N}\sum^N_{n=1}(x_n[d]-\mu[d])^2)^{1/2}$

**Covariance** ($\Sigma$) is linearly related to our correlation, with the only difference being that covariance does not have correlation's denominator $\Sigma=\frac{1}{N}\Sigma^N_{n=1}{[(x_n-\mu)(x_n-\mu)]^T}$. This means while $\sigma \in [-1,1], \Sigma \in [-\infty,\infty]$. 

If we want to remove scaling due to units, we use the z-score. **Z-score** from $x$ to $z$ is computed by:
1. Subtracting the mean,
2. Dividing by the training $\sigma$. 
Then, the $L_2$ distance becomes *unit-invariant*. Afterwards, $\mu=0$ (unbiased) and $\sigma=1$ (uniformly-scaled, or unitless). 

**Whitening** is the process of:
1. Subtracting the training mean,
2. Multiplying by $\frac{1}{\sqrt{\Sigma}}$. 
This results in an unbiased ($\mu=0$), uniformly scaled ($\sigma=1$), and uncorrelated ($\Sigma=0$, or zero $\Sigma$ between variables). Overall, it can be represented with $z=\Sigma^{-\frac{1}{2}}(x-\mu)$. We call it whitening because the process makes data look like it was sampled from white noise, or "isotrophic" Gaussian. 

$L_i$ normalization are examples of dataset *independent* normalization. These normalize the magnitude of feature vectors. Z-score and whitening are examples of dataset *dependent* normalization. These have the goal of removing feature correlation and removing scale difference. 

When we use split [[06_learning_agents_and_data#Test Data|test and train data]], we have to be sure that $\mu$ and $\Sigma$ both come from the training set. 