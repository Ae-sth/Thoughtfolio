4. Montrer que pour tout entier relatif, $m$ et $n$, on a  $$𝐸 ( \frac{𝑚 + 𝑛}{2} ) + 𝐸 ( \frac{𝑛 − 𝑚 + 1}{2} ) = 𝑛$$ 
Note: On pourra distinguer les cas $𝑚 + 𝑛$ pair et $𝑚 + 𝑛$ impairs (Raisonement par disjonctions de cas).

4. Raisonnement par disjonction,
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