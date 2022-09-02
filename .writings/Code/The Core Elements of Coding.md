# The Core Elements of Coding

It has been twenty-years since I had my first PC; a gift from my late uncle. I was about five back then. A Windows 95  that came  with a lot of exploration games; a perfect environment for the kid I was.

Until, … I got curious about how to take control of the machine and make my own stuff. Let’s face it, I was too young. 

It annoyed me that I couldn’t alter its behavior. I had to play something that someone already programmed. Luckily or … not, it came with a manual. No need to draw you a picture. I killed that PC. All I could smell was burned nylon from its inside.

By the time I got to middle school, I owned a newer model. But this time I had Internet as a bonus. The biggest exploration space I could ever dream of.

And guess what was the first thing I go looking for? 

How to make programs. I was fortunate enough  to stumble on this website which for  years that came taught me everything from coding to basics of 3D modeling.

Here is the thing. I never stick with something for too long. I try something and then somehow along the process I find the next interesting thing. I move on as I try to integrate everything into a coherent body of knowledge.

That mindset lead me to experiment with a lot of programming languages. My attitude was researcher-like. I wasn’t learning for a particular use; merely for the pleasure of discovery.

That type of experience made me synthesize a pretty generic model about the whole coding activity. In the reminder of this essay, I will layout what I could formalize from the model in question.

———

In every programming language I’ve encountered so far, there are four essential ingredients. These are, Variables, Conditionals, Loops and Functions.

I even argue that any problem-solving you want to perform programmatic-ally can be done using these four elements only. 

Variables are used to store data. They are simply labels used to reference and keep track of a directly-inserted value or some expression that evaluates to a value. All that matters is that the value in question is used to represent data.

In my opinion, values branch into two categories: (1) primitives and (2) composites.

Primitives are elementary values. They are used to express quantities and qualities of things and most often, their literals have no underlying structure. For all our purposes we’ll simply need, numbers, strings and booleans.

Composites are containers which can have for elements, primitives and even other composites. Lists and associations (dictionaries and mappings) are to me all you need in this category. They implement different element-identification schemes, index-based and key-value pair, respectively.

Conditionals and loops, help us alter the execution flow from its top-bottom default and steer it through complex decision trees and iterative tasks. These are pretty standard construction in all languages and being acquainted with if-, switch-, while- and for-statement is sufficient for all uses.

Functions, package a feature that applies a certain transformation to data or manages a certain resource (like a file or the screen) to transmit data through it. 

A function allows us to bundle a set of instructions into a callable block. It is the realization of an IPO (Input-Processing-Output) type of structure which consumes data transform it and then returns the result.

———

What I enumerated so far will help you perform coding in functional-style. Yet if we add one more element, things will get quite interesting.

Beyond the core elements, there is the notion of an Object which do not stand as an addition but more of an encapsulating layer.

Objects are elaborate data structure endowed with functionality. They are used to represent physical and even abstract parts of our problem as encapsulated wholes with coded internal logic.

The object’s logic is supposed to reproduce accurate behavior. And to do so, an object must have a state, accessors, mutators and a constructor.

The state is what holds the properties of the object as-is. The accessors are features that will regulate how we should access the properties of the object without breaking it. Mutators,  when invoked, will take the object from one legitimate state to another. And last, the constructor is what create an instance of the object and contain the code of its execution.

The general procedure is that objects are described through what is more commonly referred to as classes. Then, these descriptions are used to instantiate the object through the constructor. 

There is an obvious difference between a class and its instance. One is description while the other is realization. Yet I will equivocally refer to both as object for the simple reason that, both in conjunction help us recreate objects virtually.

Accessors and mutators are what make up the interface of the object. They enable communication among the various objects modeling our problem; providing a realistic description of how things happen.

One can also define static properties and features that are accessed through the class instead of the instance. Providing a namespace-like experience and applications that can potentially affect every instance of the object in question.

Spending a lot of time thinking in term of these core notion in coding, I converged more than once toward the idea that, code is an object. Abstracting loops and conditionals, code has variables which contain data and functions which operate on it.

 The overlap between object and code is pretty obvious.

Working with code, is like dealing with an exposed object. We define global variables (accessible from anywhere in the code) which as whole make up code’s STATE. 

Moreover we define functions and local variables to encode (and also forward) specific mechanisms and features to use and reuse for STATE MUTATION.

To push the analogy further, running the code is akin to the instantiation of an object. It creates a process; an “instance” of the code in memory.

Furthermore, static properties are analogous to importing some functionalities from another code (or a module). The object acts in this sense as a namespace.

When learning any programming language I encourage anyone to first grasp how these features are presented in the language of interest. To secure a swiss-army-knife type of knowledge.

Technically, one can do well with just Variables-Conditionals-Loops-Functions as a start. However, the leverage offered by the usage of Objects in designing solutions is unparalleled.

If VCLF-O are like words to a language. All I said so far is nothing if one doesn’t think in term of Design Patterns. That is, how to make meaningful phrases.

Design Patterns are solutions pieces that we can reuse to solve recurrent problems. If as a coder you don’t think in term of these well you are still coding amateurishly.

To come up with a pattern you need to be analytical and insightful; capable of deconstructing the problem at hand in a variety of ways. From there, you can group similarities within the same problem which empowers you with factorization ability. Or identify through analogous thinking or direct overlap of two parts belonging to two different problems.

The distilled code that you extract from such process is your pattern.

Keep in mind that not all patterns that you will come up with are good. Bad practices will make your code inefficient and even vulnerable. A case of we call anti-patterns.

Design is no easy feat. It is a creative process where one must integrate both the use and the possibility of misuse. Mistakes are unavoidable.

Ironically, my path to creation started with destruction; a mistake while trying to understand.
———