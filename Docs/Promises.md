# Promises in JavaScript

## A **Promise** is an object representing the eventual completion or failure of an asynchronous operation. Promises are a way to handle asynchronous operations (like HTTP requests, file reading, etc.) without blocking the execution of other code

A promise has three possible states:

1. **Pending**: The operation is ongoing.
2. **Fulfilled**: The operation was successful.
3. **Rejected**: The operation failed.

You create a promise using the `new Promise()` constructor, which takes an executor function with two parameters: `resolve` (for fulfillment) and `reject` (for rejection).

### Basic Syntax to Create a Promise

```javascript
const myPromise = new Promise((resolve, reject) => {
  // Simulating an asynchronous task (e.g., API call, timeout)
  const success = true; // This could be any condition

  if (success) {
    resolve("Operation was successful!");
  } else {
    reject("Operation failed.");
  }
});
```

### Handling Promises with `.then()` and `.catch()`

Once a promise is created, you handle it using `.then()` for success and `.catch()` for failure.

#### **`.then()`**: Runs when the promise is fulfilled (resolved)

#### **`.catch()`**: Runs when the promise is rejected

### Example with `.then()` and `.catch()`

```javascript
const myPromise = new Promise((resolve, reject) => {
  const success = true;

  if (success) {
    resolve("Operation was successful!");
  } else {
    reject("Operation failed.");
  }
});

myPromise
  .then((result) => {
    console.log(result); // Logs: 'Operation was successful!'
  })
  .catch((error) => {
    console.log(error); // If rejected, logs: 'Operation failed.'
  });
```

### Handling Multiple Promises (Chaining)

You can chain multiple `.then()` calls to handle a sequence of asynchronous operations. Each `.then()` returns a new promise, which allows you to chain multiple steps.

```javascript
const promise = new Promise((resolve, reject) => {
  resolve("First operation done.");
});

promise
  .then((result) => {
    console.log(result); // 'First operation done.'
    return "Second operation done.";
  })
  .then((secondResult) => {
    console.log(secondResult); // 'Second operation done.'
    return "Third operation done.";
  })
  .catch((error) => {
    console.error("Error:", error);
  });
```

### Using `.finally()`

The `.finally()` method allows you to run code after the promise settles (whether fulfilled or rejected), such as cleaning up resources or showing a loading spinner.

```javascript
myPromise
  .then((result) => {
    console.log(result); // Logs: 'Operation was successful!'
  })
  .catch((error) => {
    console.log(error); // If rejected, logs: 'Operation failed.'
  })
  .finally(() => {
    console.log("Promise settled."); // Always runs after .then() or .catch()
  });
```

### Handling Multiple Promises Concurrently with `Promise.all()`

`Promise.all()` takes an array of promises and returns a single promise that resolves when all the promises in the array resolve. If any of the promises reject, `Promise.all()` immediately rejects with the reason of the first rejected promise.

```javascript
const promise1 = Promise.resolve("First");
const promise2 = Promise.resolve("Second");
const promise3 = Promise.resolve("Third");

Promise.all([promise1, promise2, promise3])
  .then((results) => {
    console.log(results); // ['First', 'Second', 'Third']
  })
  .catch((error) => {
    console.log(error);
  });
```

### Handling the First Resolved or Rejected Promise with `Promise.race()`

`Promise.race()` returns a promise that resolves or rejects as soon as the first promise in the array resolves or rejects.

```javascript
const promise1 = new Promise((resolve, reject) => {
  setTimeout(resolve, 500, "First");
});
const promise2 = new Promise((resolve, reject) => {
  setTimeout(resolve, 100, "Second");
});

Promise.race([promise1, promise2])
  .then((result) => {
    console.log(result); // 'Second' (because it resolves first)
  })
  .catch((error) => {
    console.log(error);
  });
```

### Summary

- **Creating a Promise**: `new Promise((resolve, reject) => { /* async code */ })`
- **Handling a Promise**: `.then()` for success, `.catch()` for failure.
- **Chaining Promises**: `.then()` returns a new promise, allowing sequential handling.
- **Finally block**: `.finally()` runs after the promise is settled.
- **Handling multiple promises**: Use `Promise.all()` for all promises to resolve or `Promise.race()` for the first promise to resolve or reject.

[**Back** ⤴️](https://github.com/Stei-ITstudents/Javascript-Concepts_Before-ReactJs/tree/main)
