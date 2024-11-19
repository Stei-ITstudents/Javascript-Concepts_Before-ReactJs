# Regular Functions

In this section, we'll focus on regular functions (simply referred to as functions here), and in a future article, we will cover arrow functions (often referred to as `arrow functions`, not as `arrows`).

## 1. Defining Functions

In general, a function is a "subprogram" that can be called from external code (or internally in the case of recursion). Like any other program, a function is composed of a series of expressions forming its body. Values are passed to the function as arguments, and the function returns a value.

A function can expose certain variables (which have local scope, only within the function) as parameters. When the function is called, these parameters are substituted with values (or functions, etc.), and during the call, these values are referred to as arguments. So, we say that a function "has parameters" and we "call it with arguments." More explanations [here](https://codeburst.io/parameters-arguments-in-javascript-eb1d8bd0ef04).

Regular functions fall into two categories:

#### 1. Function Declarations (or function statements)

A declared function is a `Function object` and has all the properties and behaviors that a Function object implements: [read more here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function) about the `Function object`.

Using the `Function` object, we can declare a function like this:

```js
var multiply = new Function("x", "y", "return x * y");
```

This is similar to:

```js
function multiply(x, y) {
  return x * y;
}
```

More details and comparisons [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions#Constructor_vs._declaration_vs._expression).

A function must have:

1. A name (although anonymous functions also exist).
2. A list of parameters (which can be empty).
3. A function body enclosed in curly braces `{....}`.
4. By default, functions return `undefined`. To return a different value, the function must have a `return` statement specifying the value to return.

Example:

```js
function square(number) {
  return number * number;
}
```

Function declarations:

1. **Attach to the global object**.
2. **Can be redeclared**.
3. **Are hoisted** during declaration (more details and comparisons between function declarations and function expressions).
4. **Have scope limited to the functions in which they are declared** (or to the global object).

It's worth noting that browsers handle hoisting differently in conditional control structures. **Safari** is the only one where hoisting occurs fully within `if/else` statements. **Edge** offers no hoisting above `if`, while **Chrome** and **Firefox** behave identically, hoisting only the function's name, not its type.

Example:

```js
    console.log(a in window); // if true, `a` was attached to the window object
    console.log(typeof a); // if undefined, the type wasn't assigned to window

    if (false || true) {
    function a() { return 1; }
    }

    // In Chrome:
    >> True
    >> undefined

    // In Firefox:
    >> True
    >> undefined

    // In Edge:
    >> False
    >> undefined

    // In Safari:
    >> True
    >> function
```

Due to this inconsistency, it's recommended to avoid using function declarations inside `if/else` statements. For such cases, `function expressions` are preferred. More explanations [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function#Function_declaration_hoisting).

#### 2. Function Expressions

These are called `function expressions` because they are defined within expressions, inheriting characteristics from the variable type (`const`, `var`, `let`) they are assigned to.

```js
    const sqr = function square(number) {
    return number * number;
    }

    sqr(10)
    >> 100

    square(10)
    >> Uncaught ReferenceError: square is not defined
```

The main difference between `statement functions` and `function expressions` is that these functions can be anonymous and assigned to variables (const, let, var).

```js
const sqr = function (number) {
  return number * number;
};

sqr(10) >> 100;
```

**Note:** Contrary to expectations, regardless of the keyword used to declare a function, its type won't be hoisted (raised). More examples [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/function#Function_expression_hoisting).

---

### 2. Calling Functions

Defining a function doesn't execute the code inside it. By defining a function, we specify what will happen when the function is called.

Calling the function actually executes the actions specified in the function body with the arguments passed.

Arguments can be more than just strings or numbers; we can pass other functions or whole objects as arguments.

Functions must be called **within their scope**. However, they can be hoisted. As mentioned in the `var-const-let` document, `function declarations` are hoisted and can be called anywhere within their context (either before or after their definition). On the other hand, `function expressions`, regardless of the type of variable used, only have hoisting for their name, not their type.

Examples:

```js
    console.log(square(5));

    function square(n) { return n * n }

    >> 25
```

While:

```js
console.log(square); // square is hoisted with an initial value undefined.
console.log(square(5)); // Uncaught TypeError: square is not a function
const square = function (n) {
  return n * n;
};
```

---

### 3. Scope and the Function Stack

The function's context (function scope) refers to where the function is declared (or globally if declared globally). Documentation [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions#Function_scope).

---

### Recursion

Functions can call themselves, which is known as recursion.

Example:

```js
    function factorial(n) {
        if ((n === 0) || (n === 1)){
            return 1;
        }else{
            return (n * factorial(n - 1))};
    }

    factorial(5);
    >> 120
```

I recommend reading more about recursion [here](https://www.javascripttutorial.net/javascript-recursive-function/) and [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions#Recursion).

---

### Nested Functions and Closures

We can nest a function inside another. There are a few things to keep in mind:

- The inner function can only be called from the outer function.
- The inner function forms a closure: it can access the arguments and variables of the outer function, but the outer function cannot access the inner function's arguments or variables.

Example:

```js
function addSquares(a, b) {
  function square(x) {
    return x * x;
  }
  return square(a) + square(b);
}

a = addSquares(2, 3); // returns 13
b = addSquares(3, 4); // returns 25
```

- We can call the inner function, forming a closure, by calling the outer function and passing arguments to both.

```js
function outside(x) {
  function inside(y) {
    return x + y;
  }
  return inside;
}

fn_inside = outside(3);
fn_inside(5); // 8;

// or

outside(3)(5); // 8;
```

Documentation [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions#Nested_functions_and_closures).

### Closures

Closures are one of JavaScript's most powerful features. JavaScript allows nesting functions and grants the inner function full access to all variables defined in the outer function. However, the outer function does not have access to variables or functions within the inner function.

```js
var pet = function (name) {
  var getName = function () {
    return name; // The inner function can access variables from the outer function.
  };
  return getName;
};
myPet = pet("Vivie");

myPet(); // returns "Vivie"
```

The inner variables act as "secure stores" for the arguments and variables of the outer function.

Example of multiply-nested functions:

```js
function A(x) {
  function B(y) {
    function C(z) {
      console.log(x + y + z);
    }
    C(3);
  }
  B(2);
}
A(1); // logs 6 (1 + 2 + 3)
```

Here, A contains B, which in turn contains C. Functions B and C form closures, so B can access A, and C can access B. Because C can access B and B can access A, C can also access A. However, A can't access C.

Documentation [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions#Multiply-nested_functions).

---

### Name Conflicts

When two arguments or variables within the scope of a closure have the same name, a name conflict arises. In this case, inner variables take precedence over outer ones.

Example:

```js
function outside() {
  var x = 5;
  function inside(x) {
    return x * 2;
  }
  return inside;
}

outside()(10); // returns 20, not 10
```

In the code above, when we call `inside(10)`, the `x` inside the `inside` function is assigned the value `10`. This shadows the outer `x` (which is `5`) and leads to the result `20`.

However, if the inner function doesn't take a parameter, the outer `x` will be used:

```js
function outside() {
  var x = 5;
  function inside() {
    return x * 2; // This x refers to the variable in the outer function
  }
  return inside;
}

console.log(outside()()); // returns 10, using the outer 'x' value
```

In this case, since `inside()` doesn't have its own `x`, it refers to the `x` from the outer function `outside()`, which is `5`. So the result is `10`.

### Preventing Name Conflicts

To avoid name conflicts and shadowing issues, it's best to use **unique variable names** and ensure that inner functions only access variables they need from the outer function. This is especially important when working with closures or complex function compositions.

Using different names for variables in inner and outer scopes can help make the code clearer and prevent unexpected behavior.

```js
function outside() {
  var outerX = 5;
  function inside(innerX) {
    return innerX * 2; // Avoids shadowing the outerX variable
  }
  return inside;
}

console.log(outside()(10)); // 20
```

In this version, `outerX` is the outer variable, and `innerX` is the parameter of the inner function, avoiding any shadowing or confusion.

---

### Hoisting in Functions

In JavaScript, **hoisting** refers to the behavior of moving variable and function declarations to the top of their containing scope during the execution phase. However, the initialization (assignment) of variables is **not hoisted**.

#### Function Declarations

Function declarations are fully hoisted. This means that you can call a function before it is defined, and it will still work because the function definition is hoisted to the top of the scope.

```js
console.log(foo()); // Outputs: "Hello World!"

function foo() {
  return "Hello World!";
}
```

Here, the function `foo` can be called before it is declared because the function declaration is hoisted to the top of the scope.

#### Function Expressions

Function expressions, on the other hand, are not hoisted in the same way. Only the **variable declaration** (the variable to which the function is assigned) is hoisted, but the **function assignment** happens at the point where the function expression is evaluated. Therefore, calling the function before its assignment results in an error.

```js
console.log(foo()); // Uncaught TypeError: foo is not a function

var foo = function () {
  return "Hello World!";
};
```

In this case, the declaration of `foo` is hoisted, but the assignment of the function to `foo` happens at runtime. Therefore, trying to call `foo()` before the assignment results in a `TypeError`, because `foo` is initially `undefined` until it is assigned.

---

### `this` Keyword in Functions

In JavaScript, the behavior of the `this` keyword depends on how the function is called. The value of `this` can be tricky, especially when using regular functions, arrow functions, or when functions are used as methods or constructors.

#### Regular Functions and `this`

In regular functions, the value of `this` is determined by how the function is called:

- If the function is called as a **method** of an object, `this` refers to the object that is calling the method.
- If the function is called **globally** (outside of any object), `this` refers to the global object (`window` in browsers, or `global` in Node.js).
- If the function is called using the `new` keyword, `this` refers to the newly created object.

Example 1: Calling a method

```js
const person = {
  name: "Alice",
  greet: function () {
    console.log("Hello, " + this.name); // `this` refers to the `person` object
  },
};

person.greet(); // "Hello, Alice"
```

Example 2: Global function call

```js
function showThis() {
  console.log(this); // `this` refers to the global object
}

showThis(); // In a browser, it refers to the `window` object
```

Example 3: Using `new` keyword

```js
function Car(model) {
  this.model = model;
}

const myCar = new Car("Tesla");
console.log(myCar.model); // "Tesla"
```

#### Arrow Functions and `this`

Arrow functions do not have their own `this`. Instead, they inherit `this` from the surrounding lexical context (the scope in which they were defined). This makes arrow functions particularly useful for handling callbacks and ensuring that `this` behaves consistently.

```js
const person = {
  name: "Alice",
  greet: () => {
    console.log("Hello, " + this.name); // `this` does not refer to `person`
  },
};

person.greet(); // "Hello, undefined"
```

In this example, `this` inside the arrow function refers to the `this` of the outer context (likely the global object or `undefined` in strict mode), not the `person` object. To fix this, you would use a regular function instead of an arrow function.

[**Back** ⤴️](https://github.com/Stei-ITstudents/Javascript-Concepts_Before-ReactJs/tree/main#readme)
