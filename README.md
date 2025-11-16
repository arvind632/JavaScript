# Most Popular JavaScript Interview Questions and Answers

---

## 📌 1. What is Hoisting in JavaScript?

**Answer:**
Hoisting is JavaScript's default behavior of moving variable and function declarations to the top of their scope before execution.

* `var` is hoisted and initialized with `undefined`.
* `let` and `const` are hoisted but **not initialized** (Temporal Dead Zone).


## ⚙️ Why Does Hoisting Happen in JavaScript?

Hoisting occurs because JavaScript code is executed in **two phases** inside the **Execution Context**. 

### **1️⃣ Creation Phase
During the creation phase, JavaScript prepares memory before executing your code.

* Memory is allocated for **variables**, **functions**, and **arguments**.
* **Function declarations** are hoisted with their full definitions.
* Variables declared with **`var`** are initialized with `undefined`.
* Variables declared with **`let`** and **`const`** are placed in the **Temporal Dead Zone (TDZ)** — memory is allocated but **not initialized**.

This explains why accessing `let` or `const` before initialization causes a **ReferenceError**.

### **2️⃣ Execution Phase

After memory allocation, JavaScript runs the code **line by line**.

* Variable assignments happen in this phase.
* Functions execute when called.


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

## 🚀 3. What Is the Event Loop in JavaScript?

The **Event Loop** is a core part of the **JavaScript runtime environment**, responsible for managing **asynchronous operations** without blocking the main thread.
Because JavaScript is **single-threaded**, means it can run only **one task at a time** inside a single **call stack**.

However, in the real life applications, developers need to perform multiple operations such as:
* Fetching API data
* Login & authentication
* Add to cart / Checkout process
* Sending emails

These tasks must run smoothly **without blocking the main thread or freezing the user interface** — To solve this problem,  **Event Loop** was introduced.


Even though JavaScript executes in a single thread, and in modern applications require running multiple tasks **concurrently**.


## ⚙️ How the Event Loop Works

### **1️⃣ JavaScript runs line by line (synchronous) code in the Call Stack**

### **2️⃣ Asynchronous operations are handled by Web APIs / Node APIs**

Examples:

* `setTimeout`
* `fetch()`
* File system calls
* Event listeners

### **3️⃣ When async tasks finish, callbacks are moved to queues**

There are two main queues:

* **Callback Queue** → Timers, DOM events
* **Microtask Queue** → Promises, async/await

### **4️⃣ Event Loop monitors the Call Stack**

If the Call Stack is **empty**, the Event Loop push callback (Promis & setTimeout) into Call Stack for execution.
 
 So Event loop is continuously checks the callback queue and if there are any Callback then move it from callback queue to call stack and execute.

---

## 📌 4. What are Promises?

**Answer:**

A **Promise** is a JavaScript **object** that represents the *eventual result* of an asynchronous operation. It helps you write cleaner async code without falling into callback hell.

## 🧠 Why Do We Need Promises?

JavaScript is **single-threaded**, meaning it can execute only **one task at a time**.

But real-world applications require handling multiple asynchronous tasks such as:

* Database calls
* API requests
* File reading
* User authentication

Before promises, developers used **callbacks**, but nesting callbacks inside callbacks created complexity for understand and maintain the code:

### ❌ Callback Hell
* Complex to read
* Hard to debug
* Difficult to maintain

To solve this problem, **ES6 introduced Promises**, providing a cleaner and more structured way to handle async code.

### ✔ A Promise have 3 States

1. **Pending** – The operation has started but is not yet complete.
2. **Fulfilled** – The operation completed successfully.
3. **Rejected** – The operation failed.

---

## 🔧 How to use Promises
Promises are consumed using:
* **`.then()`** → to handle success
* **`.catch()`** → to handle errors

### 📎 Example

```js
getData()
  .then(result => console.log(result))
  .catch(error => console.log(error));
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
