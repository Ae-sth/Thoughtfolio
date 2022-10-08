![[Pasted image 20220929152343.png]]
Damsel in Distress, Laurence Demaison, 2008 

---
# Propagation of Order and Sorting Algorithms

It was cleverly solved, yet I kept thinking about it. I had more understanding to manifest.

That day, my brother showed me a sorting algorithm he implemented in assembly code. From the outline of his explanation I noticed a possibility for optimization.

I grabbed a pencil and I drew a square, “This is your algorithm and …,” I proceed by halving it across the diagonal hatching one of the resulting triangles, “we can make it this fast”.

![[Pasted image 20220929152534.png]]

Elaborating … 

Computationally, we order a list of values by looping and swapping elements when a condition isn’t satisfied. We repeat that until no swapping is needed.

To make sure that the list is sorted entirely we need at least to redo looping over elements as many times as we have elements. That is why, I drew a square at first.

![[Pasted image 20220929152554.png]]

To me, the grammar of a sorting design pattern is made of loops, conditionals and swap operations. The loop helps propagating the desired order and implementing it when conditionally through swapping.

What was the problem with the first algorithm then?

It was propagating only forward. And, many times.

A list is a unidimensional world where we can propagate along two opposed directions. The optimization I thought of takes advantage of the possibility of moving backward.

By nesting two loops, the first propagating forward and the second retracing its motion backward. We are capable of sorting all the list in one forward advance.

![[Pasted image 20220929152612.png]]

The results were as predicted. This optimization is twice as fast as the original idea. Yet, that wasn’t what interested me most. It was a certain analogical thinking that I couldn’t help but keep entertaining.

---

I once wrote somewhere in my notes,
 “Information is the cast of order on substance.” 
Sorting seems to be a process by which the cast of a certain order is carried away. Even though the substance is virtual — a digital list of numbers, it was made to follow a certain rule.

In our case, the kind of order we implemented is pretty simple; increasing order. The mental effort was directed toward optimization. Naturally the kind of information written on such list isn’t that interesting. 

Think about pictures. Aren’t they stored as some array of RGB-A values? 

Now imagine that the same pixels were scattered chaotically. Can we recover the original image? 

Looks impossible, right? We can try to rearrange and we might end up with a totally different picture. 

What if I tell you that it is theoretically possible to write THE constraint whose propagation through this bi-dimensional virtual substance would restore the image and that regardless of the entropic damage it sustained.

I don’t’ know about feasibility but in-principle we have the grounds to think that it is at least possible. But, how?

Pictures are captured color values of a scene. An assembly of physical substances expressing a natural order on top of which we can superpose layers of human order. 

And yes you get it, the biggest challenge here is how to express the composition of layered order as a rule.

The picture captures the consequence of such acting rule at a specific moment. The order imposed on its pixels is the visible aspect of the order imposed on the underlying substances.

All this to say, meaningful order and interesting information are the byproduct of sophisticated rules.

---

The need to propagate order instead of imposing it instantly reflects the fact that information cannot travel instantly. Also order must start spreading from somewhere within the substance; the source of order.

We usually start sorting from the first element of the list. So I asked myself, what if we want to start from the middle?

It was clear to me that the solution to this variation of the problem cannot be any faster than the basic case. 

I devised an algorithm on paper by drawing the same square and tried to come up with a propagation that would at least be of the same area — computation time — as the forward-backward code while starting from the middle element.

![[Pasted image 20220929152647.png]]

The solution is composed of an outward followed by an inward propagation. The first spreads as it communicates the new information throughout the whole list and the second bounces back from the limits to converge toward the source.

The resulting code is the generic answer to the sorting problem. If we move the source to the beginning we regain the former solution which is just a special case.

Now if we go back to that solution, I’d like to point out an interesting aspect of what I coded. 

The forward propagation is a wave-like movement. It permeates through the substance until it meets some resistance; a sequence of elements that doesn’t meet the required order.

![[Pasted image 20220929152703.png]]

Each time a swap is needed, it is like meeting a resistance which loses energy of the main wave and generate backward wavelets which makes sure to communicate the information about the change that happened.

Question, why swapping adjacent elements only? Can’t we come up with ideas that would use swapping distant elements?

Maybe you can, but I really can’t see how such a solution will manage to be generic, efficient and consistent. It breaks continuity by allowing instant communication between distant parts.

Nature being our greatest inspiration, we know for a fact that all interactions must happen locally — except for the case of quantum entanglement.

All in all, information must follow connected paths. That is the reason we use fields and waves to represent various physical substances and their interactions.

And if we pay close attention, all that happens is merely the byproduct of swapping things around. The dynamic and motion of objects in our universe is done on this basis too. The result of which is reality.

When an object moves from one spot to another it effectively swaps places with next immediate thing until it reaches its destination. It penetrates through the medium by giving off power — halts the loop to swap — which moves things around — backward wavelets — as it thrust through.

---

The amount of analogical overlap between the design pattern of sorting algorithms and the principles behind natural processes is somewhat surprising I have to say.

As for the list we have been playing with, its dynamic didn’t last — depending on its size —  more than hundreds of milliseconds and sometimes less before reaching stasis. The effective end of one possible world-history.

On another note, the dynamic of our universe is still ongoing. Until …
