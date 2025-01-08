# Vacanta Exercitii

---

## **1. Evenimente de bază**

a. Creează un buton care schimbă textul unui element `<p>` la click.  
b. Adaugă un câmp de input text care afișează valoarea introdusă într-un `<div>` în timp real (folosește evenimentul `input`).  
c. Creează un buton care adaugă o clasă CSS unui `<div>` pentru a-i schimba culoarea fundalului.  
d. Creează un buton care adaugă un element `<li>` într-o listă `<ul>` goală la fiecare click. Textul va fi „Item x", unde `x` este numărul curent de elemente.

---

## **2. Manipularea DOM dinamică**

a. Creează o galerie de imagini mici (thumbnails). La click pe o imagine, aceasta se afișează mărită într-o zonă de previzualizare.  
b. Creează un tabel HTML simplu și un buton care adaugă un rând gol la fiecare click.  
c. Creează un formular simplu cu două câmpuri și un buton de submit. La trimitere, afișează datele introduse într-un `<div>`.

---

## **3. Gestionarea mai multor evenimente**

a. Creează o zonă de text (`<textarea>`) care afișează numărul curent de caractere introduse, la fiecare apăsare de tastă.  
b. Creează un `<div>` care își schimbă culoarea fundalului la click pe un buton și revine la culoarea inițială când treci cu mouse-ul peste el.  
c. Creează două butoane: unul care dezactivează celălalt buton și unul care îl reactivează.

---

## **4. Delegarea evenimentelor**

a. Creează o listă dinamică. La click pe un element `<li>`, acesta este eliminat (folosește delegarea evenimentelor).  
b. Creează un buton care adaugă rânduri într-un tabel. La click pe o celulă, aceasta devine editabilă.

---

## **5. Evenimente complexe și prevenirea acțiunilor implicite**

a. Creează un link care, la click, afișează un mesaj într-un `<div>` fără a naviga la URL (folosește `preventDefault`).  
b. Creează un formular cu un câmp de email. Dacă emailul nu este completat corect, afișează o eroare și împiedică trimiterea formularului (folosește `submit` și `preventDefault`).

---

## **6. Evenimente de mouse și tastatură**

a. Creează un `<div>` care își schimbă poziția în funcție de mișcarea mouse-ului (`mousemove`).  
b. Creează un buton care afișează ce buton al mouse-ului a fost apăsat (stânga, mijloc, dreapta).  
c. Creează o funcționalitate care mută un `<div>` pe ecran cu săgețile tastaturii (`ArrowUp`, `ArrowDown`, `ArrowLeft`, `ArrowRight`).

---

## **7. Timers și evenimente combinate**

a. Creează un buton „Start" care pornește un cronometru într-un `<span>` și un buton „Stop" care îl oprește.  
b. Creează o bară de progres care se umple treptat în 5 secunde la apăsarea unui buton.

---

## **8. Evenimente personalizate**

a. Creează un element care reacționează la un eveniment personalizat (`myCustomEvent`) schimbându-și textul. Apelează evenimentul din JavaScript.

---

## **9. Drag & Drop**

a. Creează o funcționalitate de drag-and-drop pentru a muta un `<div>` între două zone.  
b. Creează o zonă de „drop" care acceptă doar un anumit element (identificat prin clasă sau ID) și afișează un mesaj de succes.

---

## **10. Interacțiuni și efecte**

a. Creează un meniu dropdown care se deschide și se închide la click.  
b. Creează un acordion în care secțiunile de conținut se extind/restrâng la click.  
c. Creează o animație simplă: un buton care mută un `<div>` dintr-o parte în alta a ecranului.

---

## **1**

a. Creează un buton care schimbă textul unui element `<p>` la click.

```js
const button = document.createElement("button");
button.textContent = "Click me!";
document.body.appendChild(button);

const paragraph = document.createElement("p");
paragraph.textContent = "Text initial";
document.body.appendChild(paragraph);

button.addEventListener("click", () => {
  paragraph.textContent = "Text schimbat";
});
paragraph.scrollIntoView({ behavior: "smooth" });
```

b. Adaugă un câmp de input text care afișează valoarea introdusă într-un `<div>` în timp real (folosește evenimentul `input`).

```js
const input = document.createElement("input");
document.body.appendChild(input);

const div = document.createElement("div");
div.textContent = "Enter some value";
div.style.marginLeft = "10px";
document.body.appendChild(div);

input.addEventListener("input", () => {
  div.textContent = "The imput value is: " + input.value;
});
div.scrollIntoView({ behavior: "smooth" });
```

c. Creează un buton care adaugă o clasă CSS unui `<div>` pentru a-i schimba culoarea fundalului.

```js
const button = document.createElement("button");
button.textContent = "Schimba culoare";
document.body.appendChild(button);

const div = document.createElement("div");
div.style.width = "115px";
div.style.height = "50px";
div.classList.add("blue");
document.body.appendChild(div);

const style = document.createElement("style");
style.textContent = `
    .blue {
        background-color: blue;
    }
    .red {
    background-color: red;
    }
`;
document.head.appendChild(style);

button.addEventListener("click", () => {
  div.classList.toggle("red");
});
div.scrollIntoView({ behavior: "smooth" });
```

d. Creează un buton care adaugă un element `<li>` într-o listă `<ul>` goală la fiecare click. Textul va fi „Item x", unde `x` este numărul curent de elemente.

```js
const button = document.createElement("button");
button.textContent = "Adauga item";
document.body.appendChild(button);

const ul = document.createElement("ul");
document.body.appendChild(ul);

let count = 0;

button.addEventListener("click", () => {
  count++;
  const li = document.createElement("li");
  li.textContent = "Item " + count;
  ul.appendChild(li);
});
ul.scrollIntoView({ behavior: "smooth" });
```

---

## **2**

a. Creează o galerie de imagini mici (thumbnails). La click pe o imagine, aceasta se afișează mărită într-o zonă de previzualizare.

```js
const images = [
  "https://raw.githubusercontent.com/CristyNel/CristyNel/main/assets/Cristy_code.gif",
  "https://raw.githubusercontent.com/Stei-ITstudents/go-auth/main/web/static/img/Screenshots/auth_development.png",
  "https://raw.githubusercontent.com/Stei-ITstudents/go-auth/main/web/static/img/go_mysql_server.png",
];

const thumbnails = document.createElement("div");
document.body.appendChild(thumbnails);

const preview = document.createElement("img");
preview.style.width = "600px";
document.body.appendChild(preview);

images.forEach((src) => {
  const img = document.createElement("img");
  img.src = src;
  img.style.width = "100px";
  img.style.marginRight = "50px";
  thumbnails.appendChild(img);

  img.addEventListener("click", () => {
    preview.src = src;
  });
});
preview.scrollIntoView({ behavior: "smooth" });
```

b. Creează un tabel HTML simplu și un buton care adaugă un rând gol la fiecare click.

```js
const button = document.createElement("button");
button.textContent = "Adauga rand";
document.body.appendChild(button);

const table = document.createElement("table");
table.style.borderCollapse = "collapse";
document.body.appendChild(table);

button.addEventListener("click", () => {
  const tr = document.createElement("tr");
  const td1 = document.createElement("td");
  const td2 = document.createElement("td");
  td1.style.border = "1px solid red";
  td2.style.border = "1px solid red";
  td1.style.width = "200px";
  td2.style.width = "200px";
  td1.style.height = "40px";
  td2.style.height = "40px";
  tr.appendChild(td1);
  tr.appendChild(td2);
  table.appendChild(tr);
  table.scrollIntoView({ behavior: "smooth" });
});

button.scrollIntoView({ behavior: "smooth" });
```

c. Creează un formular simplu cu două câmpuri și un buton de submit. La trimitere, afișează datele introduse într-un `<div>`.

```js
const form = document.createElement("form");
document.body.appendChild(form);

const input1 = document.createElement("input");
input1.type = "text";
form.appendChild(input1);

const input2 = document.createElement("input");
input2.type = "text";
form.appendChild(input2);

const button = document.createElement("button");
button.textContent = "Trimite";
form.appendChild(button);

const div = document.createElement("div");
document.body.appendChild(div);

form.addEventListener("submit", (e) => {
  e.preventDefault();
  div.innerText = `1) : ${input1.value}\n2) : ${input2.value}`;
  div.scrollIntoView({ behavior: "smooth" });
});
button.scrollIntoView({ behavior: "smooth" });
```

---

## **3**

a. Creează o zonă de text (`<textarea>`) care afișează numărul curent de caractere introduse, la fie
care apăsare de tastă.

```js
const div = document.createElement("div");
div.textContent = "Numarul de caractere: 0";
document.body.appendChild(div);

const textarea = document.createElement("textarea");
textarea.style.width = "300px";
textarea.style.height = "100px";
textarea.placeholder = "Introdu text aici";
document.body.appendChild(textarea);

textarea.addEventListener("input", () => {
  div.textContent = `Numarul de caractere: ${textarea.value.length}`;
});
textarea.scrollIntoView({ behavior: "smooth" });
```

b. Creează un `<div>` care își schimbă culoarea fundalului la click pe un buton și revine la culoarea inițială când treci cu mouse-ul peste el.

```js
const button = document.createElement("button");
button.textContent = "Schimba culoare";
document.body.appendChild(button);

const div = document.createElement("div");
div.style.width = "140px";
div.style.height = "80px";
div.classList.add("blue");
document.body.appendChild(div);

const style = document.createElement("style");
style.textContent = `
    .blue {
    background-color: blue;
    }
    .red {
    background-color: red;
    }
`;
document.head.appendChild(style);

button.addEventListener("click", () => {
  div.classList.toggle("red");
});

div.addEventListener("mouseover", () => {
  div.classList.toggle("red");
});

div.scrollIntoView({ behavior: "smooth" });
```

c. Creează două butoane: unul care dezactivează celălalt buton și unul care îl reactivează.

```js
const button1 = document.createElement("button");
button1.textContent = "Button";
document.body.appendChild(button1);

const button2 = document.createElement("button");
button2.textContent = "Button";
document.body.appendChild(button2);

button1.addEventListener("click", () => {
  if (button2.disabled) {
    button2.disabled = false;
  } else {
    button2.disabled = true;
  }
});

button2.addEventListener("click", () => {
  if (button1.disabled) {
    button1.disabled = false;
  } else {
    button1.disabled = true;
  }
});

const style = document.createElement("style");
style.textContent = `
  button {
    border-radius: 5px;
  }
`;
document.head.appendChild(style);

button2.scrollIntoView({ behavior: "smooth" });
```

---

## **4**

a. Creează o listă dinamică. La click pe un element `<li>`, acesta este eliminat (folosește delegarea evenimentelor).

```js
const ul = document.createElement("ul");
document.body.appendChild(ul);

for (let i = 1; i <= 5; i++) {
  const li = document.createElement("li");
  li.textContent = `Item ${i}`;
  ul.appendChild(li);
}

ul.addEventListener("click", (e) => {
  if (e.target.tagName === "LI") {
    e.target.remove();
  }
});

ul.scrollIntoView({ behavior: "smooth" });
```

b. Creează un buton care adaugă rânduri într-un tabel. La click pe o celulă, aceasta devine editabilă.

```js
const button = document.createElement("button");
button.textContent = "Adauga rand";
document.body.appendChild(button);

const table = document.createElement("table");
table.style.borderCollapse = "collapse";
document.body.appendChild(table);

button.addEventListener("click", () => {
  const tr = document.createElement("tr");
  const td1 = document.createElement("td");
  const td2 = document.createElement("td");
  tr.appendChild(td1);
  tr.appendChild(td2);
  table.appendChild(tr);
  table.scrollIntoView({ behavior: "smooth" });
});

table.addEventListener("click", (e) => {
  if (e.target.tagName === "TD") {
    e.target.contentEditable = true;
  }
});

const style = document.createElement("style");
style.textContent = `
  table td{
    padding-left: 10px;
    border: 2px solid red;
    width: 200px;
    height: 25px;
  }
`;
document.head.appendChild(style);

button.scrollIntoView({ behavior: "smooth" });
```
