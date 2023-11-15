No longer guaranteed to have linear behavior or a single solution. This is our main problem. 

# Local Linear Error
We use a taylor series to estimate our local linear error. After the whole pipeline, results are outputted into a Jacobian Matrix. We can minimize the error by 

# Gauss-Newton Algorithm
1. Get an initial guess for parameters $\hat{\rho}_1$ 
2. for 1 until we want to stop
	1. Find error for current guess $\hat{\rho}_1$ $\Delta y_i=y_i-f(x_i;\hat{\rho}_1)$
	2. Find Jacobian around current guess $J_{ij}=\frac{\partial f(x_i;\hat{\rho}_1)}{\partial p_j}$
	3. Calculate change in guess $\Delta \tilde{\rho}_1=(J^TJ)^{-1}J^T\Delta y$
	4. Make new guess $\hat{\rho}_{t+1}=\hat{\rho}_t+\Delta\tilde{\rho}$
