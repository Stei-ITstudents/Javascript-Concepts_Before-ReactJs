# Understanding `this`

## In JavaScript, `this` is a special keyword that refers to the **context** in which a function is called. Its value is determined by how a function is invoked. Depending on the context, `this` can behave differently, which can sometimes lead to confusion. Let's break down how `this` works in different contexts: **global scope**, **function scope**, **object methods**, and **arrow functions**

---

### `this` in Global Scope

When `this` is used in the global scope (outside of any function or object), it refers to the **global object**. In a browser environment, the global object is `window`, whereas in Node.js, it is `global`.

#### Example in Browser

```js
console.log(this); // In a browser, this will refer to the 'window' object
```

---

### `this` in Function Scope

In **regular functions**, the value of `this` depends on how the function is called. By default, in **non-strict mode**, `this` will refer to the **global object** (i.e., `window` in a browser). However, in **strict mode**, `this` will be `undefined`.

#### Example in non-strict mode

```js
function regularFunction() {
  console.log(this); // 'this' refers to the global object (window in a browser)
}

regularFunction(); // Output: window (in browsers)
```

#### Example in strict mode

```js
"use strict";
function regularFunction() {
  console.log(this); // 'this' is undefined in strict mode
}

regularFunction(); // Output: undefined
```

---

### `this` in Object Methods

When a function is called as a method of an object, `this` refers to the **object** that the method is a property of. In this case, `this` allows you to access properties and methods of the object within the method.

#### Example with Object Method

```js
const person = {
  name: "John",
  greet: function () {
    console.log(this.name); // 'this' refers to the 'person' object
  },
};

person.greet(); // Output: John
```

Here, inside the `greet` method, `this` refers to the `person` object, allowing access to the `name` property.

---

### `this` in Arrow Functions

Arrow functions behave differently when it comes to `this`. They **do not have their own `this`** context. Instead, they inherit `this` from the **lexical context** in which they are defined. This means that the value of `this` in an arrow function is determined by the surrounding (or enclosing) code where the arrow function is defined, not by how the function is called.

#### Example with Arrow Function

```js
const person = {
  name: "John",
  greet: function () {
    setTimeout(() => {
      console.log(this.name); // 'this' refers to the 'person' object, not the timeout
    }, 1000);
  },
};

person.greet(); // Output: John (after 1 second)
```

Here, the arrow function inside `setTimeout` retains the `this` value from the `greet` method's lexical context, which is the `person` object.

---

### Key Differences Summary

| Context             | Value of `this`                                                                   |
| ------------------- | --------------------------------------------------------------------------------- |
| **Global Scope**    | Refers to the global object (`window` in browsers, `global` in Node.js)           |
| **Function Scope**  | Refers to the global object in non-strict mode or `undefined` in strict mode      |
| **Object Methods**  | Refers to the object the method is called on                                      |
| **Arrow Functions** | Inherits `this` from the enclosing lexical context (does not have its own `this`) |

---

### Conclusion

The value of `this` in JavaScript depends on the **context** in which the function is called. In regular functions, `this` can refer to the global object or `undefined` (in strict mode). When calling methods on objects, `this` refers to the object. Arrow functions behave differently by inheriting the `this` value from the surrounding context, making them particularly useful in situations where you need to preserve the value of `this` from an outer scope, such as inside callbacks.

[**Back** ⤴️](https://github.com/Stei-ITstudents/Javascript-Concepts_Before-ReactJs/tree/main#readme)
