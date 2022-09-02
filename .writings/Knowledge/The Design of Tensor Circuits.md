It is the second Friday of winter holidays. 
Summary of all possible manipulations. Keep providing with an interesting outlook on things.

Possible tensor combinations
- Addition 
	For this operation we need the two tensors to be of the same rank and to possess the same index signature.
	A component-by-component addition is performed.
	The result is a tensor of the same rank and signature whose components are the result of such addition.
- Product 
	In this operation the tensors ranks are combined to yield the resulting tensors rank whose signature is the combination of both tensors combinations.
	The components of the new tensor are products of the first tensors’ components. 
[New component address] = [Old component address 1] [Old component address 2]
	
- Scaling 
	In this operation we combine a zero-rank tensor with any tensor. Every component of the tensor in question is then multiplied by the zero-rank one.
	This looks quite close to the product.
	There is this interesting aspect where we can think of a way to apply scaling only to certain components in which we need to use a tensor a selector.
 [Zero Rank] [Selector] [Tensor]
	Can we even push this further? Like think about a tensor which can act a “sorter”, rearranges the components in some fashion? That tensor would the realization of a sorting algorithm.
- Contraction
	In this operation, tensors combine by contracting indices and so, the rank changes. What is sure is that, regardless of how many contractions happened, the final rank is always lower than the combination of both tensor ranks.
	Such operation conditions the information flow in certain ways between tensors or even within the same tensor.
	

Possible index operations
- Symmetrization
	Make it so that the wirings of two indices with two others doesn’t change the result even when the wiring are crossed.
- Antisymmetrization
	The opposite. When two wirings are crossed the result is inverted (multiply by -1, inversion on the real or complex axis)

Possible operations on values
	Addition or Increment/Decrement
	Scaling or Amplification