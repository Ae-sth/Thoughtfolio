# Introductory Comments
Study of natural phenomenon by means of the methods of group theory.

*Symmetries of the system, understood as #conservation_laws, are mirrored by its differential equations. The symmetries of these equations and their solutions are the formalization of the systems properties. Since there is such direct link between properties or symmetries. I was thinking of substituting the diffeq solving process with the a solution building process. The symmetries tells about the form of the solution.*

*This route start by saying that our solution belongs to a space (of possible solution). Then by imposing symmetry restrictions we are shrinking the space into a smaller class of solutions that has the symmetries we need given the conservation laws of our phenomenon. The final class we get to are solutions that should describe our phenomenon up to the initial conditions of our problem.*

Consider a #phenomenon $F$ modelled by a system of differential equations, $S$. If $S$ has #symmetries then there is exist a group of #transformations of coordinates, $G$ which acts upon the Hilbert space, $\mathcal{H}$ associated with $S$ (space of solutions).

The representations, the invariants and covariants of these groups are *related* directly connected with the properties of $S$ which can be translated as properties (as conservation laws #noether_theorem) of the phenomenon $F$.  

---
At the end of the day, solutions (to diffeqs) are nothing but algebraic relations - equations.

Lagrange's and Galois' conclusions on the importance of symmetries regarding the solvability of equations emphasizes the importance of this historical path to appreciate the topic. (See [[Symmetries and Algebraic Equations]])

---

# Theory
A *Set* is a notion that antecedes that of a *Group*. One can define a group as a set endowed with *structure*. The structure in question is effected through the usage of a ==composition law== among the elements. 

Let $M \neq \emptyset$, any mapping $f:M \times M \longrightarrow M$ is called an **internal composition law**. 

- Associative composition laws, $$\forall x,y,z \in M, f(f(x,y),z)=f(x,f(y,z))$$
- Commutative composition laws, $$\forall x,y \in M, f(x,y)=f(y,x)$$
Let's say we have two composition rules, $f$ and $g$. 
- $f$ is distributive over $g$ if, $$\forall x,y,z \in M, f(x,g(y,z))=g(f(x,y),f(x,z))$$
An element, $e \in M$ is called ==neutral== element for the composition law, $f$, if $$\forall x \in M, f(x,e)=f(e,x)=x$$
Theorem. if an internal composition laws admits a neutral element then this element must be unique.

An element, $x' \in M$ is ==symmetric== to the element $x \in M$ if, $$f(x,x')=f(x',x)=e$$
An element, $a \in M$ is ==regular== (or cancellable) with respect to $f$ such that, $$\forall x,y \in M, (f(a,x)=f(a,y)) \wedge (f(x,a)=f(y,a)) \Rightarrow x=y $$
A mapping, $\phi: N \times M \rightarrow M$ or $\phi: M \times N \rightarrow M$ where $N \neq \emptyset$ and $M \neq \emptyset$ is called an *external* composition law on $M$ with the operators domain $N$.

An **algebraic structure** on $M$ (non-empty) is any structure determined on $M$ by a set of internal and external composition laws (with operators domains, in the case of external laws.). These laws are subject to conditions e.g. associativity or commutativity and are interconnected by relations like distributivity.

A #groupoid $(G, \circ)$ is a non-empty set $G$ endowed with only one internal composition law, $\circ$.

- A #semigroup is a groupoid where $\circ$ is associative.
	- if $\circ$ is #commutative then we add the adjective, abelian.
- A #monoid is a semigroup that admits a neutral element.
- A #group is a monoid where every element is symmetrizable.

In any group, $(G,\circ)$ the relations, $$(x \circ y)^{-1}=y^{-1} \circ x^{-1}$$ $$(x^{-1})^{-1}=x$$
are satisfied, $\forall x,y \in G$. Also, any element of $G$ is regular.

---

A #transformation $T$ of a set $M$ is a one-to-one mapping of the elements of $M$ on themselves. That is, $Tx=y$ is uniquely solvable for $x$, $\forall y$. One might also define the reverse transformation, $T^{-1}$ such that, $$Tx=y \iff x=T^{-1}y$$
Transformations form a group.
- Trivial transformation, existence of neutral element.
- Reverse transformation, existence of the symmetric.
- The combination of two transformations is another transformation, closure and associativity.



---
# Praxis



