# Exercises

## Exercise 1 > change color of div on click

```js
const div = document.querySelector("div");
const colors = [
  "red",
  "green",
  "blue",
  "yellow",
  "pink",
  "purple",
  "orange",
  "brown",
  "black",
  "white",
];
let index = 0;

div.addEventListener("click", () => {
  div.style.backgroundColor = colors[index];
  index = (index + 1) % colors.length;
});
```

## Exercise 2 > set interval and clear interval

```js
// start button
const startButton = document.createElement("button");
startButton.textContent = "Start";
startButton.style.margin = "10px";
startButton.style.borderRadius = "7px";
startButton.style.backgroundColor = "blue";
startButton.style.cursor = "pointer";
document.body.appendChild(startButton);

// progress bar
const progressBar = document.createElement("progress");
progressBar.max = 100;
progressBar.value = 0;
progressBar.style.width = "12vw";
progressBar.style.margin = "10px";
progressBar.style.height = "0.33vh";
document.body.appendChild(progressBar);

// clear button
const clearButton = document.createElement("button");
clearButton.textContent = "Clear";
clearButton.style.margin = "10px";
clearButton.style.borderRadius = "7px";
clearButton.style.backgroundColor = "blue";
clearButton.style.cursor = "pointer";
document.body.appendChild(clearButton);

let interval;
let progress = 0;

startButton.addEventListener("click", () => {
  clearInterval(interval);
  progress = 0;
  progressBar.value = 0;
  interval = setInterval(() => {
    progress += 1;
    progressBar.value = progress;
    if (progress >= 100) {
      progress = 100;
    }
  }, 600);
});

clearButton.addEventListener("click", () => {
  clearInterval(interval);
  progress = 0;
  progressBar.value = 0;
});
```

## Exercise 3 > Print the width and height of the window on resize

```js
window.addEventListener("resize", () => {
  console.log("Width:", window.innerWidth, "\n Height:", window.innerHeight);
});

// Exercise 4 > On click append the value of input to ul
const input = document.querySelector("input");
const button = document.querySelector("button");
const list = document.querySelector("ul");

// input text
const input = document.createElement("input");
input.type = "text";
document.body.appendChild(input);

// Append button
const appendButton = document.createElement("button");
appendButton.textContent = "Append";
document.body.appendChild(appendButton);

//ul
const list = document.createElement("ul");
list.style.color = "red";
document.body.appendChild(list);

//event listener
appendButton.addEventListener("click", () => {
  if (input.value) {
    const li = document.createElement("li");
    li.textContent = input.value;
    list.appendChild(li);
    input.value = "";
  }
});
```

## Exercise 5 > Increase and decrease the font size of a paragraph

```js
const increaseButton = document.querySelector("#increase");
const decreaseButton = document.querySelector("#decrease");
const paragraph = document.querySelector("p");

// Increase button
const increaseButton = document.createElement("button");
increaseButton.textContent = "Increase";
document.body.appendChild(increaseButton);

// Decrease button
const decreaseButton = document.createElement("button");
decreaseButton.textContent = "Decrease";
document.body.appendChild(decreaseButton);

// Paragraph
const paragraph = document.createElement("p");
let fontSize = 16;
paragraph.textContent = "The text Inizial 16 px";
paragraph.style.fontSize = "${fontSize}px";
document.body.appendChild(paragraph);

// Event listeners
increaseButton.addEventListener("click", () => {
  fontSize += 2;
  paragraph.style.fontSize = `${fontSize}px`;
  paragraph.textContent = `The text is increased to ${fontSize} px`;
});

decreaseButton.addEventListener("click", () => {
  fontSize -= 2;
  paragraph.textContent = `The text is decreased to ${fontSize} px`;
  paragraph.style.fontSize = `${fontSize}px`;
});
```

// Exercise 6 > Show hide paragraph

```js
//paragraph
const paragraph = document.createElement("p");
paragraph.textContent = "This is a paragraph";
document.body.appendChild(paragraph);

// button
const button = document.querySelector("button");
const paragraph = document.querySelector("p");
document.body.appendChild(paragraph);

// event listener
button.addEventListener("click", () => {
  if (paragraph.style.display === "none") {
    paragraph.style.display = "block";
    button.textContent = "Hide";
  } else {
    paragraph.style.display = "none";
    button.textContent = "Show";
  }
});
```

## Exercise 8 > render list of names

```js
const names = ['Ion', 'Maria', 'George', 'Andrei', 'Marius'];

// Create and append the list
const list = document.createElement('ul');
document.body.appendChild(list);

function renderList(names) {
list.innerHTML = '';

// Append new list items
names.forEach(name => {
const li = document.createElement('li');
li.textContent = name;
list.appendChild(li);
});
}

// Render
renderList(names);

// search input
const input = document.createElement('input');
input.type = 'text';
document.body.appendChild(input);

input.addEventListener('input', () => {
const query = input.value.toLowerCase();
const filtered = names.filter(name => name.toLowerCase().startsWith(query));
renderList(filtered);

```

// Exercise 10 > Create calculator

```js
// input
const input = document.createElement("input");
input.type = "text";
document.body.appendChild(input);

// button calculate
const button = document.createElement("button");
button.textContent = "Calculate";
document.body.appendChild(button);

// result paragraph
const result = document.createElement("p");
document.body.appendChild(result);

// event listener
button.addEventListener("click", () => {
  const numbers = input.value.split(",").map(Number);
  const subtraction = numbers.reduce((acc, number) => acc - number);
  result.textContent = "The subtraction is: ${subtraction}";
});
```

// Exercise 11 > Create chronometer

```js
// display
const timerDisplay = document.createElement("div");
timerDisplay.textContent = "0 seconds";
document.body.appendChild(timerDisplay);

// start button
const startButton = document.createElement("button");
startButton.textContent = "Start";
document.body.appendChild(startButton);

// stop button
const stopButton = document.createElement("button");
stopButton.textContent = "Stop";
document.body.appendChild(stopButton);

// reset button
const resetButton = document.createElement("button");
resetButton.textContent = "Reset";
document.body.appendChild(resetButton);

let seconds = 0;
let interval;

startButton.addEventListener("click", () => {
  // clear interval
  clearInterval(interval);
  // start interval
  interval = setInterval(() => {
    seconds += 1;
    timerDisplay.textContent = `${seconds} seconds`;
  }, 1000);
});

stopButton.addEventListener("click", () => {
  clearInterval(interval);
});

resetButton.addEventListener("click", () => {
  clearInterval(interval);
  seconds = 0;
  timerDisplay.textContent = `${seconds} seconds`;
});
```

// Exercise 12 > Create timer

```js
// display
const timerDisplay = document.createElement("div");
seconds = 10;
timerDisplay.textContent = ` Time left ${seconds} seconds`;
document.body.appendChild(timerDisplay);

// start button
const startButton = document.createElement("button");
startButton.textContent = "Start";
document.body.appendChild(startButton);

// stop button
const stopButton = document.createElement("button");
stopButton.textContent = "Stop";
document.body.appendChild(stopButton);

// reset button
const resetButton = document.createElement("button");
resetButton.textContent = "Reset";
document.body.appendChild(resetButton);

let countdown;
const alarmSound = new Audio(
  "https://assets.mixkit.co/active_storage/sfx/2462/2462-preview.mp3"
);

startButton.addEventListener("click", () => {
  clearInterval(countdown);
  countdown = setInterval(() => {
    if (isNaN(seconds)) {
      timerDisplay.textContent = "Not a number";
      return;
    }
    seconds -= 1;
    timerDisplay.textContent = `Time left ${seconds} seconds`;
    if (seconds <= 0) {
      clearInterval(countdown);
      timerDisplay.textContent = `Time expired, ${seconds} seconds`;
      alarmSound.play();
    }
  }, 1000);
});

stopButton.addEventListener("click", () => {
  clearInterval(countdown);
});

resetButton.addEventListener("click", () => {
  clearInterval(countdown);
  seconds = 10;
  timerDisplay.textContent = `Time left ${seconds} seconds`;
});
```

// Exercise 13 > To do list

```js
// title
const title = document.createElement("h1");
title.textContent = "To do list:";
document.body.appendChild(title);

// input
const todoInput = document.createElement("input");
todoInput.type = "text";
todoInput.placeholder = "Enter a task";
document.body.appendChild(todoInput);

// add button
const addTodoButton = document.createElement("button");
addTodoButton.id = "addTodoButton";
addTodoButton.textContent = "Add";
document.body.appendChild(addTodoButton);

// delete button
const deleteButton = document.createElement("button");
deleteButton.id = "deleteButton";
deleteButton.textContent = "Delete";
document.body.appendChild(deleteButton);

// ul
const todoList = document.createElement("ul");
document.body.appendChild(todoList);

// Add event listener
addTodoButton.addEventListener("click", () => {
  const task = todoInput.value.trim();
  if (task) {
    const li = document.createElement("li");

    const span = document.createElement("span");
    span.textContent = task;

    const checkbox = document.createElement("input");
    checkbox.type = "checkbox";
    li.appendChild(checkbox);
    checkbox.addEventListener("change", () => {
      if (checkbox.checked) {
        li.classList.add("completed");
      } else {
        li.classList.remove("completed");
      }
    });

    li.appendChild(span);
    todoList.appendChild(li);
    todoInput.value = "";
  }
  todoList.scrollIntoView({ behavior: "smooth" });
});

// Delete event listener
deleteButton.addEventListener("click", () => {
  const items = todoList.querySelectorAll("li");
  items.forEach((item) => {
    const checkbox = item.querySelector("input[type='checkbox']");
    if (checkbox && checkbox.checked) {
      todoList.removeChild(item);
    }
  });
});

// enter
document.addEventListener("keydown", (event) => {
  if (event.key === "Enter") {
    const task = todoInput.value.trim();
    if (task) {
      addTodoButton.click();
    } else {
      deleteButton.click();
    }
  }
});

const style = document.createElement("style");
style.textContent = `
  h1 {
    color: lightblue;
    font-family: Roboto, sans-serif;
    font-weight: bold;
    font-size: 16px;
    margin-left: 5px;
  }
  input {
    padding: 5px;
    border: "White";
    border-radius: 5px;
  }
  ul {
    list-style-type: none;
    padding: 0;
  }
  li {
    margin: 10px 0;
    display: flex;
    align-items: center;
  }
  li.completed span{
    text-decoration: line-through;
    color: gray;
  }
  button {
    margin-left: 10px;
    color: white;
    border: "White";
    padding: 5px 10px;
    cursor: pointer;
    border-radius: 5px;
  }
  button:hover {
    transition: background 0.3s;
    filter: brightness(80%);
    box-shadow: 0 0 10px rgba(255, 255, 255, 0.2);
  }
  #addTodoButton {
    background-color: blue;
  }
  #deleteButton {
    background-color: red;
  }
  body {
    font-family: Roboto, sans-serif;
    margin: 20px;
  }
`;
document.head.appendChild(style);
todoList.scrollIntoView({ behavior: "smooth" });
```
