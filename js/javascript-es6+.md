# JavaScript ES6+

### 🟡 1. `let`, `const`, and `var`

#### ✅ `var` – Pre-ES6 (not recommended now)

```js
if (true) {
  var x = 10;
}
console.log(x); // 10 — because `var` is function-scoped or global
```

> `var` is **function-scoped** and allows **re-declaration**, which can cause bugs. Modern JavaScript avoids `var`.

***

#### ✅ `let` – Block-scoped variable

```js
if (true) {
  let x = 10;
  console.log(x); // 10
}
console.log(x); // ❌ ReferenceError: x is not defined
```

> `let` is **block-scoped**, meaning it only exists within `{}`. It can be reassigned but **cannot be re-declared** in the same scope.

```js
let y = 20;
y = 30;      // ✅ allowed
let y = 40;  // ❌ Error: y has already been declared
```

***

#### ✅ `const` – Block-scoped constant

```js
const PI = 3.14159;
PI = 3.14; // ❌ Error: Assignment to constant variable
```

> `const` is used for **read-only constants** like configuration variables, API keys, etc. It **cannot be reassigned or re-declared**.

***

### 🟡 2. Template Literals (`` `string with ${variables}` ``)

```js
const name = "Alice";
const age = 25;
console.log(`Hello, my name is ${name} and I am ${age} years old.`);
// Output: Hello, my name is Alice and I am 25 years old.
```

> Template literals allow **embedding variables** directly inside strings, using \*\*backticks (`)** and` ${}\` placeholders.

***

### 🟡 3. Arrow Functions

#### ✅ One-liner

```js
const add = (a, b) => a + b;
console.log(add(5, 10)); // 15
```

#### ✅ Multi-line function

```js
const multiply = (a, b) => {
  const result = a * b;
  return result;
};
```

> Arrow functions make code more concise. In one-liners, the `return` is implicit.

***

### 🟡 4. Spread Operator (`...`)

#### ✅ Array spread

```js
const nums = [1, 2, 3];
const newNums = [...nums, 4, 5];
console.log(newNums); // [1, 2, 3, 4, 5]
```

#### ✅ Object spread

```js
const user = { name: "Alice", age: 25 };
const updatedUser = { ...user, city: "New York", name: "Bob" };
console.log(updatedUser); 
// { name: 'Bob', age: 25, city: 'New York' }
```

> `...` spread copies existing arrays/objects and can add/override properties.

***

### 🟡 5. Rest Parameters

```js
function sum(...numbers) {
  let total = 0;
  numbers.forEach(num => total += num);
  return total;
}

console.log(sum(1, 2));       // 3
console.log(sum(1, 2, 3, 4)); // 10
```

> The `...` here gathers **any number of arguments into an array**.\
> **Note**: It must be the **last parameter**.

```js
function invalid(x, ...rest, y) {} 
// ❌ SyntaxError: Rest parameter must be last
```

***

### 🟡 6. Classes, Constructors, Inheritance

#### ✅ Class with Constructor and Methods

```js
class Car {
  constructor() {
    this.speed = 50;
  }

  accelerate() {
    this.speed += 70;
  }

  checkSpeed() {
    console.log(`Current speed: ${this.speed}`);
  }
}

const myCar = new Car();
myCar.checkSpeed();   // 50
myCar.accelerate();
myCar.checkSpeed();   // 120
```

#### ✅ Inheritance with `extends` and `super`

```js
class Person {
  constructor(firstName, lastName) {
    this.firstName = firstName;
    this.lastName = lastName;
  }

  fullName() {
    return `${this.firstName} ${this.lastName}`;
  }
}

class Employee extends Person {
  constructor(firstName, lastName, age) {
    super(firstName, lastName);
    this.age = age;
  }

  details() {
    console.log(`${this.fullName()} is ${this.age} years old.`);
  }
}

const emp = new Employee("John", "Smith", 30);
emp.details(); // John Smith is 30 years old
```

> `super()` calls the parent constructor. The child class can access both its own and inherited methods.

***

### 🟡 7. Array Methods: `map()`, `filter()`, `reduce()`

#### ✅ `map()`

```js
const nums = [1, 2, 3];
const doubled = nums.map(n => n * 2);
console.log(doubled); // [2, 4, 6]
```

> Applies a function to **each element** and returns a **new array**.

***

#### ✅ `filter()`

```js
const nums = [1, 2, 3, 4];
const even = nums.filter(n => n % 2 === 0);
console.log(even); // [2, 4]
```

> Returns only elements where the condition is `true`.

***

#### ✅ `reduce()`

```js
const nums = [1, 2, 3, 4];
const total = nums.reduce((acc, curr) => acc + curr, 0);
console.log(total); // 10
```

> Accumulates all elements into a **single value**.
