# Understanding JavaScript Prototypes

## **What is a Prototype?**

### - **Definition**: A prototype is an object from which other objects inherit properties and methodEvery JavaScript object has a prototype, which serves as a template for creating properties and methods in other objects

- **Prototype Chain**: If an object doesn't have a property or method, JavaScript looks up the prototype chain to see if it's defined in its prototype.

### **How Prototypes Work**

- **Prototype Property**: Each JavaScript function has a `prototype` property that is used when creating new instances.
- **proto** Property: Every object instance has an internal `__proto__` property that points to the prototype of the constructor from which it was created.

**Example**:

```javascript
function Person(name) {
  this.name = name;
}

Person.prototype.greet = function () {
  console.log(`Hello, my name is ${this.name}`);
};

const john = new Person("John");
john.greet(); // Output: "Hello, my name is John"

// Checking the prototype chain
console.log(john.__proto__ === Person.prototype); // Output: true
console.log(Person.prototype.__proto__ === Object.prototype); // Output: true
```

### **Prototype Chain in Action**

### - **Prototype Lookup**: When you call `john.greet()`, JavaScript first checks if `greet` exists directly on `johnIf not, it looks up the chain to`Person.prototypeIf it still doesn't find it, it moves to `Object.prototype`, and if it fails there, it returns `undefined`

### **Adding Methods to Prototypes**

- **Shared Methods**: Adding methods to a prototype allows all instances of an object to share the same method, optimizing memory usage.

```javascript
Person.prototype.sayGoodbye = function () {
  console.log(`${this.name} says goodbye`);
};

const jane = new Person("Jane");
jane.sayGoodbye(); // Output: "Jane says goodbye"
```

### **Modifying Prototypes**

- **Dynamic Additions**: You can add properties or methods to an object's prototype at runtime.
- **Prototype Pollution Warning**: Modifying built-in prototypes like `Array.prototype` or `Object.prototype` can lead to unintended side effects and should be done with caution.

### **Using `Object.create()` for Prototypal Inheritance**

- This method creates a new object with the specified prototype.

```javascript
const animal = {
  speak: function () {
    console.log(`${this.name} makes a sound`);
  },
};

const dog = Object.create(animal);
dog.name = "Rex";
dog.speak(); // Output: "Rex makes a sound"
```

### **How Prototypes Relate to React Components**

- In React, classes are built on the prototype system, using `React.Component` or `React.PureComponent` as their prototype to inherit methods like `render()` and lifecycle methods.
- Before React introduced hooks, understanding prototypes was crucial for creating stateful components.

### **Key Points**

- **Prototype is Efficient**: Methods added to the prototype are shared across all instances, saving memory.
- **Chain Traversal**: JavaScript engine traverses the prototype chain when searching for a property or method.

Understanding prototypes is foundational to mastering inheritance and object-oriented programming in JavaScript.

[**Back** ⤴️](https://github.com/Stei-ITstudents/Javascript-Concepts_Before-ReactJs/tree/main#readme)
