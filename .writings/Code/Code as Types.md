# Code as Types
---

For a while now, I have been using the TS/ES combination to build various projects. 

The mixture of dynamic-typing and type-annotations trully stands as a thing on its own. 

The intent behind type annotations is to compensate for the shortcomings of dynamic typing.

True. I have seen less errors since I started using TS. But I also had some realizations I wouldn't get if I worked with static typing.

The whole type-oriented mindset rests on two ideas, (a) A type is a set of values and (b) Operations require type compatibility.

The a-idea tells you that a type stands for the possible values a variable can take. 

From a dynamic typing perspective you are constraining the value of the variable, since "de base" it can take any.

An alternative reading of this effect spells like, assigning the variable "meaningful freedom".

A meaning derived from the role played by the variable within your solution.

This is an important point.

The design in a purely dynamic-typing context is like using generic components that are capable of more freedom than needed #problem_with_being_generic.

The possiblity of forgetting their solution-assigned role and using them beyond that, presents a real risk of breaking the whole mechanism.

Static-typing allows us to design solutions via specialized components that are tailored for their role.

Choosing dynamic over static is to value design-freedom over performance.

Type-annotations add safety while using generic components by reminding us at conception time of their role and the operations we are allowed to perform on them.

In a sense, type annotations declare the kinematic space (K-space) of a variable. *Trajectory of the variable throughout the code*

Note that, I said declare and not define. Type annotating a variable isn't enough to make sure that we will treat it correctly nor that we will be capable of understanding interactions among types.

We need a rule that determines the allowed dynamics (D-space) in our design.

The b-idea does so by stating that operations - *transfer of information among components* - are only possible if there is **type compatibility**.

That is, if data was a particular substance, it can only be moved between similar containers.

This single rule - *if applied correctly* - ensures that, any component will never be used beyond what it is supposed to be.

The same idea requires the existence of type converters. Mechanisms through which a given input type is processed into an output type that is compatible with a destination variable.

Designing code through types and type conversions is surely a powerful method to algorithmic problem-solving.

Most problems are about casting (input) data that is in a "problematic" format into a desired "solved" format. It is a type conversion question.

Of course, the implementation of this grand conversion involved many underlying conversions that happen in varying orders and involve different parts of our code object.

---

