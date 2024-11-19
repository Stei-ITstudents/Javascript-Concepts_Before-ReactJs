# Variables: `var`, `const`, and `let`

---

## `const` vs `let`

- `const` behaves similarly to `let`, but the key difference is that `const` is **immutable**. Once declared, its value cannot be changed. All other characteristics of `let` also apply to `const`.

---

## `let` vs `var`

### **Scope Rules** (Scope refers to the context or region in our code where variables are valid)

- `let` has a block scope, meaning it is valid only within the block it is declared in (i.e., inside curly braces `{ }`).
- `var` has a function scope, meaning it is valid throughout the entire function where it is declared, even if it is declared after the reference.

### **Hoisting**

- `let` is only declared when the execution reaches it in the code.
- `var` is hoisted to the top of its scope and initialized with `undefined`, even if it is the last line in the function. If declared in a global context, `var` is attached to the global `window` object (in browsers).

  Example to analyze:

  ```js
  function run() {
    console.log(foo); // undefined
    var foo = "Foo";
    console.log(foo); // Foo
  }

  run();

  function checkHoisting() {
    console.log(foo); // ReferenceError
    let foo = "Foo";
    console.log(foo); // Foo
  }

  checkHoisting();
  ```

### **Creating Properties on the Global Object**

- `let` does not attach the variable as a property of the global `window` object, even when declared globally.
- `var` attaches the variable as a property of the global `window` object.

  Example:

  ```js
  var foo = "Foo"; // globally scoped
  let bar = "Bar"; // globally scoped

  console.log(window.foo); // Foo
  console.log(window.bar); // undefined
  ```

### **Redeclaration**

- `let` cannot be redeclared once declared; it can only have its value changed. (Note: In Chrome's developer console, this rule might not apply after the latest update, but it is still respected in other browsers.)
- `var` can be redeclared.

- **Variables without a Keyword**

  In JavaScript, there are no true global variables like in other languages. Instead, variables are attached as properties to the global object, which is then used as a global context.

  Note: Variables declared without `let`, `const`, or `var` are automatically added as properties to the global object. However, they do not follow hoisting rules. They are not defined as properties until the code execution reaches them.

---

### A Small Exercise

Please analyze the following code. Study the `"use strict"` directive and try to explain what the issue is with the code and the advantages of using `"use strict"`:

```js
"use strict";
function foo() {
  var variable1, variable2;

  variable1 = 5;
  varaible2 = 6; // typo: should be 'variable2'
  return variable1 + variable2;
}

function foo() {
  var variable1, variable2;

  variable1 = 5;
  varaible2 = 6; // typo: should be 'variable2'
  return variable1 + variable2;
}
```

---

### Global Environment in JavaScript

The global environment in JavaScript consists of two parts:

### **Object Environment Record (OER)**

This is essentially a large object (`window` in browsers) where certain properties are attached. This occurs with `var`, `function`, and when no keyword is used to declare a variable.

### **Declarative Environment Record (DER)**

This record is where variables declared using `const`, `let`, `class`, and imports are stored.

To better understand this, here's an example:

Every function has an `Object Environment Record (OER)` and a `Declarative Environment Record (DER)`. Together, these form the local environment of the function.

- In the `OER`, we add properties by declaring variables like this: `this.<propertyName>`.
- In the `DER`, we initialize new variables using `const`, `let`, or `var` (where `var` initializes a variable only in the declarative environment).

```js
function nbcr() {
  this.name = "a name"; // attached to OER
  let another = "another name"; // attached to DER
  return "";
}

nbcr.name; // "nbcr"
nbcr.another; // undefined
```

Similarly, the **global environment** works by following the rules for declarations as described in points 1 and 2 above.

For a more detailed explanation, you can refer to these resources:

- [Global environment records in JavaScript (StackOverflow)](https://stackoverflow.com/questions/44381045/where-does-the-browser-store-global-variables-defined-with-let-or-const#answer-44381701)
- [Declarative environment record explanation (StackOverflow)](https://stackoverflow.com/questions/20139050/what-really-is-a-declarative-environment-record-and-how-does-it-differ-from-an-a#answer-20140626)

[**Back** ⤴️](https://github.com/Stei-ITstudents/Javascript-Concepts_Before-ReactJs/tree/main)
