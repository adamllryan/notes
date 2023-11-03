Maximum a posteriori: safest choice is most likely
probabilistic inference: graphical models provide a compact way to represent joint distributions
## Var types
Query: x_q INCLUDE BOTH T AND F
Visible: x_v we know these already so consider only value
Hidden: x_h we don't know these, consider summation
### Steps:
1. Convert P(left|right) to P(left,right)/P(right)=alphaP(left,right)
2. Multiply by hidden variables summations
3. Simplify inference by moving summations as far right as possible
4. Convert query variables as vector of <T,F>
5. Break cases
6. Solve
Solutions to skip Hidden variables:
Premarginalize: create new BN with hidden variables preprocessed (exponential cost, but makes inference linear). 
Special algorithm like tree structure to create polynomial time algo. 
Approximate inference: guess