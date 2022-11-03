When using JS/TS code breaks into two levels. **Value-level** code that will run in production and **type-level** code whose utility doesn't extend beyond development.

V-level code is what makes the actual application. It is the distilled product of development.

T-level code helps us throughout the building of our application. Type annotations (TA) inform the type system about our code and make sure that things are used the way they are intended to.

TAs aren't always as easy as marking something as being a `string` or a `number`. Sometimes we need to describe more generic types that we might not know in advance. Yet, we know how they might be related to other types.

For that end, TS comes with type annotation features capable of describing algorithms for the type system to compute types based on given constraints.

> **Type-level TypeScript** is a minimal, purely-functional language.

*Function are the main mean of abstraction.*

In T-level TS, functions are **generic types**. In fact, it has enough features to be almost **Turing** complete--implying that we can solve problems of arbitrary complexity with it.

We make a token generic by appending the `<ArgTypes, ...>` to it. Then inside its description, the arguments and local variables will use these `ArgTypes`, their derivatives and composition. Thus, a structure can entirely be typed this way.

It is interesting to note that in the case of functions, the specification of those `ArgTypes` can done either in `<>` or inferred via arguments if they types are related to the `ArgTypes`. 

Example.
```typescript
function identity<T>(a: T): T{
	return a
}

// hard specification
const stringReturn = identity<string>(text /* must be string */)

// inferred from argument
const anyReturn = identity(value) /* will return the typeof value regardless of its type */
```

*Note: the second usage is even more interesting because it save us the trouble of describing something that can be guessed by the system then made available inside the block.*


