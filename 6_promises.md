## JS - Promises ✅

## 1. Promises

Promises represent a future value.
States:

* pending
* fulfilled
* rejected

### Basic usage

```js
getData().then(data => console.log(data));
```

### Sequential chaining

```js
step1()
.then(a => step2().then(b => console.log(a,b)));
```

### Error handling

```js
login(null)
.then(msg => console.log(msg))
.catch(err => console.log("Error:",err));
```

### Parallel execution

```js
Promise.all([getUsers(),getProducts()])
.then(([u,p]) => console.log(u,p));
```

### Direct resolve

```js
Promise.resolve("Hello").then(console.log);
```

---

Next Topic: Fetch API & then/catch
