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

---
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
Let $(F,*)$ and $(G, \circ)$ be two groups. A mapping $f: F \rightarrow G$ is called #homomorphism of groups, if $\forall x,y \in F, f(x*y)=f(x) \circ f(y)$. 
- $f$ injective $\rightarrow$ #monomorphism.
- $f$ surjective $\rightarrow$ #epimorphism.

A homomorphism of groups defined as, $f: G \rightarrow G$ is an #endomorphism of the group $G$.

**Theorem I.** $f(e_{F})=e_{G}$, neutral elements are mapped to each other.

**Theorem II.** $\forall x \in F, f(x^{-1})=(f(x))^{-1}$, the image of symmetric is the symmetric of the image.

**Theorem III.** The composition of two homomorphisms of groups is also a homomorphism.

---
A homomorphism of groups, $f: F \rightarrow G$ is called *isomorphism* of groups if there exist a homomorphism of groups, $g: G \rightarrow F$ such that, $g \circ f = 1_{F}$ and $f \circ g = 1_{G}$ are the identity endomorphisms.

> In other words, a one-to-one mapping between the elements of the two groups
$F$ and $G$ $(x \leftrightarrow y, x \in F, Y \in G)$ is called an *isomorphism* of groups if from
any pair of relations $x_{1} \leftrightarrow y_{1}$ and $x_{2} \leftrightarrow y_{2}$, where $x_{1},x_{2} \in F$ and $y_{1},y_{2} \in G$, it results the relation $x_{1}x_{2} \leftrightarrow y_{1}y_{2}$. Actually, isomorphic groups are roughly the same except for the names of their elements. 

**Theorem**. A homomorphism of groups is an isomorphism of groups iff it is bijective.

An isomorphism of groups $f: G \rightarrow G$ is called an **automorphism** of $G$.

---
In a group $G$, an element $g \in G$ is called the conjugate to the element $h \in G$, if $\exists x \in G$ such that $xgx^{1} = h$.

The automorphism, $f_{x}: G \rightarrow G$, defines the conjugate elements. The set of all elements conjugate to a given element form, a *conjugacy class*.

**Facts**.
- The conjugacy class of the neutral element, $e$ is $\{e\}$.
- In the abelian case, $\forall x, xgx^{-1}=gxx^{-1})=g$, thus the conjugacy class of $g$ is $\{g\}$. 
- Every element is conjugate to itself, $ggg^{-1}=g$.
- If $h$ is conjugate to $g$, then $g$ is conjugate to $h$. (Reciprocity)
- If $g$ is conjugate to $h$ and $h$ is conjugate to $i$, then $g$ is conjugate to $i$. (Transitivity)
- If $g$ is conjugate to $h$, then $g^{-1}$ is conjugate to $h^{-1}$.

---
Let $G$ be a group. A subset $H \subset G$, $H =\emptyset$, is called a **subgroup** of $G$ if the internal composition law of $G$ restricted to $H$ is an internal composition law that makes $H$ into a group.

*If a group has subgroups it is as if a symmetry is made of smaller symmetries.*

**Theorem**. A non-empty subset $H$, is a subgroup of $G$ iff, $\forall x, y \in H, xy^{-1} \in H$.

The subsets $G$ and ${e}$ are called improper subgroups and any other subgroup is a proper one.

Let $f: F \rightarrow G$ be a homomorphism of groups then,
1. $f(F)$ is a subgroup of $G$.
2. $H < G \Rightarrow f^{-1}(G)<F$.
	1. In particular, $Ker f=f^{-1}(e)$, called the kernel of, $f$.

---
Let $A$ and $B$ be two sets, not necessarily distinct. A subset $R$ in the *Cartesian* product $A \times B$ is called **binary relation** between the two sets.$$(a,b)\in R \subset A  \times B$$
If $A=B$ then, $(a,b)$ is an ordered pair of elements in $A$ and we say we have defined a relation in A.

*Notation*: $bRa$ mean, $a$ and $b$ are associated by the relation $R$.

If the relation $R$ is,
- reflexive, $\forall a \in A, aRa$.
- symmetric, $\forall a \in A, b \in B, bRa \iff aRb$.
- transitive, $\forall a \in A, b \in B, c \in C,(bRa \wedge cRb) \iff cRa$.
then, $R$ is an *equivalence* relation.

$R$ is *antireflexive* if $\nexists a \in A, aRa$.
$R$ is antisymmetric if, $(aRb \wedge bRa) \Rightarrow a=b$.

#binary #relation

---
Let $M$ be a set. A class $C$ of nonempty subsets of $M$, such that the subsets in $C$ are disjoint, and the union of all subsets in $C$ is $M$, is called a **partition** of $M$.

#partition

---
Let $R$ be a equivalence relation in $M$. The equivalence class of $x$ is, $$C_{x}=\{y|yRx,y \in M\}$$
The equivalence classes of all elements in $M$ form a partition of $M$.

The set of equivalence classes, determined by an equivalence relation $R$ in $M$, is called the **factor set** of $M$ with respect to $R$, denoted $M/R$.

#factorgroup

---
Let $G$ be a group and $H$ a subgroup of $G$. For $y \in G$ the subset, $yH=\{x|x=yh,h \in H\} \subset G$ is called *left coset*. Similarly, we have also the *right coset*. 

The left or right cosets of a subgroup $H$ in $G$ form a partition in $G$.

---
A group $G$ generated by only one of its elements is called, a **cyclic** group.

#cyclicgroup

---
The group of transformation of a set $M$ is the group of all permutations of $M$. It is called the symmetric group denoted by, $S(M)$.

In the case where, $|M|=n$ the symmetric group is denoted by $S_{n}$ and its order is, $n!$.

The symmetric group of any finite set with $n$ elements is isomorphic to, $S_{n}$.

**Theorem.** Any group $G$ (finite or infinite) is isomorphic to a subgroup of the symmetric group, $S(G)$.

*This says that all possible transformations of the set $G$ must contain inside a structure which is similar to the group (under a given law).*

#permutation #group

---
