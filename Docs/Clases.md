# Classes

## **What are JavaScript Classes?**

- **Definition**: A class is a blueprint for creating objects with shared properties and methodClasses make it easier to create multiple objects with the same structure and behavior.
- **Syntax**: Introduced in ES6 as syntactic sugar over JavaScript's prototype-based inheritance system, making OOP more familiar.

**Basic Class Structure**:

```javascript
class Person {
  // Constructor: a special method for initializing new objects
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  // Method: defines behavior for class instances
  greet() {
    console.log(
      `Hello, my name is ${this.name} and I am ${this.age} years old.`
    );
  }
}

// Instantiating a new object
const john = new Person("John", 30);
john.greet(); // Output: "Hello, my name is John and I am 30 years old."
```

**Key Concepts**:

- **Constructor Method**: Initializes the object’s properties when a new instance is created.
- **Methods**: Defined inside the class, they provide functionality to the class instances.
- **`this` Keyword**: Refers to the current instance of the class.

**Class Inheritance**:

- **Inheritance** allows one class to extend another, inheriting its properties and methods.

**Example of Inheritance**:

```javascript
class Animal {
  constructor(name) {
    this.name = name;
  }

  speak() {
    console.log(`${this.name} makes a sound.`);
  }
}

class Dog extends Animal {
  speak() {
    console.log(`${this.name} barks.`);
  }
}

const myDog = new Dog("Rex");
myDog.speak(); // Output: "Rex barks."
```

**Class Features**:

- **Static Methods**: Methods that belong to the class itself, not instances.

```javascript
class MathUtils {
  static add(a, b) {
    return a + b;
  }
}

console.log(MathUtils.add(5, 10)); // Output: 15
```

- **Getters and Setters**: Provide controlled access to properties.

```javascript
class Rectangle {
  constructor(width, height) {
    this.width = width;
    this.height = height;
  }

  get area() {
    return this.width * this.height;
  }

  set width(value) {
    if (value > 0) {
      this._width = value;
    } else {
      console.error("Width must be positive");
    }
  }

  get width() {
    return this._width;
  }
}

const rect = new Rectangle(10, 5);
console.log(rect.area); // Output: 50
```

**Benefits of Using Classes**:

- **Cleaner Syntax**: More intuitive than the prototype-based syntax.
- **Inheritance**: Simplifies code reusability through `extends`.
- **Encapsulation**: Encapsulates data and methods, providing a clear structure.

This covers the essential aspects of JavaScript classes, helping you understand how to build and extend them effectively.

[**Back** ⤴️](https://github.com/Stei-ITstudents/Javascript-Concepts_Before-ReactJs/tree/main)
