# **Destructuring**

## In JavaScript allows you to unpack values from arrays or properties from objects into distinct variables, making it easier to work with complex data structures. It can be used for arrays, objects, and even nested data structures.

### Array Destructuring

With array destructuring, you can assign variables to array elements based on their positions.

```js
let fruits = ["apple", "banana", "cherry"];
let [first, second, third] = fruits;

console.log(first); // "apple"
console.log(second); // "banana"
console.log(third); // "cherry"
```

You can also use default values if the array has fewer elements than expected:

```js
let colors = ["red"];
let [primary, secondary = "blue"] = colors;

console.log(primary); // "red"
console.log(secondary); // "blue"
```

### Object Destructuring

With object destructuring, you can assign variables based on property names from an object.

```js
let user = { name: "Alice", age: 30, location: "Paris" };
let { name, age, location } = user;

console.log(name); // "Alice"
console.log(age); // 30
console.log(location); // "Paris"
```

If you want to assign to variables with different names, you can rename them during destructuring:

```js
let person = { name: "Bob", age: 25 };
let { name: fullName, age: yearsOld } = person;

console.log(fullName); // "Bob"
console.log(yearsOld); // 25
```

### Nested Destructuring

You can destructure values inside other objects or arrays as well, even when they are nested.

```js
let data = {
  user: { name: "Charlie", age: 35 },
  city: "New York",
};

let {
  user: { name, age },
  city,
} = data;

console.log(name); // "Charlie"
console.log(age); // 35
console.log(city); // "New York"
```

For arrays nested inside objects:

```js
let profile = { name: "Dave", hobbies: ["reading", "coding", "hiking"] };
let {
  hobbies: [hobby1, hobby2],
} = profile;

console.log(hobby1); // "reading"
console.log(hobby2); // "coding"
```

### Default Values in Destructuring

If a value is `undefined`, you can assign a default value to prevent it from being `undefined` in the result.

```js
let person = { name: "Eva" };
let { name, age = 30 } = person;

console.log(name); // "Eva"
console.log(age); // 30 (default value)
```

### Rest in Destructuring

You can also collect the remaining properties in an object or elements in an array using the rest syntax (`...`).

For arrays:

```js
let colors = ["red", "green", "blue", "yellow"];
let [firstColor, ...otherColors] = colors;

console.log(firstColor); // "red"
console.log(otherColors); // ["green", "blue", "yellow"]
```

For objects:

```js
let person = { name: "Jack", age: 40, city: "Berlin" };
let { name, ...rest } = person;

console.log(name); // "Jack"
console.log(rest); // { age: 40, city: "Berlin" }
```

### Function Parameter Destructuring

Destructuring can also be used in function parameters to extract values directly from objects or arrays.

For objects:

```js
function greet({ name, age }) {
  console.log(`Hello ${name}, you are ${age} years old.`);
}

let person = { name: "Sophia", age: 28 };
greet(person); // "Hello Sophia, you are 28 years old."
```

For arrays:

```js
function calculate([x, y]) {
  return x + y;
}

let numbers = [5, 10];
console.log(calculate(numbers)); // 15
```

Destructuring provides a cleaner and more readable syntax for extracting and working with data in JavaScript, especially when dealing with complex objects and arrays.

[**Back** ⤴️](https://github.com/Stei-ITstudents/Javascript-Concepts_Before-ReactJs/tree/main#readme)
