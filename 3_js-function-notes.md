# JavaScript Functions — Backend Notes

## 1. What is a Function?

A function is a reusable block of code that performs a specific task.

```js
function greet(name) {
  return `Hello ${name}`;
}
```

Used heavily in backend because:

* routes are functions
* middleware are functions
* controllers are functions

---

## 2. Function Declaration vs Expression

### Declaration

```js
function add(a, b) {
  return a + b;
}
```

Hoisted (can call before definition)

### Expression

```js
const add = function(a, b) {
  return a + b;
};
```

Not hoisted

---

## 3. Arrow Functions

Short syntax + lexical `this`

```js
const add = (a, b) => a + b;
```

Backend usage: small callbacks

```js
app.get("/", (req, res) => res.send("OK"));
```

---

## 4. Parameters vs Arguments

```js
function login(email, password) {} // parameters
login("a@gmail.com", "123");     // arguments
```

---

## 5. Default Parameters

```js
function createUser(role = "user") {
  return role;
}
```

---

## 6. Return Statement

Stops execution and sends value back

```js
function check() {
  return true;
  console.log("never runs");
}
```

---

## 7. Callback Functions

Function passed inside another function

```js
function process(callback) {
  callback();
}

process(() => console.log("done"));
```

Backend: middleware, async operations

---

## 8. Higher Order Function

Function that accepts or returns another function

```js
function wrapper(fn) {
  return () => fn();
}
```

---

## 9. Function Scope

Variables declared inside function are not accessible outside

```js
function test() {
  let x = 10;
}
// console.log(x) ❌
```

---

## 10. Rest Parameters

Collect multiple arguments

```js
function sum(...nums) {
  return nums.reduce((a,b)=>a+b,0);
}
```

---

## Backend Mental Model

Every backend request flow:

```
Request → Middleware(fn) → Controller(fn) → Service(fn) → Response
```

Backend = composition of functions

---

Next Topic: IIFE (Immediately Invoked Function Expression)
