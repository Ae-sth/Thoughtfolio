# Draft
path - URL like utility for handling system paths

Code routes. Bad routes and good routes. Chart them all if possible.
Idea --- Design for Errors

TS Projects

.env
docs/	output of typedocs
assets/  non-code files
src/

	dist/	 contains the builds
		...
		logs/ contains the logs of the execution


	misc/ 	useful utilities
	core/	main functionalities
	tests/	unit tests to make sure every part of the code is healthy
	types/	declarations for the types specific to our system
	errors/  contains custom errors 
			can add a handler callback for a certain type of error, like let's say a countdown-retry.
	events/  contains custom events

	index.ts

--- Execflow
yarn roll - to test a single utility directly

yarn prep - installs all external dependencies if there are any
yarn reset - uninstalls the above

yarn dev - starts in watch mode

yarn clean - cleans the build destination
yarn build - makes a new build
yarn start - runs eveerything, index.ts
yarn test - runs all test

# Final
- Directory Structure
- Design for Errors
```typescript
interface Component {
	/* List all possible errors the component can run to.*/
	this.#_errors = Array<new CustomError(this)>

	/* Define handling for when the error is thrown. */
	public handleError(): void
	...
}
```
- Execution Flows
- Naming Conventions