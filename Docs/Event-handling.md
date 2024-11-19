# Event Handling

## Event handling is an essential part of making your web pages interactive. In JavaScript, events represent actions that occur in the browser, such as user interactions (clicking a button, submitting a form, pressing a key, etc.), or other occurrences (like page loading or network responses)

### Basics of Handling Events

Events are typically handled using the **addEventListener** method, which allows you to register a callback function to run when a specific event occurs on an element.

#### Syntax - Adding an Event Listener

```js
element.addEventListener(event, callback, useCapture);
```

- `event`: The type of event to listen for (e.g., `"click"`, `"keydown"`, `"submit"`, etc.).
- `callback`: The function that will be executed when the event is triggered.
- `useCapture`: (optional) A boolean that specifies whether to use event capturing. Default is `false`.

#### Example - Adding an Event Listener

```js
// Adding an event listener to a button
const button = document.querySelector("button");
button.addEventListener("click", function () {
  alert("Button clicked!");
});
```

In this example, an alert will show when the button is clicked.

---

### Common Event Types

Some of the most commonly used event types in JavaScript include:

- **Mouse Events**:
  - `click`: Fired when an element is clicked.
  - `dblclick`: Fired when an element is double-clicked.
  - `mouseover`: Fired when the mouse pointer enters an element.
  - `mouseout`: Fired when the mouse pointer leaves an element.
  - `mousemove`: Fired when the mouse moves within an element.
- **Keyboard Events**:
  - `keydown`: Fired when a key is pressed down.
  - `keyup`: Fired when a key is released.
  - `keypress`: Fired when a key is pressed and released (deprecated in modern browsers).
- **Form Events**:

  - `submit`: Fired when a form is submitted.
  - `change`: Fired when a form element's value changes (e.g., `<input>`, `<select>`).
  - `focus`: Fired when an element gains focus.
  - `blur`: Fired when an element loses focus.

- **Window Events**:
  - `load`: Fired when the page has fully loaded.
  - `resize`: Fired when the window is resized.
  - `scroll`: Fired when the page is scrolled.

---

### Preventing Default Behaviors

Many browser events, such as form submissions or anchor clicks, have default behaviors associated with them. You can prevent these default behaviors using the `preventDefault()` method.

#### Example - Preventing Form Submission

```js
const form = document.querySelector("form");
form.addEventListener("submit", function (event) {
  event.preventDefault(); // Prevents the form from submitting
  console.log("Form submission prevented!");
});
```

In this case, when the form is submitted, the default action (sending the form data) is stopped, and you can handle it in your custom way.

#### Example - Preventing Link Navigation

```js
const link = document.querySelector("a");
link.addEventListener("click", function (event) {
  event.preventDefault(); // Prevents navigation to the link's href
  console.log("Link click prevented!");
});
```

---

### Event Object

The event object contains information about the event that occurred, such as the type of event, the element that triggered it, and additional data (e.g., mouse position, key pressed).

#### Example - Accessing Event Details

```js
const button = document.querySelector("button");
button.addEventListener("click", function (event) {
  console.log(event.type); // Output: 'click'
  console.log(event.target); // Output: The button element that was clicked
});
```

You can use the event object to retrieve various details about the event, such as the mouse's coordinates or the key that was pressed.

---

### Removing Event Listeners

You can also remove event listeners using the `removeEventListener()` method. This is useful when you no longer need to listen for an event or if you want to stop listening after a certain condition is met.

### Syntax - Removing an Event Listener

```js
element.removeEventListener(event, callback, useCapture);
```

This works similarly to `addEventListener()`. You must pass the exact same function reference to `removeEventListener()` as you did with `addEventListener()`.

#### Example

```js
function handleClick() {
  alert("Button clicked!");
}

const button = document.querySelector("button");
button.addEventListener("click", handleClick);

// Later, removing the event listener
button.removeEventListener("click", handleClick);
```

---

### Event Delegation

In cases where you have multiple child elements that need to handle the same event, you can use **event delegation**. This technique involves setting up a single event listener on a parent element and letting the event "bubble" up from child elements to the parent.

#### Example - Event Delegation with Buttons

```js
const container = document.querySelector("#container");
container.addEventListener("click", function (event) {
  if (event.target && event.target.matches("button")) {
    alert("Button clicked inside the container!");
  }
});
```

Here, the click event is listened for on the parent `#container`, and if a button is clicked inside the container, the event is handled.

---

### Conclusion

Event handling is a core concept in JavaScript for building interactive websites. The `addEventListener()` method is used to listen for events on elements, and you can manage the event flow using `preventDefault()` and `stopPropagation()` methods. Common event types include mouse events, keyboard events, and form events. Additionally, understanding how to remove event listeners and utilize event delegation is important for efficient event management in complex applications.

[**Back** ⤴️](https://github.com/Stei-ITstudents/Javascript-Concepts_Before-ReactJs/tree/main#readme)
