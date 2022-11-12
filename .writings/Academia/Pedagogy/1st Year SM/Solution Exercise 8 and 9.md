# Exercise 8
1.
	(a). $A= \{x \in \mathbb{R}/6x^{2}+x-1=0\} \iff A=\{\frac{-1}{2},\frac{1}{3}\}$ 
	(b). $B=\{n \in \mathbb{Z}/n^{2} \leq 24 \} \iff B = \{-4, -3, -2, -1, 0, 1, 2, 3, 4 \}$
	(c). $C = \{ x \in \mathbb{N}/ x^{3}-4x \leq 2-x \} \iff C=\{0,1,2\}$, 
		which we can obtain by solving, $x^{3}-3x-2=0$. 
			(i) guess the first solution to be $x=2$, 
			(ii) then solve for $\{a,b,c\}$, $x^{3}-3x-2=(x-2)(ax^{2}+bx+c=0$ to find, $\{a=1,b=2,c=1\}$ 
			(iii) and then solve $x^{2}+2x+1=0$ for $x$, which we can do by noticing that, $x^{2}+2x+1=(x+1)^{2}$, 
			(iv) at the end, $x^{3}-3x-2=(x-2)(x+1)^{2}$.
			(v) $x^{3}-3x-2 \leq 0 \Rightarrow (x-2) \leq 0$, leading to, $(x \leq 2 \wedge x \in \mathbb{N}) \iff x={0,1,2}$
	(d). $D = \{ x \in \mathbb{Z}/ x \leq 0 \wedge -4 < x < 10\} \iff D=]-4,0]$
2.
	(a). $E = ]-\infty, 5] \cup ]10, +\infty[ \iff E=\{x \in \mathbb{R}/ x \leq 5 \wedge x > 10\}$
	(b). $F = \{4,5,6,7,...,11\} \iff F = \{x \in \mathbb{N}/ x \geq 4 \wedge x \leq 11 \}$
	(c). $I = ]4, +\infty] \cup \{2\} \iff I = \{ x \in \mathbb{R}/ x > 4 \wedge x=2 \}$
	(d). $J = \{1, \frac{1}{2}, \frac{1}{4}, \frac{1}{8}, ... \} \iff J = \{ x \in \mathbb{R}/ x=\frac{1}{2^{n}} , n \in \mathbb{N}\}$
2.
	(\*). $A=\{ x \in \mathbb{R} / x \leq 5 \vee x > 10 \} \iff A = ]- \infty, 5] \cup ]10, +\infty [$
	(\*\*). $B = \{ x \in \mathbb{R}/ x \leq 5 \wedge -10 < x < 6  \} \iff B = ]-10, 5]$
	(a). $A \cup B = A$, $A \cap B = B$, $C_{\mathbb{R}}A=]5,10]$, $C_{\mathbb{R}}B=]-\infty,-10] \cup ]5, +\infty[$, $A/B=A \cap C_{\mathbb{R}}B =]-\infty, -10] \cup ]10, +\infty[$, $B/A=B \cap C_{\mathbb{R}}A= \emptyset$  
	(b). 
		- $A \subset B$? Is $(\forall x \in A, x \in E) \wedge (\exists x \in E, x \notin F)$ true? We can reason as follows, for A to be included inside B, A needs to be a smaller set than B before anything. Then if that is not the case it safe to say that, $A \nsubseteq B$ .
		- $B \subset A$? Yes.
	(c).
		- $1 \in \mathbb{R}$? Yes.
		- $1 \subset \mathbb{R}$? No.
		- $\{ 1 \} \subset \mathbb{R}$? Yes.
		- $\emptyset \in \mathbb{R}$? No.
		- $\emptyset \subset \mathbb{R}$? Yes.

# Exercise 9
1. $P=(\forall x, y \in \mathbb{R}, xy\sqrt{2}-x-y+\sqrt{2}=\frac{1}{\sqrt{2}} \Rightarrow (x=\frac{\sqrt{2}}{2} \vee y=\frac{\sqrt{2}}{2}))$, we can demonstrate $P$ by direct substitution of either $x$ or $y$ with their value and see that everything simplifies.
2. $Q=(\forall a \in \mathbb{R}^{*}_{+}, \forall b \in \mathbb{R}^{*}_{+}, \sqrt{a+b} < \sqrt{a}+\sqrt{b})$, to demonstrate $Q$ we start from $(\sqrt{a}+\sqrt{b})^{2}=a+b+2\sqrt{a}\sqrt{b} > a + b \Rightarrow \sqrt{a}+\sqrt{b} > \sqrt{a+b}$.
	- Alternative, "par l'absurde", $Neg(Q)=True(!)$ 
	 $$
	 \begin{eqnarray}
		 a + b &\geq& a + b + 2 \sqrt{ab} \nonumber \\
		  2 \sqrt{ab} &\leq& 0(!) \nonumber
	 \end{eqnarray}
	 $$
3. $R=\{ \forall p \in \mathbb{N}, p/3 \notin \mathbb{N} \Rightarrow p^{2}/3 \notin \mathbb{N} \}$, by absurd, $R'=\{ p/3 \notin \mathbb{N} \wedge p^{2}/3 \in \mathbb{N} \}$ and if we assume that it is true for all $p$'s then we can find the counter example by picking $p=5$ for which $R'$ is false and then $R$ is true.
	- Alternative, "disjonction des cas", suppose $p$ is not divisible by 3, $\exists k \in \mathbb{N}, p=3k+1 \wedge p=3k+2$.
		1. $p=3k+1 \Rightarrow p^{2}=(3k+1)^{2}=3k'+1$, this is not divisible by 3.  
		1. $p=3k+2 \Rightarrow p^{2}=(3k+3)^{2}=3k'+1$, this is not divisible by 3.  
1. $S= \{ \forall p \in \mathbb{N}, \exists !n \in \mathbb{N}, p^{2}/16 \notin \mathbb{N} \Rightarrow (p/2)\neq 2n \}$, employing "la contraposé", $(p/2) = 2n \Rightarrow p^{2}/16 \in \mathbb{N}$ should be also true. By developing, $(p/2) = 2n \iff p=4n \iff p^{2}=16n^{2} \iff p^{2}/16=n^{2} \in \mathbb{N}$.
2. $T(n)=(\forall n \in \mathbb{N}, \sum_{k=0}^{n} 3^{k} = \frac{3^{n+1}-1}{2})$, via recurrence, $T(0)=(3^{0}=\frac{3-1}{2})=True$, we assume that  $T(n)= True$ and check $T(n+1)=True?$ for which we have $\sum_{k=0}^{n+1} 3^{k} = \frac{3^{n+2}-1}{2} \iff 3^{n+1}+\sum_{k=0}^{n} 3^{k} = \frac{3^{n+1}-1}{2} + 3^{n+1} = \frac{3^{n+2}-1}{2}$ 
3. $U=\{ \forall n \in \mathbb{N}, (3^{2n+1}+2^{n+2})/7 \in \mathbb{N} \} \iff U=\{ \forall n \in \mathbb{N}, \exists k \in \mathbb{N}, (3^{2n+1}+2^{n+2}) = 7k \}$, by recurrence, $U(0)=\{3^{1}+2^{2}=7 \Rightarrow k=1 \in \mathbb{N} \}$, assume $U(n)=True$, we check $U(n+1)$. We have, 
$$
	\begin{eqnarray}
		3^{2(n+1)+1}+2^{(n+1)+2} &=&9 \times 3^{2n+1}+ 2 \times 2^{n+2}  \nonumber \\
		&=&(7+2) \times 3^{2n+1}+ 2 \times 2^{n+2} \nonumber \\
		&=& 2 \times  (3^{2n+1}+2^{n+2}) + 7 \times 3^{2n+1} \nonumber \\
		&=&2 \times 7k + 7 \times 3^{2n+1} \nonumber \\
		&=&7 \times (2 \times k + 7 \times 3^{2n+1}) \nonumber 
	\end{eqnarray}
$$
which shows that yes, $3^{2(n+1)+1}+2^{(n+1)+2}$ is divisible by $7$  and so $U=True$.         


