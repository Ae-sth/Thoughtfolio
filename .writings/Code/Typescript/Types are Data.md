>Every programming language is about **transforming data** and Type-level TypeScript makes no exception. The main difference with other programming languages is that our data are **types**! We will write programs that take types as input and output some other types.

*This is something we can agree on.*

## Categories of Type
- **Primitive types**: `number`, `string`, `boolean`, `symbol`, `bigint`, `undefined` and `null`.
```ts
type Primitives =
  | number
  | string
  | boolean
  | symbol
  | bigint
  | undefined
  | null;
```
- **Literal types** are exact types which refer to single possible value—the one specified.
- **Data structures**: *objects*, *records*, *lists* and *tuples*. 
```typescript
type DataStructures =
  | { key1: boolean; key2: number } // objects
  | { [key: string]: number } // records
  | [boolean, number] // tuples
  | number[]; // arrays
```
- Union and Intersection types
```ts
type Union = X | Y; // “either a value of type X or of type Y”

type Intersection = X & Y; // “a value that is simultaneously of type X and Y”
```

## Types as Sets (of possible values)

>An interesting feature of TypeScript is that a value can belong to **more than one type**. For example, the value `2` can be assigned to a variable of type `number`, but also to a variable of type `2`, or even of type `1 | 2 | 3`. This property is called **subtyping**. It means that types can be included in other types, or, in other words, that types can be **subsets** of other types.
 This implies that not only unions, but all types are sets! Types can **contain** other types, **overlap** with each other, or be **mutually exclusive**.

*Sets are the organizing notion in TS. That implies that every feature must flow from the logic of sets. (see below)*

>The concept of **assignability** is omnipresent in TypeScript. Most type errors will tell you that some type isn't assignable to some other type. When you start thinking about types as sets of values, assignability becomes much more intuitive — **_“A is assignable to B”_** just means **_“the set B includes all values within the set A”_**, or **_“A is a subset of B”_**.

## The Top-Type `unknown`

>`unknown` contains each and every type you will ever use in TypeScript.

*It is the set of all sets.*

```ts
A | unknown = unknown
A & unknown = A
```

## The Bottom-Type `never`

>In TypeScript, the empty set is called `never`.

*Any part of code that cannot be reached will be typed never.*

>An interesting property of `never` is that it's a **subtype** of **every other types** — it's at the very **bottom** of our hierarchy of sets. That means you can assign a value of type `never` to any other type.

```ts
A | never = A
A & never = never
```

## The case of `any`

>To be honest, `any` doesn't fit well in our mental model because it doesn't respect the laws of Set Theory. `any` is both the **supertype** **and** the **subtype** of **every other TypeScript type**. `any` is _all over the place_.

![[Pasted image 20221112153508.png]]


>In addition to not making much sense, `any` has the tendency to **spread** in a codebase because as soon as you use it in a type expression, it evaluates to `any`

```ts
A | any = any
A & any = any
```