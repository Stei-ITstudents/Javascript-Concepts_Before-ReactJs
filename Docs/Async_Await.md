# **Async/Await**

## Is a modern JavaScript feature that simplifies working with asynchronous code, making it more readable and easier to manage. It is built on top of Promises and allows you to write asynchronous code in a synchronous style

- **`async`**: When you declare a function as `async`, it always returns a Promise, even if you don't explicitly return one. This allows you to use `await` within the function.
- **`await`**: This keyword can only be used inside an `async` function. It pauses the function's execution until the Promise is resolved or rejected, making it easier to handle asynchronous operations without blocking the main thread.

### How It Works

When you call an `async` function, it returns a Promise. Inside the function, you can use `await` to wait for a Promise to resolve before continuing with the rest of the code. This removes the need for chaining `.then()` or handling errors with `.catch()`.

### Example

```js
async function getData() {
  try {
    const data = await fetch("https://api.example.com/data"); // Wait for the data
    const json = await data.json(); // Wait for the JSON conversion
    console.log(json);
  } catch (error) {
    console.error("Error:", error); // Handle any errors that occur during the fetch or JSON parsing
  }
}

getData();
```

### Explanation

- The `getData` function is marked as `async`, so it will return a Promise.
- Inside `getData`, `await` is used to pause the execution until the `fetch` operation completes. It waits for the response before moving to the next line.
- If any error occurs (e.g., a network error or the API is unreachable), it is caught by the `catch` block.

### Benefits

- **Cleaner syntax**: No need for chaining `.then()` and `.catch()` methods.
- **Error handling**: The `try-catch` block works similarly to synchronous code, making error handling easier and more intuitive.
- **More readable**: Async/Await turns asynchronous operations into more readable code that looks like it's executing synchronously, improving the maintainability of your code.

In short, `async/await` makes it easier to write and manage asynchronous code in JavaScript by reducing complexity and improving clarity.

[**Back** ⤴️](https://github.com/Stei-ITstudents/Javascript-Concepts_Before-ReactJs/tree/main)
