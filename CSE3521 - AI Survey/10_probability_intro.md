# Probability Basics
Begin with set omega (sample space). an event is a subset of omega. Probability space/model is sample space with probability function P(A) for every event A subset omega. 
0<=P(A)<=1; P(omega)=1;SUM(P(Ai))=P(UiAi)
## Random Variables
Random variable is set of values X=truth provable value. Must be capital letter
## Proposition
MultiD samples defined by values of set of random variables. 

Prior Probability: Unconditional probabilities do not change with evidence. Joint probability for set of variables gives probability of every atomic event. 
Probability for Continuous Variables: The integral =1
Gaussian Density: Kinda a bell curve
Conditional Probability: P(a | b) P(a given b=True)
P(~a|b)+P(a|b)=1, P(a|~b)+P(~a|~b)=1
# Rules
Normalization: P(a|b)=P(a,b)/P(b)
Product Rules: P(a,b)=P(a)P(b|a)
Chain Rules: P(a,b,c)=P(a)P(b,c|a)=P(a)P(b|c)P(c|a,b)
Independent iff P(A|B)=P(A) or P(B|A)=P(B) or P(a,b)=P(a)P(b)
Conditional independence reduces size of representation from e^n to n^x
Bayes' Rule: P(a|b)=P(a.b)/P(b)=P(b|a)P(a)/P(b)
With Conditional Independence: P(a|b,c)=P(b,c|a)P(a)=alphaP(b|a)P(c|a)P(a)


# Basics
An **event** is a possible outcome in a sample space. The probability of an event is denoted as P(A). We can only determine P(A) for discrete, atomic events, like dice. This is because the probability of a continuous value being true is $\frac{1}{\overline{\overline{\mathbb{R}}}}=\frac{1}{\infty}=0$. We can do ranges, though!

