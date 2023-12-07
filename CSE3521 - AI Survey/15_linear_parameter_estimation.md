# Curve Fitting

**Curve fitting** is the process of fitting a curve to a set of points. We want to do this in order to discover more relationships and model relationships as a mathematical function. A function is *linear* if it can be written as a sum of terms $f(x,y,...)=ax+by+...+c$. It is [[16_nonlinear_model_parameter_estimation#Nonlinear Parameter Estimation|nonlinear]] if we can't express it in linear terms, such as if it includes the term $axe^{by}$. 

This time, our process will be taking $x,y$ data points and their desired target values then finding $a,b,c$ to get $x,y$ closest to the target values. 

We consider "closest" to target values as having the least error over all data points and targets. We use the following types of total error:
- **Sum of Absolute Error** - $E_1=\sum_i{|z_i-f(x_i,y_i)|}$
- **Maximum Error** - $E_\infty=\text{max}_i|z_i-f(x_i,y_i)|$
- **Sum of Squared Error** - $E_2=\sum_i{[z_i-f(x_i,y_i)]^2}$

We choose SSE because it is the cheapest and easiest to do. 

# Linear Least Squares
**Linear least squares** is to minimize SSE for a linear parameter function. The approximation for this becomes $E=\sum_i|A\rho-b|_i^2$, where $A$ is the matrix comprised of $x,y$ values for every system and $b$ is the 1xN array made of the solution value. Next, we take the partial derivatives to the unknown variables and solve against zero. Plug in data, then we are left with a line passing through our dataset. 

Alternatively, instead of a partial derivative, $\hat{\rho}=(A^TA)^{-1}A^Tb$. So we just need to define A and b correctly, where A and b are our parameter matrix and our solution side, respectively. Remember, this is only an approximate best solution. 

However, in order to use LLS, relationships must be linear. It also become very expensive to calculate inverse matrices for large parameter size models. Outliers can hurt performance, too, by raising squared error. 