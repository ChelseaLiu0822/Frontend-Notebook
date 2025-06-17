# Page 1



**21. What is a closure?**

A closure is a function that **remembers** the variables from its lexical scope even when the function is executed outside that scope.

Example:

```javascript
function outer() {
  let counter = 0;
  return function() {
    counter++;
    return counter;
  }
}
let fn = outer();
console.log(fn()); // 1
console.log(fn()); // 2
```

`fn` retains access to `counter` even after `outer()` has returned.

**22. What are the common use cases of closures?**

* Implementing private variables
* Creating factory functions
* Managing asynchronous behavior
* Encapsulating logic in module patterns

Example - private variables:

```javascript
function createCounter() {
  let count = 0;
  return {
    increment() { count++; return count; },
    decrement() { count--; return count; },
    getCount() { return count; }
  }
}
```

**23. What are the potential pitfalls of closures?**

* **Memory leaks**: Retained references may prevent garbage collection.
* **Over-retention**: Keeping unnecessary variables alive.
* **In loops**: Closures inside loops may capture variables incorrectly if not scoped properly (e.g., use `let` instead of `var`).

Example:

```javascript
for (var i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), 0); // prints 3, 3, 3
}
```

Fix:

```javascript
for (let i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), 0); // prints 0, 1, 2
}
```

Would you like to continue with questions 24 and beyond?
