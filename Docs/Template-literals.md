# **Template Literals** in JavaScript provide a way to create strings more easily and dynamically. They are introduced in **ECMAScript 6 (ES6)** and allow for string interpolation, multi-line strings, and easier expression embedding

## Key Features of Template Literals

### **String Interpolation (Embedding Variables and Expressions)**

Template literals allow you to embed variables or expressions inside strings, making the code cleaner and more readable. This is done using the `${}` syntax inside backticks (`` ` ``).

- **Example**:

```js
let name = "Alice";
let age = 25;

let greeting = `Hello, my name is ${name} and I am ${age} years old.`;
console.log(greeting); // "Hello, my name is Alice and I am 25 years old."
```

In this example, the values of `name` and `age` are inserted directly into the string.

### **Multi-line Strings**

Template literals can span multiple lines, which eliminates the need for concatenating strings with newline characters (`\n`) or using other methods.

- **Example**:

```js
let multiline = `This is a string
that spans multiple
lines.`;
console.log(multiline);
// Output:
// This is a string
// that spans multiple
// lines.
```

In this case, the string automatically preserves the line breaks, which is much cleaner than manually adding `\n`.

### **Expression Embedding**

You can embed not just variables, but also any JavaScript expression within `${}`. This includes function calls, arithmetic operations, or even ternary operators.

- **Example**:

```js
let a = 10;
let b = 5;
let result = `The sum of ${a} and ${b} is ${a + b}.`;
console.log(result); // "The sum of 10 and 5 is 15."

let isEven = (x) => x % 2 === 0;
let message = `The number ${a} is ${isEven(a) ? "even" : "odd"}.`;
console.log(message); // "The number 10 is even."
```

### **Tag Functions (Tagged Templates)**

Template literals can be passed to a function for more advanced handling. These are called "tagged templates". The function receives the template literal as input, along with an array of string literals and interpolated expressions.

- **Example**:

```js
function tag(strings, ...values) {
  console.log(strings); // Array of string literals
  console.log(values); // Array of interpolated values
  return strings.reduce((acc, str, i) => acc + str + (values[i] || ""), "");
}

let name = "Alice";
let age = 25;
let greeting = tag`Hello, my name is ${name} and I am ${age} years old.`;
console.log(greeting); // "Hello, my name is Alice and I am 25 years old."
```

In this case, the `tag` function processes the template string and interpolated values before returning the final string.

### **Nesting Template Literals**

You can also nest template literals inside each other for more complex formatting or structure.

- **Example**:

```js
let name = "Bob";
let timeOfDay = "morning";
let message = `Good ${timeOfDay}, ${name}!`;

console.log(message); // "Good morning, Bob!"
```

### Advantages of Template Literals

- **Cleaner and More Readable**: With template literals, you avoid the cumbersome syntax of concatenating strings with `+` and can directly embed variables and expressions.

- **Without Template Literals**:

```js
let greeting = "Hello, my name is " + name + " and I am " + age + " years old.";
```

- **No Need for Manual Line Breaks**: Template literals allow you to easily create strings that span multiple lines without needing explicit newline characters or string concatenation.

- **Expression Evaluation**: You can embed complex expressions inside template literals, making it easier to compute values dynamically and directly include them in strings.

### Summary of Template Literals Features

- **String Interpolation**: Embed variables and expressions using `${}` inside backticks.
- **Multi-line Strings**: Easily create strings that span multiple lines.
- **Expression Embedding**: Evaluate expressions directly inside the template string.
- **Tagged Templates**: Pass template literals to functions for more control over string processing.
- **Cleaner Syntax**: Avoid cumbersome concatenation and manual line breaks.

### Example of All Features Combined

```js
const name = "Charlie";
const age = 30;
const currentYear = 2024;
const birthYear = currentYear - age;

// Multi-line string with expressions
const message = `
Hello, ${name}!
You are ${age} years old.
You were born in ${birthYear}.
`;

console.log(message);

// Using a tagged template function
function customTag(strings, ...values) {
  let result = strings[0];
  for (let i = 0; i < values.length; i++) {
    result += `${values[i]}` + strings[i + 1];
  }
  return result.toUpperCase();
}

const greeting = customTag`Hello, ${name}! How are you today?`;
console.log(greeting); // "HELLO, CHARLIE! HOW ARE YOU TODAY?"
```

In this example:

- The first part demonstrates multi-line and expression embedding.
- The second part demonstrates the use of a tagged template (`customTag`), which processes the template string and expressions and transforms the result to uppercase.

Template literals simplify string creation, making your code more readable and expressive while improving maintainability.

[**Back** ⤴️](https://github.com/Stei-ITstudents/Javascript-Concepts_Before-ReactJs/tree/main)
