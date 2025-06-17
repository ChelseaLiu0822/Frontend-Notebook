# React Components, Props, State, and Rendering

## Introduction to Components

* **Component**: Core building block of a React application.
  * Used for **reusability**.
  * Helps to **separate UI into smaller pieces** of code.

### Types of Components

* **Class Component**:
  * Used **before React 16.8**.
  * Was necessary because function components couldn't manage state or hooks.
* **Function Component** (recommended after React 16.8):
  * More readable, compact, and better performance.
  *   Syntax:

      ```js
      function ComponentName() {
        return (
          <div>
            // UI
          </div>
        );
      }
      ```

      Or:

      ```js
      const ComponentName = function() {
        return (
          <div>
            // UI
          </div>
        );
      }
      ```

      Or (preferred):

      ```js
      const ComponentName = () => {
        return (
          <div>
            // UI
          </div>
        );
      };
      ```

### Using Components

*   Example:

    ```js
    const Home = () => {
      return (
        <div>
          <h2>Home Page</h2>
        </div>
      );
    };
    export default Home;
    ```
*   To use a component in another component:

    ```js
    import Home from './Home';

    function App() {
      return (
        <div>
          <Home />
        </div>
      );
    }
    ```

## Dynamic Data Rendering

*   Render variables using `{}` in JSX:

    ```js
    const title = "My Home Page";
    const obj = { name: "sumit", age: 35 };

    return (
      <div>
        <h2>{title}</h2>
        <p>{obj.name} is {obj.age}</p>
      </div>
    );
    ```
*   Render arrays using `.map()`:

    ```js
    const courses = ["Angular", "React", "Node"];
    return (
      <ul>
        {courses.map((val, ind) => (
          <li key={ind}>{val}</li>
        ))}
      </ul>
    );
    ```
* **Note**: Always add a unique `key` prop when rendering lists to avoid warnings.

### Conditional Rendering

*   **Using Logical `&&` Operator**:

    ```js
    {errMsg !== "" && <p>{errMsg}</p>}
    ```
*   **Using Ternary Operator**:

    ```js
    {courses.length > 0 ? (
      <>
        <h4>Courses</h4>
        <ul>
          {courses.map((val, ind) => <li key={ind}>{val}</li>)}
        </ul>
      </>
    ) : (
      <p>No courses found</p>
    )}
    ```
* **Note**: If rendering multiple elements conditionally, use `<></>` (React Fragment) or a parent element to wrap them.

### Props

* Props (short for **properties**) allow you to pass data from a **parent component** to a **child component**.
* Props are **read-only**.
*   Example (in App.js):

    ```js
    const heading = "Ecommerce Project";
    const category = ["mens", "womens", "kids"];

    <About heading={heading} category={category} />
    ```

#### Reading Props

1.  **Using props object**:

    ```js
    const About = (props) => {
      return (
        <>
          <h2>{props.heading}</h2>
          <ul>
            {props.category.map((val, ind) => <li key={ind}>{val}</li>)}
          </ul>
        </>
      );
    };
    ```
2.  **Using destructuring (preferred)**:

    ```js
    const About = ({ heading, category }) => {
      return (
        <>
          <h2>{heading}</h2>
          <ul>
            {category.map((val, ind) => <li key={ind}>{val}</li>)}
          </ul>
        </>
      );
    };
    ```

## State in Functional Components

* Used to manage dynamic data in a component.
* **State changes trigger re-rendering**.
*   Use the `useState` hook:

    ```js
    import { useState } from 'react';

    const [count, setCount] = useState(0);
    ```
*   **Reading state**:

    ```js
    {count}
    ```
*   **Updating state**:

    ```js
    setCount(val => val + 1);
    ```

#### Example: Counter Component

```js
import { useState } from 'react';

const Counter = () => {
  const [count, setCount] = useState(0);

  return (
    <>
      <h2>State Counter Example</h2>
      <p>The state counter is {count}</p>
      <button onClick={() => setCount(val => val + 1)}>++</button>
      <button onClick={() => setCount(val => val - 1)}>--</button>
      <button onClick={() => setCount(0)}>Reset</button>
    </>
  );
};

export default Counter;
```
