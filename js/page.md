# Page

## 📘 JavaScript ES6+ and Asynchronous Programming

### 🌐 Asynchronous JavaScript

#### 🌀 What is Asynchronous Programming?

* **Synchronous**: Executes line-by-line. Waits for one task to complete before starting the next.
* **Asynchronous**: Executes tasks without waiting. Allows multiple operations at once without blocking the main thread.

***

### 🔁 Callbacks

#### ➤ Definition

* A **callback** is a function passed as an argument to another function, executed after the main function completes.
* Used to handle asynchronous operations like loading data, timers, or fetching from an API.

#### ➤ Example

```html
<h2>Callback example</h2>
<script>
function mainFunction(callback){
  console.log("Perform Operation...");
  setTimeout(() => {
    callback("Task Completed!");
  }, 2000);
}

function callbackFunction(result){
  console.log(`Result: ${result}`);
}

mainFunction(callbackFunction);
</script>
```

#### ➤ Real-World Scenario: Nested Callbacks

```js
// Example: Handle 3 async operations in nested callbacks
getUser(101, (user) => {
  getServices(user, (services) => {
    getServiceCost(services, (cost) => {
      console.log(`The service cost is ${cost}`);
    });
  });
});
```

#### ➤ Callback Hell

* Deeply nested callbacks are hard to manage.
* Known as **"callback hell"** or **"pyramid of doom"**.
* To solve this, JavaScript introduced **Promises** in ES6.

***

### 🔮 Promises

#### ➤ What is a Promise?

A promise is an object that represents the eventual result of an asynchronous operation.

#### ➤ Promise States

1. **Pending**: Initial state.
2. **Resolved**: Operation successful.
3. **Rejected**: Operation failed.

> ✅ Promises return a value (either resolved or rejected).\
> ❌ Promises are not cancellable once initiated.

#### ➤ Syntax

```js
let promise = new Promise((resolve, reject) => {
  let age = 23;
  if (age > 18) {
    resolve("Eligible");
  } else {
    reject("Not Eligible");
  }
});

promise
  .then((res) => console.log(res))
  .catch((err) => console.log(err));
```

#### ➤ Real Example Using Promises

```js
function getUser(id) {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve({ userId: id, username: "John" });
    }, 2000);
  });
}

function getServices(user) {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve(["A", "B", "C", "D"]);
    }, 4000);
  });
}

function getServiceCost(services) {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve(services.length * 500);
    }, 6000);
  });
}

// Promise chaining
getUser(101)
  .then((user) => getServices(user))
  .then((services) => getServiceCost(services))
  .then((cost) => console.log(`The service cost is ${cost}`))
  .catch((err) => console.log(err));
```

***

### 🌍 Fetch API

#### ➤ What is Fetch?

`fetch()` is used to retrieve resources from a server. It returns a **Promise**.

#### ➤ Syntax

```js
fetch(url)
  .then(res => res.json())
  .then(data => console.log(data))
  .catch(err => console.log(err));
```

#### ➤ Options

| Property | Description                         |
| -------- | ----------------------------------- |
| method   | HTTP method: GET, POST, PUT, DELETE |
| headers  | Custom headers like Content-Type    |
| body     | Request payload (used in POST/PUT)  |

***

#### ➤ Example: Consuming JSONPlaceholder API

```js
const URL = "https://jsonplaceholder.typicode.com/posts";
fetch(URL)
  .then(res => res.json())
  .then(data => {
    data.forEach(post => {
      console.log(post.title, post.body);
    });
  })
  .catch(err => console.log(err));
```

#### ➤ DOM Rendering Example

```html
<button id="btn">Fetch Posts</button>
<div id="target"></div>

<script>
document.getElementById("btn").addEventListener("click", () => {
  const URL = "https://jsonplaceholder.typicode.com/posts";
  fetch(URL)
    .then(res => res.json())
    .then(data => {
      let str = "";
      data.forEach(post => {
        str += `<h4>${post.title}</h4><p>${post.body}</p><hr>`;
      });
      document.getElementById("target").innerHTML = str;
    })
    .catch(err => console.log(err));
});
</script>
```

***

### 📌 Task

> 🔧 **Assignment**:\
> Consume all JSONPlaceholder APIs and render their data in the DOM.\
> URL: [https://jsonplaceholder.typicode.com](https://jsonplaceholder.typicode.com/)

以下是根据你提供的截图和完整课堂录音整理的**GitBook格式英文笔记**，包含所有讲解内容，结构清晰、覆盖全面：

***

## JavaScript CRUD Application & Async/Await (with `json-server`)

### 1. Introduction to Async/Await

#### What is Async/Await?

* Async/Await is used to handle asynchronous operations in a more synchronous-looking and readable way.
* It is based on **Promises**.

#### Key Concepts

* `async` keyword:
  * If used before a function, the function **returns a Promise**.
* `await` keyword:
  * Used **inside async functions** to wait for a Promise to resolve.

#### Syntax Example

```javascript
const functionName = async () => {
  await somePromise;
};
```

* The code inside appears synchronous but runs asynchronously.

***

### 2. CRUD Application with `json-server`

#### What is `json-server`?

* A **Node.js module** that simulates a REST API using a JSON file.
* Used for quick prototyping and front-end testing.
* Supports all CRUD operations: GET, POST, PUT, DELETE.

#### Installation

```bash
npm i json-server -g
```

#### Create `products.json`

Create a `server` folder and add the following file:

```json
{
  "products": [
    { "id": 1, "name": "A", "price": 4567, "quantity": 7 },
    { "id": 2, "name": "B", "price": 5567, "quantity": 6 },
    { "id": 3, "name": "C", "price": 6567, "quantity": 7 }
  ]
}
```

#### Run Server

```bash
json-server --watch products.json --port 3001
```

* Access the endpoint at `http://localhost:3001/products`
* You can test GET endpoints directly in the browser.

***

### 3. Frontend: Fetch & Render Products

#### IIFE with Async/Await

```javascript
(async () => {
  const URL = "http://localhost:3001/products";
  const target = document.getElementById("target");

  try {
    let res = await fetch(URL);
    let data = await res.json();
    console.log(data);

    let str = "";
    data.forEach((pro) => {
      str += `
        <div class="col-sm-4">
          <div class="card">
            <h4>${pro.name}</h4>
            <p>Price : Rs.${pro.price}<br>Quantity : ${pro.quantity}</p>
            <button class="btn btn-danger" onclick="delPro(${pro.id})">Delete</button>
          </div>
        </div>
      `;
    });
    target.innerHTML = str;
  } catch (err) {
    console.log("Error: " + err);
  }
})();
```

***

### 4. Delete Product

#### Delete Handler

```javascript
async function delPro(id) {
  if (confirm("Do you want to delete?")) {
    try {
      let res = await fetch(`${URL}/${id}`, {
        method: "DELETE"
      });
      let data = await res.json();
      alert("Product deleted");
      window.location.reload();
    } catch (err) {
      console.log("Error: " + err);
    }
  }
}
```

***

### 5. Add Product Page

#### HTML Form

```html
<h2>Add Product</h2>
<input type="text" id="name" class="form-control" placeholder="Name" required>
<input type="number" id="price" class="form-control" placeholder="Price" required>
<input type="number" id="quantity" class="form-control" placeholder="Quantity" required>
<button class="btn btn-success" onclick="addProduct()">Add</button>
```

#### Add Product Function

```javascript
async function addProduct() {
  let name = document.getElementById("name").value;
  let price = document.getElementById("price").value;
  let quantity = document.getElementById("quantity").value;

  let formData = { name, price, quantity };

  try {
    let res = await fetch(URL, {
      method: "POST",
      body: JSON.stringify(formData),
      headers: { "Content-Type": "application/json" }
    });
    let data = await res.json();
    alert("Product added");
    location.href = "./index.html";
  } catch (err) {
    console.log("Error: " + err);
  }
}
```

* `json-server` auto-generates an `id` for new products.
* Be careful: sometimes IDs may be malformed (`BAD`) due to testing limitations.

***

### 6. Real-Time Behavior Notes

* `json-server` is **not production-grade**, but useful for testing and frontend training.
* If you use a `<form>` with method `POST`, it may reload the page before JS executes.
  * **Use buttons with `onclick` handlers instead.**
* To prevent form reload, use `event.preventDefault()` in a submit handler.

***

### 7. Homework Task (Assigned)

> Add an **Edit Feature**:

* Clicking an "Edit" button should open a pre-filled form.
* On clicking “Update”, send a PUT request to update the product.



