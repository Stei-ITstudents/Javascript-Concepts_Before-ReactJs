# **Asynchronous Programming**

## In JavaScript allows you to execute code without blocking the main execution thread, which is crucial for tasks like handling I/O operations, making HTTP requests, or dealing with timers. It enables your program to stay responsive while waiting for time-consuming tasks to complete

### Key Concepts of Asynchronous Programming

#### Callback Functions

A **callback** is a function passed as an argument to another function. It is executed when the asynchronous task finishes. While useful, callbacks can lead to deeply nested structures known as **callback hell**.

Example:

```js
function fetchData(callback) {
  setTimeout(() => {
    console.log("Data fetched");
    callback();
  }, 2000);
}

fetchData(() => {
  console.log("Callback executed");
});
```

#### Promises

A **promise** is an object that represents the eventual completion or failure of an asynchronous operation. It has three states:

- **Pending**: The operation is still ongoing.
- **Fulfilled**: The operation completed successfully.
- **Rejected**: The operation failed.

A promise can be handled using `.then()` for successful completion and `.catch()` for handling errors.

Example:

```js
const fetchData = new Promise((resolve, reject) => {
  setTimeout(() => {
    const success = true;
    if (success) {
      resolve("Data fetched successfully");
    } else {
      reject("Error occurred");
    }
  }, 2000);
});

fetchData
  .then((message) => console.log(message))
  .catch((error) => console.log(error));
```

#### Async/Await

`async` and `await` are syntactic features that simplify working with promises by making asynchronous code look more like synchronous code.

- **async**: Makes a function return a promise.
- **await**: Pauses the execution of the async function until the promise resolves.

Example:

```js
async function fetchData() {
  try {
    const data = await new Promise((resolve) => {
      setTimeout(() => resolve("Data fetched successfully"), 2000);
    });
    console.log(data);
  } catch (error) {
    console.log("Error:", error);
  }
}

fetchData();
```

In this example, the `await` keyword pauses the function until the promise is resolved. If the promise is rejected, it is caught by the `try-catch` block.

This approach makes asynchronous code easier to read and maintain, especially compared to using nested callbacks.

[**Back** ⤴️](https://github.com/Stei-ITstudents/Javascript-Concepts_Before-ReactJs/tree/main)
