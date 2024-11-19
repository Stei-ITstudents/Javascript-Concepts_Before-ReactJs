# **Scope**

## In JavaScript refers to the accessibility of variables, functions, and objects in some particular part of your code during runtime. Understanding scope helps in managing the lifecycle of variables and controlling where they can be accessed or modified

### Types of Scope

- **Global Scope**
- **Function Scope**
- **Block Scope**

### Global Scope

When a variable is declared outside any function or block, it is in the **global scope**. Variables in the global scope are accessible from anywhere in the code, but should be used cautiously as they can lead to naming conflicts and unintended behavior.

#### Example

```js
let globalVar = "I'm a global variable";

function checkGlobal() {
  console.log(globalVar); // Accessing global variable
}

checkGlobal(); // Output: I'm a global variable
console.log(globalVar); // Output: I'm a global variable
```

Here, `globalVar` is accessible both inside and outside the function `checkGlobal()`.

### Function Scope

Variables declared within a **function** using `var`, `let`, or `const` are accessible only within that function and its inner functions. This is known as **function scope**. The important distinction is that `var` is function-scoped, while `let` and `const` are block-scoped.

#### Example of Function Scope

```js
function exampleFunction() {
  var functionScoped = "I am scoped to this function";
  let blockScopedLet = "I'm block scoped with let";
  const blockScopedConst = "I'm block scoped with const";

  console.log(functionScoped); // Works fine
  console.log(blockScopedLet); // Works fine
  console.log(blockScopedConst); // Works fine
}

exampleFunction();
console.log(functionScoped); // Error: functionScoped is not defined
console.log(blockScopedLet); // Error: blockScopedLet is not defined
console.log(blockScopedConst); // Error: blockScopedConst is not defined
```

In this case:

- `functionScoped` is available only within the `exampleFunction` because it is declared with `var`, which is function-scoped.
- `blockScopedLet` and `blockScopedConst` are also scoped to the function but behave like block-scoped variables inside code blocks (e.g., loops or conditionals).

### Block Scope

**Block scope** refers to variables that are declared within a specific block of code, such as within an `if`, `for`, or `while` loop. In JavaScript, `let` and `const` are block-scoped, meaning that they are only available within the block of code where they are defined.

#### Example of Block Scope

```js
if (true) {
  let blockScoped = "I am block-scoped with let";
  const anotherBlockScoped = "I am block-scoped with const";
  var functionScopedVar = "I am function-scoped with var";

  console.log(blockScoped); // Works fine
  console.log(anotherBlockScoped); // Works fine
  console.log(functionScopedVar); // Works fine
}

console.log(blockScoped); // Error: blockScoped is not defined
console.log(anotherBlockScoped); // Error: anotherBlockScoped is not defined
console.log(functionScopedVar); // Output: I am function-scoped with var
```

- `blockScoped` and `anotherBlockScoped` are **only accessible within the `if` block**, not outside of it.
- `functionScopedVar`, declared with `var`, is **accessible outside the block** because `var` is not block-scoped but function-scoped.

### Differences in Declaration Keywords

- **`var`**:
  - **Function-scoped**: `var` is scoped to the function in which it is declared. If declared outside any function, it becomes a global variable.
  - **Hoisting**: `var` declarations are hoisted to the top of their scope, but the initialization remains where it is written. So, the variable is accessible (with an `undefined` value) before its actual declaration in the code.

#### Example of `var` hoisting

```js
console.log(myVar); // Output: undefined (due to hoisting)
var myVar = 10;
console.log(myVar); // Output: 10
```

- **`let`** and **`const`**:
  - **Block-scoped**: Both `let` and `const` are scoped to the block in which they are declared. They cannot be accessed outside of that block.
  - **No hoisting (temporal dead zone)**: Unlike `var`, `let` and `const` declarations are hoisted, but they cannot be accessed until the actual line of declaration is reached. This area where the variables are hoisted but not accessible is known as the **temporal dead zone**.

#### Example of `let` and `const`

```js
console.log(myLetVar); // ReferenceError: Cannot access 'myLetVar' before initialization
let myLetVar = 20;
console.log(myLetVar); // Output: 20

console.log(myConstVar); // ReferenceError: Cannot access 'myConstVar' before initialization
const myConstVar = 30;
console.log(myConstVar); // Output: 30
```

### Summary of Scope with `var`, `let`, and `const`

| Scope Type         | `var`                                                        | `let` / `const`                                               |
| ------------------ | ------------------------------------------------------------ | ------------------------------------------------------------- |
| **Global Scope**   | Accessible globally                                          | Accessible globally                                           |
| **Function Scope** | Function-scoped                                              | Function-scoped                                               |
| **Block Scope**    | Not block-scoped (hoisted within function)                   | Block-scoped (hoisted but not accessible until declared)      |
| **Hoisting**       | Hoisted to top of the function, initialized with `undefined` | Hoisted but remains in "temporal dead zone" until initialized |

### Conclusion

Understanding the differences between **global**, **function**, and **block scope** is crucial for managing variables in JavaScript. While `var` is function-scoped and has hoisting behavior, `let` and `const` are block-scoped and behave differently in terms of hoisting. This impacts variable access and helps prevent errors in your code.

[**Back** ⤴️](https://github.com/Stei-ITstudents/Javascript-Concepts_Before-ReactJs/tree/main)
