# JavaScript Objects — Backend Notes

> Focus: Backend data handling, APIs, reduce, symbols, destructuring

---

## 1️⃣ Object Literal

Object banane ka sab se common tareeqa.

```js
const user = {
  name: "Ali",
  age: 22
};
```

* `{}` se direct object banta hai
* Har baar naya object memory mein banta hai

```js
const a = {};
const b = {};
a === b // false
```

---

## 2️⃣ Singleton Object (Concept)

Singleton **syntax nahi**, **pattern** hai.

Matlab:

> poori app mein ek hi object instance use ho

```js
const config = {
  appName: "MyApp"
};

module.exports = config;
```

* Har file jo import karegi → same object milega
* Backend mein cache, config, DB connection ke liye use hota

---

## 3️⃣ Object Keys — Number vs String

JavaScript object ki keys **hamesha string hoti hain**.

```js
const box = {};
box[1] = 100;

console.log(box); // { "1": 100 }
```

Matlab:

```js
box[1] === box["1"] // true
```

---

## 4️⃣ Bracket vs Dot Notation

### Dot notation

```js
user.name
```

* Fixed key
* Simple access

### Bracket notation

```js
user["name"]
user[key]
```

* Dynamic key
* Variable ke through access

⚠️ Important:

```js
user[name] // name is a variable, NOT "name"
```

---

## 5️⃣ Symbols in Objects

Symbol ek **unique key** hoti hai.

```js
const mySymbol = Symbol("key");

const obj = {
  [mySymbol]: "secret"
};
```

* Symbol key string nahi hoti
* Dot notation se access nahi hoti

```js
obj[mySymbol] // works
obj.mySymbol  // undefined
```

---

## 6️⃣ Functions as Object Properties

JavaScript mein function bhi value hoti hai.

```js
const user = {
  greet: function() {
    console.log("Hello");
  }
};
```

Call karne ke tareeqay:

```js
user.greet();
user["greet"]();
```

---

## 7️⃣ Object Destructuring

Object se direct values nikaalna.

```js
const course = {
  name: "JS",
  price: 999
};

const { name, price } = course;
```

---

### Rename during destructuring

```js
const { courseInstructor: instructor } = course;
```

Matlab:

```
course.courseInstructor → instructor
```

---

## 8️⃣ Reduce with Objects (MOST IMPORTANT 🔥)

### Sum per key

```js
const totals = payments.reduce((box,p)=>{
  box[p.user] = (box[p.user] || 0) + p.amount;
  return box;
},{});
```

Logic:

* Agar key pehli dafa aaye → 0 se start
* Agar exist karti ho → add karo

---

### Grouping per key

```js
const grouped = logs.reduce((box,l)=>{
  if(!box[l.user]) box[l.user] = [];
  box[l.user].push(l.action);
  return box;
},{});
```

Logic:

* Agar array exist nahi → pehle banao
* Phir push karo

---

## 9️⃣ Why `if(!box[key])` is needed

```js
if(!box[user]){
  box[user] = [];
}
```

Reason:

* `.push()` sirf array pe chalta hai
* `undefined.push()` crash karta hai

---

## 10️⃣ Object vs Map

| Feature      | Object      | Map       |
| ------------ | ----------- | --------- |
| Key type     | string only | any type  |
| JSON support | ✔           | ❌         |
| Order        | unreliable  | preserved |
| Backend use  | API data    | caching   |

---

## 11️⃣ Backend Usage Summary

Objects backend mein use hote hain for:

* API responses
* Config
* Grouping DB data
* Caching
* Permission maps

---

## 🧠 Golden Rules

* Object keys are strings
* Bracket notation evaluates expression
* Reduce = register update
* `[]` → grouping
* `0` → summing

---

## 📌 Final Thought

> Backend objects are about **data transformation**, not UI state
