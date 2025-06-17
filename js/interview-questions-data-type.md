# ❓ Interview Questions Ⅰ: Data Type

## **1. What are the data types in JavaScript, and what are their differences?**

JavaScript has a total of eight data types: Undefined, Null, Boolean, Number, String, Object, Symbol, and BigInt.

Among them, Symbol and BigInt are newly added in ES6:

* Symbol represents a unique and immutable data type. It is mainly used to solve potential global variable conflicts.
* BigInt is a numeric data type that can represent integers of arbitrary precision. It allows safe storage and operation of large integers, even those beyond the safe integer range that Number can represent.

These data types can be categorized into primitive types and reference types:

* Stack: Primitive data types (Undefined, Null, Boolean, Number, String)
* Heap: Reference data types (objects, arrays, and functions)

The main difference between the two lies in **storage location**:

* Primitive types are stored directly in the stack (a simple data segment), take up less space, have a fixed size, and are frequently used, so they are stored in the stack.
* Reference types are stored in the heap as objects, take up more space, and have variable sizes. If stored in the stack, they would affect performance. Instead, a pointer is stored in the stack, which points to the starting address of the object in the heap. When the interpreter needs to retrieve a reference value, it first gets the address from the stack and then accesses the object in the heap.

The concept of stack and heap exists both in data structures and operating system memory:

* In data structures:
  * Stack uses a LIFO (last-in, first-out) method for data access.
  * Heap is a priority queue, where elements are sorted based on priority, such as size.
* In operating systems:
  * Stack memory is automatically allocated and released by the compiler. It stores function parameters and local variables. Its operation is similar to the stack in data structures.
  * Heap memory is usually allocated and released manually by developers. If not released, it may be collected by the garbage collector at program termination.

## **2. What are the ways to detect data types?**

**(1) typeof**

```javascript
console.log(typeof 2);               // number
console.log(typeof true);            // boolean
console.log(typeof 'str');           // string
console.log(typeof []);              // object
console.log(typeof function(){});    // function
console.log(typeof {});              // object
console.log(typeof undefined);       // undefined
console.log(typeof null);            // object
```

Arrays, objects, and null all return "object"; others are correctly identified.

**(2) instanceof**

`instanceof` can correctly determine the type of an object. **Its internal mechanism is to check whether the prototype of the constructor appears anywhere in the prototype chain of the object.**

```javascript
console.log(2 instanceof Number);            // false
console.log(true instanceof Boolean);        // false
console.log('str' instanceof String);        // false
console.log([] instanceof Array);            // true
console.log(function(){} instanceof Function); // true
console.log({} instanceof Object);           // true
```

`instanceof` **can only correctly determine reference types**, not primitive types. It checks whether the prototype property of the constructor exists in the object's prototype chain.

**(3) constructor**

```javascript
console.log((2).constructor === Number);         // true
console.log((true).constructor === Boolean);     // true
console.log(('str').constructor === String);     // true
console.log(([]).constructor === Array);         // true
console.log((function() {}).constructor === Function); // true
console.log(({}).constructor === Object);        // true
```

`constructor` serves two purposes: determining the type of data and allowing instances to access their constructors. Note: If an object is created with a modified prototype, `constructor` cannot be used to determine its type:

```javascript
function Fn(){};
Fn.prototype = new Array();
var f = new Fn();
console.log(f.constructor === Fn);    // false
console.log(f.constructor === Array); // true
```

**(4) Object.prototype.toString.call()**

`Object.prototype.toString.call()` uses the toString method of the Object prototype to determine the data type:

```javascript
var a = Object.prototype.toString;
console.log(a.call(2));
console.log(a.call(true));
console.log(a.call('str'));
console.log(a.call([]));
console.log(a.call(function(){}));
console.log(a.call({}));
console.log(a.call(undefined));
console.log(a.call(null));
```

The reason `obj.toString()` and `Object.prototype.toString.call(obj)` return different results is because array, function, etc., **are instances of Object and have overridden the toString method**. So when you call `toString()` on these types, their custom implementation is called. To get the actual object type, use the toString method on Object's prototype.

## **3. What are the ways to determine if a value is an array?**

* Use Object.prototype.toString.call():

```javascript
Object.prototype.toString.call(obj).slice(8, -1) === 'Array';
```

* Use prototype chain comparison:

```javascript
obj.__proto__ === Array.prototype;
```

* Use ES6's Array.isArray():

```javascript
Array.isArray(obj);
```

* Use instanceof:

```javascript
obj instanceof Array;
```

* Use Array.prototype.isPrototypeOf:

```javascript
Array.prototype.isPrototypeOf(obj);
```

## **4. What is the difference between null and undefined?**

First of all, both Undefined and Null are primitive data types, and each has only one value: undefined and null.

`undefined` means "not defined," while `null` means "empty object." Typically, a variable that has been declared but not assigned a value returns `undefined`, whereas `null` is often assigned to a variable that is expected to hold an object in the future as an initialization value.

`undefined` is not a reserved keyword in JavaScript, which means it can be used as a variable name. However, doing so is very risky and will affect the reliability of `undefined` checks. A safe way to obtain an `undefined` value is to use `void 0`.

When using `typeof` to check these two types, the result for `null` is "object." This is a historical bug. When using double equals `==` to compare the two, the result is true; with triple equals `===`, the result is false.

## **5. What is the result of `typeof null` and why?**

The result of `typeof null` is `object`.

In the first version of JavaScript, all values were stored in 32-bit units. Each unit contained a small **type tag (1-3 bits)** and the actual data value. The type tag was stored in the low-order bits of each unit and there were five data types:

```
000: object   - the stored data points to an object
  1: int      - the stored data is a 31-bit signed integer
010: double   - the stored data is a double-precision floating point number
100: string   - the stored data points to a string
110: boolean  - the stored data is a boolean value
```

If the lowest bit is 1, the type tag occupies only one bit; if the lowest bit is 0, the tag uses three bits to store the remaining types.

There are two special data types:

* `undefined` has a value of `(-2)^30` (a number beyond the integer range);
* `null` has a machine-level value of a NULL pointer (i.e., all bits set to 0).

That means the type tag for `null` is also `000`, which is the same as the tag for `object`. Therefore, `typeof null` returns `object`.

## **6. What is the implementation principle of the `instanceof` operator?**

The `instanceof` operator is used to check whether the `prototype` property of a constructor appears anywhere in the prototype chain of an object.

Example implementation:

```javascript
function myInstanceof(left, right) {
  let proto = Object.getPrototypeOf(left);  // get the prototype of the object
  let prototype = right.prototype;          // get the prototype of the constructor

  while (true) {
    if (!proto) return false;
    if (proto === prototype) return true;
    proto = Object.getPrototypeOf(proto);   // continue up the prototype chain
  }
}
```

## **7. Why does `0.1 + 0.2 !== 0.3`, and how can we make them equal?**

Example:

```javascript
let n1 = 0.1, n2 = 0.2;
console.log(n1 + n2);  // 0.30000000000000004
```

This result is not what we expect. To get `0.3`, we can convert it:

```javascript
(n1 + n2).toFixed(2); // Note: toFixed uses rounding
```

`toFixed(num)` rounds the number to the specified number of decimal places. But why does `0.1 + 0.2` result in such a number?

The computer stores numbers in binary, and both `0.1` and `0.2` have infinite repeating binary fractions:

* 0.1 in binary: `0.0001100110011001100...`
* 0.2 in binary: `0.00110011001100...`

These are recurring binary numbers. JavaScript uses the IEEE 754 standard for 64-bit floating-point numbers. The fractional part can only retain 52 bits, and the rest are truncated or rounded.

Thus, the result of `0.1 + 0.2` in binary, when converted back to decimal, becomes `0.30000000000000004`.

IEEE 754 format:

* 1 bit for sign (0 = positive)
* 11 bits for exponent
* 52 bits for fraction

To store exponent values (which can be negative), IEEE uses a **bias** of 1023. So an exponent of `-4` becomes `-4 + 1023 = 1019`, which in binary is `1111111011`.

So 0.1 is stored as:

```
0 1111111011 1001100110011001100110011001100110011001100110011001
```

To resolve `0.1 + 0.2 === 0.3`, use a precision threshold:

```javascript
function numberepsilon(arg1, arg2) {
  return Math.abs(arg1 - arg2) < Number.EPSILON;
}
console.log(numberepsilon(0.1 + 0.2, 0.3)); // true
```

`Number.EPSILON` is the difference between 1 and the smallest value greater than 1 that can be represented as a Number in JavaScript.

## **8. How to obtain a safe `undefined` value?**

Since `undefined` is just an identifier, it can be reassigned, which is dangerous for comparisons. The expression `void <expression>` always returns `undefined`. So `void 0` is a safe and reliable way to produce `undefined`.

## **9. What is the result of `typeof NaN`?**

`NaN` means "Not a Number" and is a **sentinel value** that indicates a numeric operation failed.

```javascript
typeof NaN; // "number"
```

`NaN` is a special value. It is **not equal to itself**, and `NaN !== NaN` is `true`. It is the only value in JavaScript that is **not reflexive**.

## **10. What is the difference between `isNaN` and `Number.isNaN`?**

* `isNaN()` converts the argument to a number first, so non-numeric values may return `true`, which can cause incorrect results.
* `Number.isNaN()` checks if the argument is strictly of type `number` and is `NaN`, without type coercion. It provides a more accurate way to detect `NaN`.

## **11. What are the coercion rules for the `==` operator?**

When using `==`, if the types of the <mark style="color:red;">**operands**</mark> are **not the same**, type <mark style="color:red;">**coercion**</mark> occurs. Assuming we are comparing `x` and `y`, the following process applies:

1. If the types are the same, directly compare the values.
2. If different, JavaScript attempts to coerce them to the same type:
3. If one is `null` and the other is `undefined`, return `true`.
4. If one is a `string` and the other is a `number`, convert the string to a number and compare.

```javascript
1 == '1'
     ↓
1 ==  1
```

5. If one is `boolean`, convert it to a number and then compare.

```javascript
'1' == true
       ↓
'1' == 1
       ↓
1 == 1 // true
```

6. If one is an object and the other is a `string`, `number`, or `symbol`, convert the object to a primitive value and compare.

```javascript
'1' == { name: 'js' }
       ↓
'1' == '[object Object]' // false
```

Flowchart for `==` coercion:

\[Image omitted here in text. Original shows the step-by-step decision flow for the `==` operator.]

The key takeaway: `==` involves implicit type conversion and can lead to unexpected results. Prefer `===` unless you are deliberately relying on coercion.

## **12. Rules for Converting Other Values to Strings**

* **Null and Undefined types**:\
  `null` is converted to `"null"`, and `undefined` is converted to `"undefined"`.
* **Boolean type**:\
  `true` is converted to `"true"`, and `false` is converted to `"false"`.
* **Number type**:\
  The value is directly converted to its string representation, though very small or very large numbers will use exponential notation.
* **Symbol type**:\
  The value is converted directly, but only explicit type coercion is allowed; implicit type coercion will throw an error.
* **Ordinary objects**:\
  Unless the object defines its own `toString()` method, `Object.prototype.toString()` is called, returning the value of its internal `[[Class]]` property (e.g., `"[object Object]"`). If the object has its own `toString()` method, that method will be called during string conversion, and its return value will be used.

## **13. Rules for Converting Other Values to Numbers**

* **Undefined type**:\
  Converts to `NaN`.
* **Null type**:\
  Converts to `0`.
* **Boolean type**:\
  `true` converts to `1`, and `false` converts to `0`.
* **String type**:\
  Conversion is the same as using the `Number()` function. If the string contains non-numeric characters, it converts to `NaN`; an empty string converts to `0`.
* **Symbol type**:\
  Cannot be converted to a number; attempting to do so throws an error.
*   **Objects (including arrays)**:\
    First converted to the corresponding primitive value. If the returned primitive value is not numeric, it is then coerced to a number following the rules above.

    To convert an object to its corresponding primitive value, the abstract operation `ToPrimitive` is used. This operation (via the internal `DefaultValue` method) first checks if the value has a `valueOf()` method. If it exists and returns a primitive, that value is used for coercion. If not, the `toString()` return value (if present) is used for coercion.

    If neither `valueOf()` nor `toString()` returns a primitive value, a `TypeError` is thrown.

## **14. Rules for Converting Other Values to Boolean**

The following are _falsy_ values:

* `undefined`
* `null`
* `false`
* `+0`, `-0`, and `NaN`
* `""` (empty string)

When coerced to a Boolean, these falsy values convert to `false`.

Logically, all values not included in the above list are considered _truthy_ and will convert to `true`.

## **15. Return values of `||` and `&&` operators**

`||` and `&&` first evaluate the first operand. If the operand is not a boolean value, it is converted to a boolean before the evaluation.

For `||`, if the evaluation result is `true`, it returns the value of the first operand. If it is `false`, it returns the value of the second operand.

For `&&`, it is the opposite: if the evaluation result is `true`, it returns the value of the second operand. If it is `false`, it returns the value of the first operand.

`||` and `&&` return the value of one of their operands, not the result of the boolean evaluation.

## **16. Differences between `Object.is()`, `===`, and `==`**

When using the double equals (`==`) for equality comparison, if the two operands have different types, type coercion is performed before comparing.

When using the triple equals (`===`), if the two operands have different types, no type coercion is performed, and `false` is returned directly.

When using `Object.is` for comparison, it behaves the same as `===` in most cases, but it handles some special cases differently — for example, `-0` and `+0` are not considered equal, and two `NaN` values are considered equal.

## 17. What are wrapper types in JavaScript?

In JavaScript, primitive types do not have properties or methods. However, for convenience, when accessing properties or methods of primitive values, JavaScript will automatically and implicitly convert the primitive value into an object behind the scenes. For example:

```javascript
const a = "abc"
a.length; // 3
a.toUpperCase(); // "ABC"
```

When accessing `'abc'.length`, JavaScript converts `'abc'` behind the scenes to `String('abc')`, and then accesses its `length` property.

JavaScript can also explicitly convert primitive types into wrapper types using the `Object` function:

```javascript
var a = 'abc'
Object(a) // String {"abc"}
```

You can also use the `valueOf` method to unwrap the wrapper type back to the primitive type:

```javascript
var a = 'abc'
var b = Object(a)
var c = b.valueOf() // 'abc'
```

See what the following code will output:

```javascript
var a = new Boolean(false);
if (!a) {
  console.log("Oops"); // never runs
}
```

The code will not print anything because although the underlying primitive value is `false`, once wrapped as a wrapper type, it becomes an object. Since objects are truthy, the `if` condition is `false`, so the loop body does not execute.

## 18. How does implicit type conversion work in JavaScript?

First, let's introduce the `ToPrimitive` method. This is an internal method that every value in JavaScript implicitly has, used to convert a value (whether it's a primitive value or an object) into a primitive value. If the value is already a primitive, it is returned as-is. If it's an object, it works like this:

```javascript
/**
 * @obj The object to convert
 * @type The expected result type
 */
ToPrimitive(obj, type)
```

The `type` can be `"number"` or `"string"`.

#### (1) When `type` is `"number"`:

* Call `obj.valueOf()`. If it returns a primitive, return it. Otherwise, move to the next step.
* Call `obj.toString()`. If it returns a primitive, return it. Otherwise, move to the next step.
* Throw a `TypeError`.

#### (2) When `type` is `"string"`:

* Call `obj.toString()`. If it returns a primitive, return it. Otherwise, move to the next step.
* Call `obj.valueOf()`. If it returns a primitive, return it. Otherwise, move to the next step.
* Throw a `TypeError`.

The main difference between the two is the order of calling `toString` and `valueOf`. By default:

* If the object is a `Date`, `type` defaults to `"string"`.
* Otherwise, `type` defaults to `"number"`.

To summarize these rules for non-Date objects, converting to a primitive type can be simplified as:

```javascript
var objToNumber = value => Number(value.valueOf().toString())
objToNumber([]) === 0
objToNumber({}) === NaN
```

In JavaScript, implicit type conversion mainly occurs with operators like `+`, `-`, `*`, `/`, `==`, `>`, `<`. These operators can only operate on primitive types, so the first step is to convert both operands to primitive types using `ToPrimitive`, and then proceed with the operation.

Below are the implicit conversion rules for primitive values under different operators (for objects, `ToPrimitive` will convert them to primitive first, and then these rules apply):

***

#### `+` operator

If either operand is a string, both will be implicitly converted to strings. Otherwise, both are converted to numbers.

```javascript
1 + '23' // '123'
1 + false // 1
1 + Symbol() // Uncaught TypeError: Cannot convert a Symbol value to a number
'1' + false // '1false'
false + true // 1
```

***

#### `-`, `*`, `/` operators

`NaN` is treated as a number too.

```javascript
1 * '23' // 23
1 * false // 0
1 / 'aa' // NaN
```

***

#### `==` operator

Both operands are converted to numbers as much as possible:

```javascript
3 == true // false, 3 → 3, true → 1
'0' == false // true, '0' → 0, false → 0
'0' == 0 // true, '0' → 0
```

***

#### `<`, `>` operators

If both are strings, compare alphabetically:

```javascript
'ca' < 'bd' // false
'a' < 'b' // true
```

Otherwise, convert to numbers and compare:

```javascript
'12' < 13 // true
false > -1 // true
```

***

#### For objects

Objects are first converted to primitives via `ToPrimitive`, then type conversion proceeds:

```javascript
var a = {}
a > 2 // false
```

Conversion process:

```javascript
a.valueOf() // {}, still an object, next step
a.toString() // "[object Object]"
Number(a.toString()) // NaN
NaN > 2 // false
```

Another example:

```javascript
var a = { name: 'Jack' }
var b = { age: 18 }
a + b // "[object Object][object Object]"
```

Process:

```javascript
a.valueOf() // {}, still an object
a.toString() // "[object Object]"
b.valueOf() // {}, still an object
b.toString() // "[object Object]"
a + b // "[object Object][object Object]"
```

## 19. When does the `+` operator perform string concatenation?

According to the ES5 specification, if either operand is a string or can be converted to a string through the following steps, the `+` operator will perform concatenation. If one of the operands is an object (including arrays), `ToPrimitive` is called first. This `ToPrimitive` operation internally calls `[[DefaultValue]]` with `Number` as the preferred type. If it cannot be converted to a string, it will be converted to a number for arithmetic calculation.

In short:\
If either operand of `+` is a string (or is ultimately converted to a string through the above process), string concatenation is performed.\
Otherwise, numeric addition is performed.

For operators other than `+`, as long as one operand is a number, the other operand will be converted to a number.

## 20. Why was the BigInt proposal introduced?

In JavaScript, `Number.MAX_SAFE_INTEGER` represents the largest safe integer, which is `9007199254740991`. Calculations within this range will not suffer from precision loss (excluding decimals). However, once this range is exceeded, JavaScript calculations can become inaccurate. This has traditionally required third-party libraries to handle large integer computations. Therefore, the BigInt proposal was introduced to address this issue natively.

## 21. Is `Object.assign` or the spread operator a deep copy or a shallow copy? What’s the difference between them?

Both `Object.assign` and the spread operator (`...`) perform **shallow copies**, not deep copies.

#### What is a shallow copy?

A shallow copy only copies the property values at the first level. If a property’s value is a reference (such as an object or array), the reference is copied, not the actual nested object. This means changes to nested objects will affect both the original and the copied object.

#### Example:

```javascript
const obj = { a: 1, b: { c: 2 } };

const shallow1 = Object.assign({}, obj);
const shallow2 = { ...obj };

shallow1.b.c = 42;
console.log(obj.b.c); // 42 — nested object is shared
console.log(shallow2.b.c); // 42 — same nested object is shared
```

***

#### What is the difference between `Object.assign` and the spread operator?

* **Syntax difference**:
  * `Object.assign({}, obj)` copies properties into a target object.
  * `{ ...obj }` creates a new object with the copied properties.
* **Prototype**:
  * `Object.assign` copies enumerable own properties, including symbol properties.
  * The spread operator copies enumerable own properties **except for properties keyed by symbols**.
* **Usage flexibility**:
  * Spread syntax is more concise and often preferred for creating new objects in modern JavaScript.
  * `Object.assign` allows merging multiple source objects into a target object.

