## Agent Design

AI is categorized by: (**human**,**rational**) behavior and (**thinking**,**acting**) results.

**Rational** is to give the correct answer when able.

Performance is success measure, environment is problem setting, actuator is functionality, sensor is knowledge.

**Fully** or **partially observable** refers to knowledge availability.  
**Discrete** or **Continuous** refers to atomic-ness of the problem setting.  
**Episodic** or **Sequential** is if each situation impacts the next.  
**Single** or **multi** agent is number of agents.  
**Dynamic** or **static** is if problem changes with time.  
**Deterministic** or **stochastic** is if states are fully determined by previous state and action, or there is element of randomness.

## Uninformed Search

Removing unnecessary details is key to problem definition.

A search state graph path is contained in every node of a search tree.

A well-defined problem's successor function should list successor states and valid actions for current state.

Uninformed search expands until a solution is found, informed search uses prior knowledge.

Well-defined problem search states should include information needed to detect goals and that will affect the state when an action is performed.

Complete is if a solution is found and optimal is the best solution.

UCS takes small steps, BFS uses a queue and DFS uses a stack.

## Informed Search

An admissible heuristic never overestimates the remaining cost and a consistent heuristic never overestimates the step cost.

A* search sums heuristic and current path cost. We should allow revisits and use a consistent heuristic w/ closed set to avoid revisits with A* search.

## Adversarial Search

Alpha-beta pruning is used with minimax, not a replacement. Alpha is expected to increase, beta should decrease. A utility function evaluates performance, a game ends by a terminal test function.

## Learning Agents

Machine learning is about detecting and using data patterns. Data sets only need an associated label if we are discussing supervised learning.  
Feature extraction only wants features that are informative, aid interpretability, and are easier for machine learning algorithms to process.  
We want our models to generalize data, not memorize data (overfitting).

## Data to Features

Bag of words uses normalization to fix long and short documents being represented differently. Bag of words keeps word frequencies in a vector representation but loses grammar and word order. A histogram is used to represent feature distributions.

## Correlation and Normalization

Z-score guarantees unbiased (mean=0) and uniformly scaled (standard deviation=1) values, and whitening guarantees unbiased, uniformly scaled, and uncorrelated data. Neither guarantees reduced redundancy (non-sparse).  
Training, test, and new data set $\mu,\Sigma$ comes from training set.  
Correlation and covariance are related by a scalar factor. Correlation is the measure of how two variables are linearly related. Removing correlation from a data set can look like you are rotating the data.

## Dimensionality Reduction

The goal of principal component analysis is to transform the feature space into a smaller linear space where variance is maximized and transformational reversal loss is minimized.  
Eigenvalue represents variance in a particular direction, eigenvector is is the direction of variance, covariance is how different features are correlated, and M is related to how much variance to keep or throw out.  
PCA should be unbiased, reduce redundancy/sparseness, be decorrelated.  
PCA reduces redundancy where whitening scales.

## Bayesian Networks

In Bayesian Networks, nodes are random variables, directed edges represent dependency between parent/child, and likelihood of children given parents is shown in the conditional probability table.  
The chain rule of probability is a repeated application of the product rule and allows us to factorize a joint probability into many conditional probabilities.  
Edges in a probabilistic graphical model help us see conditional independence between variables.

## Probability Introduction

Independence is stronger but rarer property than conditional independence. P(A) true and false sums to 1, and P(A) is between 0 and 1.  
A prior probability has no dependencies, a posterior does.

## Probabilistic Inference

See doc for process.

## Probabilistic Parameter Estimation

Primary motivation for maximum likelihood estimation is to maximize likelihood of the data.

## Mixture Models

See doc for process. The EM algorithm Evaluation step evaluates likelihood of a datapoint to come from a component, not which it had to come from. EM is used to minimize hidden variables. Maximization updates the parameter estimations.

## Linear Parameter Estimation

A function is linear if all $a,b,...$ is a coefficient of $x,y,...$. Linear least squares error function has one minima. A model function is used to represent the relationship between various values. Parameter vector rows match up with columns of the A matrix. Error describes the difference between data points and target values. Issues with linear least sqares are expensive costs, limited relationships, and sensitivity to outliers. It uses linear model functions and sum of squared error. $\rho$ vector has a row for every parameter, $b$ vector has a row for every data point, and A matrix has a column for every parameter and a row for each data point. Classification results in a desired integer, clustering results in an integer, curve fitting/actions result in a desired real number.

## Nonlinear Parameter Estimation

### Gauss-Newton

Nonlinear least squares is different from linear least squares because there are multiple possible minima, model functions are nonlinear, and there is no closed-form solution. Results may depend on initial parameter value estimations. The main idea of GN is to approximate non-linear error function with linear error function. Jacobian matrix has a row for each data point and a column for each parameter. Partial derivate for every parameter. Every parameter update leads to a change in $\Delta\tilde{\rho}$,$\Delta y$, and the Jacobian matrix.

### Gradient Descent

Random restart fixes getting stuck in local minima, momentum fixes flat region saddle points. and Adam (dynamic learning rate selection) fixes minima oscillation.  
To get closer to minima, move in the opposite direction of gradient of the error function.  
Learning rate is used to control convergence speed and size of steps we take.

## Perceptrons

A problem is linearly separable if you can draw a line through it. AND,OR, and range functions (x>y etc) are linearly separable, and XOR, $x==y$, and $x>y^2$ are not. Perceptron learning rule will find a boundary if possible, but it may not be the best. SVMs will give you the best boundary. Recurrent networks can have cycles, feed-forward networks don't. Excitatory synapses increase potential and inhibitory decrease. Nodes/neurons in a NN have activation level/function, input and output links, and weights. Back-propagation algorithm is used to find learn weights for multi-layer neural networks. Neural networks are an example of a bottom-up model. Usable activation functions include: sigmoid, sign, step, and ReLU. Networks without a hidden layer can represent linearly separable functions, one layer can model any continuous function, and two can model any discontinuous. All must be sufficiently wide.
