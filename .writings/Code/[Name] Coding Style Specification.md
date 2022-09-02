# [Name] Coding Style Specification
---
## Directory Structure

The ideal directory structure should be as follow,
```
repository/
	docs/
	assets/
	deps/
	dist/
		logs/
	src/
		tests/
		types/
		errors/
		misc/
		events/
		core/
		components/
		index.xx
```

- `repository` contains the configuration files.
- `docs` target directory for compiled documentation.
- `assets` contains non-code files.
- `deps` contains external code dependencies.
- `dist` target directory for builds.
	- `logs` target directory for runtime logs.
- `src` contains the code base.
	- `tests` unit testing descriptions.
	- `types` custom type definitions and interfaces.
	- `error` custom error definitions.
	- `misc` generic utilities.
	- `events` custom event definitions.
	- `core` code base core.
	- `components` peripheral utilities.
	- `index.xx` main interface of the code.

---
## Execution Flows
- `yarn roll <path/to/file/within/dist>` running a single file.
- `yarn start` performs both buidling and launching.
- `yarn build` builds to dist/.
- `yarn clean` clears the content of dist/.
- `yarn test` run all tests/.
- `yarn check <path/to/test/file>` checks if a component broke by running its tests.
- `yarn dev` starts in watch mode.
---
## Naming Conventions
- *Rule 1 (module)*: __Files__ and __directories__ ought to be named in lowercase with the (.) dot and (-) dash as the allowed special characters. #chaincase
- *Rule 2 (functional)*: **Variables** ought to be named in lowercase #snakecase while **functions** should be in capitalized #snakecase.
	- *Note: the above applies to **static** members in the context of OOP.*
- *Rule 3 (object)*: *Classes* are named in #pascalcase. **Properties** (attributes and methods) should be in #camelcase.
- *Rule 4*: **Constants** are written in uppercase #snakecase.
---
## Coding Heuristics
- Before anything, make a logger `src/misc/logger.xx`.
- Design for errors. Design through types. Design Components.
- Writes the test as soon as you write the component.
---
### Design for Errors

Specify failure modes as part of coding the solution. Extend the `Error` class with the properties and necessary handling that is aware of its components.

```typescript
interface Component {
	/* List all possible errors the component can run to.*/
	this.#_errors = Array<new CustomError(this)>

	/* Define handling for when the error is thrown. */
	public handleError(): void
	...
}
```

### Design through Types

Define "as much as possible" custom types to represent the set of values that are part of the solution description. 

(see [Coding as Typism])

### Design Components

Build components, units with a single responsability equipped with logging and error handling.
