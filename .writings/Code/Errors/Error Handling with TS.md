*A way to use type checking in your error-handling routine.*

## Approach: "*encode error states into the TypeScript type system*"

Note: *By doing the above we are adopting an approach that doesn't use the `try ...(throw) ... catch` mechanism as it is only a sugar syntax for the `if ... else` decision-structure.*

```ts
// No information in the type that this is an error,
// you would have to inspect the value to check
let firstError: string = "Something terrible occurred";

interface TerribleError {
  code: "TERRIBLE_ERROR";
  message: string;
}
// It is clearly indicated in the type that this is an error,
// the exact value of the variable is less important
let secondError: TerribleError = {
  code: "TERRIBLE_ERROR",
  message: "Something terrible occurred",
};
```

### 1 - Potential errors are indicated in function signatures

```js
function doSomethingRisky(): TerribleError | number {
  // ...
}
```

- The compiler will not allow you to forget to check errors.
- It can be used to standardize error handling.

>When you have a generic type like `Error<E>` where `E` is some wrapped data about the error, you now have a generic way of handling errors throughout your codebase. You may even want to go a step further and wrap the good path in some kind of `Success` type — we often use the pattern of a `Result` type that is defined as something like `type Result<T, E> = Success<T> | Error<E>`.

*The above matches my vision.*

- [ ] *Check* https://github.com/supermacro/neverthrow, and write [[Neverthrow Usage Reference]].
- [ ] https://medium.com/fashioncloud/a-functional-programming-approach-to-error-handling-in-typescript-d9e8c58ab7f

#error #typescript 

