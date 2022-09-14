# Type-Space
## Top and Bottom Types 
TS includes three special types that server interesting roles.
	- `never`, the (bottom) type that corresponds to the "empty-set". A variable with type "never" cannot have any value and thus should not even exist, hence the name.
	- `any`, the (top) type that refers to all possible types. A variable with type "any" has unrestricted freedom and is as unsafe to use as a generic component #problem_with_being_generic.
	- `unknown`, is a "safer" top type which also refers to all possible types but requires restriction before being used.



## Atomic and Molecular Types
- Atomic types: `undefined`, `null`, `boolean`, `number`, `bigint`, `string`, `symbol` and `object` (plus `void` for conversion types).
- Molecular types:
	- Array:
		- List: `T[]`.
		- Tuple: `[valueA, valueB, ...]`.
	- Object:
		- Dictionary: `{[key: string | number]: T}` - *index signature*.
		- Record: `type R = { propA: T, propB: U, ...}`.
	- Union: `T | U | ...`.

## Utility Types
- `Partial<Type>`, constructs a type with all properties of `T` set to optional.
- `Required<Type>`, constructs a type with all properties of `T` set to required.

- `Record<Keys, Type>`, constructs an object type whose property keys are `Keys` and whose property values are `Type`. *This utility can be used to map the properties of a type to another type.*
- `Array<Type>`, constructs an array whose values are `Type`.

- `Pick<Type, Keys>`, constructs a type by picking the set of properties `Keys` (string literal or union of string literals) from `Type`.
- `Omit<Type, Keys>`, constructs a type by picking all properties from `Type` and then removing `Keys` (string literal or union of string literals).

- `Parameters<ConversionType>`, constructs a tuple type from the types used in the parameters of a function type.
- `ReturnType<ConversionType>`, constructs a type consisting of the return type of a function.

- `ConstructorParameters<Type>`, constructs a tuple or array type from the types of a constructor function type. It produces a tuple type with all the parameter types (or the type `never` if `Type` is not a function).
- `InstanceType<Type>`, constructs a type consisting of the instance type of a constructor function in `Type`.

- `Exclude<UnionType, ExcludedMemebers`, constructs a type by excluding from `UnionType` all union members that are assignable to `ExcludedMembers`.
- `Extract<Type, Union>`, constructs a type by extracting from `Type` all union members that are assignable to `Union`. (*Note: should have been better called,`Overlap`.*)

- `NonNullable<Type>`, constructs a type by excluding `null` and `undefined` from `Type`.

## Conditional Types
- `SomeType extends OtherType ? TrueType : FalseType;`

## Generics and Conversions
- Generics, `generic<ArgType> TypeExpressionWith_ArgType_`
- Conversions, `( args: ArgsType) => ReturnType`

## Type guards, assertions and restrictions
- Type Guards
```typescript
if( /*/ guard /*/ ) { /* Do something. */ }

/* Possible guards */

( typeof variable === /*/ ["string" | "number" | "bigint" | "boolean" | "symbol" | "undefined" | "object" | "function"] /*/ )

( variable ) // guards against null and undefined

( variableA /*/ === | !== /*/ variableB ) // narrows to the intersection or difference between typeA and typeB.

( "property" in variable ) // 

( variable instanceof Class ) //
```
- Type Assertions - Custom Type Guards
```typescript
function isType(arg: unknown): arg is Type {

	return (pet as Type).property !== undefined;

}
```

# Special features
## Enums
## Namespaces
```typescript
namespace Context {
	export 
}
```
---
`infer` keyword

---
# References

![[TypeScript Interfaces.png]]

![[TypeScript Classes.png]]

![[TypeScript Control Flow Analysis.png]]

![[TypeScript Types.png]]

---
# Type-Praxis
```typescript

/* Defines a mutable version of a structure */
type Mutable<Type> = {
	-readonly [Property in keyof Type]: Type[Property];
};

/* Make all optional props concrete */
type Concrete<Type> = {
	[Property in keyof Type]-?: Type[Property];
};

```