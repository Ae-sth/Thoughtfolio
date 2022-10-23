*Idea: Unfolding code.*

**Description**: A code whose initial content is not reflective of its end. It gets reveals as the code runs and modifies itself (its binary) through cycles.

Purpose & Keywords: #obfuscation, #encryption, #compression, #transform, #morphism


## Problematic

The described code has two aspects, a *functional* side which represent an actual utility that is being carried away and a *transformational* side which aims at rewriting the functionality of the code. 

Now, given a certain origin state and a desired target state what's the transformation that through a number (to fix) of applications (cycles) will take us from the former state to the latter.

Example: "Hello world!" program $\rightarrow$ A reverse TCP connection.

This type of code doesn't reveal anything about its true intentions by static analysis. It needs to be ran in order to know exactly what it is meant to do.

## Approach

If by code state we refer to the binary loaded in-memory (RAM) of our program then a state ought to contain at any given time of the execution a mixture of functional and transformational code. 

This coupling makes solving the above problematic a non-straightforward task. Although it can be an interesting exercise to pick two different simple states and try to write a morphing code which goes from one to the other.

In hope of finding a generalized approach to this unique type of problem only possible due to the existence of algorithmic structures and the machines that run them, I am thinking of transposing the problematic through conceptual mapping to an equivalent problem (equivalence need to be proven).

Generally, state transformations are viewed as the action of a matrix (transformation) on a vector (state) to yield a new vector. $$ Av=w $$
But in the case where the state (function) and transformation are coupled the above scheme will not work.

Then, I propose matrices to represent the #transfunctional mixture.

Each state (binary snapshot) of the code will be represented as a matrix where the diagonal elements stand for the functional code - *code that will run utility* - and the anti-diagonal elements for the transforming code - *code will modify the function.

And so, the matrix product will represent the successive runs of the code (cycles). $$ (X \circ X^{2})^{n} \iff A \times A = B \rightarrow B \times B = C \rightarrow ...$$
*Open Questions*
- What does running the code translate to here? Multiplication by self. But is that accurate enough?

In this new representation our problem translates as the determination of anti-diagonal elements of the initial state so that after $n$ cycles the initial diagonal transforms into the target diagonal.

**_Example_**. 2x2 $$ X = \left( \begin{array}{cc} i &&  a \\ b && j \end{array} \right) \rightarrow Y = \left( \begin{array}{cc} k && * \\ * && l \end{array} \right) $$

The $*$ means that we do not care about the values in that case. Now given let's say $n=\{0,1,2,...\}$ what are the $a_{12}$ and $a_{21}$ so that we get from $X$-state to the $Y$-state.

- It is clear that for $n=0$ there are no solutions because no run was effected.
- For $n=1$, it wouldn't make sense to have solutions here except if origin state is already the target we are looking for.
- For $n=2$ we get a two second order equations to solve and we have an anti-diagonal solution only when these equations share at least one solution.
- From this point onward we might have to deal with higher order equations.
- It could be that not all mutation are possible.