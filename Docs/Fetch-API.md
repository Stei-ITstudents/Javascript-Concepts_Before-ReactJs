# Fetch API

## The **Fetch API** is a modern web API used to make HTTP requests in JavaScript. It is more powerful and flexible than the older `XMLHttpRequest`, providing a cleaner syntax for handling asynchronous requests

### Key Features

- **Promises**: The Fetch API uses Promises, which means you can use `then()`, `catch()`, or `async/await` for handling the results.
- **Streams**: Fetch supports streaming responses, allowing you to work with large files efficiently.

### Basic Syntax

```js
fetch(url, options)
  .then((response) => response.json()) // Parse the JSON response
  .then((data) => console.log(data)) // Handle the data
  .catch((error) => console.log(error)); // Handle errors
```

### Parameters

- **`url`**: The URL of the resource you want to fetch.
- **`options`** (optional): An object that can include additional settings, such as HTTP method, headers, body, etc.

### Example 1: Simple GET Request

```js
fetch("https://api.example.com/data")
  .then((response) => response.json()) // Parse the JSON response
  .then((data) => console.log(data)) // Handle the data
  .catch((error) => console.error("Error:", error)); // Handle errors
```

### Example 2: POST Request with Data

```js
const postData = {
  name: "John",
  age: 30,
};

fetch("https://api.example.com/data", {
  method: "POST",
  headers: {
    "Content-Type": "application/json",
  },
  body: JSON.stringify(postData),
})
  .then((response) => response.json()) // Parse the JSON response
  .then((data) => console.log(data)) // Handle the data
  .catch((error) => console.error("Error:", error)); // Handle errors
```

### Example 3: Using `async/await` with Fetch

```js
async function fetchData() {
  try {
    const response = await fetch("https://api.example.com/data");
    if (!response.ok) {
      // Check if response is successful
      throw new Error("Network response was not ok");
    }
    const data = await response.json(); // Parse the JSON response
    console.log(data); // Handle the data
  } catch (error) {
    console.error("Error:", error); // Handle errors
  }
}

fetchData();
```

### Response Object

The `fetch` call returns a **Response** object that includes:

- **`response.ok`**: A boolean indicating whether the request was successful (status code 200-299).
- **`response.status`**: The HTTP status code.
- **`response.json()`**: A method to parse the response as JSON (returns a Promise).
- **`response.text()`**: A method to parse the response as plain text.
- **`response.blob()`**: A method to parse the response as binary data.

### Error Handling

The Fetch API does **not** reject an HTTP error (like 404 or 500); it only rejects if there's a network error or if the request is blocked. You need to check the `response.ok` to handle HTTP errors:

```js
fetch("https://api.example.com/data")
  .then((response) => {
    if (!response.ok) {
      throw new Error("Network response was not ok");
    }
    return response.json(); // Parse JSON if successful
  })
  .then((data) => console.log(data)) // Handle the data
  .catch((error) => console.error("Fetch error:", error)); // Handle errors
```

### Advantages of Fetch API

- **More readable syntax**: The Promise-based approach makes code more readable and avoids "callback hell."
- **Better handling of HTTP requests**: Fetch provides a clear and flexible way to send various types of HTTP requests (GET, POST, PUT, DELETE, etc.).
- **Built-in support for streaming**: Fetch allows working with large files efficiently by using streams.
- **CORS support**: Fetch includes built-in support for Cross-Origin Resource Sharing (CORS), making it easier to handle cross-origin requests.

The Fetch API is a powerful tool for modern web development, offering an easy and flexible way to make network requests.

[**Back** ⤴️](https://github.com/Stei-ITstudents/Javascript-Concepts_Before-ReactJs/tree/main#readme)
