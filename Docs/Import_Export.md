# Import/Export

## The `import` and `export` syntax is a key part of **ES6 modules**, which help divide code into smaller, reusable, and maintainable pieces. This is essential for large-scale applications, as it allows for better organization, easier debugging, and simpler dependency management

---

### Exporting Code from a Module

To make a function, object, or variable available for use in other files, you must first **export** it.

#### Named Exports

Named exports allow you to export multiple values from a module. When importing them, you need to use the same name.

#### Example

```js
// module.js
export const name = "Alice";
export function greet() {
  console.log("Hello, " + name);
}
```

You can also export in one statement:

```js
// module.js
const name = "Alice";
function greet() {
  console.log("Hello, " + name);
}
export { name, greet };
```

---

### Default Export

A module can only have one **default export**. This is useful when you want to export a single entity, such as a class, function, or object.

#### Example - Function

```js
// module.js
export default function greet() {
  console.log("Hello, World!");
}
```

In the case of a class:

```js
// module.js
export default class Person {
  constructor(name) {
    this.name = name;
  }
  greet() {
    console.log("Hello, " + this.name);
  }
}
```

---

### Importing Code into a Module

To use code from other modules, you can **import** the exported values. There are two main ways to import: **named imports** and **default imports**.

#### Named Imports

When you use named exports, you must import each item by name. The names must match the exported identifiers.

#### Example - Named Imports

```js
// main.js
import { name, greet } from "./module.js";

console.log(name); // Alice
greet(); // Hello, Alice
```

You can also rename the imported names using the `as` keyword:

```js
// main.js
import { name as userName, greet as greetUser } from "./module.js";

console.log(userName); // Alice
greetUser(); // Hello, Alice
```

---

#### Default Import

When importing the default export from a module, you can give it any name.

#### Example - Default Import

```js
// main.js
import greet from "./module.js";

greet(); // Hello, World!
```

You can also rename the default import if desired:

```js
// main.js
import greetFunction from "./module.js";

greetFunction(); // Hello, World!
```

---

### Importing All Exports

If a module has multiple named exports, you can import all of them at once using the `* as` syntax.

#### Example - Importing Everything

```js
// main.js
import * as module from "./module.js";

console.log(module.name); // Alice
module.greet(); // Hello, Alice
```

This syntax imports everything from the module into a single object (`module` in this case), which can be accessed via `module.name` and `module.greet()`.

---

### Mixing Default and Named Imports

You can import both the default export and named exports from the same module.

#### Example - Mixing Imports

```js
// module.js
export default function greet() {
  console.log("Hello, World!");
}
export const name = "Alice";
export const age = 30;

// main.js
import greet, { name, age } from "./module.js";

console.log(name); // Alice
console.log(age); // 30
greet(); // Hello, World!
```

---

### File Extensions and Import Paths

When using ES6 modules, file extensions are important. You should always include the `.js` extension when importing modules, unless you are working in an environment that handles it for you.

```js
// Correct
import { greet } from "./greet.js";

// Incorrect (without file extension)
import { greet } from "./greet";
```

For relative paths, `./` refers to the current directory, and `../` refers to the parent directory. Absolute paths depend on the environment, but typically in a web application, you'd be working with relative paths.

---

### Summary

- **Named exports**: Export multiple items from a module and import them by name.
- **Default export**: Export a single entity (function, class, or object) and import it with any name.
- **Importing**: Use `import` to bring exported code into another file, with support for named, default, and mixed imports.
- **File extensions**: Ensure that you include `.js` in the import path when using ES6 modules.

[**Back** ⤴️](https://github.com/Stei-ITstudents/Javascript-Concepts_Before-ReactJs/tree/main)
