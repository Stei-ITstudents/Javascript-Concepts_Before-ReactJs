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

// Exercise > Create a chronometer

// Exercise > Create a calculator
