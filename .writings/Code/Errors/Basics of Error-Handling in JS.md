>During the program execution unexpected, problematic situations may occur. The program should be able to handle these **extraordinary cases** in a proper way. JavaScript uses exceptions for this purpose, which are a *mechanism for handling errors*.  

Normal cases (good flow) are handled through `if ... else` structures while exceptional cases (bad flow) via `throw` inside a `try ... catch` structures.

```js
throw exception // The 'exception' can be a value of any type.
```

> When an exception is thrown, interpreter stops immediately usual program execution and jumps to the *nearest exception handler*. Exceptions handlers are defined by catch clause of try-catch statement.

IMPORTANT: ***If an exception is thrown and no exception handler is found, the exception is treated as an error.***

>The `Error` is the most generic constructor. An Error object has property name that specifies the *type of error* and property name that provides *details about the exception passed to the constructor*.

```js
throw new Error("An unexpected error occurred");
```

We can define our own errors that extend the `Error` interface and do much more sophisticated handling.

```js
try { 
	statement; // it can potentially throw an exception 
	} catch (exc) { 
	statement; // exception handling 
	} finally {
	    // always execute statements here regardless of whether or not an exception occurs
	}
```

>If a statement in the try block throws an exception, normal flow is stopped and there is jump to the catch block. If exception do not occur, the catch block is omitted.


