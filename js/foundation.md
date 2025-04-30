# 🧱 Foundation

## Editor

#### Ways to Add JavaScript to HTML

1.  **Inline**

    ```html
    <button onclick="alert('Hello')">Click Me</button>
    ```
2.  **Internal Script**

    ```html
    <script>
      alert("Welcome to JavaScript");
    </script>
    ```
3.  **External Script**

    ```html
    <script src="script.js"></script>
    ```

* Best practice: use external scripts for reusability and separation of concerns.

## Data Type

There are **primitive types** and **Object**.

The primitive type includes **Number, Boolean, String, Null, Undefined, Symbol, and BigInt**.

Object includes Array, Object, etc.

## Declaration

#### `var`, `let`, and `const`

| Keyword | Scope    | Reassignable | Hoisting      |
| ------- | -------- | ------------ | ------------- |
| `var`   | Function | ✅            | ✅ (undefined) |
| `let`   | Block    | ✅            | ❌             |
| `const` | Block    | ❌            | ❌             |

```js
var x = 10;
let y = 20;
const z = 30;
```

* `let` and `const` are introduced in **ES6**.
* `const` variables cannot be reassigned.

> “Always try to use `let` and `const` instead of `var`.”

***

## BOM Pop-Up Methods

Part of the **Browser Object Model (BOM)**, used for user interaction:

* `prompt()`: Accepts user input as a **string** at runtime.
* `alert()`: Displays message in a **dialog box**.
* `confirm()`: Used to confirm actions like deletion (`OK` / `Cancel`).

***

## Functions in JavaScript

#### 3 Ways to Define Functions

1. **Traditional Function**

```javascript
function add(a, b) {
  return a + b;
}
```

2. **Function Expression**

```javascript
const add = function(a, b) {
  return a + b;
}
```

3. **Arrow Function (ES6)**

```javascript
const add = (a, b) => a + b;
```

#### Calling Functions

```javascript
alert(`The sum is ${add(10, 49)}`);
```

***

Here are the **GitBook-style notes** based strictly on your uploaded screenshots and the transcribed recording, without integrating any other prior content:

## Event Handling in JavaScript

#### 🔹 What are Events?

Events trigger specific actions in response to user interaction or browser behavior. Examples include clicking, hovering, typing, etc.

#### 🔹 Common Events

* `onclick`
* `ondblclick`
* `onmouseover`
* `onmouseout`
* `onkeyup`
* `onkeydown`
* `onkeypress`
* `onblur`
* `onfocus`
* `onchange`
* `onload`
* `onsubmit`
* `onscroll`

#### 🔹 Example Function

```js
function changeBgColor(value) {
  document.bgColor = value;
}
```

#### 🔹 How to Use Events

```html
<body onload="changeBgColor('purple')">
  <button onclick="changeBgColor('red')">Red</button>
  <button onmouseover="changeBgColor('green')" onmouseout="changeBgColor('white')">Hover</button>
</body>
```

***

## Built-in JavaScript Methods

#### 📦 Array Methods

```js
let arr = [2, 3, 4, 5, 6, 7, 8, 9];
console.log(arr);
```

**Push / Pop**

```js
arr.push(99);    // Add to end
arr.pop();       // Remove from end
```

**Shift / Unshift**

```js
arr.shift();     // Remove from start
arr.unshift(1);  // Add to start
```

**Includes**

```js
arr.includes(4);  // true or false
```

#### 🔗 Resources

* [MDN: Array Methods](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)
* [MDN: String Methods](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)

#### 🕒 Date Methods

```js
let d = new Date();
d.getHours();
d.getMinutes();
d.getSeconds();
```

#### ➗ Math Methods

```js
Math.sqrt(16);   // Square root
Math.pow(2, 3);  // Power
```

***

## The DOM (Document Object Model)

#### 🔹 What is the DOM?

* DOM = Document Object Model
* A tree-like structure representing HTML elements as nodes.
* DOM allows **runtime manipulation** of page content using JavaScript.

#### 🔹 Purpose

* Add, remove, or modify elements/content/styles dynamically.
* JavaScript manipulates the DOM via built-in methods.

#### 🔹 Tree Structure Example

```
Document
└── HTML
    ├── Head
    │   └── Title
    └── Body
        └── h1
```

***

### Accessing DOM Elements

#### By ID (most common)

```js
document.getElementById("myId");
```

#### By Class / Tag / Name

```js
document.getElementsByClassName("className"); // returns HTMLCollection
document.getElementsByTagName("tag");         // returns HTMLCollection
document.getElementsByName("name");           // returns NodeList
```

***

### Manipulating DOM Elements

#### Set/Get HTML Content

```js
element.innerHTML = "New content";
```

#### Set/Get Text Content

```js
element.textContent = "New text";
```

#### Dynamic Styling

```js
element.style.color = "green";
```

***

### 🛠 Practical Examples

#### Example 1: Update Paragraph on Button Click

```html
<p id="target">Lorem ipsum</p>
<button id="btn">Perform</button>
```

```js
let btn = document.getElementById("btn");
let para = document.getElementById("target");

btn.addEventListener("click", () => {
  let data = para.innerHTML;
  alert(data);
  para.innerHTML = "Hello! We are learning JavaScript";
  para.style.color = "green";
});
```

***

#### Example 2: Create Elements Dynamically

```html
<ul id="menu"></ul>
<button id="btn">Create List</button>
```

```js
let btn = document.getElementById("btn");
let menu = document.getElementById("menu");

let categories = ["Men", "Women", "Kids"];

btn.addEventListener("click", () => {
  categories.forEach(cat => {
    let li = document.createElement("li");
    li.textContent = cat;
    menu.appendChild(li);
  });
});
```

***

### ✅ Assignment

* Practice using different JavaScript event types.
* Explore and test predefined array, string, math, and date methods.
* Review DOM structure and practice accessing and modifying elements.
* Create dynamic content using `createElement()` and `appendChild()`.









