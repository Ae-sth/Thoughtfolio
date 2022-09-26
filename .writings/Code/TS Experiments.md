```typescript
/**
 * All possible types (sets of values) are part of `any`. Thus, the expression below is valid of any other type.
 */
type NeverExtendsAny = never extends any? true: false // True. Always.

/**
 * The type `unknown` is `any` under the constraint of having to restrict it. The result is valid for any other type that is not `any` nor `never`.
 */
type UnknownExtensNever = unknown extends never? true: false // False. Always.

/**
 * Nothing extends `never` beside `never`.
 */
type NeverExtendsNever = never extends never? true: false // True. Trivial.

/**
 * This case is quite interesting as it says that `never` is part of `any`.
 */
type AnyExtendsNever = any extends never? true: false // Boolean?! It did not choose between true or false. Both are possible.

```