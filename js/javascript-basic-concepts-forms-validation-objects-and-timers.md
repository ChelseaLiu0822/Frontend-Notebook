# 📒 JavaScript Basic Concepts: Forms, Validation, Objects, and Timers

## 📋 Form Handling in JavaScript

#### 🔹 Getting and Setting Form Values

To get or set the value of a form field:

```js
document.getElementById("field_id").value
```

#### 🔹 Example: Sum Two Numbers

**HTML**

```html
<input type="text" id="num1"><br>
<input type="text" id="num2"><br>
<input type="text" id="result"><br>
<button id="btn">Calculate</button>
```

**JavaScript**

```js
let btn = document.getElementById("btn");
btn.addEventListener("click", () => {
  let num1 = parseInt(document.getElementById("num1").value);
  let num2 = parseInt(document.getElementById("num2").value);
  document.getElementById("result").value = num1 + num2;
});
```

***

## ✅ Form Validation

#### 🔹 Basic Validation

Check if form fields are empty before submission:

```js
function validate() {
  let name = document.getElementById("name").value;
  if (name === "") {
    alert("Enter Name Field");
    return false;
  }
  return true;
}
```

#### 🔹 Displaying Error Messages Inline

Use dedicated elements for error output:

```html
<p id="name_err" style="color:red;"></p>
```

```js
document.getElementById("name_err").textContent = "Enter Name Field";
```

Clear error messages or prevent re-submission with:

```js
document.getElementById("name_err").textContent = "";
```

***

### ✨ Regular Expression (Regex) Validation

#### 🔹 Example: Validate Name Only Allows Letters and Spaces

```js
let nameRegex = /^[a-zA-Z ]*$/;
if (!nameRegex.test(name)) {
  document.getElementById("name_err").textContent = "Only alphabets allowed in Name";
}
```

Repeat similar logic for validating **email** and **mobile number** using appropriate regex patterns.

***

## 🧱 JavaScript Objects

#### 🔹 Definition

Objects store data as key-value pairs.

```js
let person = {
  firstName: "John",
  lastName: "Cena",
  fullName: function() {
    return this.firstName + " " + this.lastName;
  }
};
```

#### 🔹 Accessing Object Properties & Methods

```js
console.log(person.firstName); // John
console.log(person.fullName()); // John Cena
```

#### 🔹 Modifying Objects

```js
person.gender = "Male";            // Add property
delete person.fullName;            // Delete property
```

#### 🔹 Iterating Over Object

```js
for (let key in person) {
  console.log(person[key]);
}
```

#### 🔹 Get Values as Array

```js
let values = Object.values(person); // ["John", "Cena", "Male"]
```

***

## ⏲ Timers and Intervals

#### 🔹 setTimeout

Runs a function once after a delay.

```js
setTimeout(() => {
  console.log("Runs once after 4 seconds");
}, 4000);
```

#### 🔹 setInterval

Repeats a function at specified intervals.

```js
let timer = setInterval(() => {
  console.log("Runs every 3 seconds");
}, 3000);
```

#### 🔹 clearInterval

Stops a repeating interval.

```js
clearInterval(timer);
```

***

## ⌛ Stopwatch Example

**HTML**

```html
<p id="timer">0</p>
<button id="start">Start</button>
<button id="stop">Stop</button>
```

**JavaScript**

```js
let count = 0;
let timerId;
let timer = document.getElementById("timer");

document.getElementById("start").addEventListener("click", () => {
  count = 0;
  timerId = setInterval(() => {
    timer.innerHTML = ++count;
  }, 1000);
});

document.getElementById("stop").addEventListener("click", () => {
  clearInterval(timerId);
});
```

***

### 📝 Assignments

#### 🔹 Task 1: Registration Form

Create a registration form with:

* Fields: name, email, mobile, password, confirm password
* Validations:
  * All fields must be filled
  * Valid email format
  * Mobile number should be digits only
  * Passwords must match
  * Use **regex** for validation

{% embed url="https://codepen.io/ChelseaLiu0822/embed/raaKygb?default-tab=html,result" %}

#### 🔹 Task 2: Image Slider

* Create an image slider using `setInterval`
* Change images every 3 or 4 seconds automatically

