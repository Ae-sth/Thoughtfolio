# 1. Pick 


```ts
type Pick<T, K extends keyof T> = { [P in K]: T[P]; }
```

#pick #record

# 2. Tuple to Object

```ts
type TupleToObject<T extends readonly (number | string)[]> = { [U in T[number]]: U }

const tupleMix = [1, '2', 3, '4'] as const
TupleToObject<typeof tupleMix> // { 1: 1; '2': '2'; 3: 3; '4': '4' }
```

#transformation #tuple #object

# 3. First Element

```ts
type First<T extends any[]> = T extends [infer First, ...any]? First: never
```

#array #element

# 4. Length

```ts
type Length<T extends readonly any[]> = T["length"]
```

#array #number

# 5. Exclude (from Unions)

```ts
type Exclude<T, U> = T extends U? never: T

Exclude<'a' | 'b' | 'c', 'a'> // 'b' | 'c'
```

