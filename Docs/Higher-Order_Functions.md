# **Higher-Order Functions**

## Are functions that take one or more functions as arguments or return a function as a result. In JavaScript, higher-order functions are commonly used with array methods to perform operations like transformation, filtering, and accumulation of array data

Some commonly used higher-order functions in JavaScript are `.map()`, `.filter()`, `.reduce()`, and `.forEach()`. These methods allow you to manipulate arrays without needing explicit loops.

### `.map()`

The `.map()` method creates a new array populated with the results of calling a provided function on every element in the original array.

#### Example 1

```js
const numbers = [1, 2, 3, 4];
const doubled = numbers.map((num) => num * 2); // Multiply each element by 2
console.log(doubled); // Output: [2, 4, 6, 8]
```

- **Use case**: You can use `.map()` when you want to transform every item in an array into something else (e.g., doubling numbers, converting strings to uppercase).

### `.filter()`

The `.filter()` method creates a new array with all elements that pass the test implemented by the provided function.

#### Example 2

```js
const numbers = [1, 2, 3, 4, 5];
const evenNumbers = numbers.filter((num) => num % 2 === 0); // Filter only even numbers
console.log(evenNumbers); // Output: [2, 4]
```

- **Use case**: Use `.filter()` when you want to keep only the elements that meet a certain condition (e.g., filtering out odd numbers or strings that contain a certain character).

### `.reduce()`

The `.reduce()` method applies a function against an accumulator and each element in the array (from left to right) to reduce it to a single value.

#### Example 3

```js
const numbers = [1, 2, 3, 4];
const sum = numbers.reduce(
  (accumulator, currentValue) => accumulator + currentValue,
  0
); // Sum all elements
console.log(sum); // Output: 10
```

- **Use case**: Use `.reduce()` when you need to calculate a single value from an array, such as a sum, product, or combining elements in some way (e.g., reducing an array of numbers to their sum).

### `.forEach()`

The `.forEach()` method executes a provided function once for each element in the array. It does not return a value, unlike the other methods.

#### Example 4

```js
const numbers = [1, 2, 3, 4];
numbers.forEach((num) => console.log(num * 2)); // Log each element multiplied by 2
// Output: 2, 4, 6, 8
```

- **Use case**: Use `.forEach()` when you want to iterate over all elements of an array to perform an action (such as logging values or modifying each element directly), but do not need to return a new array.

### Summary

- **`.map()`**: Transforms each element in the array.
- **`.filter()`**: Filters the array based on a condition.
- **`.reduce()`**: Reduces the array to a single value.
- **`.forEach()`**: Performs a function on each element without returning anything.

These higher-order functions help write concise and expressive code by abstracting away the need for explicit loops. They enhance the readability and maintainability of JavaScript code.

[**Back** ⤴️](https://github.com/Stei-ITstudents/Javascript-Concepts_Before-ReactJs/tree/main)
