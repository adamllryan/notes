## Basics

The sample space (set of all values) is denoted as $\Omega$. For a dice, it would be the set $\{1,2,3,4,5,6\}\in\Omega$.

An **event** $A$ is a subset of $\Omega$: $A\subseteq\Omega$. An event is a possible outcome in a sample space. The probability of an event is denoted as P(A). When we refer to *capital* $A$, this means we are referring to the event. When we refer to *lowercase* $a$, we are referring to the outcome of $a$, where $+a$ means $A=\text{True}$ and $-a$ means $A=\text{False}$.

We can only determine $P(A)$ for discrete, atomic events, like dice. This is because the probability of a continuous value being true is $\frac{1}{\overline{\overline{\mathbb{R}}}}=\frac{1}{\infty}=0$. We can do ranges, though!

Some truths about probabilities that are essential to know are:

- P(+a)+P(-a)=1
- Gaussian Density $\mapsto$ $P(X=x)=\frac{1}{\sqrt{2\pi\sigma^2}}e^{\frac{-(x-\mu)^2}{2\sigma^2}}$ around mean (center) $\mu$.

**Conditional probability** is the probability of something given something else has a truth value. $P(A|B)$ is the probability of $A$ given $B$. Note:

- $P(+a|b)+P(-a|b)=1$, whether $b$ is true or false.
- If $b$ is irrelevant to a in $P(A|B)$, we may be able to simplify the statement to $P(A)$

**Enumeration** is the property where $P(A|B)=\frac{P(A,B)}{P(B)}=\frac{P(A,B)}{P(+a,B)+P(-a,B)}$.

The conditional probability **chain rule** states that $P(A,B,C)=P(A)\cdot P(B,C|A)=P(A)\cdot P(B|C)\cdot P(C|A,B)$. We can also apply the **product rule**, which is $P(A,B)=P(A)\cdot P(B|A)$.

**Independence** is the concept that if $P(A|B)=P(A)$ or $P(B|A)=P(B)$ or $P(A,B)=P(A)\cdot P(B)$, then $A$ and $B$ are not related. They can be separated from each other without becoming incorrect. Similarly, *conditional* independence is when $P(A,B|C)=P(A|C)\cdot P(B|C)$ or $P(A|B,C)=P(A|C)$ or $P(B|A,C)=P(B|C)$.

**Baye's Rule** states that $P(A|B)=\frac{P(A,B)}{P(B)}=\frac{P(B|A)\cdot P(A)}{P(B)}$, and it is useful for assessing diagnostic probability from causal probability. We can use it in its distribution form: $\alpha P(B|A)P(A)$, where $\alpha$ is our normalization factor or denominator.
