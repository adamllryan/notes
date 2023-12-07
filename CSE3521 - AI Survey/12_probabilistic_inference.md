How do we determine the probability of a value when we have a Bayesian Network?
# Probabilistic Inference
The first step is to survey what data we have. We are going to have the following categories of data:
- Query variable ($x_q$), what we are asking about. 
- Visible variable ($x_v$), what we know. 
- Hidden variable ($x_h$), what we don't know. 

Once we divide our variables into these categories, we can continue. 

1. Begin with Bayes' Rule:
$P(x_q|x_v, \theta)$ becomes $\alpha P(x_q, x_v|\theta)$. 

Next, we need to marginalize. 
2. For every hidden variable, we need to repeat this process:

$P(x_q|x_v, \theta)=\alpha \sum_{x_h}{P(x_q,x_h,x_v|\theta)}$ . 

Every hidden variable results in an additional summation. 

3. Expand out the joint probability using the Bayes Network. 
4. Using known values, fill out what we can. A query variable should be left without a true or false value because we need to determine both. 
5. Factor out as much as you can to simplify calculations. Any known values on the outside can be absorbed into the $\alpha$. 
6. Begin to evaluate. Summations should just be the sum of the hidden variable when it is true and when it is false. The query variable should be evaluated for true and false, so it becomes a vector. 
7. Once complete, normalize against the true and false vector that you have for $x_q$. 

Notice: this is time-intensive and long! We want to skip as much as we can. One solution is to **premarginalize**, or create a new BN with its hidden variables preprocessed (exponential cost, but makes inference linear). Another solution is to create a special algorithm like tree structure to create a polynomial time algorithm. Finally, we can always approximate a guess. 