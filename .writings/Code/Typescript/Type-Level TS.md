
# Variables
## Global Scope (default)
```typescript
type GlobalTypeAlias = TypeExpression 
```
## Local Scope
```typescript
type TypeAlias = TypeA extends infer GlobalTypeAlias?
	GlobalTypeAlias extends TypeB? TrueReturnType: FalseReturnType
	: never
```
*Note: (1) The usage of `never` in the conditional-type says (and this is my own interpretation) that this alternative should never be taken, unless the predicate evaluate to `never`. (2) The usage of `infer` is only possible with this type of expressions.*

# Functions
```typescript
type GenericType<
		ArgType extends ContraintType = DefaultArgType /*Optional*/,
    > = 
	|TypeExpression /* Uses `ArgType`.*/

```
*Note: (1) Recursion is possible to simulate loops. ==Capped at 999 depth.== (2) Here `extends` is used to ensure type-compatibility.*

# Conditionals
```typescript
type ConditionalType = TypeA extends TypeB ? TrueReturnType: FalseReturnType
```
*Note: The meaning of `extends` in the condition-context is to mean whether `TypeA` can be substituted by `TypeB`; do we have enough interface overlap (in characteristics (=== properties or attributes) and behavior (=== methods and features)).*

# Mappings
```typescript
/**
 * Union types are like the analog of lists in the type-world.
 */
type ItemsType = "One" | "Two" | "Etc"

type IterationType = {
	[ItemType in ItemsType]: `Do something with ${ItemType}`
} [ItemsType]

```
---
# Filtering
```typescript

type Filter<T> = {
    [K in keyof T as T[K] extends CriteriaType ? K : never]: string
}

```
---
# Pattern Matching
```typescript
type StringType = 'foo-bar'
type MatchType = StringType extends `foo-${infer PatternType}` ? PatternType : never // 'bar'

```