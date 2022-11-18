> a decorator is simply a way of wrapping one piece of code with another — literally “decorating” it. This is a concept you might well have heard of previously as **functional composition**, or **higher-order functions**.

```js
/* No fancy syntax */

function doAction(){ 
	// some action
}

function loggingWrapper(action){
	return function(){
		// logs pre-call
		action() // call
		// logs post-call

		// could return something
	}
}

const result = loggingWrapper(doAction)

```

>the only types of decorator that are supported are on classes and members of classes.

*More reasons to do OOP.*

>Decorators are actually nothing more than functions that return another function, and that are called with the appropriate details of the item being decorated. These decorator functions are evaluated once when the program first runs, and *the decorated code is replaced with the return value*.

# Property Decorators

Decorators of this type are called with three parameters:

-   `target`, the **class** that the member is on.
-   `name`, the **name of the member** in the class.
-   `descriptor`, **the member descriptor**.

```js
// the @readonly decorator
function readonly(target, name, descriptor) {
  descriptor.writable = false;
  return descriptor;
}


class Example {
  a() {}
  @readonly
  b() {} // we can't write on 'b'
}
```

> We can actually replace the decorated function with different behavior.

```javascript
// the @log decorator
function log(target, name, descriptor) {
// saving the original behavior to call within the new one
  const original = descriptor.value; 

// checking if the property is a method
  if (typeof original === 'function') {
	// passing the new behavior into the descriptor
    descriptor.value = function(...args) {
      console.log(`Arguments: ${args}`);
      try {
		// call the old behavior
        const result = original.apply(this, args);
        console.log(`Result: ${result}`);
        return result;
      } catch (e) {
        console.log(`Error: ${e}`);
        throw e;
      }
    }
  }
	// return the behavior
  return descriptor;
}
```

>Taking it up a notch, we can arrange for our decorator to take some arguments.

```javascript

// the @log decorator with an argument
function log(name) {
  return function decorator(t, n, descriptor) {
    const original = descriptor.value;
    if (typeof original === 'function') {
      descriptor.value = function(...args) {
        console.log(`Arguments for ${name}: ${args}`);
        try {
          const result = original.apply(this, args);
          console.log(`Result from ${name}: ${result}`);
          return result;
        } catch (e) {
          console.log(`Error from ${name}: ${e}`);
          throw e;
        }
      }
    }
    return descriptor;
  };
}


class Example {
  @log('some tag')
  sum(a, b) {
    return a + b;
  }
}

const e = new Example();
e.sum(1, 2);
// Arguments for some tag: 1,2
// Result from some tag: 3
```


# Class Decorators

>Class decorators are applied to the entire class definition all in one go.

>The decorator function is called with a **single parameter** which is the constructor function being decorated.

```javascript
// the class-level @log decorator
function log(target) {
  return (...args) => {
    console.log(args); // just logs the arguments passed to the constructor
    return new target(...args);
  };
}

@log
class Example {
  constructor(name, age) {
  }
}

const e = new Example('Graham', 34);
// [ 'Graham', 34 ]
console.log(e);
// Example {}
```

>Passing parameters into class decorators works exactly the same as for class members.

```javascript
function log(name) {
  return function decorator(target) {
    return (...args) => {
      console.log(`Arguments for ${name}: args`);
      return new target(...args);
    };
  }
}

@log('Demo')
class Example {
  constructor(name, age) {}
}

const e = new Example('Graham', 34);
// Arguments for Demo: args
console.log(e);
// Example {}
```


 #decorator #higher-order #function