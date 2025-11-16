# Most Popular JavaScript Interview Questions and Answers (For Experienced Developers)

A curated list of the **most frequently asked JavaScript interview questions**, specifically tailored for **2+ to 10+ years experienced developers**. This guide covers advanced concepts, real-world problem‑solving, and tricky scenarios.

---

## 📌 1. What is Hoisting in JavaScript?

**Answer:**
Hoisting is JavaScript's default behavior of moving variable and function declarations to the top of their scope before execution.

* `var` is hoisted and initialized with `undefined`.
* `let` and `const` are hoisted but **not initialized** (Temporal Dead Zone).

```js
console.log(a); // undefined
var a = 10;
```

---

## 📌 2. Difference Between `var`, `let`, and `const`?

**Answer:**

| Feature   | var             | let   | const |
| --------- | --------------- | ----- | ----- |
| Scope     | Function        | Block | Block |
| Reassign  | Yes             | Yes   | No    |
| Redeclare | Yes             | No    | No    |
| Hoisting  | Yes (undefined) | TDZ   | TDZ   |

---

## 📌 3. What is the Event Loop?

**Answer:**
Event loop manages asynchronous operations in JavaScript. It continuously checks the **call stack** and **callback queue**, pushing tasks from the queue to stack when it becomes empty.

---

## 📌 4. What are Promises?

**Answer:**
A Promise represents an asynchronous operation.

* `pending`
* `fulfilled`
* `rejected`

```js
new Promise((resolve, reject) => {
  resolve("Done");
});
```

---

## 📌 5. Difference Between Promise and Async/Await?

**Answer:**

* Async/Await is syntactical sugar over Promises.
* Makes asynchronous code look synchronous.

```js
async function test(){
  const data = await fetch();
}
```

---

## 📌 6. What is Debouncing?

**Answer:**
Debouncing delays function execution until after a certain time has elapsed since the last call.

Used for: search boxes, window resize, scroll events.

```js
function debounce(fn, delay){
  let timer;
  return function(){
    clearTimeout(timer);
    timer = setTimeout(() => fn.apply(this, arguments), delay);
  }
}
```

---

## 📌 7. What is Throttling?

**Answer:**
Allows a function to be executed only once in a given interval.

```js
function throttle(fn, limit){
  let flag = true;
  return function(){
    if(flag){
      fn();
      flag = false;
      setTimeout(()=> flag = true, limit);
    }
  }
}
```

---

## 📌 8. What is Closure?

**Answer:**
Function that remembers its outer scope even after execution.

```js
function parent(){
  let x = 10;
  return function(){ console.log(x); }
}
```

---

## 📌 9. What is Currying?

**Answer:**
Transforming a function with multiple arguments into a sequence of functions.

```js
const add = a => b => c => a + b + c;
```

---

## 📌 10. Explain Call, Apply, Bind.

```js
function test(a){ console.log(this.name, a); }

test.call({name:"Arvind"}, 10);
test.apply({name:"Arvind"}, [10]);
const fn = test.bind({name:"Arvind"}); fn(10);
```

---

## 📌 11. What is Execution Context?

**Answer:**
Environment where JS code is executed.

* Global Execution Context
* Function Execution Context

Each context has:

* Memory (Variable Environment)
* Code Execution Phase

---

## 📌 12. What is First-Class Function?

Functions treated as variables.

```js
const fn = () => {}
```

---

## 📌 13. What are Arrow Functions? Differences?

* Lexical `this` (no own `this`)
* Cannot be used as constructor
* No `arguments` object

---

## 📌 14. What are Pure Functions?

A function that:

* Same input → same output
* No side effects

---

## 📌 15. What is a Callback Function?

Function passed as an argument to another function.

---

## 📌 16. Explain the JavaScript Memory Leak.

Common causes:

* Global variables
* Forgotten timers
* Closures holding unused references

---

## 📌 17. What is Prototypal Inheritance?

Objects inherit properties from a prototype.

```js
const obj = {a:10};
const child = Object.create(obj);
```

---

## 📌 18. What is Event Delegation?

Using a single parent listener to handle events of multiple children.

---

## 📌 19. What is the Difference Between `==` and `===`?

* `==` → compares after type conversion
* `===` → no conversion

---

## 📌 20. Deep Copy vs Shallow Copy

**Shallow Copy:**

```js
const obj2 = {...obj1};
```

**Deep Copy:**

```js
const deep = JSON.parse(JSON.stringify(obj));
```

---

## 📌 21. What is the `this` Keyword?

`this` refers to the object that is executing the function.

Depends on:

* Global
* Method
* Constructor
* Arrow function

---

## 📌 22. What is a Generator Function?

Function that can pause and resume.

```js
function* gen(){ yield 1; yield 2; }
```

---

## 📌 23. What is a Module in JavaScript?

Reusable pieces of code.

```js
import sum from "./sum.js";
```

---

## 📌 24. What is Optional Chaining?

```js
a?.b?.c
```

Prevents errors when accessing nested properties.

---

## 📌 25. What is the Purpose of `use strict`?

Enables strict mode — prevents silent errors.

---

## 🙌 Contribute

Pull requests are welcome! Enhance questions, add examples, or update advanced concepts.

---

## ⭐ Support

If this helped you, give it a **star ⭐** to help others find it!
