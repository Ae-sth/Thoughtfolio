# Exercice (5 points)

1. Soient (𝑃), (𝑄) et (𝑅) trois propositions, donner la négation. 
	a.  $(𝑃) \wedge (non(𝑄) \vee (𝑅))$ 
	b.  $((𝑃) \wedge (𝑄)) ⇒ (𝑅)$
	
2. Soient $a$ et $b$ des réels positifs, en utilisant le raisonnement par l'absurde montrez que,$$\frac{a}{1+b}=\frac{b}{1+a} \Rightarrow a = b$$
3. En utlisant les identités remarquables et géometrique,
	- developper, $(1-x)^{3}$
	- factoriser, $8-x^{3}$.

*Données*: $$(a+b)^{n}=\sum_{k=0}^{n}C_{n}^{k}a^{n-k}b^{k}$$ $$C_{n}^{k}=\frac{n!}{k!(n-k)!}$$ $$a^{n+1}-b^{n+1}=(a-b)\sum_{k=0}^{n}a^{k}b^{n-k}$$



---

# Solution
1. 
	a.  $(𝑃) \wedge (non(𝑄) \vee (𝑅)) \rightarrow (non(𝑃) \vee (𝑄)) \wedge non((P) \wedge (𝑅))$ 
	b. $((𝑃) \wedge (𝑄)) ⇒ (𝑅) \rightarrow (𝑃) \wedge (𝑄) \wedge non(R)$ 
	
2. Par l'absurde, $non(\frac{a}{1+b}=\frac{b}{1+a} \Rightarrow a = b) \equiv (\frac{a}{1+b}=\frac{b}{1+a} \wedge a \neq b)$, on reécrit le LHS pour avoir, $\frac{a}{1+b}=\frac{b}{1+a} \iff a(1+a)=b(1+b) \iff a=b$ qui nous méne a une contradiction.
3. 
	- Developpment, $$(1-x)^{3}=1+3.(-x)+3.(-x)^{2}+(-x)^{3}=1-3x+3x^{2}-x^{3}$$
	- Factorization, $$8-x^{3}=2^{3}-x^{3}=(2-x)(x^{2}+2x+4)$$
