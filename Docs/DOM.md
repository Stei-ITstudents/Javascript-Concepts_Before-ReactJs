# **DOM (Document Object Model)** and how JavaScript interacts with it. The DOM represents the structure of a webpage as a tree of objects, and JavaScript allows us to manipulate this tree to change the content, structure, and style of a page dynamically

## **What is the DOM?**

The DOM is a programming interface for HTML and XML documents. It provides a structured representation of the document as a tree of nodes. Each node represents a part of the page (elements, attributes, text, etc.), and you can access, modify, add, or delete these nodes using JavaScript.

## **Accessing DOM Elements**

You can access DOM elements using several methods. Some of the most common ones are:

- **`getElementById()`** - Selects an element by its ID.
- **`getElementsByClassName()`** - Selects elements by their class name.
- **`getElementsByTagName()`** - Selects elements by their tag name.
- **`querySelector()`** - Selects the first element matching a CSS selector.
- **`querySelectorAll()`** - Selects all elements matching a CSS selector.

```javascript
// Accessing elements by ID
const element = document.getElementById("myElement");

// Accessing elements by class name
const elements = document.getElementsByClassName("myClass");

// Accessing elements by tag name
const listItems = document.getElementsByTagName("li");

// Using querySelector (first match)
const firstDiv = document.querySelector("div");

// Using querySelectorAll (all matches)
const allDivs = document.querySelectorAll("div");
```

## **Manipulating DOM Elements**

Once you have a reference to an element, you can manipulate its properties or add event listeners to interact with the user.

## **Changing Content:**

- **`innerText`**: Changes or retrieves the text content of an element.
- **`innerHTML`**: Changes or retrieves the HTML content inside an element (not recommended for security reasons).

```javascript
const element = document.getElementById("myElement");
element.innerText = "New content here!";
element.innerHTML = "<span>Updated content</span>";
```

## **Changing Attributes:**

You can modify attributes of HTML elements using methods like `setAttribute()`, `getAttribute()`, and `removeAttribute()`.

```javascript
const image = document.getElementById("myImage");
image.setAttribute("src", "newImage.jpg");
image.setAttribute("alt", "A new image");
const src = image.getAttribute("src"); // 'newImage.jpg'
```

## **Modifying Style:**

The `style` property allows you to modify CSS styles directly from JavaScript.

```javascript
const element = document.getElementById("myElement");
element.style.color = "red";
element.style.backgroundColor = "yellow";
```

## **Creating and Adding Elements**

You can create new elements and add them to the DOM.

```javascript
// Create a new element
const newDiv = document.createElement("div");
newDiv.innerText = "This is a new div";

// Append the new element to an existing one
document.body.appendChild(newDiv);

// Insert the new element at a specific position
const referenceNode = document.getElementById("existingElement");
document.body.insertBefore(newDiv, referenceNode);
```

## **Removing Elements**

You can remove elements from the DOM with the `remove()` method or `parentNode.removeChild()`.

```javascript
// Using remove
const element = document.getElementById("myElement");
element.remove();

// Using removeChild
const parent = document.getElementById("parentElement");
parent.removeChild(element);
```

## **Event Handling**

JavaScript allows you to handle events like clicks, keyboard input, etc.

- **`addEventListener()`** is the recommended way to handle events as it allows multiple listeners for the same event.

```javascript
const button = document.getElementById("myButton");

// Add event listener to button
button.addEventListener("click", function () {
  alert("Button clicked!");
});

// Remove event listener
button.removeEventListener("click", function () {
  alert("Button clicked!");
});
```

You can also use **inline event handlers** (not recommended):

```html
<button onclick="alert('Button clicked!')">Click me</button>
```

## **Traversing the DOM**

Once you access an element, you can navigate through the DOM tree using properties like `parentNode`, `childNodes`, `nextSibling`, `previousSibling`, etc.

```javascript
const parent = document.getElementById("parentElement");

// Accessing child elements
const firstChild = parent.firstElementChild;
const lastChild = parent.lastElementChild;

// Traversing siblings
const nextSibling = parent.nextElementSibling;
const previousSibling = parent.previousElementSibling;
```

## **Handling Forms**

You can manipulate forms and form elements (like `<input>`, `<select>`, etc.) through the DOM.

```javascript
// Accessing form elements
const input = document.getElementById("myInput");

// Changing value
input.value = "New input value";

// Getting value
const value = input.value;
```

## **DOM Manipulation and React**

In React, DOM manipulation is handled by React itself through its Virtual DOM. You generally won't need to directly interact with the DOM like in vanilla JavaScript because React efficiently manages the DOM updates for you.

However, you can still use native DOM methods and event handling in certain cases, especially for integrating third-party libraries or handling specific tasks.

[**Back** ⤴️](https://github.com/Stei-ITstudents/Javascript-Concepts_Before-ReactJs/tree/main)
