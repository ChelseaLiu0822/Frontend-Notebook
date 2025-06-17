# Styling and Routing in React.js

## Applying Styles in React.js

React provides multiple ways to apply CSS:

#### 1.1 Inline Styles

* Use `style={{}}` syntax in JSX.
* Must use double curly braces: outer `{}` for JSX expression, inner `{}` for JavaScript object.

```jsx
<p style={{ color: 'red' }}>Text in red</p>
```

Example in component:

```jsx
<h2 style={{ color: 'green' }}>Welcome to Mern Training</h2>
```

Alternative:

```jsx
const styles = { color: 'green' };
<h2 style={styles}>Welcome to Mern Training</h2>
```

#### 1.2 Using CSS Classes

* Use `className` instead of `class` (as per JSX syntax).

```jsx
<div className="container">...</div>
```

### 2. Integrating Bootstrap in React.js

#### 2.1 Using CDN (in `public/index.html`)

* Add `<link>` and `<script>` for Bootstrap CSS and JS:

```html
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
```

#### 2.2 Installing via NPM

```bash
npm i bootstrap --save
```

Then import in `index.js`:

```js
import "bootstrap/dist/css/bootstrap.min.css";
import "bootstrap/dist/js/bootstrap.bundle";
```

Use Bootstrap classes like:

```jsx
<div className="container">
  <button className="btn btn-success">Success</button>
  <button className="btn btn-danger">Danger</button>
</div>
```

### 3. React Router (v6)

#### 3.1 Installation

```bash
npm i react-router-dom --save
```

#### 3.2 Main Components

* `BrowserRouter`: Top-level router
* `Routes`: Container for route definitions
* `Route`: Individual route
* `Link`: For navigation (replaces `<a>`)
* `Outlet`: For rendering nested routes

#### 3.3 Defining Routes

```jsx
import { BrowserRouter as Router, Routes, Route } from "react-router-dom";
import Home from "./components/Home";
import About from "./components/About";
import Counter from "./components/Counter";

<Router>
  <Routes>
    <Route path="/" element={<Home />} />
    <Route path="about" element={<About />} />
    <Route path="counter" element={<Counter />} />
  </Routes>
</Router>
```

#### 3.4 Navigation with `Link`

```jsx
import { Link } from "react-router-dom";

<nav>
  <Link to="/">Home</Link>
  <Link to="/about">About</Link>
  <Link to="/counter">Counter</Link>
</nav>
```

### 4. Layout and Components

#### Component Structure

```
src/
├── components/
│   ├── Home.jsx
│   ├── About.jsx
│   ├── Counter.jsx
│   ├── Gallery.jsx
│   ├── Contact.jsx
│   └── Nav.jsx
```

#### Example Component (`Gallery.jsx`)

```jsx
const Gallery = () => {
  return <h2>Gallery Page</h2>;
};
export default Gallery;
```

#### Example Layout with Router

```jsx
import { BrowserRouter as Router, Routes, Route } from "react-router-dom";
import Home from "./components/Home";
import About from "./components/About";
import Contact from "./components/Contact";
import Gallery from "./components/Gallery";
import Nav from "./components/Nav";

const App = () => {
  return (
    <main>
      <Router>
        <Nav />
        <section className="container">
          <Routes>
            <Route path="/" element={<Home />} />
            <Route path="about" element={<About />} />
            <Route path="gallery" element={<Gallery />} />
            <Route path="contact" element={<Contact />} />
          </Routes>
        </section>
      </Router>
    </main>
  );
};

export default App;
```

### 5. Handling 404 (Not Found) Routes

```jsx
import NotFound from "./components/NotFound";

<Route path="*" element={<NotFound />} />
```

### 6. Nested Routing Example

#### Sidebar Navigation (e.g., inside `Contact.jsx`)

```jsx
import { Link, Outlet } from "react-router-dom";

const Contact = () => (
  <div className="row">
    <div className="col-3">
      <ul>
        <li><Link to="india">India</Link></li>
        <li><Link to="usa">USA</Link></li>
        <li><Link to="china">China</Link></li>
      </ul>
    </div>
    <div className="col">
      <Outlet />
    </div>
  </div>
);

export default Contact;
```

#### Defining Nested Routes in App

```jsx
<Route path="contact" element={<Contact />}>
  <Route path="india" element={<India />} />
  <Route path="usa" element={<Usa />} />
  <Route path="china" element={<China />} />
</Route>
```

#### Nested Components Example (`India.jsx`)

```jsx
const India = () => <h3>India Office</h3>;
export default India;
```

***

Let me know if you want a downloadable Markdown or PDF version!
