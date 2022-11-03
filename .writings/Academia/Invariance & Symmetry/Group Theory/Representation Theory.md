*The theory of group representations is the result of the introduction of calculus and classical algebra as methods of the group theory.*

In general, the objective of the theory of group representations is to **study the homomorphisms of an arbitrary group onto all possible groups of linear operators**.

Let $G$ be a group and $\mathcal{L}$ a complex linear space. Any mapping $T:G \rightarrow G_{\mathcal{L}}$ by which which $\forall g \in G$ corresponds a linear operator $T(g)$ acting on $\mathcal{L}$, such that: 
1. $T(e)=1$, where $1$ is the identity operator on $\mathcal{L}$.
2. $T(g_{1}g_{2})=T(g_{1})T(g_{2}), \forall g_{1},g_{2} \in G$ 
is called a **representation of $G$ in the space $\mathcal{L}$**.

(1. and 2.) $\Rightarrow T(g^{-1})T(g)=T(g^{-1}g)=T(e)=1 \Rightarrow T(g^{-1})=[T(g)]^{-1}$. $G_{\mathcal{L}}$ is the group of linear operators on $\mathcal{L}$ which map $\mathcal{L}$ onto itself in a one-to-one manner.
*How so 'map onto oneself one-to-one'?*

$G \backsimeq G_{\mathcal{L}} \Rightarrow$ the representation is *faithful*. *If to each element of $G$ corresponds only one element of $G_\mathcal{L}$ and vice versa then the group is represented as accurately as possible. The other case would be where multiple elements would have the same representation and thus non-distinguished, the representation is then not faithful as it lost a distinction made originally by the group.*

*Theorem* - Every group is homomorphic to a group of transformations mapping a set onto itself. *Isn't this a rehash of the every group is a subgroup of the the symmetric group? Mapping onto oneself, isn't that done through permutations.*

==A simple group (whose invariant subgroups are only ${e}$ and itself) has only faithful representations.== *Being a simple group implies that the group is structureless symmetry wise (see [[Subgroup and Cosets]]), how would that be related to the fact of having only faithful representation?*

If $T$ is a representation of $G$ in $\mathcal{L}$, then $\mathcal{L}$ transforms in compliance with this representation. *A group represents symmetry transformations and a representation of these operations implements means to express that symmetry on that space via operators acting on its states.* 

The dimension of $\mathcal{L}$ is called the dimension of the representation, so that a group can have finite- or infinite-dimensional representations.

If the representation space is finite dimensional $dim(\mathcal{L})=n$, we may choose a basis $\{e_{i}\}_{i=0}^{n}$ in $\mathcal{L}$ and the operators $T(g)$ maybe expressed in this basis as square nonsingular matrices of order $n$,$$T(g) \rightarrow t(g)= \left[ \begin{array}[ccc] & t_{11} && \cdots && t_{1n} \\ \vdots && \ddots && \vdots \\ t_{n1} && \cdots && t_{nn} \end{array} \right]$$
Matrix elements write as, $$T(g)e_{k}=\sum_{l=1}^{n} t_{lk}e_{l}$$
The conditions for being a representation translate in term of $t(g)$ as,$$\begin{eqnarray} t(e)&=&1 \nonumber \\ t(g_{1}g_{2})&=&t(g_{1})t(g_{2}) \end{eqnarray}$$
where, $$t_{jk}(g_{1}g_{2})=\sum_{l=1}^{n}t_{jl}(g_{1})t_{lk}(g_{2})$$
In a space complex numbers $\mathbb{C}^{n}$ we associate to each $g \in G$ an operator $T(g)$ of matrix $t(g)$, such that, $T(g): x \rightarrow x'$ where $x=\{x_{1}, x_{2}, ..., x_{n}\}$ and $x'=\{x'_{1}, x'_{2}, ...,x'_{n}\}$ are elements of $\mathbb{C}^{n}$ and $$x'_{i}=\sum_{i=0}^{n}t(g)_{ij}x_{j}$$

---
Let $H$ be a subgroup of $G$ then, $$T|_{H}=\{T(h)|h \in H \subset G\}$$
is called the *restriction* of $T$ to the subgroup $H$.

---
Let $\mathcal{M}$ be a subspace of $\mathcal{L}$. It is **invariant** with respect to $T$, if all $T(g)$'s transform the vectors of $\mathcal{M}$ into themselves. 

The restriction of the representation to the invariant subspace, $T|_{\mathcal{M}}$, constitutes representation of $T$ in $\mathcal{M}$. 

The operators $T(g)$ induce $\widetilde{T}(g)$ in the quotient space $\widetilde{\mathcal{L}}=\mathcal{L}/\mathcal{M}$. *What does this mean?*

A representation of a group is called *irreducible*, if the representation space do not contain any nontrivial invariant subspaces. Otherwise, it is *reducible*.

---
In the same space $\mathcal{L}$ may exist several representations of the same group $G$, but not all of these are essentially different.

There are representation which we may call **equivalent**. Let $T$ and $S$ be two representations on $\mathcal{L}$ if, $$T(g)=A^{-1}S(g)A, g \in G$$
where $A$ is an arbitrary operator on $\mathcal{L}$, then $$T(g_{1})T(g_{2})=A^{-1}S(g_{1})AA^{-1}S(g_{2})A=A^{-1}S(g_{1}g_{2})A=T(g_{1}g_{2})$$
they are **equivalent representations**.

---
Two representation $S$ and $T$ of the group $G$ acting in $\mathcal{L}$ and $\mathcal{M}$ respectively are called equivalent if there exists $A: \mathcal{L} \rightarrow \mathcal{M}$ (*bijectively*) and satisfies, $$AT(g)=S(g)A,\forall g \in G$$
*Note*: $\mathcal{L}=\mathcal{M} \Rightarrow (T(g)=A^{-1}S(g)A \iff AT(g)=S(g)A)$

**Schur's Lemma I.** $A$ is either one-to-one or $A=0$ (the mapping does not exist).

**Schur's Lemma II.** Let $T$ be a finite irreducible representation of group $G$ in the space $\mathcal{L}$. Every operator $B$ acting on $\mathcal{L}$ which commutes with all operators $T(g)$, $g \in G$, has the form $B=\lambda 1$ where $\lambda$ is a scalar. $$ BT(g)=T(g)B, \forall g \in G \Rightarrow B=\lambda 1, \lambda \ is \ scalar.$$



