# Code as a Propagation

Much like any thought I’ve had so far. Ideas come in pair and the result is something interesting.

This, is no exception.

Back when I wrote about objects[†] and order[‡], I made a realization. Regulating loops with counters is like using a fraction of their potential.

When you learn to code, you are told to be careful with loops. Yet even though they are the feature we appreciate most in computers, a mis-manipulation can easily stuck your program in an infinite loop. 

With practice, safe patterns were developed. And to this day, usage of counter is a default goto. These are special “number” variables which we employ to keep track of the loop state. When a certain value is reached, the loop stops.

For most cases, using loops this way is sufficient to solve many problems. Yet, I am bringing to your attention that, this is just one way of doing things. 

Loops are by design capable of running indefinitely. That is both their strength and something we do not accept in its entirety. 

As finite beings we are mostly interested in finite things. The usage of a loop within a computation is useful only if it ends. 

We are interested in finite propagations. A process by which we move from a state to another by repeating the same transformation on the same object.

Finite propagations must have finite ends — a clear starting point and at least a condition which defines the final state. The process can either be determined or random.

There is no better illustration to these ideas than, walking. 

In redoing the same action that is, stepping, each step produces a small translation which when compounded takes us from point A to point B — from one spatial state to another.

Now we can either have a determined route to follow or just wonder around until we recognize the place we are seeking.

Describing loops as propagations was the door to my first realization. Loops can be regulated by sophisticated objects instead of simple counters.

I call such objects, propagators.

To be one, an object must have two features, a state and transformation — or mutation — function. The state is data structure with all representative properties. The mutation function must alter the object state to the next viable state.

Counters are a very simple instance of propagators. Their state is an integer type variable while any arithmetic operation on integers which labels steps can serve as a mutation function.

In practice we mostly use, incrementation and decremetation to produce forward and backward propagation respectively.

Solving certain problems employing only counter-type loops can get messy very fast; especially if your propagation scheme is complex. You might find yourself nesting loops and crafting nasty conditions.

Yet, by using propagators you can push the complexity inside the object to keep a clean facade by using just a simple loop. 

The gain is mostly representational. 

An elegant pattern. Easier to debug and adjust by just altering the propagator’s logic; as it is what encodes the loop dynamic.

———

For a while, I thought that using propagators was just something no one would find practically interesting except me. I wasn’t planning on making a case for it.

However, I had a second realization. 

In my head, code split into unit actions. Each was represented by a ring and the rings combines to make a chain. 

The image was sophisticated. It was no simple chain. Some rings were big enough to contain smaller ones, forming complex patterns.

I immediately understood that rings stood for loops. But how can code be viewed as interlocking loops?

I had to invoke an old idea, namely that, code is an object. And so it has, states. Each unit action mutates code closer to its terminal state — where the code has fulfilled its purpose.

Code is the design of decision pathways — an architecture — through which its own object propagates.

Yet, how can rings — loops — enter the picture?

The idea is that, for code to terminate successfully it needs to enact certain state sequences which lead to the right termination.  So if each unit action makes a step along that sequence and factoring in the fact that, an action can fail, then we can loop on each unit until it produces a viable state and then move the next unit.

This is how, I made sense of the chain. An inspiration for a pattern language that is primarily about loops. Its ingredients being, loop instructions, propagators plus the break and continue statements.

A ring within an execution process is a loop regulated by a propagator. The continue statements will skip the execution to the next loop state while, break terminates the loop redirecting the flow to the next ring.

The kind of code you make out of this type of patterns is one which will continue to run until it fulfills its purpose. At each ring failure, it will reset the state and mutate again.

Dynamic informational ecosystems — where things can go wrong for multiple reasons — are the best use case for such design language. 

———

As you can see both realizations were necessary to come up with something interesting both in theory and in practice.

They say that, 
“You need two to make one.”
It is the case for this writing.

## References
†The Design of An Object-based Operating System
‡Propagation of Order and Sorting Algorithms