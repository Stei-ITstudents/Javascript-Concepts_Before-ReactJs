# **Closures**

## In JavaScript refer to the ability of a function to retain access to its lexical environment, even after the function has finished executing. This means that a function can "remember" the variables and parameters from the scope in which it was created, even if that scope is no longer in the execution stack

In other words, a closure occurs when a function is able to access variables from its outer (enclosing) function, even after the outer function has returned.

### How Closures Work

When you define a function inside another function, the inner function retains access to variables from the outer function, even after the outer function has finished execution.

#### Example

```js
function outerFunction() {
  let outerVariable = "I am from outer scope";

  function innerFunction() {
    console.log(outerVariable); // inner function has access to outer function's variable
  }

  return innerFunction; // Returning the inner function as a closure
}

const closure = outerFunction();
closure(); // Output: I am from outer scope
```

In this example:

1. `outerFunction` defines a variable `outerVariable`.
2. Inside `outerFunction`, there’s an `innerFunction` that tries to access `outerVariable`.
3. `outerFunction` returns the `innerFunction`, but when `outerFunction` completes execution, it should normally be removed from the stack, and its variables should be inaccessible.
4. However, because `innerFunction` is a closure, it retains access to `outerVariable` from its lexical environment, even after `outerFunction` has finished executing.

### Lexical Scope and Closures

The key concept behind closures is **lexical scope**. Lexical scope means that a function’s scope is determined by where the function is defined, not where it is called.

In the example above:

- The lexical environment of `innerFunction` includes `outerVariable` because `innerFunction` is defined inside `outerFunction`.

### Practical Use of Closures

Closures are useful for many common JavaScript patterns, such as:

- **Data encapsulation**: Keeping some data private and only exposing necessary functionality.
- **Function factories**: Creating specialized functions that are customized with specific parameters.

#### Example: Function Factory

```js
function createCounter() {
  let count = 0;
  return {
    increment: function () {
      count++;
      console.log(count);
    },
    decrement: function () {
      count--;
      console.log(count);
    },
    getCount: function () {
      console.log(count);
    },
  };
}

const counter = createCounter();
counter.increment(); // Output: 1
counter.increment(); // Output: 2
counter.decrement(); // Output: 1
counter.getCount(); // Output: 1
```

In this example:

- The `createCounter` function returns an object with methods (`increment`, `decrement`, `getCount`), each of which forms a closure.
- These methods retain access to the `count` variable, even after `createCounter` has completed execution.

### Summary

- A **closure** is a function that retains access to variables from its lexical scope, even after the outer function has finished execution.
- Closures allow for powerful JavaScript patterns like function factories, data privacy, and deferred execution.
- Closures are created when a function is returned or passed around and still has access to variables from its outer function.

[**Back** ⤴️](https://github.com/Stei-ITstudents/Javascript-Concepts_Before-ReactJs/tree/main)
