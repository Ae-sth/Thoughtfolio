>Objects and Records are two of the most common **data structures** we can manipulate in Type-level TypeScript. They will be the bread and butter of our type-level **algorithms**, so understanding how they work is essential.

```ts
type SomeObject = { key1: boolean; key2: number };
type SomeRecord = { [key: string]: number };
```


## Object-Type

>Object types define **sets of JavaScript objects**.

*Objects are sets of types.*

>[...] **objects with more properties are assignable to objects with fewer properties**, but in contexts where **objects are defined inline**, TypeScript has **extra rules** to make sure we don't mistakenly assign props that we couldn't use afterward because our types would forbid us to do so.

To access the type of a property, we can use the square brackets notation. *We can read several keys at once if we pass them as Union type.*

```ts
type User = { name: string; age: number; role: "admin" | "standard" };
type NameOrAge = User["name" | "age"]; // => string | number
```

>The `keyof` keyword lets you retrieve the **union of all keys** in an object type.

```ts
type User = {
  name: string;
  age: number;
  role: "admin" | "standard";
};

type UserValues = User[keyof User]; //  string | number | "admin" | "standard"
```

>Object types can define properties that may or may not be present. The way to set a property as optional is to use the `?:` key modifier.

```ts
type BlogPost = { title: string; tags?: string[] };
//                                   ^ this property is optional!
```

We can use `&` to merge objects and build them modularly.

```ts
type WithName = { name: string };
type WithAge = { age: number };
type WithRole = { role: "admin" | "standard" };

type User = WithName & WithAge & WithRole;
type Organization = WithName & WithAge; // organizations don't have a role
```

>the *intersection of two objects* contains the **union of their keys**.

```ts
type A = { a: string };
type KeyOfA = keyof A; // => 'a'

type B = { b: number };
type KeyOfB = keyof B; // => 'b'

type C = A & B;
type KeyOfC = keyof C; // => 'a' | 'b'
```

>the *union of two objects* contains the **intersection of their keys**.

```ts
type A = { a: string; c: boolean };
type KeyOfA = keyof A; // => 'a' | 'c'

type B = { b: number; c: boolean };
type KeyOfB = keyof B; // => 'b' | 'c'

type C = A | B;
type KeyOfC = keyof C; // => ('a' | 'c') & ('b' | 'c') <=> 'c'
```

## Record-Type

>Just like Object types, Records also represent sets of objects. The difference is that **all keys** of a record must share **the same type**.

```ts
type Record<K, V> = { [key in K]: V };
```

>`in` lets us assign a type of value for every key in the union `K`.

```ts
type InputState = { [key in "valid" | "edited" | "focused"]: boolean };
// <=>
type InputState = { valid: boolean; edited: boolean; focused: boolean };
```