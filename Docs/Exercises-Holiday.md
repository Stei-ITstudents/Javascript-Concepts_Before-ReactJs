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

```
