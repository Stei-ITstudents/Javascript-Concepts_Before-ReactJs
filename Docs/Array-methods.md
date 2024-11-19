# These array methods are powerful for manipulating and iterating over arrays in JavaScript. Here's a breakdown of each method and how to use them effectively

## Array Methods: `.map()`, `.filter()`, `.reduce()`, and `.forEach()`

### **`.map()`**

- **Purpose**: Creates a new array by applying a function to each element in the original array.
- **Returns**: A new array with transformed elements.
- **Does Not**: Mutate the original array.

**Example**:

```javascript
const numbers = [1, 2, 3, 4, 5];
const doubled = numbers.map((num) => num * 2);
console.log(doubled); // [2, 4, 6, 8, 10]
```

**Use Case**: Transforming each element, such as formatting data or applying mathematical operations.

---

### **`.filter()`**

- **Purpose**: Creates a new array with elements that pass a condition specified in a callback function.
- **Returns**: A new array with only elements that satisfy the condition.
- **Does Not**: Mutate the original array.

**Example**:

```javascript
const numbers = [1, 2, 3, 4, 5];
const evens = numbers.filter((num) => num % 2 === 0);
console.log(evens); // [2, 4]
```

**Use Case**: Extracting elements based on specific criteria, such as filtering out invalid data or getting active users.

---

### **`.reduce()`**

- **Purpose**: Reduces an array to a single value by applying a function to an accumulator and each element of the array.
- **Returns**: A single accumulated value (number, object, string, etc.).
- **Does Not**: Mutate the original array.

**Syntax**:

```javascript
array.reduce((accumulator, currentValue, currentIndex, array) => {
  // operation
}, initialValue);
```

**Example**:

```javascript
const numbers = [1, 2, 3, 4, 5];
const sum = numbers.reduce((acc, num) => acc + num, 0);
console.log(sum); // 15
```

**Use Case**: Calculating totals, combining values, or flattening nested arrays.

---

### **`.forEach()`**

- **Purpose**: Executes a provided function once for each array element.
- **Returns**: `undefined` (used for side effects).
- **Does**: Iterates over elements but does **not** create a new array or return values.

**Example**:

```javascript
const numbers = [1, 2, 3, 4, 5];
numbers.forEach((num) => console.log(num * 2));
// Logs: 2, 4, 6, 8, 10 (side effect: logging to console)
```

**Use Case**: When you need to perform an operation that does not require storing the result, such as logging data or modifying an external variable.

---

### Summary of When to Use Each

- **`.map()`**: When you need to create a new array with transformed data.
- **`.filter()`**: When you need to filter elements based on conditions.
- **`.reduce()`**: When you need to accumulate data into a single value (e.g., sum, object, or nested structure).
- **`.forEach()`**: When you need to perform an operation on each element without returning anything (e.g., logging or modifying external state).

Let me know if you need examples that combine these methods or more in-depth use cases!

[**Back** ⤴️](https://github.com/Stei-ITstudents/Javascript-Concepts_Before-ReactJs/tree/main)
