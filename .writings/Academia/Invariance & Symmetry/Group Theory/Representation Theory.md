*The theory of group representations is the result of the introduction of calculus and classical algebra as methods of the group theory.*

In general, the objective of the theory of group representations is to **study the homomorphisms of an arbitrary group onto all possible groups of linear operators**.

Let $G$ be a group and $\mathcal{L}$ a complex linear space. Any mapping $T:G \rightarrow G_{\mathcal{L}}$ by which which $\forall g \in G$ corresponds a linear operator $T(g)$ acting on $\mathcal{L}$, such that: 
1. $T(e)=1$, where $1$ is the identity operator on $\mathcal{L}$.
2. $T(g_{1}g_{2})=T(g_{1})T(g_{2}), \forall g_{1},g_{2} \in G$ 
is called a **representation of $G$ in the space $\mathcal{L}$**.

(1. and 2.) $\Rightarrow T(g^{-1})T(g)=T(g^{-1}g)=T(e)=1 \Rightarrow T(g^{-1})=[T(g)]^{-1}$. $G_{\mathcal{L}}$ is the group of linear operators on $\mathcal{L}$ which map $\mathcal{L}$ onto itself in a one-to-one manner.
*How so 'map onto oneself one-to-one'?*

$G \backsimeq G_{\mathcal{L}} \Rightarrow$ the representation is *faithful*.

==A simple group (whose invariant subgroups are only ${e}$ and itself) has only faithful representations.==

The dimension of $\mathcal{L}$ is called the dimension of the representation, so that a group can have finite- or infinite-dimensional representations.

If the representation space is finite dimensional $dim(\mathcal{L})=n$, we may choose a basis $\{e_{i}\}_{i=0}^{n}$ in $\mathcal{L}$ and the operators $T(g)$ maybe expressed in this basis as square nonsingular matrices of order $n$,$$T(g) \rightarrow t(g)= \left[ \begin{array}[ccc] & t_{11} && \cdots && t_{1n} \\ \vdots && \ddots && \vdots \\ t_{n1} && \cdots && t_{nn} \end{array} \right]$$
Matrix elements write as, $$T(g)e_{k}=\sum_{l=1}^{n} t_{lk}e_{l}$$
The conditions for being a representation translate in term of $t(g)$ as,$$\begin{eqnarray} t(e)&=&1 \nonumber \\ t(g_{1}g_{2})&=&t(g_{1})t(g_{2}) \end{eqnarray}$$
where, $$t_{jk}(g_{1}g_{2})=\sum_{l=1}^{n}t_{jl}(g_{1})t_{lk}(g_{2})$$
