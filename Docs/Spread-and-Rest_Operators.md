# **Spread and Rest Operators**

## In JavaScript are both represented by the same syntax `...`, but they serve different purposes depending on how they are used

### Spread Operator (`...`)

The **spread operator** is used to **unpack** or **spread** elements from an array or object into a new array or object. It allows you to copy elements or properties or combine them with other values.

#### In Arrays

- The spread operator can be used to copy all elements from an array or to combine multiple arrays.

```js
// Copying an array
let numbers = [1, 2, 3];
let copiedNumbers = [...numbers];
console.log(copiedNumbers); // [1, 2, 3]

// Combining arrays
let moreNumbers = [4, 5, 6];
let allNumbers = [...numbers, ...moreNumbers];
console.log(allNumbers); // [1, 2, 3, 4, 5, 6]
```

#### In Objects

- The spread operator can be used to copy properties from one object to another or merge multiple objects.

```js
// Copying an object
let person = { name: "John", age: 30 };
let clonedPerson = { ...person };
console.log(clonedPerson); // { name: "John", age: 30 }

// Merging objects
let address = { city: "New York", country: "USA" };
let personWithAddress = { ...person, ...address };
console.log(personWithAddress); // { name: "John", age: 30, city: "New York", country: "USA" }
```

#### In Function Calls

- The spread operator can be used to pass an array of values as individual arguments to a function.

```js
function sum(a, b, c) {
  return a + b + c;
}

let numbers = [1, 2, 3];
console.log(sum(...numbers)); // 6
```

### Rest Operator (`...`)

The **rest operator** is used to **collect** or **group** multiple elements into an array. It is often used in function parameters or in destructuring to collect leftover elements.

#### In Function Parameters

- The rest operator can collect multiple arguments passed to a function into an array.

```js
function greet(...names) {
  console.log(names);
}

greet("Alice", "Bob", "Charlie"); // ["Alice", "Bob", "Charlie"]
```

#### In Object Destructuring

- The rest operator can be used to collect remaining properties in an object that are not explicitly destructured.

```js
let person = { name: "Alice", age: 30, city: "New York" };
let { name, ...rest } = person;

console.log(name); // "Alice"
console.log(rest); // { age: 30, city: "New York" }
```

#### In Array Destructuring

- The rest operator can collect remaining elements in an array into a new array.

```js
let fruits = ["apple", "banana", "cherry", "date"];
let [first, second, ...others] = fruits;

console.log(first); // "apple"
console.log(second); // "banana"
console.log(others); // ["cherry", "date"]
```

### Key Differences Between Spread and Rest

- **Spread** is used to **expand** elements into individual items.

  - Example: `[...arr]`, `{...obj}`, `sum(...numbers)`

- **Rest** is used to **collect** multiple items into a single array or object.
  - Example: `function(...args)`, `let [first, ...rest] = arr`, `let {name, ...otherProps} = person`

### Combining Spread and Rest

You can combine both operators to handle more complex scenarios. For example, in a function where you want to take the first argument and then collect the rest:

```js
function processData(first, ...rest) {
  console.log(first); // First item
  console.log(rest); // Remaining items
}

let data = [1, 2, 3, 4, 5];
processData(...data); // Output: 1 [2, 3, 4, 5]
```

In summary:

- **Spread** copies or expands values (arrays or objects) into individual elements.
- **Rest** collects multiple elements into a single array or object.

[**Back** ⤴️](https://github.com/Stei-ITstudents/Javascript-Concepts_Before-ReactJs/tree/main#readme)
