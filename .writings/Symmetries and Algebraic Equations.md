Examine the behavior of a function, $f(x_{0}, ..., x_{n})$ with respect to different permutations of its variables.
1. The function may remain unchanged, e.g. $f=x_{0}+...+x_{n} \equiv \sum x_{i}$ (because in this example all variables have the same coefficient and put in a commutative composition thus there is technically no way of distinguishing among the variables to begin with and so no way to tell if a permutation even happened)
2. Or, produce distinct values for each permutation, e.g. $f=\sum^{n} ix_{i}$ which can have $n!$ distinct possible values.

#Lagrange - for an arbitrary function $f$ with $n$ variables, the number of distinct values which can be taken by the function for all possible permutations is always a divisor of, $n!$.

case. $f=x_{1}x_{2}+x_{3}x_{4}$ has only 3 distinct values for all $4!=24$ permutations and 3 is a divisor of 24.

#Lagrange - the existence of functions like the above for $n=3$ and $n=4$ explains the possibility to solve by radicals equations of 3rd and 4th order. 

*Elaboration: does that mean that if function of this kind do not exist at a certain order then it is not solvable at that order?*

#Ruffini - the algebraic solution of the general equation of degree greater than four is impossible. (Why?)

The number of possible values a function with five variables can take, cannot be 3, 4 or 8 (*value arrived at by some elimination process*) which are divisor of $5!=120$. Thus it is impossible to solve the quintic equation.

*Note: On one hand we are speaking of functions with n variable and on the other of equations of n order. How are they related?*

#Cauchy - had to the idea of considering substitution operations of variables (of functions) as objects by themselves. $$\left( \begin{array}{cccc} a_{1} & a_{2} & a_{3} & ... \\ b_{1} & b_{2} & b_{3} & ... \end{array} \right) = \left( \begin{array}{c} A \\ B \end{array} \right)$$
The above is read as the following permutation (viewed as a substitution), $\{a_{1} \rightarrow b_{1}, a_{2} \rightarrow b_{2}, a_{3} \rightarrow b_{3}, ...\}$. It obeys a composition rule, $$\left( \begin{array}{c} A \\ B \end{array} \right) \left( \begin{array}{c} B \\ C \end{array} \right) = \left( \begin{array}{c} A \\ C \end{array} \right)$$

---
*Equivalence classes, section 1.1.2 [[Applications of the Theory of Groups in Mechanics and Physics]]*

To work on consuming this topic. 
Questions,
1. Is it how it sounds? Just a class of similar problems related by transformations in their variables?