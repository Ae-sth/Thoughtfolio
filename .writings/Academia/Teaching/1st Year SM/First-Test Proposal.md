# Exercice (5 points)

1. Soient (𝑃), (𝑄) et (𝑅) trois propositions, donner la négation. 
	a.  $(𝑃) \wedge (non(𝑄) \vee (𝑅))$ 
	b.  $((𝑃) \wedge (𝑄)) ⇒ (𝑅)$
	
2. Soient $a$ et $b$ des réels positifs, en utilisant le raisonnement par l'absurde montrez que,$$\frac{a}{1+b}=\frac{b}{1+a} \Rightarrow a = b$$

3. Montrer que pour tout entier relatif, $m$ et $n$, on a  $$𝐸 ( \frac{𝑚 + 𝑛}{2} ) + 𝐸 ( \frac{𝑛 − 𝑚 + 1}{2} ) = 𝑛$$ 
Indices:
	- On pourra distinguer les cas $𝑚 + 𝑛$ pair et $𝑚 + 𝑛$ impairs (Raisonement par disjonctions de cas).



# Solution
1. 
	a.  $(𝑃) \wedge (non(𝑄) \vee (𝑅)) \rightarrow (non(𝑃) \vee (𝑄)) \wedge non((P) \wedge (𝑅))$ 
	b. $((𝑃) \wedge (𝑄)) ⇒ (𝑅) \rightarrow (𝑃) \wedge (𝑄) \wedge non(R)$ 
	
2. Par l'absurde, $non(\frac{a}{1+b}=\frac{b}{1+a} \Rightarrow a = b) \equiv (\frac{a}{1+b}=\frac{b}{1+a} \Rightarrow a \neq b)$, on reécrit le LHS pour avoir, $\frac{a}{1+b}=\frac{b}{1+a} \iff a(1+a)=b(1+b) \iff a=b$ qui nous méne a une contradiction.
3. Raisonnement par disjonction,
	- case $m+n$ pair du coup, $m+n=2p, p\in \mathbb{Z}$,$$
	\begin{eqnarray}
		𝐸 ( \frac{𝑚 + 𝑛}{2} ) + 𝐸 ( \frac{𝑛 − 𝑚 + 1}{2} ) &=& 𝐸 ( \frac{2p}{2} ) + 𝐸 ( \frac{2p - m − 𝑚 + 1}{2} ) \nonumber \\
		. &=& 𝐸 ( p ) + 𝐸 ( \frac{2p − 2𝑚 + 1}{2} ) \nonumber \\
		.&=& p + 𝐸 ( p-m+\frac{1}{2} ) \nonumber \\
		.&=& 2p-m \nonumber \\
		.&=& n \nonumber 
	\end{eqnarray}
	$$
	- case $m+n$ impair du coup, $m+n=2p+1, p\in \mathbb{Z}$,$$
	\begin{eqnarray}
		𝐸 ( \frac{𝑚 + 𝑛}{2} ) + 𝐸 ( \frac{𝑛 − 𝑚 + 1}{2} ) &=& 𝐸 ( \frac{2p+1}{2} ) + 𝐸 ( \frac{2p +1  - m − 𝑚 + 1}{2} ) \nonumber \\
		. &=& 𝐸 ( p + \frac{1}{2} ) + 𝐸 ( \frac{2p − 2𝑚 + 2}{2} ) \nonumber \\
		.&=& p + 𝐸 ( p-m+1 ) \nonumber \\
		.&=& 2p-m +1 \nonumber \\
		.&=& n \nonumber 
	\end{eqnarray}
	$$
	
