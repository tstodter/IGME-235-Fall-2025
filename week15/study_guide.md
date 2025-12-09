# IGME-235 Final Exam Study Guide 

## Exam Checklist

**Can you do these from memory?**

* [ ] Explain browser (client) vs web server
* [ ] Say which side sends common HTTP request headers
* [ ] Distinguish block vs inline vs generic container elements
* [ ] Apply multiple CSS classes to one element
* [ ] Navigate relative file paths with `..` and folders
* [ ] Match CSS selector types to examples (type, class, id, universal, pseudo-class)
* [ ] Read basic hex color codes (`#RRGGBB`)
* [ ] Use `getElementById`, `querySelector`, `querySelectorAll`
* [ ] Add a `click` event listener with `addEventListener`
* [ ] Create object literals and simple ES6 classes
* [ ] Explain `let` block scope and truthy/falsy
* [ ] Distinguish primitives vs reference types
* [ ] Use `push`, `pop`, `shift`, `unshift`, `filter`
* [ ] Explain JSON, API keys (high level), CORS issue + simple fix
* [ ] Explain what PixiJS is, what it uses, and what it replaced

**Key Syntax to Memorize:**

* Multiple classes:

  ```html
  <div class="myclass1 myclass2"></div>
  ```
* Generic containers:

  ```html
  <div></div> <!-- block -->
  <span></span> <!-- inline -->
  ```
* Relative link examples:

  ```html
  <!-- index.html -> proj/p2/proj2.html -->
  <a href="proj/p2/proj2.html">Project2</a>

  <!-- proj/p2/proj2.html -> dev/test.html -->
  <a href="../../dev/test.html">Test</a>
  ```
* External stylesheet:

  ```html
  <link rel="stylesheet" type="text/css" href="styles.css" />
  ```
* DOM + style:

  ```js
  document.getElementById("success").style.color = "green";
  ```
* Event listener pattern:

  ```js
  button.addEventListener("click", doStuff);
  ```
* Arrow function with defaults:

  ```js
  let addThem = (x = 0, y = 0) => x + y;
  ```

---

## Web & HTML Essentials

### Client–Server & HTTP Request Headers

* Browser (client) sends HTTP **request** to server.
* Typical request headers (from browser):

  * `Host`, `User-Agent`, `Accept-Language`, `Accept-Encoding`, `Connection`, `Cache-Control`.
* Be able to recognize a list of these as: **sent by the web browser to the server**.

### Block vs Inline & Generic Containers

* **Block-level**: start on new line, full width.

  * Examples: `<div>`, `<p>`, headings, `<header>`, `<main>`, `<footer>`.
* **Inline**: flow within a line.

  * Examples: `<span>`, `<a>`, `<strong>`, `<em>`.
* **Generic containers**:

  * `<div>` = generic block container.
  * `<span>` = generic inline container.

### Multiple Classes

Correct (memorize):

```html
<div class="myclass1 myclass2"></div>
```

---

## CSS Essentials

### Core Selector Types

* **Universal**: `* { ... }` – everything.
* **Type**: `nav { ... }` – all `<nav>` elements.
* **Class**: `.featured { ... }` – elements with `class="featured"`.
* **ID**: `#theme { ... }` – element with `id="theme"`.

### Special Selectors

* **Descendant**: `p strong { ... }` – `<strong>` anywhere inside `<p>`.
* **Child**: `li > span { ... }` – `<span>` directly inside `<li>`.
* **Attribute**: `img[alt="decoration"] { ... }`.
* **Pseudo-class**: `a:hover { ... }`.

### Interaction Pseudo-Class

* `:hover` – activated when mouse is over element.

Example:

```css
button:hover {
  background-color: lightgray;
}
```

### Hex Colors

* Format: `#RRGGBB`.
* Examples to know:

  * `#0000FF` → blue
  * `#FF0000` → red
  * `#00FF00` → green

---

## JavaScript: Core Concepts

### Blocks & `let` Scope

* Blocks use `{ }`.
* `let` is **block-scoped**.

```js
let x = 1;
let y;
if ("Hello") {
  x++;            // x becomes 2
  let y = 1;      // inner y (different variable)
  y++;
}
let z = 1;
console.log(x);   // 2
console.log(y);   // undefined (outer y never assigned)
console.log(z);   // 1
```

### Truthy / Falsy

Falsy values:

* `0`, `""`, `null`, `undefined`, `NaN`, `false`.

```js
if (0) {
  console.log("zero!");
} else {
  console.log("NOT zero!"); // runs
}

if ("false") {
  console.log("true!");    // runs (non-empty string is truthy)
} else {
  console.log("NOT true!");
}
```

### Primitives vs Reference Types

**Primitive example (copy by value):**

```js
let x = "1";
let y = x;
x = "2";
// x: "2"  y: "1"
```

**Array example (reference):**

```js
let x = [1, 2, 3];
let y = [4, 5, 6];
y = x;
x.push(4);
y.push(5);
// x and y are BOTH [1, 2, 3, 4, 5]
```

Be able to predict the final values.

### Array Methods & `filter`

* `push` – add to end.
* `pop` – remove/return last.
* `unshift` – add to beginning.
* `shift` – remove/return first.

`filter` example (know pattern):

```js
let myNumbers = [10, -3, -1, 5.5];
let myNumbers2 = myNumbers.filter(n => n > 3);
```

### Arrow Functions with Defaults

Pattern to know:

```js
let addThem = (x = 0, y = 0) => x + y;
```

---

## Objects & Classes

### Object Literal Pattern

```js
let dog = {
  breed: "poodle",
  left: 0,
  speed: 10,
  move() {
    this.left += this.speed;
  }
};
```

### ES6 Class Pattern

```js
class Amphibian {
  constructor(hungry) {
    this.isHungry = hungry;
  }

  eat() {
    this.isHungry = false;
  }
}
```

---

## DOM & Events

### Selecting Elements

Methods emphasized:

* `document.getElementById("id")`
* `document.querySelector("selector")`
* `document.querySelectorAll("selector")`

### Changing Content & Style

**Turn paragraph text green:**

```html
<p id="success">You did it!</p>
```

```js
document.getElementById("success").style.color = "green";
```

**Change first footer or create fallback:**

```js
let footer = document.querySelector("footer");
if (footer) {
  footer.innerHTML = "End of Page";
} else {
  let p = document.createElement("p");
  p.textContent = "Page not done";
  document.body.appendChild(p);
}
```

### Adding a Click Listener

Given:

```html
<button>Click Me!</button>
```

Pattern:

```js
function doStuff() {
  let h1 = document.createElement("h1");
  h1.textContent = "Final Exam!";
  document.body.appendChild(h1);
}

let button = document.querySelector("button");
button.addEventListener("click", doStuff);
```

---

## Data Basics

### JSON, API Keys

* **JSON** = JavaScript Object Notation, text format for structured data.
* **API key**: identifies the calling app/user; used to track usage and control access.

---

## Bonus: Simple 2×2 Grid

Given:

```html
<div id="mainGrid">
  <header>Page Title</header>
  <nav>Navigation Items</nav>
  <main>Primary Content</main>
  <aside>Sidebar Info</aside>
</div>
```

One simple solution:

```css
#mainGrid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-template-rows: auto auto;
}
```
