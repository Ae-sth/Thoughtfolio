>In Type-level TypeScript, code branching is known as **Conditional Types**.


```ts
type TrueOrFalse = A extends B ? true : false;
/*                 -----------   ----   -----
                      ^          /         \
                 condition    branch     branch
                             if true    if false
          
                   \-------------------------/
                                ^
                        Conditional Type
*/
```

>"A extends B" means "**Is A assignable to B?**"

## If Type-Level Function

```ts
type If<A extends boolean, B, C> = A extends true ? B : C;
```

>**Type Constraints** let us make sure that one of our type-level function parameters **will always be assignable to some type.**

### `infer` De-structuring

> It enables us to **declare a type variable** by **destructuring** the type on the left-hand side of `extends`.

```ts
type GetRole<User> =
  User extends { name: string; role: infer Role }
    ? Role //                          ^ new! 🤔
    : never;

type t1 = GetRole<{ name: "Gabriel"; role: "admin" }>;
// => 'admin'
```

>You can only use it in the truthy code branch.

>`infer` can be used inside any kind of type-level data structure, including tuples!

```ts
type Head<tuple> = tuple extends [infer first, ...any] ? first : never;
```

```ts
type Tail<tuple> = tuple extends [any, ...infer rest] ? rest : [];
```

```ts
type FirstAndLast<tuple> = tuple extends [infer first, ...any[], infer last]
  ? [first, last]
  : [];
```


## Function Types

>at the type level, **function types are data structures too**!

>They are essentially wrappers around a Tuple representing the list of arguments bundled with an arbitrary return type

```ts
// this type
type IsEqual = (a: number, b: number) => boolean;
// contains the same type-level information as this one
type IsEqual = {
  inputs: [a: number, b: number];
  output: boolean;
};
```

> For example, we can retrieve the **list of parameters** as a **tuple** using `infer`:

```ts
type Parameters<F> = F extends (...params: infer P) => any ? P : never;

type Fn = (name: string, id: number) => string;

type t1 = Parameters<Fn>; // => [name: string, id: number]
```

> And here is how to retrieve the return type of any function:

```ts
type ReturnType<F> = F extends (...params: any[]) => infer R ? R : never;

type Fn = (name: string, id: number) => string;

type t1 = ReturnType<Fn>; // => string
```

## `infer` with custom generics

>the `infer` keyword can also be used in place of a generic type parameter.

```ts
type MyOwnGeneric<A, B> = { content: A; children: B[] };

type ExtractParams<S> = S extends MyOwnGeneric<infer A, infer B>
  ? [A, B]
  : never;

type t1 = ExtractParams<MyOwnGeneric<number, boolean>>;
// => [number, boolean]
```

## Variable Assignement

>I want to show you one more thing: how to assign a **local variable** in a type-level **expression**!

```ts
type Fn<I> = SuperHeavyComputation<I> extends infer Result
  //                                     ^  🤯  ^ 
  ? [Result, Result, Result]
  : never; // this branch can never be reached
```

>We can use `infer` directly after `extends`. This will have the effect of assigning the result of `SuperHeavyComputation<I>` to a variable. The downside is that we need to declare an "else" code branch even though we know it will never be reached because any type is assignable to `infer Result`.


