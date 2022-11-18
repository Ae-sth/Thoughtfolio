
## Tuple-type

>Tuple types define sets of arrays with a **fixed length**, and each index can contain a value of **a different type**.

```ts
type SomeTuple = [string, number]
```

>Tuples are essentially **lists of types**!They can contain zero, one, or many items, and each one can be a completely different type. Unlike unions, types in a tuple are ordered and can be present more than once.


Tuples are indexed by **number literal types**.

```ts
SomeTuple[1] // -> string
```

We can read several elements using a Union type,

```ts
SomeTuple[1|2] // -> string | number
```

*since `number` is the union of all number literals then using it as index returns all elements as a union.*

```ts
SomeTuple[number] // -> string | number 
```

We can use the spread operator `...` to combine tuples and fill a tuple with the content of another,

```ts
type TupleA = [1, 2]
type TupleB = [3, 4]

type TupleAB = [...TupleA, ...TupleB] // -> [1, 2, 3, 4]
```

>The Tuple syntax allows giving names to indices. Just like with objects, names precede values, and names and values are separated by a colon `:` character.

```ts
type User = [firstName: string, lastName: string];
```

>A lesser-known feature of tuples is their ability to have optional indices! To mark an index as optional, you only need to add a question mark `?` after it.

```ts
type OptTuple = [string, number?];
//                             ^ optional index!
```

## Array-type

>They represent sets of arrays with an **unknown length**.

```ts
type Tags = string[];
```

>Since all values in an `Array` have the same type, arrays don't contain a ton of type-level information — they're just wrappers around a single type.

## Variadic Tuples + Arrays

>Since the introduction of [Variadic Tuples](https://github.com/microsoft/TypeScript/pull/39094), we can use the `...` rest element syntax to mix Arrays and Tuples. This allows us to create types representing arrays **with any number of values**, but with a few **fixed types** at specific indices.

We can use these to model things with certain invariants at given positions like card and serial numbers.

```ts
// number[] that starts with 0
type PhoneNumber = [0, ...number[]];

// string[] that ends with a `!`
type Exclamation = [...string[], "!"];

// non-empty list of strings
type NonEmpty = [string, ...string[]];

// starts and ends with a zero
type Padded = [0, ...number[], 0];
``````ts
// number[] that starts with 0
type PhoneNumber = [0, ...number[]];

// string[] that ends with a `!`
type Exclamation = [...string[], "!"];

// non-empty list of strings
type NonEmpty = [string, ...string[]];

// starts and ends with a zero
type Padded = [0, ...number[], 0];
```


>This is great to **capture** some of the **invariants** of our code that we often don't bother typing properly.

## Tuples as Function Arguments

```ts
type UserTuple = [name: string, age?: number, ...addresses: string[]];
function createUser(...args: UserTuple) {
  const [name, age, ...addresses] = args;
  //     ~~~~  ~~~     ~~~~~~~~~
  //      ^     ^          ^
  //  string   number   string[]
}

// the same as,
function createUser(name: string, age?: number, ...addresses: string[])
```

>Using tuples to type function parameters can be convenient if you want to **share the types of parameters** between several different functions:


```ts
function createUser(...args: UserTuple) {}
function updateUser(user: User, ...args: UserTuple) {}
```

>or if your function has **several signatures**:


```ts
type Name =
  | [first: string, last: string]
  | [first: string, middle: string, last: string];

function createUser(...name: Name) {}
```