# Type-Builings
1. Classes as types
```typescript

/**
 * First, we need to declare the interface of our class. This is what will be used as a class-type.
 * @remarks:
 * You cannot use `type` because of the second step. It will throw duplicate token.
 */
interface ClassType {
	new (args: ArgType): ClassType
	// the rest of the interface ...
}

/**
 * Second, declare the class. This is what will be passed as a value.
 */
class ClassType implements ClassType {
	constructor (args: ArgType) {
		// initialization code
	}

	// the rest of the properties
}

/**
 * Note: If you plan on using class-types in let's say a union-type, you have to make sure their constructors match with the smallest signature.
 */
function case_handling( kindOfObject: ClassTypeA | ClassTypeB /*...*/ ) {
	return new kindOfObject(/* args */) // construction code
}

case_handling(ClassTypeA) // @returns An object of type `ClassTypeA`

```
2. Functions as types
```typescript

```
4. Record utilities
```typescript
/**
 * Utilities to use on Record-types.
 */
namespace RecordUtils {
	/**
	 * Key extraction
	 */
	export type Keys<T> =
		|keyof T

	/**
	* Value extraction
	* @remarks
	* Does not work for enums.
	*/
	export type Values<T> =
		|T[keyof T]

	/**
	 * Key-Value -> Value-Key transformation
	 */
	export type ReverseMap<T extends Record<keyof T, keyof any>> =
		|{
			[P in T[keyof T]]: {
				[K in keyof T]: T[K] extends P ? K : never
			}[keyof T]	
		}
}
```
---
5. Type testing
```typescript
export type Expect<T extends true> = T;

export type Equal<X, Y> = (<T>() => T extends X ? 1 : 2) extends <	
	T,>	() => T extends Y ? 1 : 2
	? true
	: false;
```
---
# Type-Transformation
```typescript
```