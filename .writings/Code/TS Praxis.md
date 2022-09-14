1. Deep Value (subproperty) #deepvalue
```typescript

/**
 * Extract a subproperty and make sure the returned value is acurately typed.
 * 
 * @remarks
 * We can have multiple generic rely on each other.
 * Generics can be inferred from usage ?!
 * 
 */

function get_deep_value<
		Obj,
		Prop extends keyof Obj,
		Subprop extends keyof Obj[Prop]
	> ( 
		obj: Obj, 
		prop: Prop, 
		subprop: Subprop
	) {
	
	return arg[prop][subprop]
	
}

```
---
2. A table to rule them all.
```typescript

/**
 * 
 */
interface TableProps<Item>{
	items: Array<Item>,
	renderItem(item: Item) => unknown
}

function Table<Item,>(props: TableProps<Item>){
	return null
}

```
---
3. Classes as types
```typescript
/**
 * Close enough but not yet there!
 *
 */
type Class<T extends abstract new (...args: any) => any> =
  |(new (...args: ConstructorParameters<T>)=> T)
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
