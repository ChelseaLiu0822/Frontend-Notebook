# Introduction to React.js

## What is React?

React.js is an **open-source**, **cross-platform** JavaScript library developed and maintained by **Facebook**. It is used for building **User Interfaces (UI)**, particularly the **front-end** of applications.

* **View Layer**: React serves as the view (presentation) layer in the MVC architecture.
* **SPA Support**: With React, developers can build **Single Page Applications (SPA)**, where the content updates dynamically without refreshing the whole page.

***

## Features of React.js

* **Component-Based Architecture**\
  React applications are composed of reusable components. This structure makes code more **manageable, scalable, and reusable**.
*   **JSX (JavaScript Syntax Extension)**\
    JSX allows writing **HTML within JavaScript**. This makes the code cleaner and easier to read.

    > ❗ Browsers do **not support JSX** directly.\
    > React uses a **transpiler called Babel** to convert JSX into regular JavaScript before it is executed by the browser.
* **Virtual DOM**\
  React uses a **virtual DOM** to boost performance:
  * On first load, the virtual DOM takes a copy of the real DOM.
  * When updates occur, React compares the new virtual DOM with the previous one.
  * Only the parts that changed are re-rendered in the real DOM.
  * This results in **faster and more efficient UI updates**.

***

## Setting Up React Environment

#### 1. Install Node.js

* Go to [https://nodejs.org](https://nodejs.org/) and download/install the latest version based on your OS (Windows/Linux/Mac).

#### 2. Check Node.js Installation

Open a terminal or command prompt and run:

```bash
node -v
```

#### 3. Create a React Application

**Option 1: Using Create React App (CRA)**

```bash
npx create-react-app appname
```

**Option 2: Using Vite**

```bash
npm create vite@latest appname
```

* You will be prompted to choose a framework → select `React`
* Then choose `JavaScript` or `TypeScript`

#### 4. Install Dependencies (for Vite)

Navigate into the project directory:

```bash
cd appname
npm install
```

***

## Running a React Application

To start the React development server, run:

```bash
npm start
```

This will start the app at [http://localhost:3000](http://localhost:3000/) by default.

***

## Folder Structure Overview

#### 1. `node_modules/`

* Contains all the third-party packages used in the project.

#### 2. `public/`

* Static assets are stored here (e.g., images).
* `index.html`: The **single HTML file** for the SPA.

#### 3. `src/`

Contains all source files and components:

| File          | Purpose                      |
| ------------- | ---------------------------- |
| `index.js`    | Entry point of the React app |
| `App.js`      | Default component            |
| `App.css`     | Styles for `App` component   |
| `App.test.js` | Testing file for `App`       |
| `index.css`   | Main CSS for global styles   |

#### 4. `package.json`

* Lists project dependencies and scripts (`start`, `build`, `test`, etc.).

#### 5. `package-lock.json`

* Locks the versions of dependencies for consistency across installs.

***

## How React App Bootstraps

1. `public/index.html` contains:

```html
<div id="root"></div>
```

2. `src/index.js` renders the root component:

```js
const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);
```

3. This mounts the `App` component into the `<div id="root"></div>` in `index.html`.
4. Modifying `App.js`:

```js
function App() {
  return (
    <div>
      <h2>Welcome to React Training</h2>
    </div>
  );
}
```

When saved, the browser auto-updates the UI without reloading the whole page.

