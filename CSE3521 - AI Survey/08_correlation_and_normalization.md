>[!NOTE]
> This is incomplete. Lesser priority
# Correlation
**Correlation** (Pearson's correlation coefficient) is the *degree* to which a pair of variables are linearly related. We take a training set and denote $x\in \mathbb{R}^D$, where D is the number of dimensions of each data instance. 
# Feature Correlation

Mean
STD
## Between dimensions
Correlation between two dimensions (d,d'):
Feature correlation between dimensions
$p_{d,d'}=\frac{E_x[(x[d]-\mu[d])(x[d']-\mu[d'])]}{\sigma_d\sigma_{d'}}=\frac{\frac{1}{N}\sum^{N}_{n=1}{[(x[d]-\mu[d])(x[d']-\mu[d'])]}}{\sigma_d\sigma_{d'}}$
## Correlation vs covariance
Correlation is [-1,1] meanwhile covariance is (-inf,inf)
Covariance is the same formula without the denominator of $\sigma_d\sigma_{d'}$. 
## Properties

Changing units changes distance, STD, and COV. 
### Dataset-dependent normalization

#### Z-score
We can remove scaling from units with z score. Process:
Subtract mean
Divide by standard deviation
$L_2$ distance becomes unit invariant.
After the process, the new training set will have mean=0 and STD=1
# Feature Whitening
Process:
Subtract training mean. 
Multiply by the inverse sqrt(cov)
cov=$\Sigma=\frac{1}{N}\Sigma^N_{n=1}{[(x_n-\mu)(x_n-\mu)]^T}$
This makes
Unbiased: mean=0
Uniformly scaled: std=1
uncorrelated: cov=0 between variables
# Dataset-independent vs. dependent normalization
Examples of independent: L1,L2 normalization. Goal is to normalize the magnitude of feature vectors. We assume feature variables or dimensions are on the same scale with no correlation. 
Examples of dependent: Z-score, whitening. Goal is to remove feature correlation and remove scale difference. 
## Dependent costs
For new inputs, we need to normalize those new inputs too! The mean and standard deviation/covariance must be calculated from the training set. Test set must be normalized by values coming from the training set!

We can represent data as a histogram or using kernel density estimation. 
# Linear Algebra

## Inner product

## Vector projection of x on w

## Matrix trace

# Matrix Decomposition

##  Eigenvectors and eigenvalues

## Eigen-decomposition

## Singular value decomposition

###  SVD + ED

## Square matrix trace

# Correlation

## Feature correlation

## Feature Whitening

# Covariance

## Covariance matrix

## Feature Correlation

Z-score guarantees unbiased (mean=0) and uniformly scaled (standard deviation=1) values, and whitening guarantees unbiased, uniformly scaled, and uncorrelated data. Neither guarantees reduced redundancy (non-sparse). 
Training, test, and new data set $\mu,\Sigma$ comes from training set. 
Correlation and covariance are related by a scalar factor. Correlation is the measure of how two variables are linearly related. Removing correlation from a data set can look like you are rotating the data. 