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
