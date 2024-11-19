# **Error Handling** in JavaScript is a mechanism used to manage and respond to runtime errors that occur during the execution of code. It helps developers anticipate potential issues, catch them when they arise, and handle them gracefully without crashing the application

In JavaScript, error handling is mainly done using **`try`, `catch`, `finally`** blocks, and it is often accompanied by throwing custom errors when needed.

## Key Concepts in Error Handling

### **Try-Catch Block**

The `try` block contains code that may potentially throw an error. If an error occurs, the `catch` block is executed to handle the error. The `catch` block receives the error object, which contains details about the error.

- **Syntax**:

  ```js
  try {
    // Code that may throw an error
  } catch (error) {
    // Code to handle the error
  }
  ```

- **Example**:

  ```js
  try {
    let result = riskyFunction(); // This might throw an error
    console.log(result);
  } catch (error) {
    console.log("Error caught:", error.message);
  }
  ```

  In the above example, if `riskyFunction()` throws an error, the control moves to the `catch` block, and the error message is logged.

### **Throwing Errors**

In JavaScript, you can manually throw an error using the `throw` statement. This is useful for creating custom error messages or conditions that need to be handled by the `catch` block.

- **Syntax**:

  ```js
  throw new Error("Something went wrong");
  ```

- **Example**:

  ```js
  function validateAge(age) {
    if (age < 18) {
      throw new Error("Age must be 18 or older.");
    }
    return "Valid age.";
  }

  try {
    console.log(validateAge(16)); // Throws an error
  } catch (error) {
    console.log(error.message); // Logs: Age must be 18 or older.
  }
  ```

  Here, the `throw` statement is used to manually throw an error if the age is less than 18, and the `catch` block handles the error.

### **Finally Block**

The `finally` block is executed regardless of whether an error occurs or not. It is typically used for cleanup operations, like closing files, releasing resources, or restoring states.

- **Syntax**:

  ```js
  try {
    // Code that may throw an error
  } catch (error) {
    // Error handling code
  } finally {
    // Code that will always execute, regardless of an error
  }
  ```

- **Example**:

  ```js
  try {
    let result = riskyFunction(); // This might throw an error
  } catch (error) {
    console.log("Caught error:", error.message);
  } finally {
    console.log("This always runs, regardless of error.");
  }
  ```

  In this case, no matter what happens in the `try` or `catch` blocks, the `finally` block will always run.

### **Custom Errors**

JavaScript allows you to create custom error types by extending the built-in `Error` object. This can be helpful for more specific error handling.

- **Syntax**:

  ```js
  class CustomError extends Error {
    constructor(message) {
      super(message); // Call the parent class constructor
      this.name = "CustomError"; // Set the error name
    }
  }
  ```

- **Example**:

  ```js
  class ValidationError extends Error {
    constructor(message) {
      super(message);
      this.name = "ValidationError";
    }
  }

  function validateInput(input) {
    if (input < 0) {
      throw new ValidationError("Input must be a positive number.");
    }
  }

  try {
    validateInput(-5);
  } catch (error) {
    if (error instanceof ValidationError) {
      console.log("Validation error:", error.message);
    } else {
      console.log("Unknown error:", error.message);
    }
  }
  ```

  Here, we create a `ValidationError` class that extends `Error`, and we use `instanceof` to catch specific errors.

### Common Built-in Error Types

JavaScript has several built-in error types that can be used for specific error handling scenarios:

- **`Error`**: The generic error object used when no other specific error type is needed.
- **`TypeError`**: Occurs when a value is not of the expected type (e.g., trying to call a method on a non-object).
- **`ReferenceError`**: Raised when trying to access a variable that doesn't exist.
- **`SyntaxError`**: Happens when the JavaScript engine encounters an error in the syntax of the code.
- **`RangeError`**: Thrown when a value is out of range (e.g., array index is out of bounds).
- **`URIError`**: Occurs when there is an invalid URI (Uniform Resource Identifier) manipulation.
- **`EvalError`**: Thrown when there's an error in the use of `eval()`.

### Example of Handling Different Error Types

```js
function testFunction(x) {
  if (typeof x !== "number") {
    throw new TypeError("The argument must be a number");
  }
  if (x < 0) {
    throw new RangeError("Number must be positive");
  }
  return x * 2;
}

try {
  console.log(testFunction("string")); // Throws TypeError
} catch (error) {
  if (error instanceof TypeError) {
    console.log("TypeError caught:", error.message);
  } else if (error instanceof RangeError) {
    console.log("RangeError caught:", error.message);
  } else {
    console.log("Unknown error:", error.message);
  }
}
```

### Summary of Error Handling in JavaScript

- **`try-catch` blocks** are used to catch runtime errors and handle them.
- **`throw`** is used to manually trigger errors.
- **`finally`** ensures code runs after the `try` and `catch`, even if an error occurs.
- You can create **custom error types** for more specific error handling.
- JavaScript has several **built-in error types** like `TypeError`, `ReferenceError`, etc.

By using error handling, you can make your code more robust, user-friendly, and easier to debug, ensuring that it behaves gracefully even when unexpected issues arise.

[**Back** ⤴️](https://github.com/Stei-ITstudents/Javascript-Concepts_Before-ReactJs/tree/main#readme)
